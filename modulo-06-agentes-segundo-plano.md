# Módulo 6: Usando Agentes en Segundo Plano

**Objetivo:** Aprende a usar agentes especializados para tareas complejas

**Tiempo Estimado:** 35-45 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Entender qué son los agentes y cómo funcionan
- Usar el agente Explore para navegar bases de código
- Usar el agente Plan para diseñar implementaciones
- Usar agentes de propósito general para tareas complejas
- Saber cuándo usar agentes vs herramientas simples
- Ejecutar múltiples tareas en paralelo

---

## Lección 1: ¿Qué Son los Agentes?

### Entendiendo los Agentes

Los **agentes** son asistentes de IA especializados que pueden manejar tareas complejas de forma autónoma. A diferencia de las herramientas simples, los agentes pueden:

- Tomar múltiples pasos para completar una tarea
- Tomar decisiones basadas en lo que encuentran
- Usar múltiples herramientas en secuencia
- Trabajar en segundo plano mientras tú continúas

### Analogía

**Herramientas simples** = Dar instrucciones paso a paso
- "Lee este archivo"
- "Busca esta palabra"
- "Edita esta línea"

**Agentes** = Delegar una tarea completa
- "Explora este proyecto y dime cómo funciona la autenticación"
- "Planifica cómo implementar esta característica"

---

## Lección 2: El Agente Explore (Explorar)

### Propósito

El agente Explore está diseñado para:
- Navegar y entender bases de código
- Encontrar archivos y patrones relevantes
- Responder preguntas sobre el código
- Crear mapas mentales del proyecto

### Cuándo Usarlo

Usa el agente Explore cuando:
- Te unes a un proyecto nuevo
- Necesitas encontrar dónde está implementado algo
- Quieres entender la arquitectura
- Buscas patrones específicos en el código

### Ejemplos de Uso

**Exploración general:**
```
Usa el agente Explore para darme un resumen completo de la estructura de este proyecto
```

**Búsqueda específica:**
```
Explora el código y encuentra dónde se implementa el sistema de caché
```

**Análisis de arquitectura:**
```
Explora este proyecto y explícame su arquitectura, incluyendo cómo fluyen los datos
```

**Encontrar patrones:**
```
Explora el código y muéstrame cómo se manejan los errores en todo el proyecto
```

### Lo Que el Agente Hace

Cuando pides una exploración, el agente:

1. **Mapea la estructura** - Lee directorios y archivos
2. **Identifica archivos clave** - package.json, README, configuraciones
3. **Analiza el código** - Lee archivos importantes
4. **Busca patrones** - Encuentra conexiones y flujos
5. **Genera un informe** - Te da un resumen comprensible

---

## Lección 3: El Agente Plan (Planificar)

### Propósito

El agente Plan está diseñado para:
- Diseñar estrategias de implementación
- Identificar archivos que necesitan cambios
- Considerar trade-offs arquitectónicos
- Crear planes paso a paso

### Cuándo Usarlo

Usa el agente Plan cuando:
- Vas a implementar una característica grande
- Necesitas refactorizar código extenso
- Quieres considerar diferentes enfoques
- Necesitas un plan antes de escribir código

### Ejemplos de Uso

**Planificar una característica:**
```
Usa el agente Plan para diseñar cómo implementar un sistema de notificaciones push
```

**Planificar refactorización:**
```
Planifica cómo migrar esta aplicación de JavaScript a TypeScript
```

**Planificar integración:**
```
Planifica cómo integrar pagos con Stripe en esta aplicación
```

### Lo Que Recibirás

Un plan típico incluye:

1. **Resumen del enfoque** - La estrategia general
2. **Archivos a crear/modificar** - Lista de cambios necesarios
3. **Orden de implementación** - Pasos secuenciales
4. **Consideraciones** - Trade-offs y decisiones
5. **Dependencias** - Lo que necesitas antes de empezar

---

## Lección 4: Agente de Propósito General

### Propósito

El agente de propósito general puede:
- Manejar tareas de múltiples pasos
- Investigar y resolver problemas
- Ejecutar secuencias de acciones
- Adaptarse según lo que encuentra

### Cuándo Usarlo

Usa este agente cuando:
- La tarea requiere investigación y acción
- Necesitas que tome decisiones en el camino
- La tarea tiene múltiples fases
- No estás seguro de qué herramientas se necesitan

### Ejemplos de Uso

**Investigación y acción:**
```
Investiga por qué los tests están fallando y corrígelos
```

**Múltiples pasos:**
```
Analiza las dependencias desactualizadas, actualiza las que sean seguras, y ejecuta los tests
```

**Resolución de problemas:**
```
Encuentra y corrige todos los problemas de seguridad en el código de autenticación
```

---

## Lección 5: Ejecutando Tareas en Segundo Plano

### Cómo Funciona

Algunas tareas pueden ejecutarse en segundo plano mientras continúas trabajando:

```
Ejecuta los tests en segundo plano y avísame cuando terminen
```

```
Inicia el servidor de desarrollo en segundo plano
```

### Ver Tareas en Ejecución

Usa el comando:
```
/tasks
```

Verás algo como:
```
Tareas en ejecución:
1. [ejecutando] Tests unitarios (2 min)
2. [ejecutando] Servidor de desarrollo (activo)
```

### Obtener Resultados

Cuando una tarea en segundo plano termina, puedes pedir los resultados:

```
¿Terminaron los tests? Muéstrame los resultados
```

---

## Lección 6: Cuándo Usar Cada Enfoque

### Usa Herramientas Simples Cuando:

- Conoces exactamente qué archivo leer/editar
- La tarea es directa y de un solo paso
- Quieres control total sobre cada acción
- La tarea es rápida y simple

**Ejemplos:**
- "Lee server.js"
- "Añade esta línea al archivo config.js"
- "Ejecuta npm test"

### Usa Agentes Cuando:

- La tarea requiere exploración o investigación
- Necesitas múltiples pasos coordinados
- No sabes exactamente dónde buscar
- Quieres delegar una tarea completa

**Ejemplos:**
- "Explora este proyecto y encuentra los endpoints de la API"
- "Planifica cómo añadir autenticación"
- "Investiga y corrige este bug"

### Tabla de Decisión

| Situación | Usar |
|-----------|------|
| Leer un archivo específico | Herramienta Read |
| Encontrar algo en el proyecto | Agente Explore |
| Editar una línea conocida | Herramienta Edit |
| Implementar característica nueva | Agente Plan primero |
| Ejecutar un comando | Herramienta Bash |
| Investigar un problema | Agente general |

---

## Lección 7: Mejores Prácticas con Agentes

### Da Contexto Claro

**Menos efectivo:**
```
Explora el código
```

**Más efectivo:**
```
Explora el código enfocándote en cómo se maneja la autenticación y autorización de usuarios
```

### Especifica el Nivel de Detalle

```
Explora el proyecto de forma rápida y dame un resumen de alto nivel
```

vs

```
Explora el proyecto exhaustivamente y documenta cada módulo y sus dependencias
```

### Combina con Seguimiento

Después de un agente, puedes hacer preguntas de seguimiento:

```
[Después de exploración]
Basándote en lo que encontraste, ¿cuál sería la mejor forma de añadir tests?
```

### Verifica los Planes

Después de recibir un plan, revísalo:

```
¿Hay algún riesgo o consideración que no hayas mencionado en el plan?
```

---

## Ejercicio Práctico

### Ejercicio 1: Exploración

En un proyecto existente:

```
Usa el agente Explore para:
1. Darme un resumen de la arquitectura
2. Identificar los archivos más importantes
3. Explicar el flujo de datos principal
```

### Ejercicio 2: Planificación

Con el mismo proyecto:

```
Usa el agente Plan para diseñar cómo añadir:
- Un sistema de logging
- Que registre todas las llamadas a la API
- Con diferentes niveles (info, warning, error)
- Que guarde logs en archivos
```

### Ejercicio 3: Tarea Compleja

```
Ejecuta una tarea que:
1. Encuentre todos los console.log en el código
2. Los reemplace por llamadas a un logger
3. Me muestre un resumen de los cambios
```

---

## Comandos Útiles

### Para Agentes

```
Usa un agente para [tarea]
```

```
Explora [enfoque específico]
```

```
Planifica [característica/cambio]
```

### Para Segundo Plano

```
/tasks                    # Ver tareas activas
Ejecuta [X] en segundo plano
¿Cómo van las tareas en segundo plano?
```

---

## Lista de Verificación del Módulo 6

Verifica que puedas:

- [ ] Explicar la diferencia entre herramientas y agentes
- [ ] Usar el agente Explore para entender código
- [ ] Usar el agente Plan para diseñar implementaciones
- [ ] Ejecutar tareas en segundo plano
- [ ] Decidir cuándo usar agentes vs herramientas
- [ ] Combinar agentes con seguimiento efectivo

---

## Resumen

| Agente | Propósito | Cuándo Usar |
|--------|-----------|-------------|
| Explore | Navegar y entender código | Proyectos nuevos, buscar implementaciones |
| Plan | Diseñar estrategias | Antes de implementar características grandes |
| General | Tareas complejas | Investigación, múltiples pasos |

---

## ¿Qué Sigue?

¡Excelente! Ahora sabes usar agentes para tareas complejas.

En el **Módulo 7**, aprenderemos sobre operaciones Git y control de versiones con Claude Code - commits, ramas, pull requests, y más.

---

*¡Módulo 6 Completado!*
