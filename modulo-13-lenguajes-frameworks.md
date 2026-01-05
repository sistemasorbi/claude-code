# Módulo 13: Trabajando con Diferentes Lenguajes y Frameworks

**Objetivo:** Usa Claude Code a través de diferentes stacks tecnológicos y lenguajes

**Tiempo Estimado:** 45-60 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Usar Claude Code con proyectos Python
- Trabajar con ecosistemas JavaScript/TypeScript
- Construir aplicaciones Go
- Desarrollar proyectos Rust
- Manejar Java y Spring Boot
- Trabajar con múltiples lenguajes en un proyecto
- Entender mejores prácticas específicas de cada lenguaje

---

## Lección 1: Desarrollo Python

### Configurando Proyectos Python

**Crea un nuevo proyecto Python:**

```
Crea un nuevo proyecto Python con:
- Entorno virtual
- requirements.txt
- Estructura de directorio src/
- pytest para testing
- black para formateo
- pylint para linting
- setup.py para gestión de paquetes
```

---

### Aplicación Web Flask

```
Crea una API Flask con:
- Patrón de fábrica de aplicación
- Blueprints para rutas
- SQLAlchemy para base de datos
- Flask-JWT-Extended para auth
- Fixtures de pytest para testing
- Gestión de configuración (dev/prod)
```

---

### Proyecto Django

```
Crea un proyecto Django para un blog con:
- Modelo de usuario personalizado
- App de blog con posts y comentarios
- Django REST framework para API
- Autenticación y permisos
- Personalización de interfaz admin
- Tests para modelos, vistas y API
```

---

### Aplicación FastAPI

```
Crea una aplicación FastAPI con:
- Documentación de API automática
- Modelos Pydantic para validación
- Operaciones de BD async
- Autenticación JWT
- Configuración CORS
- Configuración Docker
```

---

## Lección 2: JavaScript/TypeScript

### Backend Node.js

**Express con TypeScript:**

```
Crea una API Express TypeScript con:
- Modo estricto de TypeScript
- Routing de Express con tipos
- TypeORM para base de datos
- Autenticación JWT
- Validación con Zod
- Testing con Jest
- ESLint y Prettier
```

---

### Frontend React

**Aplicación React moderna:**

```
Crea una app React con:
- TypeScript
- React Router para navegación
- React Query para fetching de datos
- Context API para gestión de estado
- Tailwind CSS para estilos
- Vitest para testing
- Estructura de biblioteca de componentes
```

---

### Next.js Full-Stack

```
Crea una aplicación Next.js con:
- App Router (última versión)
- Server Components
- API Routes
- Server Actions
- Autenticación con NextAuth
- Base de datos con Prisma
- Tailwind CSS
- Configuración de despliegue
```

---

## Lección 3: Desarrollo Go

### Aplicación CLI en Go

```
Crea una herramienta CLI en Go que:
- Use Cobra para comandos
- Maneje flags y argumentos
- Lea archivos de configuración
- Interactúe con APIs
- Tenga manejo de errores apropiado
- Incluya tests
- Pueda compilarse para múltiples plataformas
```

---

### Servidor Web Go

```
Crea un servidor web Go con:
- Router Chi
- Middleware (logging, recovery, CORS)
- Base de datos con sqlx o GORM
- Autenticación JWT
- Logging estructurado
- Graceful shutdown
- Containerización Docker
```

---

## Lección 4: Desarrollo Rust

### Herramienta CLI Rust

```
Crea una aplicación CLI Rust con:
- Clap para parseo de argumentos
- Manejo de errores con thiserror o anyhow
- I/O de archivos
- Parsing JSON/YAML con serde
- Testing con framework de test integrado
- Documentación con rustdoc
```

---

### API Web Rust

```
Crea una API web Rust con Actix-web:
- Rutas RESTful
- Base de datos con SQLx
- Autenticación JWT
- Validación de solicitudes
- Manejo de errores
- Tests
- Documentación OpenAPI
```

---

## Lección 5: Java y Spring Boot

### API REST Spring Boot

```
Crea una aplicación Spring Boot con:
- Build Maven o Gradle
- Spring Data JPA
- Spring Security con JWT
- Validación
- Manejo de excepciones
- Documentación Swagger/OpenAPI
- Tests JUnit
- Configuración Docker
```

---

## Lección 6: Proyectos Políglotas

### Trabajando con Múltiples Lenguajes

**Ejemplo: Arquitectura de Microservicios**

```
Tengo un proyecto con:
- Servicio ML en Python (FastAPI)
- Gateway de API en Go
- Frontend Node.js (Next.js)
- Procesador de datos en Rust

Ayúdame a:
1. Configurar la estructura del monorepo
2. Configurar Docker Compose para desarrollo local
3. Configurar tipos/contratos compartidos
4. Crear comunicación entre servicios
5. Configurar testing para cada servicio
```

---

### Tareas Específicas por Lenguaje

**Cambia contexto basado en archivo:**

```
Estoy trabajando en una base de código políglota.
Cuando me pidas añadir características:
- En archivos .py: Usa mejores prácticas Python
- En archivos .go: Sigue idiomas de Go
- En archivos .ts: Usa patrones TypeScript
- En archivos .rs: Sigue convenciones Rust
```

---

## Lección 7: Mejores Prácticas por Lenguaje

### Mejores Prácticas Python

```
Revisa este código Python y asegura que siga:
- Guía de estilo PEP 8
- Type hints donde sea apropiado
- Docstrings para funciones/clases
- List comprehensions sobre loops (donde sea legible)
- Context managers para recursos
- Manejo apropiado de excepciones
```

---

### Mejores Prácticas JavaScript/TypeScript

```
Revisa este código TypeScript para:
- Anotaciones de tipo apropiadas
- Evitar tipos 'any'
- Usar const/let, no var
- Async/await sobre callbacks
- Patrones de programación funcional
- Error boundaries en React
```

---

### Mejores Prácticas Go

```
Revisa este código Go para:
- Manejo de errores apropiado
- Uso efectivo de goroutines
- Uso de channels
- Diseño de interfaces
- Estructura de paquetes
- Patrones idiomáticos de Go
```

---

### Mejores Prácticas Rust

```
Revisa este código Rust para:
- Ownership y borrowing
- Manejo de errores con Result
- Uso de traits
- Evitar clones innecesarios
- Lifetimes apropiados
- Abstracciones de costo cero
```

---

## Práctica Práctica

### Ejercicio 1: Proyecto Python FastAPI

**Tarea:** Construye una aplicación FastAPI completa

```
Crea una API FastAPI de gestión de tareas con:
- Usuarios y autenticación
- Operaciones CRUD para tareas
- Base de datos con SQLAlchemy
- Operaciones async
- Validación de entrada con Pydantic
- Tests con pytest
- Documentación en README
```

---

### Ejercicio 2: TypeScript Full-Stack

**Tarea:** Construye aplicación Next.js + API

```
Crea una aplicación Next.js de blog con:
- Server components para listar posts
- Client components para interacciones
- API routes para CRUD
- Base de datos con Prisma
- TypeScript en todo
- Tailwind para estilos
```

---

### Ejercicio 3: Microservicio Go

**Tarea:** Construye un servicio Go

```
Crea un microservicio Go que:
- Sirva una API REST
- Se conecte a PostgreSQL
- Tenga endpoint de health check
- Logging estructurado
- Graceful shutdown
- Container Docker
- Config de despliegue Kubernetes
```

---

### Ejercicio 4: Integración Políglota

**Tarea:** Conecta servicios en diferentes lenguajes

```
Construye un sistema con:
- Servicio de modelo ML en Python
- API Node.js que llame al servicio ML
- Servicio Go para procesamiento de datos
- Todos comunicándose via HTTP/gRPC
- Configuración Docker Compose
- Contratos de API compartidos
```

---

## Lista de Verificación del Módulo 13

- [ ] Puedo crear proyectos Python (Flask, Django, FastAPI)
- [ ] Puedo construir apps JavaScript/TypeScript (Node, React, Next.js)
- [ ] Puedo desarrollar aplicaciones Go
- [ ] Puedo escribir programas Rust
- [ ] Puedo trabajar con Java/Spring Boot
- [ ] Puedo manejar proyectos políglotas
- [ ] Conozco mejores prácticas específicas de cada lenguaje

---

## Comandos Específicos por Lenguaje

### Python
```bash
# Crear entorno virtual
python -m venv venv

# Activar (Linux/Mac)
source venv/bin/activate

# Instalar dependencias
pip install -r requirements.txt

# Ejecutar tests
pytest
```

### Node.js/TypeScript
```bash
# Instalar dependencias
npm install

# Ejecutar servidor dev
npm run dev

# Ejecutar tests
npm test

# Build
npm run build
```

### Go
```bash
# Inicializar módulo
go mod init

# Instalar dependencias
go mod tidy

# Ejecutar
go run main.go

# Test
go test ./...

# Build
go build
```

### Rust
```bash
# Crear nuevo proyecto
cargo new myproject

# Build
cargo build

# Ejecutar
cargo run

# Test
cargo test
```

---

## ¿Qué Sigue?

¡Ahora puedes usar Claude Code con cualquier lenguaje de programación importante!

**¿Listo para el Módulo 14?** A continuación, dominaremos la integración de APIs y trabajo con servicios externos.

---

*¡Módulo 13 Completado!*
