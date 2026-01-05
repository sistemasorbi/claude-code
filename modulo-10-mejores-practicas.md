# Módulo 10: Mejores Prácticas de Flujo de Trabajo de Desarrollo

**Objetivo:** Aprende flujos de trabajo de desarrollo profesional para maximizar productividad con Claude Code

**Tiempo Estimado:** 35-45 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Usar gestión de tareas efectivamente con TodoWrite
- Seguir mejores prácticas de revisión de código
- Escribir documentación clara y útil
- Implementar manejo robusto de errores
- Añadir logging significativo
- Organizar código para mantenibilidad
- Aplicar mejores prácticas de seguridad
- Optimizar para rendimiento

---

## Lección 1: Gestión de Tareas con TodoWrite

### ¿Qué es TodoWrite?

**TodoWrite** es el sistema de gestión de tareas integrado de Claude Code que te ayuda a:
- Rastrear en qué estás trabajando
- Ver progreso de un vistazo
- Mantenerte organizado en tareas complejas
- Comunicar progreso a otros

---

### Cuándo Usar TodoWrite

**Usa TodoWrite para:**
- Características de múltiples pasos (3+ pasos)
- Tareas complejas que requieren planificación
- Cuando el usuario solicita múltiples cosas
- Rastrear progreso de implementación

**No uses para:**
- Tareas simples y únicas
- Cambios triviales
- Correcciones rápidas

---

### Creando una Lista de Tareas

```
Necesito añadir autenticación de usuarios a la app.

Crea una lista de tareas para:
1. Configurar tablas de BD para usuarios
2. Crear endpoint de registro
3. Crear endpoint de login
4. Añadir generación de token JWT
5. Añadir middleware de autenticación
6. Proteger rutas existentes
7. Añadir tests
8. Actualizar documentación
```

**Claude Code crea:**
```
✓ Configurar tablas de BD para usuarios
→ Crear endpoint de registro (en progreso)
○ Crear endpoint de login
○ Añadir generación de token JWT
○ Añadir middleware de autenticación
○ Proteger rutas existentes
○ Añadir tests
○ Actualizar documentación
```

---

### Rastreando Progreso

**Claude Code automáticamente:**
- Marca tareas in_progress al empezar
- Marca completadas cuando termina
- Muestra estado actual
- Solo una tarea in_progress a la vez

**Puedes pedir:**
```
Muéstrame la lista de tareas actual
¿Qué queda por hacer?
Marca la tarea 3 como completada
```

---

## Lección 2: Mejores Prácticas de Revisión de Código

### Revisar Antes de Hacer Commit

**Siempre revisa cambios antes de hacer commit:**

```
Antes de hacer commit, muéstrame:
1. Todos los archivos que cambiaron
2. Qué cambió en cada archivo
3. Cualquier problema potencial
4. Sugerencias de mejora
```

---

### Lista de Verificación de Auto-Revisión

**Pide a Claude Code que verifique:**

```
Revisa mis cambios y verifica:
- Vulnerabilidades de seguridad
- Problemas de rendimiento
- Manejo de errores faltante
- Duplicación de código
- Nombres de variables poco claros
- Tests faltantes
- Documentación incompleta
```

---

### Revisando Código de Otros

**Cuando revisas pull requests:**

```
Necesito revisar este pull request.
Ayúdame a:
1. Entender qué hace
2. Verificar bugs
3. Verificar que sigue nuestros patrones
4. Sugerir mejoras
5. Verificar cobertura de tests
```

---

## Lección 3: Documentación

### Comentarios de Código

**Cuándo añadir comentarios:**

**Buenos comentarios explican POR QUÉ:**
```javascript
// Usa backoff exponencial para evitar sobrecargar la API
// cuando está experimentando problemas
const delay = Math.pow(2, retryCount) * 1000;
```

**Malos comentarios explican QUÉ (el código debe ser auto-explicativo):**
```javascript
// Multiplica 2 a la potencia de retryCount por 1000
const delay = Math.pow(2, retryCount) * 1000;
```

---

### Documentación de Funciones

**Solicita comentarios JSDoc:**

```
Añade comentarios JSDoc a todas las funciones en userService.js con:
- Descripción de lo que hace la función
- Tipos y descripciones de parámetros
- Tipo y descripción de retorno
- Ejemplos de uso
- Cualquier excepción que lance
```

---

### Archivos README

**Crea READMEs comprehensivos:**

```
Crea un README.md para este proyecto con:
- Descripción del proyecto
- Lista de características
- Prerrequisitos
- Instrucciones de instalación
- Ejemplos de uso
- Documentación de API
- Guías de contribución
- Información de licencia
```

---

### Documentación de API

```
Genera documentación de API para todos los endpoints en routes/:
- Para cada endpoint lista:
  * Método HTTP y ruta
  * Descripción
  * Requisitos de autenticación
  * Parámetros/body de solicitud
  * Formato de respuesta con ejemplos
  * Posibles errores
```

---

## Lección 4: Manejo de Errores

### Manejo Comprehensivo de Errores

**Pide manejo de errores apropiado:**

```
Añade manejo de errores a las consultas de BD en userService.js:
- Bloques try/catch para todas las operaciones async
- Mensajes de error específicos para diferentes fallos
- Tipos de error apropiados (no solo Error)
- Logging de errores
- No exponer errores internos a usuarios
```

---

### Tipos de Error

**Crea clases de error personalizadas:**

```
Crea clases de error personalizadas para:
- ValidationError (400)
- AuthenticationError (401)
- AuthorizationError (403)
- NotFoundError (404)
- DatabaseError (500)

Cada una debe:
- Extender Error
- Establecer código de estado apropiado
- Tener mensaje significativo
```

---

### Respuestas de Error

**Formato consistente de error:**

```
Crea middleware de respuesta de error que retorne:
{
  "error": {
    "status": 400,
    "message": "Validación fallida",
    "details": [
      "Email es requerido",
      "Contraseña debe tener al menos 8 caracteres"
    ]
  }
}
```

---

## Lección 5: Logging

### Logging Estratégico

**Qué registrar:**
- Operaciones importantes (login de usuario, cambios de datos)
- Errores y excepciones
- Métricas de rendimiento
- Eventos de seguridad
- Llamadas a APIs externas

**Qué NO registrar:**
- Contraseñas o datos sensibles
- Info de debug excesiva en producción
- Información personal identificable (PII)

---

### Implementar Logging

```
Añade logging a lo largo de la aplicación:

1. Crea utilidad de logger con niveles:
   - error: Errores que necesitan atención
   - warn: Condiciones de advertencia
   - info: Eventos importantes
   - debug: Depuración detallada (solo dev)

2. Añade logging a:
   - Todos los manejadores de error
   - Intentos de autenticación
   - Operaciones de BD
   - Llamadas a APIs externas

3. Incluye contexto útil:
   - Timestamp
   - ID de usuario (si aplica)
   - ID de solicitud
   - Operación siendo realizada
```

---

### Formato de Log

**Solicita logs estructurados:**

```
Configura logger para output:
{
  "timestamp": "2025-01-15T10:30:00.000Z",
  "level": "info",
  "message": "Usuario inició sesión",
  "userId": "123",
  "ip": "192.168.1.1",
  "requestId": "abc-def-123"
}
```

---

## Lección 6: Organización de Código

### Estructura de Archivos

**Organiza por característica:**

```
Ayúdame a reorganizar de:
src/
  ├── routes/       (todas las rutas juntas)
  ├── controllers/  (todos los controladores juntos)
  └── models/       (todos los modelos juntos)

A:
src/
  ├── users/
  │   ├── user.model.js
  │   ├── user.controller.js
  │   ├── user.routes.js
  │   └── user.test.js
  ├── tasks/
  │   ├── task.model.js
  │   ├── task.controller.js
  │   ├── task.routes.js
  │   └── task.test.js
```

---

### Principio DRY (No Te Repitas)

**Encuentra y elimina duplicación:**

```
Encuentra código duplicado en este proyecto y refactoriza:
1. Busca lógica repetida
2. Extrae en funciones compartidas
3. Crea módulos de utilidades
4. Actualiza todos los usos
5. Verifica que nada se rompa
```

---

### Responsabilidad Única

```
El archivo userController.js está haciendo demasiado.
Refactoriza para que:
- El controlador solo maneje solicitudes/respuestas HTTP
- La capa de servicio maneje lógica de negocio
- La capa de repositorio maneje base de datos
- Cada capa tenga responsabilidad única
```

---

## Lección 7: Mejores Prácticas de Seguridad

### Validación de Entrada

```
Añade validación de entrada comprehensiva:
- Valida toda entrada de usuario
- Sanitiza datos antes de consultas de BD
- Usa consultas parametrizadas (prevenir SQL injection)
- Valida uploads de archivos
- Verifica límites de longitud de entrada
- Permite solo valores permitidos (whitelist)
```

---

### Autenticación y Autorización

```
Revisa y mejora seguridad de autenticación:
- Usa bcrypt para hashing de contraseñas (salt rounds 10+)
- Implementa rate limiting en login
- Añade bloqueo de cuenta después de intentos fallidos
- Usa solo HTTPS
- Configuración segura de cookies
- Valida tokens JWT apropiadamente
- Implementa refresh tokens
```

---

### Gestión de Secretos

```
Asegura que no haya secretos en código:
1. Encuentra cualquier secreto hardcodeado
2. Mueve a variables de entorno
3. Añade .env a .gitignore
4. Crea plantilla .env.example
5. Documenta vars de entorno requeridas
```

---

### Headers de Seguridad

```
Añade headers de seguridad usando helmet.js:
- Content Security Policy
- X-Frame-Options
- X-Content-Type-Options
- Strict-Transport-Security
- X-XSS-Protection
```

---

## Lección 8: Optimización de Rendimiento

### Optimización de Base de Datos

```
Optimiza consultas de base de datos:
1. Añade índices en columnas consultadas frecuentemente
2. Corrige problemas de consulta N+1
3. Usa joins en lugar de múltiples consultas
4. Implementa paginación para sets de resultados grandes
5. Añade logging de consultas de BD para encontrar consultas lentas
```

---

### Caché

```
Implementa caché para operaciones costosas:
- Cachea consultas de BD que raramente cambian
- Cachea respuestas de APIs externas
- Establece TTL (time to live) apropiado
- Implementa estrategia de invalidación de caché
```

---

### Operaciones Async

```
Optimiza con operaciones async:
- Usa Promise.all para operaciones paralelas
- No uses await en loops (usa Promise.all o for...of)
- Mueve operaciones lentas a jobs en segundo plano
- Implementa colas de jobs para tareas pesadas
```

---

## Lección 9: Ejemplo de Flujo de Trabajo Completo

### Flujo de Desarrollo de Características

**Añadiendo una característica profesionalmente:**

**Paso 1: Planificar**
```
Crea una lista de tareas para añadir característica de reset de contraseña
```

**Paso 2: Crear rama**
```
Crea una nueva rama git: feature/password-reset
```

**Paso 3: Escribir tests primero (TDD)**
```
Escribe tests para reset de contraseña:
- Solicitar token de reset
- Verificar token
- Resetear contraseña
```

**Paso 4: Implementar**
```
Implementa reset de contraseña siguiendo el plan:
- Añadir columna de BD para tokens de reset
- Crear endpoint de solicitud de reset
- Crear endpoint de verificar y resetear
- Añadir validación apropiada
- Añadir manejo de errores
- Añadir logging
```

**Paso 5: Revisar**
```
Revisa todos los cambios antes de hacer commit:
- Verificar problemas de seguridad
- Verificar manejo de errores
- Verificar cobertura de tests
- Revisar calidad de código
```

**Paso 6: Commit**
```
Crea un commit con mensaje significativo
```

**Paso 7: Crear PR**
```
Crea un pull request con:
- Resumen de cambios
- Pasos de testing
- Consideraciones de seguridad
```

---

## Práctica Práctica

### Ejercicio 1: Refactorizar para Calidad

**Tarea:** Mejorar calidad de código

```
Toma un archivo existente desordenado y refactorízalo:
1. Añade manejo de errores apropiado
2. Añade logging
3. Divide funciones grandes
4. Elimina duplicación
5. Añade documentación
6. Añade tests
```

---

### Ejercicio 2: Auditoría de Seguridad

**Tarea:** Encuentra y corrige problemas de seguridad

```
Revisa esta aplicación por problemas de seguridad:
1. Verifica validación de entrada
2. Verifica autenticación
3. Busca riesgos de SQL injection
4. Verifica secretos expuestos
5. Verifica headers seguros
6. Corrige todos los problemas encontrados
```

---

### Ejercicio 3: Optimización de Rendimiento

**Tarea:** Acelera código lento

```
Este endpoint es lento. Optimízalo:
1. Encuentra el cuello de botella
2. Añade índices de BD
3. Implementa caché
4. Optimiza consultas
5. Mide la mejora
```

---

## Lista de Verificación del Módulo 10

Antes de completar este curso, asegúrate de poder:

- [ ] Usar TodoWrite para gestión de tareas
- [ ] Revisar código antes de hacer commit
- [ ] Escribir documentación clara
- [ ] Implementar manejo de errores apropiado
- [ ] Añadir logging estratégico
- [ ] Organizar código de forma mantenible
- [ ] Seguir mejores prácticas de seguridad
- [ ] Optimizar para rendimiento
- [ ] Aplicar flujos de trabajo profesionales

---

## La Mentalidad del Desarrollador Profesional

### Calidad Sobre Velocidad

- Escríbelo bien la primera vez
- Los tests ahorran tiempo a largo plazo
- La documentación ayuda al tú del futuro
- La seguridad no es opcional

### Comunicación

- Mensajes de commit claros
- Descripciones de PR comprehensivas
- Buena documentación
- Logs significativos

### Mejora Continua

- Revisa tu propio código críticamente
- Aprende de los errores
- Mantente actualizado en mejores prácticas
- Refactoriza cuando sea apropiado

---

## ¿Qué Sigue?

¡Felicidades! Has completado los **10 módulos principales!**

Ahora tienes:
- ✅ Fundamento sólido en Claude Code
- ✅ Capacidad de construir aplicaciones completas
- ✅ Habilidades de desarrollo profesional
- ✅ Conocimiento de mejores prácticas

**Opcional: Módulos Avanzados**
- Módulo 11: Servidores MCP
- Módulo 12: Skills y Hooks
- Módulo 13: Múltiples Lenguajes/Frameworks
- Módulo 14: Integración de API
- Módulo 15: Despliegue a Producción

**¡O empieza a construir!**
- Aplica estas habilidades a proyectos reales
- Contribuye a código abierto
- Construye tu portafolio
- Ayuda a otros a aprender

---

## Consejos Pro Finales

1. **Planifica antes de codificar** - Unos minutos planeando ahorran horas depurando

2. **Testea mientras construyes** - No dejes testing para después

3. **Haz commits frecuentes** - Commits pequeños y frecuentes son mejores

4. **Documenta mientras está fresco** - Escribe docs mientras recuerdas por qué

5. **Seguridad primero** - Es más difícil de añadir después

6. **El rendimiento importa** - Pero no optimices prematuramente

7. **El código se lee más de lo que se escribe** - Optimiza para legibilidad

8. **Pide ayuda** - Claude Code siempre está ahí para asistir

---

*¡Módulo 10 Completado - Curso Principal Terminado!*

**¡Ahora estás listo para construir aplicaciones profesionales con Claude Code!**
