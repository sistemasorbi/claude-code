# Módulo 3: Entendiendo las Herramientas de Claude Code

**Objetivo:** Domina las diferentes capacidades que tiene Claude Code

**Tiempo Estimado:** 40-50 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Entender qué hace cada herramienta de Claude Code
- Saber cuándo usar cada herramienta
- Reconocer el uso de herramientas cuando sucede
- Pedir el uso de herramientas específicas cuando sea necesario
- Combinar herramientas para tareas complejas

---

## Lección 1: ¿Qué Son las Herramientas?

### Entendiendo las Herramientas de Claude Code

Las **herramientas** son las capacidades que tiene Claude Code para interactuar con tu sistema. Piensa en ellas como las "manos" de Claude Code.

**Sin herramientas, Claude Code solo puede:**
- Tener conversaciones contigo
- Proporcionar información
- Hacer sugerencias

**Con herramientas, Claude Code puede:**
- Leer archivos de tu computadora
- Escribir y editar código
- Ejecutar comandos
- Buscar en internet
- ¡Y mucho más!

### Categorías de Herramientas

Claude Code tiene varias categorías de herramientas:

1. **Operaciones de Archivos** - Read, Write, Edit
2. **Búsqueda** - Grep, Glob
3. **Ejecución** - Bash
4. **Agentes** - Task
5. **Web** - WebSearch, WebFetch
6. **Cuadernos** - NotebookEdit
7. **Gestión** - TodoWrite

---

## Lección 2: Herramientas de Lectura y Escritura

### Read (Leer)

**Propósito:** Leer archivos de tu sistema

**Cuándo se usa:**
- Para ver el contenido de un archivo
- Para entender código existente
- Para revisar cambios
- Para analizar archivos de configuración

**Ejemplo de cómo pedirlo:**
```
Muéstrame el contenido del archivo server.js
```

```
Lee el archivo package.json y dime qué dependencias tiene
```

**Lo que verás:**
```
╭─ Read: server.js ───────────────────────────╮
│ const express = require('express');         │
│ const app = express();                       │
│ // ... resto del archivo                    │
╰─────────────────────────────────────────────╯
```

### Write (Escribir)

**Propósito:** Crear nuevos archivos

**Cuándo se usa:**
- Para crear archivos desde cero
- Para generar nuevos componentes
- Para crear archivos de configuración
- Para escribir documentación

**Ejemplo de cómo pedirlo:**
```
Crea un nuevo archivo llamado utils.js con funciones auxiliares
```

```
Escribe un archivo README.md para este proyecto
```

**Lo que verás:**
```
╭─ Write: utils.js ───────────────────────────╮
│ Creando nuevo archivo...                    │
│ ✓ Archivo creado exitosamente               │
╰─────────────────────────────────────────────╯
```

### Edit (Editar)

**Propósito:** Modificar archivos existentes

**Cuándo se usa:**
- Para hacer cambios específicos
- Para corregir errores
- Para añadir funcionalidad
- Para refactorizar código

**Ejemplo de cómo pedirlo:**
```
En el archivo server.js, cambia el puerto de 3000 a 8080
```

```
Añade manejo de errores a la función getUserById
```

**Lo que verás:**
```
╭─ Edit: server.js ───────────────────────────╮
│ - const PORT = 3000;                        │
│ + const PORT = 8080;                        │
╰─────────────────────────────────────────────╯
```

---

## Lección 3: Herramientas de Búsqueda

### Glob

**Propósito:** Encontrar archivos por patrones de nombre

**Cuándo se usa:**
- Para encontrar todos los archivos de cierto tipo
- Para localizar archivos en subdirectorios
- Para ver la estructura del proyecto

**Patrones comunes:**
- `*.js` - Todos los archivos JavaScript en el directorio actual
- `**/*.py` - Todos los archivos Python en cualquier subdirectorio
- `src/**/*.tsx` - Todos los archivos TSX dentro de src/
- `**/test*` - Todos los archivos que contengan "test" en el nombre

**Ejemplo de cómo pedirlo:**
```
Encuentra todos los archivos TypeScript en este proyecto
```

```
Muéstrame todos los archivos de prueba
```

### Grep

**Propósito:** Buscar texto dentro de archivos

**Cuándo se usa:**
- Para encontrar dónde se usa una función
- Para buscar TODO o FIXME
- Para localizar importaciones
- Para encontrar patrones específicos

**Ejemplo de cómo pedirlo:**
```
Busca todas las funciones que usen console.log
```

```
Encuentra todas las veces que se importa React
```

```
Busca todos los comentarios TODO en el código
```

**Lo que verás:**
```
╭─ Grep: "console.log" ───────────────────────╮
│ src/utils.js:15:  console.log('Debug:', x)  │
│ src/api.js:42:    console.log('Error:', e)  │
│ tests/test.js:8:  console.log('Testing')    │
╰─────────────────────────────────────────────╯
```

---

## Lección 4: Herramienta de Ejecución - Bash

### Bash

**Propósito:** Ejecutar comandos de terminal

**Cuándo se usa:**
- Para instalar dependencias
- Para ejecutar programas
- Para operaciones Git
- Para compilar código
- Para ejecutar tests
- Para comandos del sistema

**Ejemplos de uso:**

**Instalación de paquetes:**
```
Instala Express y nodemon como dependencias
```
Claude Code ejecutará: `npm install express nodemon`

**Ejecutar programas:**
```
Ejecuta el servidor de desarrollo
```
Claude Code ejecutará: `npm run dev` o comando apropiado

**Operaciones Git:**
```
Muéstrame el estado de git
```
Claude Code ejecutará: `git status`

**Ejecutar tests:**
```
Ejecuta todas las pruebas
```
Claude Code ejecutará: `npm test` o similar

### Procesos en Segundo Plano

Algunos comandos se pueden ejecutar en segundo plano:

```
Inicia el servidor en segundo plano
```

Esto permite que el servidor siga ejecutándose mientras continúas trabajando.

---

## Lección 5: Herramienta Task (Agentes)

### Task (Tarea)

**Propósito:** Lanzar agentes especializados para tareas complejas

**Tipos de agentes disponibles:**

#### Agente Explore (Explorar)
Para navegar y entender bases de código
```
Explora esta base de código y explícame su arquitectura
```

#### Agente Plan (Planificar)
Para diseñar estrategias de implementación
```
Planifica cómo implementar un sistema de autenticación
```

#### Agente de Propósito General
Para tareas complejas de múltiples pasos
```
Investiga las mejores prácticas para manejo de errores en APIs REST
```

**Cuándo usar agentes:**
- Tareas que requieren múltiples pasos
- Exploración exhaustiva del código
- Investigación profunda
- Planificación de implementaciones

---

## Lección 6: Herramientas Web

### WebSearch (Búsqueda Web)

**Propósito:** Buscar información en internet

**Cuándo se usa:**
- Para encontrar documentación actualizada
- Para buscar soluciones a errores
- Para investigar mejores prácticas
- Para encontrar ejemplos de código

**Ejemplo de cómo pedirlo:**
```
Busca la documentación oficial de React hooks
```

```
Busca cómo resolver el error "CORS policy blocked"
```

### WebFetch (Obtener Contenido Web)

**Propósito:** Obtener contenido de una URL específica

**Cuándo se usa:**
- Para leer documentación de una API
- Para analizar una página específica
- Para obtener ejemplos de una URL conocida

**Ejemplo de cómo pedirlo:**
```
Obtén la documentación de la API de Stripe desde https://stripe.com/docs/api
```

---

## Lección 7: Herramienta TodoWrite

### TodoWrite (Escribir Tareas)

**Propósito:** Gestionar una lista de tareas para el trabajo actual

**Cuándo se usa:**
- Para proyectos con múltiples pasos
- Para mantener un registro del progreso
- Para organizar tareas complejas
- Para visualizar lo que queda por hacer

**Estados de las tareas:**
- `pending` - Pendiente
- `in_progress` - En progreso
- `completed` - Completada

**Ejemplo de uso:**
```
Crea una lista de tareas para implementar el login de usuarios
```

Claude Code creará algo como:
```
□ Crear modelo de Usuario
□ Implementar ruta de registro
□ Implementar ruta de login
□ Añadir middleware de autenticación
□ Crear tests
```

---

## Lección 8: Combinando Herramientas

### Flujos de Trabajo Comunes

**Añadir una nueva característica:**
1. **Grep** - Encontrar código relacionado
2. **Read** - Entender el código existente
3. **Edit** - Hacer los cambios
4. **Bash** - Ejecutar tests

**Depurar un error:**
1. **Read** - Ver el archivo con el error
2. **Grep** - Buscar usos relacionados
3. **Edit** - Corregir el problema
4. **Bash** - Verificar la corrección

**Entender un proyecto nuevo:**
1. **Glob** - Ver la estructura de archivos
2. **Read** - Revisar archivos clave (README, package.json)
3. **Task (Explore)** - Análisis profundo si es necesario

### Ejemplo Práctico

**Solicitud:**
```
Encuentra dónde se maneja la autenticación, muéstrame ese código, y añade logging para cada intento de login
```

**Claude Code hará:**
1. **Grep** - Buscar "auth" o "login" en el código
2. **Read** - Leer los archivos encontrados
3. **Edit** - Añadir las líneas de logging
4. **Bash** - (opcional) Ejecutar tests para verificar

---

## Ejercicio Práctico

### Practica con Cada Herramienta

En un proyecto existente o nuevo, prueba cada herramienta:

**1. Read:**
```
Muéstrame el archivo principal del proyecto
```

**2. Write:**
```
Crea un archivo llamado notas.md con instrucciones de uso
```

**3. Edit:**
```
En notas.md, añade una sección sobre instalación
```

**4. Glob:**
```
Encuentra todos los archivos JavaScript
```

**5. Grep:**
```
Busca todas las funciones que exporten algo
```

**6. Bash:**
```
Muéstrame la versión de Node.js instalada
```

**7. Task:**
```
Usa un agente para explorar la estructura del proyecto
```

---

## Lista de Verificación del Módulo 3

Antes de continuar, verifica que puedas:

- [ ] Explicar qué hace cada herramienta principal
- [ ] Reconocer cuándo Claude Code usa cada herramienta
- [ ] Pedir el uso de herramientas específicas
- [ ] Entender los patrones de Glob y Grep
- [ ] Saber cuándo usar agentes vs herramientas simples
- [ ] Combinar herramientas para tareas complejas

---

## Referencia Rápida de Herramientas

| Herramienta | Propósito | Ejemplo de Uso |
|-------------|-----------|----------------|
| Read | Leer archivos | "Muéstrame server.js" |
| Write | Crear archivos | "Crea utils.py" |
| Edit | Modificar archivos | "Cambia el puerto a 8080" |
| Glob | Buscar archivos | "Encuentra todos los .ts" |
| Grep | Buscar en contenido | "Busca TODO en el código" |
| Bash | Ejecutar comandos | "Instala express" |
| Task | Tareas complejas | "Explora este proyecto" |
| WebSearch | Buscar en web | "Busca documentación de X" |
| WebFetch | Obtener URL | "Obtén info de esta URL" |
| TodoWrite | Gestionar tareas | "Crea lista de tareas" |

---

## ¿Qué Sigue?

¡Excelente! Ahora entiendes todas las herramientas de Claude Code.

En el **Módulo 4**, aplicaremos este conocimiento para trabajar eficientemente con archivos y código - lectura, escritura, edición y refactorización.

---

*¡Módulo 3 Completado!*
