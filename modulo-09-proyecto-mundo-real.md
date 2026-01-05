# Módulo 9: Proyecto del Mundo Real - Construyendo una Aplicación Completa

**Objetivo:** Aplica todo lo que has aprendido construyendo una aplicación completa lista para producción

**Tiempo Estimado:** 3-6 horas (puede hacerse en múltiples sesiones)

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, habrás:
- Construido una aplicación completa desde cero
- Implementado autenticación y autorización
- Creado una base de datos con esquema apropiado
- Escrito tests comprehensivos
- Añadido manejo apropiado de errores
- Creado documentación
- Usado Git para control de versiones
- Desplegado una aplicación funcionando

---

## Opciones de Proyecto

Elige un proyecto que te interese:

### Opción 1: API de Gestión de Tareas
Una API REST para gestionar tareas y proyectos

**Características:**
- Autenticación de usuarios (registro/login)
- Crear, leer, actualizar, eliminar tareas
- Organizar tareas en proyectos
- Asignar tareas a usuarios
- Marcar tareas como completadas
- Filtrar y buscar tareas

**Tecnologías:** Node.js, Express, SQLite/PostgreSQL, JWT

---

### Opción 2: Plataforma de Blog
Un sistema de blogging completo con frontend y backend

**Características:**
- Cuentas de usuario
- Crear/editar/eliminar publicaciones
- Editor de texto enriquecido
- Comentarios en publicaciones
- Etiquetas y categorías
- Funcionalidad de búsqueda

**Tecnologías:** React/Next.js, Node.js, Express, Base de datos

---

### Opción 3: Servicio de Acortador de URLs
Un servicio para crear URLs cortas

**Características:**
- Acortar URLs largas
- Códigos cortos personalizados
- Rastrear analytics de clics
- Fechas de expiración para enlaces
- Cuentas de usuario para gestionar enlaces
- API para acceso programático

**Tecnologías:** Node.js, Express, Redis/Base de datos

---

### Opción 4: Dashboard del Clima
Un dashboard de información del clima

**Características:**
- Buscar clima por ciudad
- Pronóstico de 5 días
- Guardar ubicaciones favoritas
- Alertas del clima
- Visualización de datos históricos
- Diseño responsivo para móvil

**Tecnologías:** React, API externa del clima, backend Node.js

---

### Opción 5: Aplicación CLI de Tareas
Un potente gestor de tareas de línea de comandos

**Características:**
- Añadir/completar/eliminar tareas
- Categorías y etiquetas
- Fechas de vencimiento y prioridades
- Buscar y filtrar
- Persistencia de datos
- CLI colorida e interactiva

**Tecnologías:** Node.js, Commander.js, Chalk, SQLite

---

## Construiremos: API de Gestión de Tareas

**Para este módulo, construiremos la Opción 1 paso a paso.**
(¡Puedes aplicar el mismo proceso a cualquier proyecto!)

---

## Fase 1: Planificación y Configuración

### Paso 1: Definir Requisitos

```
Quiero construir una API de Gestión de Tareas.

Ayúdame a crear un documento de requisitos completo incluyendo:
- Lista de características
- Endpoints de API necesarios
- Esquema de base de datos
- Enfoque de autenticación
- Recomendaciones de stack tecnológico
```

---

### Paso 2: Planificación de Estructura del Proyecto

```
Para esta API de Gestión de Tareas, ayúdame a planificar:
- Estructura de carpetas del proyecto
- Organización de archivos
- Separación de responsabilidades (rutas, controladores, servicios, modelos)
- Gestión de configuración
- Dónde deben ir los tests
```

---

### Paso 3: Inicializar Proyecto

```
Inicializa un nuevo proyecto Node.js para la API de Gestión de Tareas con:
- package.json con metadatos apropiados
- Express.js
- SQLite con better-sqlite3
- JWT para autenticación
- bcrypt para hashing de contraseñas
- Jest para testing
- ESLint y Prettier para calidad de código
- nodemon para desarrollo
```

---

### Paso 4: Configurar Estructura del Proyecto

```
Crea la siguiente estructura de carpetas:
src/
  ├── routes/       (rutas de API)
  ├── controllers/  (manejadores de solicitudes)
  ├── services/     (lógica de negocio)
  ├── models/       (modelos de base de datos)
  ├── middleware/   (auth, validación, etc.)
  ├── utils/        (funciones auxiliares)
  └── config/       (configuración)
tests/
  ├── unit/
  └── integration/
.env.example
.gitignore
README.md
```

---

## Fase 2: Configuración de Base de Datos

### Paso 5: Diseñar Esquema de Base de Datos

```
Diseña el esquema de base de datos para:

Tabla Users:
- id, email, password_hash, name, created_at

Tabla Projects:
- id, name, description, owner_id, created_at

Tabla Tasks:
- id, title, description, project_id, assigned_to, status, priority, due_date, created_at, completed_at

Crea el esquema SQL con:
- Tipos de datos apropiados
- Claves foráneas y restricciones
- Índices para rendimiento
```

---

### Paso 6: Crear Conexión a Base de Datos

```
Crea un módulo de conexión a base de datos en src/config/database.js que:
- Se conecte a base de datos SQLite
- Cree tablas si no existen
- Exporte la instancia de base de datos
- Incluya manejo de errores
- Tenga un método para ejecutar migraciones
```

---

### Paso 7: Crear Modelos de Base de Datos

```
Crea archivos de modelo para User, Project, y Task con métodos:

Modelo User:
- create(email, password, name)
- findByEmail(email)
- findById(id)
- verifyPassword(email, password)

Modelo Project:
- create(name, description, ownerId)
- findById(id)
- findByOwner(ownerId)
- update(id, data)
- delete(id)

Modelo Task:
- create(taskData)
- findById(id)
- findByProject(projectId)
- update(id, data)
- delete(id)
- markComplete(id)
```

---

## Fase 3: Autenticación

### Paso 8: Crear Middleware de Autenticación

```
Crea middleware de autenticación en src/middleware/auth.js que:
- Extraiga token JWT del header Authorization
- Verifique el token
- Añada info del usuario al objeto request
- Retorne 401 si el token es inválido/falta
```

---

### Paso 9: Crear Rutas de Auth

```
Crea rutas de autenticación en src/routes/auth.js:

POST /api/auth/register
- Valida entrada (email, password, name)
- Hashea contraseña
- Crea usuario
- Retorna token JWT

POST /api/auth/login
- Valida credenciales
- Verifica contraseña
- Retorna token JWT

GET /api/auth/me
- Requiere autenticación
- Retorna info del usuario actual
```

---

### Paso 10: Implementar Hashing de Contraseñas

```
Crea un módulo utilitario para hashing de contraseñas en src/utils/password.js con:
- hash(password) - retorna contraseña hasheada
- verify(password, hash) - retorna boolean
Usa bcrypt con salt rounds de 10
```

---

## Fase 4: Características Principales

### Paso 11: Rutas de Proyectos

```
Crea rutas de proyectos en src/routes/projects.js:

GET /api/projects
- Lista todos los proyectos para el usuario autenticado
- Filtrado opcional por nombre

POST /api/projects
- Crea nuevo proyecto
- Requiere: name, description (opcional)
- Establece owner_id al usuario actual

GET /api/projects/:id
- Obtiene un solo proyecto
- Verifica que el usuario sea propietario

PUT /api/projects/:id
- Actualiza proyecto
- Verifica que el usuario sea propietario

DELETE /api/projects/:id
- Elimina proyecto y todas sus tareas
- Verifica que el usuario sea propietario
```

---

### Paso 12: Rutas de Tareas

```
Crea rutas de tareas en src/routes/tasks.js:

GET /api/tasks
- Lista todas las tareas para el usuario autenticado
- Filtros opcionales: project_id, status, priority
- Ordenamiento opcional

POST /api/tasks
- Crea nueva tarea
- Requiere: title, project_id
- Opcional: description, due_date, priority, assigned_to

GET /api/tasks/:id
- Obtiene una sola tarea
- Verifica que el usuario tenga acceso

PUT /api/tasks/:id
- Actualiza tarea
- Verifica que el usuario tenga acceso

PATCH /api/tasks/:id/complete
- Marca tarea como completada
- Establece timestamp completed_at

DELETE /api/tasks/:id
- Elimina tarea
- Verifica que el usuario tenga acceso
```

---

### Paso 13: Añadir Validación de Entrada

```
Crea middleware de validación usando express-validator para:
- Formato de email
- Fortaleza de contraseña (mín 8 caracteres)
- Campos requeridos
- Tipos de datos
- Longitudes de strings

Añade validación a todas las rutas
Retorna mensajes de error claros
```

---

## Fase 5: Manejo de Errores y Logging

### Paso 14: Manejador Global de Errores

```
Crea middleware de manejo de errores en src/middleware/errorHandler.js que:
- Capture todos los errores
- Registre errores en consola (con stack trace en desarrollo)
- Retorne códigos de estado apropiados
- No exponga información sensible
- Maneje diferentes tipos de error:
  * Errores de validación → 400
  * Errores de autenticación → 401
  * Errores de autorización → 403
  * Errores no encontrado → 404
  * Errores de base de datos → 500
```

---

### Paso 15: Añadir Logging

```
Configura logging usando un logger simple en src/utils/logger.js:
- Registra solicitudes (método, ruta, status, duración)
- Registra errores con stack traces
- Diferentes niveles de log (info, warn, error)
- Opcionalmente escribe a archivo en producción
```

---

## Fase 6: Testing

### Paso 16: Tests Unitarios

```
Crea tests unitarios para:

src/utils/password.test.js
- Prueba hashing de contraseñas
- Prueba verificación de contraseñas

src/models/user.test.js
- Prueba creación de usuario
- Prueba búsqueda de usuarios
- Prueba verificación de contraseña

src/models/task.test.js
- Prueba operaciones CRUD de tareas
- Prueba completar tareas
```

---

### Paso 17: Tests de Integración

```
Crea tests de integración para todos los endpoints de API:

tests/integration/auth.test.js
- Prueba flujo de registro
- Prueba flujo de login
- Prueba rutas protegidas
- Prueba credenciales inválidas

tests/integration/projects.test.js
- Prueba crear proyectos
- Prueba listar proyectos
- Prueba actualizar proyectos
- Prueba eliminar proyectos
- Prueba autorización

tests/integration/tasks.test.js
- Prueba crear tareas
- Prueba listar con filtros
- Prueba completar tareas
- Prueba eliminar tareas
```

---

### Paso 18: Ejecutar Tests y Corregir Problemas

```
Ejecuta todos los tests con cobertura:
npm test -- --coverage

Corrige cualquier test fallido
Apunta a al menos 80% de cobertura
Añade tests para cualquier ruta crítica no cubierta
```

---

## Fase 7: Documentación

### Paso 19: Documentación de API

```
Crea documentación de API comprehensiva en README.md:

Para cada endpoint, documenta:
- Método HTTP y ruta
- Requisitos de autenticación
- Body/parámetros de solicitud
- Formato de respuesta
- Ejemplos de solicitudes y respuestas
- Posibles códigos de error
```

---

### Paso 20: Instrucciones de Configuración

```
Añade al README.md:
- Descripción del proyecto
- Prerrequisitos (versión de Node.js, etc.)
- Pasos de instalación
- Variables de entorno necesarias
- Cómo ejecutar en desarrollo
- Cómo ejecutar tests
- Cómo construir para producción
```

---

## Fase 8: Control de Versiones

### Paso 21: Inicializar Git

```
Inicializa repositorio git
Crea un buen archivo .gitignore para Node.js
Crea commit inicial con estructura del proyecto
```

---

### Paso 22: Hacer Commits de Tu Progreso

```
Crea commits significativos para cada característica importante:
- "Añade esquema de base de datos y modelos"
- "Implementa autenticación"
- "Añade endpoints CRUD de proyectos"
- "Añade características de gestión de tareas"
- "Añade validación de entrada"
- "Añade manejo de errores y logging"
- "Añade tests comprehensivos"
- "Añade documentación"
```

---

### Paso 23: Crear Repositorio en GitHub

```
Crea un nuevo repositorio en GitHub
Añade origen remoto
Haz push de tu código
Crea un buen README con badges
```

---

## Fase 9: Preparación para Despliegue

### Paso 24: Configuración de Entorno

```
Crea manejo apropiado de variables de entorno:
- .env.example con todas las variables requeridas
- config/env.js para cargar y validar vars de entorno
- Diferentes configs para dev/test/producción
```

---

### Paso 25: Preparación para Producción

```
Añade optimizaciones de producción:
- Middleware de compresión
- Rate limiting
- Configuración CORS
- Headers de seguridad (helmet.js)
- Límites de tamaño de solicitud
- Instrucciones de configuración HTTPS apropiada
```

---

### Paso 26: Crear Scripts de Inicio

```
Añade scripts a package.json:
- "start": Servidor de producción
- "dev": Desarrollo con nodemon
- "test": Ejecutar todos los tests
- "test:watch": Ejecutar tests en modo watch
- "lint": Ejecutar ESLint
- "format": Ejecutar Prettier
```

---

## Fase 10: Mejoras Opcionales

### Ideas de Mejora

**Añadir más características:**
```
- Recordatorios de fecha de vencimiento de tareas
- Comentarios en tareas
- Adjuntos de archivos a tareas
- Ordenamiento por prioridad
- Funcionalidad de búsqueda
- Paginación para listas
- Historial/log de auditoría de tareas
- Características de colaboración en equipo
```

**Mejorar calidad de código:**
```
- Añadir TypeScript
- Añadir versionado de API
- Añadir caché de solicitudes
- Añadir optimización de consultas de BD
- Añadir logging comprehensivo
- Añadir monitoreo y métricas
```

---

## Lista de Verificación Final

Antes de considerar tu proyecto completo:

**Funcionalidad:**
- [ ] Todas las características principales funcionan
- [ ] La autenticación es segura
- [ ] Las operaciones de BD son correctas
- [ ] La validación funciona apropiadamente
- [ ] El manejo de errores es comprehensivo

**Calidad de Código:**
- [ ] El código está bien organizado
- [ ] Las funciones son pequeñas y enfocadas
- [ ] Los nombres son descriptivos
- [ ] No hay duplicación de código
- [ ] ESLint pasa sin errores

**Testing:**
- [ ] Tests unitarios para modelos y utilidades
- [ ] Tests de integración para todos los endpoints
- [ ] Los tests cubren casos límite
- [ ] Todos los tests pasan
- [ ] Cobertura es 80%+

**Documentación:**
- [ ] README es comprehensivo
- [ ] Los endpoints de API están documentados
- [ ] Las instrucciones de configuración son claras
- [ ] El código tiene comentarios útiles
- [ ] Se proporcionan ejemplos

**Control de Versiones:**
- [ ] El historial de Git está limpio
- [ ] Los commits son significativos
- [ ] El código está en GitHub
- [ ] .gitignore es apropiado
- [ ] No hay secretos en el repositorio

**Listo para Producción:**
- [ ] Se usan variables de entorno
- [ ] Se siguen mejores prácticas de seguridad
- [ ] El manejo de errores no expone info
- [ ] El logging es adecuado
- [ ] El rendimiento es aceptable

---

## Desplegando Tu Proyecto

### Opción 1: Desplegar a Heroku

```
Ayúdame a desplegar esta aplicación a Heroku:
1. Crear app de Heroku
2. Añadir base de datos PostgreSQL
3. Configurar variables de entorno
4. Configurar scripts de build
5. Desplegar y probar
```

---

### Opción 2: Desplegar con Docker

```
Crea un Dockerfile para esta aplicación:
- Usar imagen Node.js Alpine
- Copiar e instalar dependencias
- Copiar código fuente
- Exponer puerto
- Establecer comando de inicio

También crea docker-compose.yml para desarrollo local
```

---

### Opción 3: Desplegar a VPS

```
Crea guía de despliegue para VPS Ubuntu:
- Instalar Node.js
- Configurar gestor de procesos (PM2)
- Configurar reverse proxy Nginx
- Configurar SSL con Let's Encrypt
- Configurar firewall
- Configurar reinicios automáticos
```

---

## Lo Que Has Logrado

Al completar este proyecto, has:

✅ Construido una API completa y funcionando
✅ Implementado autenticación segura
✅ Creado un esquema de base de datos apropiado
✅ Escrito tests comprehensivos
✅ Añadido manejo apropiado de errores
✅ Creado buena documentación
✅ Usado flujo de trabajo Git profesional
✅ Hecho tu código listo para producción

**¡Este es un proyecto de portafolio real que puedes mostrar a empleadores!**

---

## Siguientes Pasos

**Para ir más allá:**

1. **Añade un frontend:** Construye una app React que use tu API
2. **Añade más características:** Implementa las ideas de mejora
3. **Despliégalo:** Ponlo funcionando en un servidor real
4. **Obtén feedback:** Pide a otros que revisen tu código
5. **Contribuye a código abierto:** ¡Ahora tienes las habilidades!

---

## ¡Módulo 9 Completado!

¡Felicitaciones por construir una aplicación completa! Has aplicado todo de los módulos anteriores y creado algo real y valioso.

**¿Listo para el Módulo 10?** En el módulo final del curso principal, aprenderemos mejores prácticas profesionales de flujo de trabajo para llevar tu proceso de desarrollo al siguiente nivel.

---

*¡Módulo 9 Completado - Ahora eres un constructor!*
