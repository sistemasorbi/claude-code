# Módulo 14: Integración de APIs y Tareas Web

**Objetivo:** Domina el trabajo con APIs externas y recursos web usando Claude Code

**Tiempo Estimado:** 40-50 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Usar WebSearch de Claude Code para encontrar documentación
- Obtener documentación de APIs con WebFetch
- Integrar APIs de terceros en tus proyectos
- Manejar diferentes métodos de autenticación
- Implementar rate limiting y cuotas
- Manejar errores de API con gracia
- Construir wrappers completos de API

---

## Lección 1: Usando WebSearch para Desarrollo

### Encontrando Documentación

**Busca documentación oficial:**
```
Busca la última documentación de la API de Stripe
```

```
Encuentra la documentación oficial de React para hooks
```

```
Busca mejores prácticas de middleware en Node.js Express
```

---

### Encontrando Soluciones

**Busca problemas específicos:**
```
Busca cómo arreglar "error CORS en API Express"
```

```
Encuentra soluciones para "manejo de expiración de token JWT"
```

```
Busca "prevenir SQL injection en Node.js"
```

---

### Investigando Librerías

```
Busca los mejores paquetes npm para:
- Enviar emails
- Generar PDFs
- Procesar imágenes
- Colas de trabajos en segundo plano
```

---

## Lección 2: Usando WebFetch para Documentación de APIs

### Obteniendo y Entendiendo Docs

```
Obtén la documentación de https://docs.stripe.com/api/customers/create
y crea una función TypeScript para crear un cliente
```

```
Obtén docs de https://api.github.com
y muéstrame cómo listar repositorios para un usuario
```

---

### Generando Código desde Docs

```
Obtén la documentación de la API de SendGrid
y crea una clase de servicio de email completa con:
- Método para enviar email
- Método para enviar email con plantilla
- Manejo de errores apropiado
- Tipos TypeScript
```

---

## Lección 3: Integrando APIs REST

### Integración Simple de API

**Ejemplo: API del Clima**

```
Crea un servicio del clima que integre con la API de OpenWeatherMap:
- Acepta nombre de ciudad como entrada
- Llama a la API del clima
- Parsea y devuelve temperatura, condiciones, humedad
- Maneja errores de API
- Cachea resultados por 10 minutos
- Incluye tipos TypeScript
```

**Claude Code creará:**

```typescript
// weather.service.ts
import axios from 'axios';

interface WeatherData {
  temperature: number;
  conditions: string;
  humidity: number;
  city: string;
}

class WeatherService {
  private apiKey: string;
  private cache: Map<string, { data: WeatherData; expiry: number }>;

  constructor(apiKey: string) {
    this.apiKey = apiKey;
    this.cache = new Map();
  }

  async getWeather(city: string): Promise<WeatherData> {
    // Verifica caché primero
    const cached = this.cache.get(city);
    if (cached && cached.expiry > Date.now()) {
      return cached.data;
    }

    try {
      const response = await axios.get(
        'https://api.openweathermap.org/data/2.5/weather',
        {
          params: {
            q: city,
            appid: this.apiKey,
            units: 'metric'
          }
        }
      );

      const data: WeatherData = {
        temperature: response.data.main.temp,
        conditions: response.data.weather[0].description,
        humidity: response.data.main.humidity,
        city: response.data.name
      };

      // Cachea por 10 minutos
      this.cache.set(city, {
        data,
        expiry: Date.now() + 10 * 60 * 1000
      });

      return data;
    } catch (error) {
      if (axios.isAxiosError(error)) {
        if (error.response?.status === 404) {
          throw new Error(`Ciudad "${city}" no encontrada`);
        }
        throw new Error(`Error de API del clima: ${error.message}`);
      }
      throw error;
    }
  }
}

export default WeatherService;
```

---

### Integración Compleja de API

```
Crea un cliente de API de GitHub con:
- Autenticación OAuth
- Métodos para:
  * Listar repositorios del usuario
  * Obtener detalles de repositorio
  * Crear issue
  * Listar y crear pull requests
- Soporte de paginación
- Manejo de rate limit
- Manejo comprehensivo de errores
- Tipos TypeScript completos
```

---

## Lección 4: Métodos de Autenticación

### Autenticación con API Key

**API key simple en header:**

```
Crea un cliente de email SendGrid que:
- Use API key desde variable de entorno
- Tenga método para enviar email
- Tenga método para enviar con plantilla
- Valide direcciones de email
- Maneje errores de SendGrid apropiadamente
```

---

### Integración OAuth 2.0

```
Implementa flujo OAuth de GitHub:
1. Genera URL de autorización
2. Maneja callback con código de auth
3. Intercambia código por access token
4. Almacena token de forma segura
5. Usa token para solicitudes de API
6. Maneja refresh de token
```

**Claude Code creará el flujo OAuth completo con mejores prácticas de seguridad.**

---

### Gestión de Token JWT

```
Crea un cliente de API para nuestro servicio interno que:
- Haga login para obtener token JWT
- Almacene token de forma segura (no en texto plano)
- Incluya token en todas las solicitudes autenticadas
- Maneje expiración de token
- Refresque token automáticamente
- Haga logout y limpie tokens
```

---

## Lección 5: Rate Limiting

### Implementando Rate Limiting del Lado Cliente

```
Crea una clase de rate limiter que:
- Limite llamadas a API a X por segundo
- Encole solicitudes cuando se alcance el límite
- Procese cola automáticamente
- Tenga backoff exponencial para reintentos
- Respete headers de rate limit de API
- Registre cuando se alcancen límites
```

**Ejemplo de implementación:**

```typescript
class APIRateLimiter {
  private queue: Array<() => Promise<any>> = [];
  private processing = false;
  private requestsPerSecond: number;
  private lastRequestTime: number = 0;

  constructor(requestsPerSecond: number) {
    this.requestsPerSecond = requestsPerSecond;
  }

  async execute<T>(fn: () => Promise<T>): Promise<T> {
    return new Promise((resolve, reject) => {
      this.queue.push(async () => {
        try {
          const result = await fn();
          resolve(result);
        } catch (error) {
          reject(error);
        }
      });

      if (!this.processing) {
        this.processQueue();
      }
    });
  }

  private async processQueue() {
    this.processing = true;

    while (this.queue.length > 0) {
      const now = Date.now();
      const timeSinceLastRequest = now - this.lastRequestTime;
      const minInterval = 1000 / this.requestsPerSecond;

      if (timeSinceLastRequest < minInterval) {
        await this.sleep(minInterval - timeSinceLastRequest);
      }

      const request = this.queue.shift();
      if (request) {
        this.lastRequestTime = Date.now();
        await request();
      }
    }

    this.processing = false;
  }

  private sleep(ms: number): Promise<void> {
    return new Promise(resolve => setTimeout(resolve, ms));
  }
}
```

---

## Lección 6: Manejo de Errores

### Manejo Robusto de Errores de API

```
Crea manejo comprehensivo de errores para llamadas a API que:
- Distinga entre tipos de error:
  * Errores de red (sin conexión)
  * Errores 4xx de cliente (bad request, unauthorized, etc.)
  * Errores 5xx de servidor (problemas temporales)
  * Errores de timeout
- Reintente errores apropiados (5xx, timeouts)
- No reintente errores de cliente (4xx)
- Use backoff exponencial para reintentos
- Registre todos los errores con contexto
- Devuelva mensajes de error amigables
```

---

### Lógica de Reintento con Backoff Exponencial

```typescript
async function fetchWithRetry<T>(
  url: string,
  options: RequestInit = {},
  maxRetries: number = 3
): Promise<T> {
  for (let attempt = 0; attempt < maxRetries; attempt++) {
    try {
      const response = await fetch(url, options);

      // No reintentar errores de cliente
      if (response.status >= 400 && response.status < 500) {
        const error = await response.text();
        throw new Error(`Error de cliente ${response.status}: ${error}`);
      }

      // Reintentar errores de servidor
      if (response.status >= 500) {
        if (attempt === maxRetries - 1) {
          throw new Error(`Error de servidor ${response.status} después de ${maxRetries} intentos`);
        }
        // Esperar antes de reintentar (backoff exponencial)
        await sleep(Math.pow(2, attempt) * 1000);
        continue;
      }

      // Éxito
      return await response.json();

    } catch (error) {
      if (attempt === maxRetries - 1) {
        throw error;
      }
      // Error de red - reintentar con backoff
      await sleep(Math.pow(2, attempt) * 1000);
    }
  }

  throw new Error('Máximo de reintentos excedido');
}

function sleep(ms: number): Promise<void> {
  return new Promise(resolve => setTimeout(resolve, ms));
}
```

---

## Lección 7: Construyendo Wrappers Completos de API

### Cliente de API Listo para Producción

```
Construye un wrapper completo de API de Stripe con:

Características Principales:
- Gestión de clientes (crear, obtener, actualizar, eliminar)
- Procesamiento de pagos
- Manejo de suscripciones
- Verificación de webhooks

Infraestructura:
- Tipos TypeScript para todos los endpoints
- Manejo de errores apropiado con clases de error personalizadas
- Lógica de reintento para fallos transitorios
- Rate limiting
- Logging de solicitud/respuesta
- Claves de idempotencia para reintentos seguros
- Tests comprehensivos con respuestas mockeadas

Seguridad:
- API key desde entorno
- Validación de entrada
- Verificación de firma de webhook
```

---

## Práctica Práctica

### Ejercicio 1: App CLI del Clima

**Tarea:** Construye una herramienta de línea de comandos del clima

```
Crea una app CLI del clima que:
1. Tome nombre de ciudad como argumento
2. Llame a API de OpenWeatherMap
3. Muestre clima actual de forma bonita
4. Muestre pronóstico de 5 días
5. Cachee respuestas
6. Maneje errores con gracia
7. Tenga salida colorida

Ejemplo de uso:
node weather.js "Madrid"
```

---

### Ejercicio 2: Herramienta CLI de GitHub

**Tarea:** Construye un cliente de GitHub

```
Crea una herramienta CLI de GitHub que:
- Se autentique con token de acceso personal
- Liste tus repositorios
- Muestre issues abiertos para un repo
- Cree nuevos issues
- Liste pull requests
- Cree pull requests
- Todo con manejo de errores apropiado y formato bonito
```

---

### Ejercicio 3: Dashboard Multi-API

**Tarea:** Combina múltiples APIs

```
Construye un servicio de resumen diario que obtenga:
- Clima de OpenWeatherMap
- Noticias principales de NewsAPI
- Precios de acciones de Alpha Vantage
- Tu actividad de GitHub desde API de GitHub

Combina todo en un resumen diario
Maneja fallo de APIs individuales con gracia
Cachea cada uno apropiadamente
Envía como email o muestra en terminal
```

---

## Lista de Verificación del Módulo 14

Antes de pasar al Módulo 15, asegúrate de poder:

- [ ] Usar WebSearch para encontrar documentación
- [ ] Usar WebFetch para obtener docs de API
- [ ] Integrar APIs REST
- [ ] Manejar diferentes métodos de autenticación
- [ ] Implementar rate limiting
- [ ] Manejar errores de API con lógica de reintento
- [ ] Construir wrappers completos de API
- [ ] Testear integraciones de API apropiadamente

---

## Mejores Prácticas

**Integración de API:**
- ✅ Usa variables de entorno para API keys
- ✅ Implementa manejo de errores apropiado
- ✅ Añade lógica de reintento para fallos transitorios
- ✅ Cachea cuando sea apropiado
- ✅ Respeta rate limits
- ✅ Registra interacciones de API
- ✅ Valida todas las entradas
- ✅ Usa TypeScript para type safety

**Seguridad:**
- ✅ Nunca hagas commit de API keys
- ✅ Usa solo HTTPS
- ✅ Valida respuestas de API
- ✅ Sanitiza antes de usar datos
- ✅ Maneja tokens de forma segura

**Testing:**
- ✅ Mockea respuestas de API en tests
- ✅ Testea escenarios de error
- ✅ Testea rate limiting
- ✅ Testea flujos de autenticación

---

## Errores Comunes a Evitar

❌ Hardcodear API keys
❌ No manejar errores
❌ Ignorar rate limits
❌ No usar tipos TypeScript
❌ Exponer datos sensibles en logs
❌ No cachear solicitudes costosas
❌ No validar respuestas de API

---

## ¿Qué Sigue?

¡Excelente trabajo! Ahora puedes integrar con cualquier API y construir integraciones poderosas.

**¿Listo para el Módulo 15?** El módulo final cubre desplegar tus aplicaciones a producción.

---

*¡Módulo 14 Completado!*
