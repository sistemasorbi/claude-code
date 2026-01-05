# Módulo 4: Trabajando con Archivos y Código

**Objetivo:** Aprende cómo leer, escribir y modificar código efectivamente

**Tiempo Estimado:** 40-50 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Leer y entender código existente eficientemente
- Escribir nuevos archivos con Claude Code
- Hacer ediciones precisas sin romper código
- Refactorizar código para mejorarlo
- Navegar grandes bases de código
- Aprender patrones del código existente

---

## Lección 1: Leyendo Código

### Pidiendo Ver Archivos

Hay muchas formas de pedir a Claude Code que lea archivos:

**Formas directas:**
```
Muéstrame el archivo server.js
```

```
Lee el contenido de src/utils/helpers.py
```

```
¿Qué hay en package.json?
```

### Leyendo Partes Específicas

Para archivos grandes, puedes pedir partes específicas:

```
Muéstrame solo la función handleLogin en auth.js
```

```
Lee las primeras 50 líneas de app.py
```

```
Muéstrame las líneas 100-150 de database.js
```

### Entendiendo Código

No solo leas - pide explicaciones:

```
Lee server.js y explícame qué hace cada función
```

```
Muéstrame la lógica de autenticación y explica el flujo paso a paso
```

```
Lee el middleware de errores y dime si sigue mejores prácticas
```

### Comparando Archivos

Puedes pedir comparaciones:

```
Compara las funciones en utils.js y helpers.js
```

```
¿Qué diferencias hay entre config.dev.js y config.prod.js?
```

---

## Lección 2: Escribiendo Nuevos Archivos

### Creación Básica

**Archivo simple:**
```
Crea un archivo llamado constantes.js con las constantes de la aplicación
```

**Con especificaciones:**
```
Crea un archivo utils/validators.js que contenga:
- Una función para validar emails
- Una función para validar contraseñas (mínimo 8 caracteres)
- Una función para validar nombres de usuario
```

### Creando Múltiples Archivos

Puedes pedir varios archivos a la vez:

```
Crea la estructura de un componente React llamado UserProfile:
- UserProfile.jsx con el componente
- UserProfile.css con estilos básicos
- UserProfile.test.js con tests
- index.js que exporte el componente
```

### Creando Desde Ejemplos

Si tienes un patrón que te gusta:

```
Mira cómo está estructurado el componente Button.jsx
y crea un componente Card.jsx siguiendo el mismo patrón
```

### Creando Archivos de Configuración

```
Crea un archivo .env.example con las variables de entorno que necesita este proyecto
```

```
Genera un archivo docker-compose.yml para ejecutar la aplicación con una base de datos PostgreSQL
```

---

## Lección 3: Editando Código Existente

### Ediciones Simples

**Cambios de valor:**
```
En config.js, cambia el timeout de 5000 a 10000 milisegundos
```

**Renombrar:**
```
Renombra la función getData a fetchUserData en el archivo api.js
```

### Añadiendo Código

**Añadir función:**
```
En utils.js, añade una función formatDate que tome una fecha y devuelva el formato DD/MM/YYYY
```

**Añadir importación:**
```
Añade la importación de lodash al inicio de helpers.js
```

**Añadir manejo de errores:**
```
Añade try-catch a todas las funciones async en userService.js
```

### Eliminando Código

```
Elimina todos los console.log de producción en src/
```

```
Quita la función deprecatedMethod de utils.js y todas sus referencias
```

### Ediciones Precisas

Claude Code hace ediciones precisas que no rompen el código:

**Antes (en server.js):**
```javascript
const express = require('express');
const app = express();
const PORT = 3000;
```

**Tu solicitud:**
```
Cambia el puerto a 8080 y añade cors
```

**Después:**
```javascript
const express = require('express');
const cors = require('cors');
const app = express();
app.use(cors());
const PORT = 8080;
```

Claude Code solo cambia lo necesario y añade lo nuevo en el lugar correcto.

---

## Lección 4: Refactorización

### ¿Qué es Refactorizar?

Refactorizar es mejorar el código sin cambiar su comportamiento.

### Refactorizaciones Comunes

**Extraer función:**
```
Este código en handleSubmit está muy largo.
Extrae la lógica de validación a una función separada.
```

**Simplificar condicionales:**
```
Simplifica los if-else anidados en la función processOrder
```

**Modernizar código:**
```
Convierte las funciones con callback en async/await en userApi.js
```

**Mejorar nombres:**
```
Renombra las variables con nombres poco descriptivos en utils.js
```

### Ejemplo de Refactorización

**Antes:**
```javascript
function p(d) {
    let r = [];
    for (let i = 0; i < d.length; i++) {
        if (d[i].a === true) {
            r.push(d[i]);
        }
    }
    return r;
}
```

**Solicitud:**
```
Refactoriza esta función para que sea más legible y use métodos modernos de JavaScript
```

**Después:**
```javascript
function filterActiveItems(items) {
    return items.filter(item => item.isActive);
}
```

---

## Lección 5: Navegando Bases de Código Grandes

### Estrategias de Exploración

**Empezar por lo general:**
```
Dame un resumen de la estructura de este proyecto
```

**Identificar puntos de entrada:**
```
¿Cuál es el archivo principal de esta aplicación?
```

**Seguir el flujo:**
```
Muéstrame el flujo desde que un usuario hace login hasta que recibe el token
```

### Encontrando Código Específico

**Por funcionalidad:**
```
¿Dónde se implementa la paginación?
```

**Por nombre:**
```
Encuentra la definición de la clase DatabaseConnection
```

**Por patrón:**
```
Muéstrame todos los lugares donde se hace una llamada a la API
```

### Entendiendo Dependencias

```
¿Qué archivos importan userService.js?
```

```
¿De qué depende el módulo de autenticación?
```

```
Muéstrame el grafo de dependencias del componente Dashboard
```

---

## Lección 6: Aprendiendo de Código Existente

### Identificando Patrones

```
¿Qué patrón de diseño se usa en este proyecto para manejar el estado?
```

```
¿Cómo está estructurado el manejo de errores en esta aplicación?
```

### Aplicando Patrones

```
Usa el mismo patrón de validación que se usa en userController.js
para crear productController.js
```

```
Sigue la convención de nombres del proyecto para crear nuevas rutas
```

### Mejorando Basándose en Patrones

```
Los otros controladores tienen tests. Genera tests para paymentController
siguiendo el mismo estilo.
```

---

## Ejercicio Práctico

### Proyecto: Mejorando una Aplicación

Crea o usa un proyecto existente y practica:

**1. Lectura:**
```
Lee todos los archivos de configuración y hazme un resumen
```

**2. Escritura:**
```
Crea un archivo CONTRIBUTING.md con guías para contribuir al proyecto
```

**3. Edición:**
```
Añade comentarios JSDoc a las funciones principales
```

**4. Refactorización:**
```
Encuentra código duplicado y extráelo a funciones reutilizables
```

**5. Navegación:**
```
Crea un diagrama de la arquitectura del proyecto basándote en el código
```

---

## Mejores Prácticas

### Para Leer Código

1. **Lee el contexto primero** - Entiende el propósito del archivo
2. **Sigue las importaciones** - Entiende las dependencias
3. **Lee los tests** - Revelan el comportamiento esperado
4. **Busca patrones** - Identifica convenciones del proyecto

### Para Escribir Código

1. **Sigue las convenciones existentes** - Mantén consistencia
2. **Escribe código auto-documentado** - Usa nombres descriptivos
3. **Incluye manejo de errores** - Desde el principio
4. **Piensa en tests** - Escribe código testeable

### Para Editar Código

1. **Entiende antes de cambiar** - Lee primero
2. **Haz cambios mínimos** - No refactorices de más
3. **Verifica después de editar** - Ejecuta tests
4. **Usa control de versiones** - Commit antes de cambios grandes

### Para Refactorizar

1. **Ten tests primero** - Asegura que no rompes nada
2. **Pasos pequeños** - Refactoriza incrementalmente
3. **Un cambio a la vez** - No mezcles refactorizaciones
4. **Verifica constantemente** - Ejecuta tests frecuentemente

---

## Lista de Verificación del Módulo 4

Verifica que puedas:

- [ ] Leer archivos completos y parciales
- [ ] Pedir explicaciones del código
- [ ] Crear nuevos archivos con especificaciones
- [ ] Hacer ediciones precisas
- [ ] Refactorizar código para mejorarlo
- [ ] Navegar bases de código grandes
- [ ] Identificar y aplicar patrones

---

## Comandos Útiles

### Lectura
- "Muéstrame [archivo]"
- "Lee las líneas [X] a [Y] de [archivo]"
- "Explica [función/clase] en [archivo]"

### Escritura
- "Crea [archivo] con [contenido/propósito]"
- "Genera [tipo de archivo] para [propósito]"
- "Escribe [archivo] siguiendo el patrón de [otro archivo]"

### Edición
- "En [archivo], cambia [X] a [Y]"
- "Añade [código] a [archivo]"
- "Elimina [código] de [archivo]"

### Refactorización
- "Refactoriza [código] para [mejora]"
- "Extrae [código] a [función/componente]"
- "Moderniza [código] usando [patrón/técnica]"

---

## ¿Qué Sigue?

¡Excelente trabajo! Ahora sabes trabajar eficientemente con archivos y código.

En el **Módulo 5**, aprenderemos el arte del prompting efectivo - cómo comunicar tareas de programación de manera clara y precisa para obtener los mejores resultados.

---

*¡Módulo 4 Completado!*
