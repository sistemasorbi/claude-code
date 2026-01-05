# Módulo 11: Servidores MCP - Extendiendo Claude Code

**Objetivo:** Aprende a usar y crear servidores del Protocolo de Contexto de Modelo (MCP) para extender las capacidades de Claude Code

**Tiempo Estimado:** 40-50 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Entender qué es MCP y por qué es poderoso
- Saber cómo instalar y configurar servidores MCP
- Usar servidores MCP comunes (sistema de archivos, base de datos, etc.)
- Crear tu propio servidor MCP personalizado
- Integrar servicios de terceros con MCP

---

## Lección 1: Entendiendo MCP

### ¿Qué es MCP?

**Protocolo de Contexto de Modelo (MCP)** es una forma estándar de dar a Claude Code acceso a datos y servicios externos.

**Piensa en los servidores MCP como plugins que:**
- Dan a Claude Code nuevas capacidades
- Se conectan a bases de datos, APIs, sistemas de archivos
- Proporcionan conocimiento específico del dominio
- Extienden lo que Claude Code puede hacer

---

### ¿Por Qué Usar MCP?

**Sin MCP:**
- Limitado a herramientas integradas
- No puede acceder a tus bases de datos directamente
- No puede integrarse con tus servicios
- Contexto limitado sobre tus sistemas

**Con MCP:**
- Accede a bases de datos directamente
- Conéctate a tus herramientas (GitHub, Notion, etc.)
- Integraciones personalizadas
- Extensibilidad ilimitada

---

## Lección 2: Instalando Servidores MCP

### Archivo de Configuración

**Los servidores MCP se configuran en:**
```
~/.config/claude/config.json
```

**Ejemplo de configuración:**
```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/ruta/al/directorio/permitido"]
    }
  }
}
```

---

### Instalando Tu Primer Servidor MCP

**Pide ayuda a Claude Code:**

```
Ayúdame a instalar el servidor MCP de sistema de archivos.
Quiero darte acceso a mi directorio /home/usuario/proyectos.
```

**Claude Code:**
1. Te mostrará la configuración a añadir
2. Te ayudará a editar el archivo config
3. Verificará que la configuración funcione

---

## Lección 3: Servidores MCP Comunes

### Servidor MCP de Sistema de Archivos

**Propósito:** Acceder a archivos y directorios

**Configuración:**
```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/ruta/permitida"]
    }
  }
}
```

**Uso:**
```
Usando el servidor MCP de sistema de archivos, lista todos los archivos Python en mi directorio de proyectos
```

---

### Servidor MCP de PostgreSQL

**Propósito:** Consultar y gestionar bases de datos PostgreSQL

**Configuración:**
```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {
        "POSTGRES_URL": "postgresql://usuario:pass@localhost:5432/nombrebd"
      }
    }
  }
}
```

**Uso:**
```
Usando el servidor MCP de postgres, muéstrame todas las tablas en la base de datos
Consulta la tabla de usuarios y muéstrame el esquema
```

---

### Servidor MCP de SQLite

**Propósito:** Trabajar con bases de datos SQLite

**Configuración:**
```json
{
  "mcpServers": {
    "sqlite": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sqlite", "/ruta/a/base-de-datos.db"]
    }
  }
}
```

**Uso:**
```
Usando el servidor MCP de sqlite, analiza el esquema de la base de datos
Encuentra todas las tablas con datos de usuario
```

---

### Servidor MCP de GitHub

**Propósito:** Interactuar con repositorios de GitHub

**Configuración:**
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "tu-token-de-github"
      }
    }
  }
}
```

**Uso:**
```
Usando el servidor MCP de GitHub:
- Lista mis repositorios
- Muestra issues abiertos en mi-repo
- Crea un issue para el bug que acabo de encontrar
```

---

## Lección 4: Creando un Servidor MCP Personalizado

### ¿Por Qué Crear Servidores Personalizados?

**Crea servidores MCP personalizados para:**
- Las APIs internas de tu empresa
- Bases de datos o almacenes de datos personalizados
- Herramientas o servicios especializados
- Conocimiento específico del dominio

---

### Conceptos Básicos de Servidores MCP

**Un servidor MCP proporciona:**
- **Tools (Herramientas)** - Funciones que Claude puede llamar
- **Resources (Recursos)** - Datos que Claude puede acceder
- **Prompts** - Plantillas de prompt predefinidas

---

### Creando un Servidor MCP Simple

**Ejemplo: Servidor MCP de API del Clima**

```javascript
// weather-mcp-server.js
import { McpServer } from '@modelcontextprotocol/sdk';

const server = new McpServer({
  name: 'weather',
  version: '1.0.0'
});

// Define una herramienta
server.addTool({
  name: 'get_weather',
  description: 'Obtiene el clima actual para una ciudad',
  parameters: {
    type: 'object',
    properties: {
      city: {
        type: 'string',
        description: 'Nombre de la ciudad'
      }
    },
    required: ['city']
  },
  handler: async ({ city }) => {
    // Llama a la API del clima
    const response = await fetch(
      `https://api.weather.com/...?city=${city}`
    );
    const data = await response.json();

    return {
      temperature: data.temp,
      conditions: data.conditions,
      humidity: data.humidity
    };
  }
});

server.start();
```

---

### Configurando Tu Servidor Personalizado

**Añade a config.json:**
```json
{
  "mcpServers": {
    "weather": {
      "command": "node",
      "args": ["/ruta/a/weather-mcp-server.js"],
      "env": {
        "WEATHER_API_KEY": "tu-api-key"
      }
    }
  }
}
```

---

### Usando Tu Servidor Personalizado

```
Usando el servidor MCP del clima, ¿cuál es el clima en Madrid?
```

---

## Lección 5: Características Avanzadas de MCP

### Recursos

**Proporciona datos que Claude puede leer:**

```javascript
server.addResource({
  uri: 'company://employees',
  name: 'Directorio de Empleados',
  description: 'Lista de todos los empleados',
  mimeType: 'application/json',
  handler: async () => {
    const employees = await db.query('SELECT * FROM employees');
    return JSON.stringify(employees);
  }
});
```

---

### Prompts

**Plantillas de prompt predefinidas:**

```javascript
server.addPrompt({
  name: 'code_review',
  description: 'Revisa código siguiendo estándares de la empresa',
  template: async ({ filename }) => {
    const standards = await loadCompanyStandards();
    return `Revisa ${filename} según estos estándares:\n${standards}`;
  }
});
```

---

## Lección 6: Ejemplos de MCP del Mundo Real

### Ejemplo 1: MCP de Base de Datos de Empresa

**Escenario:** Acceder a la base de datos de tu empresa

```javascript
// company-db-mcp.js
import { McpServer } from '@modelcontextprotocol/sdk';
import pg from 'pg';

const server = new McpServer({
  name: 'company-db',
  version: '1.0.0'
});

const db = new pg.Client({
  connectionString: process.env.DATABASE_URL
});

server.addTool({
  name: 'query_customers',
  description: 'Consulta datos de clientes',
  parameters: {
    type: 'object',
    properties: {
      filter: { type: 'string' }
    }
  },
  handler: async ({ filter }) => {
    const result = await db.query(
      'SELECT * FROM customers WHERE $1',
      [filter]
    );
    return result.rows;
  }
});

server.start();
```

---

### Ejemplo 2: MCP de API Interna

**Escenario:** Conectar a tus servicios internos

```javascript
// internal-api-mcp.js
server.addTool({
  name: 'deploy_service',
  description: 'Despliega un servicio a producción',
  parameters: {
    type: 'object',
    properties: {
      service: { type: 'string' },
      version: { type: 'string' }
    },
    required: ['service', 'version']
  },
  handler: async ({ service, version }) => {
    const response = await fetch(
      `https://internal-api.company.com/deploy`,
      {
        method: 'POST',
        headers: {
          'Authorization': `Bearer ${process.env.API_TOKEN}`,
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({ service, version })
      }
    );

    return await response.json();
  }
});
```

---

## Lección 7: Mejores Prácticas

### Seguridad

**Protege datos sensibles:**
- Usa variables de entorno para secretos
- Valida todas las entradas
- Limita acceso a operaciones sensibles
- Usa autenticación/autorización
- Registra todas las acciones en log de auditoría

---

### Manejo de Errores

**Maneja errores con gracia:**

```javascript
server.addTool({
  name: 'risky_operation',
  handler: async (params) => {
    try {
      const result = await doSomethingRisky(params);
      return result;
    } catch (error) {
      console.error('Operación fallida:', error);
      throw new Error(`Error al realizar operación: ${error.message}`);
    }
  }
});
```

---

### Rendimiento

**Optimiza para velocidad:**
- Cachea datos accedidos frecuentemente
- Usa connection pooling para bases de datos
- Implementa timeouts
- Limita tamaños de resultados

---

## Práctica Práctica

### Ejercicio 1: Instalar y Usar Servidores MCP

**Tarea:** Configura servidores MCP comunes

```
1. Instala el servidor MCP de sistema de archivos
2. Configúralo para tu directorio de proyectos
3. Úsalo para analizar tu código
4. Instala el servidor MCP de GitHub
5. Úsalo para listar tus repositorios
```

---

### Ejercicio 2: Crear un Servidor MCP Simple

**Tarea:** Construye un servidor MCP personalizado

```
Crea un servidor MCP que:
- Se conecte a un archivo JSON de notas
- Proporcione herramientas para:
  * Listar todas las notas
  * Buscar notas por palabra clave
  * Añadir nueva nota
  * Eliminar nota

Pruébalo con Claude Code
```

---

### Ejercicio 3: Construir un Servidor MCP Práctico

**Tarea:** Crea una integración útil

**Elige uno:**
- Gestor de lista de tareas (conecta a archivo o BD)
- Ayudante de Git (atajos para operaciones git comunes)
- Generador de plantillas de proyecto
- Biblioteca de snippets de código

---

## Lista de Verificación del Módulo 11

- [ ] Entender qué es MCP
- [ ] Saber cómo configurar servidores MCP
- [ ] Poder instalar servidores MCP comunes
- [ ] Poder crear servidores MCP personalizados
- [ ] Entender consideraciones de seguridad de MCP
- [ ] Poder usar MCP para extender Claude Code

---

## Servidores MCP Disponibles

**Servidores oficiales:**
- @modelcontextprotocol/server-filesystem
- @modelcontextprotocol/server-postgres
- @modelcontextprotocol/server-sqlite
- @modelcontextprotocol/server-github
- @modelcontextprotocol/server-slack

**Servidores de la comunidad:**
- Muchos más en npm y GitHub
- Busca "mcp-server" en npm

---

## ¿Qué Sigue?

¡Ahora entiendes cómo extender Claude Code con servidores MCP! Puedes:
- Conectarte a cualquier base de datos
- Integrarte con cualquier API
- Crear herramientas personalizadas
- Construir asistentes específicos del dominio

**¿Listo para el Módulo 12?** A continuación, aprenderemos sobre Skills y Hooks - personalizando el comportamiento de Claude Code aún más.

---

*¡Módulo 11 Completado!*
