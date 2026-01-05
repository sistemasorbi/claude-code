# Módulo 2: Iniciando Tu Primer Proyecto

**Objetivo:** Aprende diferentes formas de comenzar a construir con Claude Code

**Tiempo Estimado:** 30-40 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Iniciar proyectos desde cero describiendo lo que quieres
- Navegar y modificar bases de código existentes
- Usar plantillas para inicio rápido
- Clonar y entender repositorios de código abierto
- Elegir el mejor enfoque para diferentes situaciones

---

## Lección 1: Empezando Desde Cero

### Cuándo Usar Este Enfoque

Empezar desde cero es perfecto cuando:
- Tienes una idea clara de lo que quieres construir
- Quieres un inicio limpio
- Estás aprendiendo un nuevo lenguaje o framework
- Necesitas control total sobre la estructura del proyecto

### El Proceso Básico

**Paso 1: Crea una carpeta vacía**
```bash
mkdir mi-nuevo-proyecto
cd mi-nuevo-proyecto
```

**Paso 2: Inicia Claude Code**
```bash
claude
```

**Paso 3: Describe tu proyecto**
```
Quiero crear una API REST usando Node.js y Express que maneje una lista de tareas (todo list). Debería tener endpoints para crear, leer, actualizar y eliminar tareas.
```

Claude Code entonces:
1. Analizará tus requisitos
2. Creará la estructura de archivos apropiada
3. Escribirá el código inicial
4. Configurará las dependencias

### Consejos para Empezar Desde Cero

**Sé específico sobre:**
- Qué lenguaje/framework usar
- Qué funcionalidad necesitas
- Cualquier requisito específico
- Patrones de diseño preferidos

**Ejemplo de prompt más detallado:**
```
Crea un proyecto de API REST con Node.js y Express que:
- Use TypeScript
- Tenga una carpeta src/ para el código fuente
- Incluya tests con Jest
- Tenga endpoints CRUD para usuarios
- Use SQLite como base de datos
- Incluya validación de entrada
```

---

## Lección 2: Trabajando con Código Existente

### Cuándo Usar Este Enfoque

Trabajar con código existente es ideal cuando:
- Te uniste a un nuevo proyecto
- Necesitas corregir bugs en código existente
- Quieres añadir características a algo que ya funciona
- Estás manteniendo o actualizando software

### Abriendo un Proyecto Existente

**Paso 1: Navega al directorio del proyecto**
```bash
cd /ruta/a/tu/proyecto
```

**Paso 2: Inicia Claude Code**
```bash
claude
```

**Paso 3: Pide a Claude que explore la base de código**
```
Ayúdame a entender este proyecto. ¿Cuál es su estructura y qué hace?
```

Claude Code usará herramientas para:
- Leer la estructura de archivos
- Examinar archivos clave (package.json, README, etc.)
- Entender la arquitectura
- Darte un resumen

### Explorando la Base de Código

**Preguntas útiles para hacer:**

```
¿Cuáles son los archivos principales de este proyecto?
```

```
¿Dónde está implementada la lógica de autenticación?
```

```
Muéstrame cómo funciona el manejo de errores
```

```
¿Qué dependencias usa este proyecto?
```

### Haciendo Cambios a Código Existente

**Para añadir una característica:**
```
Añade una nueva ruta /api/estadisticas que devuelva el conteo de todos los elementos en la base de datos
```

**Para corregir un bug:**
```
Hay un bug donde los usuarios pueden enviar un formulario vacío. Añade validación para prevenir esto.
```

**Para refactorizar:**
```
Refactoriza la función processData en utils.js para que sea más legible y añade manejo de errores
```

---

## Lección 3: Usando Plantillas

### Cuándo Usar Este Enfoque

Las plantillas son geniales cuando:
- Quieres mejores prácticas desde el inicio
- Necesitas una estructura estándar de proyecto
- Quieres ahorrar tiempo en la configuración
- Estás aprendiendo un nuevo framework

### Pidiendo a Claude Code que Use Plantillas

**Para un proyecto React:**
```
Crea un nuevo proyecto React con TypeScript usando create-react-app. Incluye React Router y una estructura básica de componentes.
```

**Para una API de Node.js:**
```
Configura un proyecto de API Express con:
- Estructura MVC
- Variables de entorno con dotenv
- Configuración básica de seguridad con helmet
- Configuración de CORS
- Manejo de errores
```

**Para un proyecto Python:**
```
Crea un proyecto Flask con:
- Entorno virtual
- requirements.txt
- Patrón de fábrica de aplicaciones
- Blueprints para rutas
- Configuración básica de testing
```

### Estructuras de Proyecto Comunes

Claude Code conoce las mejores prácticas para muchos frameworks:

**Proyecto React/Next.js:**
```
proyecto/
├── src/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── utils/
│   └── styles/
├── public/
├── tests/
├── package.json
└── README.md
```

**API de Node.js/Express:**
```
proyecto/
├── src/
│   ├── routes/
│   ├── controllers/
│   ├── services/
│   ├── models/
│   ├── middleware/
│   └── utils/
├── tests/
├── config/
├── package.json
└── README.md
```

**Proyecto Python/Flask:**
```
proyecto/
├── app/
│   ├── routes/
│   ├── models/
│   ├── services/
│   └── templates/
├── tests/
├── config.py
├── requirements.txt
└── README.md
```

---

## Lección 4: Clonando y Entendiendo Repositorios

### Cuándo Usar Este Enfoque

Clonar repositorios es perfecto cuando:
- Quieres aprender de código de alta calidad
- Necesitas contribuir a código abierto
- Quieres adaptar código existente para tus necesidades
- Estás investigando cómo otros resolvieron un problema

### El Proceso

**Paso 1: Clona el repositorio**
```bash
git clone https://github.com/usuario/proyecto-interesante.git
cd proyecto-interesante
```

**Paso 2: Inicia Claude Code**
```bash
claude
```

**Paso 3: Pide una explicación**
```
Explícame la estructura de este proyecto y sus componentes principales
```

### Preguntas para Entender Código Nuevo

**Preguntas de alto nivel:**
```
¿Cuál es el propósito principal de este proyecto?
```

```
¿Cuáles son las tecnologías principales usadas?
```

```
¿Cómo está organizado el código?
```

**Preguntas específicas:**
```
¿Cómo funciona el sistema de autenticación?
```

```
¿Dónde se manejan las llamadas a la API?
```

```
¿Cuál es el flujo de datos en esta aplicación?
```

### Aprendiendo de Proyectos de Código Abierto

Proyectos excelentes para aprender:
- Aplicaciones full-stack pequeñas y medianas
- Librerías con buena documentación
- Proyectos con tests comprehensivos
- Código de desarrolladores reconocidos

**Ejemplo de flujo de aprendizaje:**
```
1. Clona el proyecto
2. Pide a Claude Code un resumen general
3. Identifica las partes más interesantes
4. Profundiza en componentes específicos
5. Intenta hacer pequeños cambios
6. Lee los tests para entender el comportamiento esperado
```

---

## Ejercicio Práctico: Probando Cada Enfoque

### Ejercicio 1: Desde Cero

Crea un nuevo directorio y pide a Claude Code:

```
Crea una aplicación de calculadora simple en Python que:
- Tenga funciones para sumar, restar, multiplicar y dividir
- Incluya una función main que pida al usuario dos números y una operación
- Maneje errores como división por cero
- Tenga tests unitarios básicos
```

### Ejercicio 2: Modificando Código Existente

Después de crear la calculadora, pide:

```
Añade las siguientes características a la calculadora:
- Operación de potencia
- Operación de raíz cuadrada
- Historial de las últimas 5 operaciones
- Opción para limpiar el historial
```

### Ejercicio 3: Entendiendo Código

Pide a Claude Code:

```
Explícame cómo funciona el manejo de errores en el código que acabas de crear.
¿Qué pasaría si el usuario ingresa texto en lugar de números?
```

---

## Mejores Prácticas

### Para Empezar Desde Cero

1. **Planifica antes de codificar** - Ten clara la estructura básica
2. **Empieza simple** - Añade complejidad gradualmente
3. **Pide explicaciones** - Entiende el código que se genera
4. **Revisa el código** - No aceptes todo ciegamente

### Para Código Existente

1. **Explora primero** - Entiende antes de modificar
2. **Haz cambios pequeños** - Evita refactorizaciones masivas
3. **Prueba después de cada cambio** - Verifica que nada se rompió
4. **Usa control de versiones** - Haz commits frecuentes

### Para Plantillas

1. **Elige la plantilla adecuada** - No sobrecompliques
2. **Personaliza según necesites** - Las plantillas son puntos de partida
3. **Entiende la estructura** - Sabe por qué cada archivo existe
4. **Actualiza dependencias** - Mantén el proyecto seguro

### Para Repositorios Clonados

1. **Lee el README primero** - Entiende el propósito
2. **Revisa los issues** - Conoce los problemas conocidos
3. **Sigue las guías de contribución** - Respeta las reglas del proyecto
4. **Empieza por issues fáciles** - "good first issue" es tu amigo

---

## Lista de Verificación del Módulo 2

Antes de continuar al Módulo 3, verifica que puedas:

- [ ] Crear un proyecto desde cero con Claude Code
- [ ] Explorar y entender código existente
- [ ] Pedir estructuras de proyecto basadas en plantillas
- [ ] Clonar y analizar repositorios
- [ ] Elegir el enfoque correcto para cada situación
- [ ] Hacer cambios incrementales a código existente

---

## ¿Qué Sigue?

¡Excelente trabajo! Ahora conoces múltiples formas de comenzar proyectos con Claude Code.

En el **Módulo 3**, profundizaremos en las herramientas de Claude Code - entenderás exactamente qué puede hacer cada herramienta y cuándo usarlas.

---

*¡Módulo 2 Completado!*
