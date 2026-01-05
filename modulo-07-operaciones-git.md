# Módulo 7: Operaciones Git y Control de Versiones

**Objetivo:** Domina los flujos de trabajo de Git con Claude Code

**Tiempo Estimado:** 40-50 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Usar Git efectivamente con la ayuda de Claude Code
- Crear commits con mensajes significativos
- Trabajar con ramas de forma eficiente
- Crear y gestionar pull requests
- Revisar código antes de hacer commit
- Resolver conflictos de merge con asistencia de IA
- Usar GitHub CLI (gh) integrado

---

## Lección 1: Fundamentos de Git con Claude Code

### ¿Por Qué Git es Importante?

Git es un sistema de control de versiones que:
- Guarda el historial de tu código
- Permite colaborar con otros
- Te deja experimentar sin miedo
- Facilita revertir errores

### Inicializando un Repositorio

Si tu proyecto no tiene Git:

```
Inicializa un repositorio Git en este directorio
```

Claude Code ejecutará:
```bash
git init
```

También puede crear un `.gitignore` apropiado:

```
Crea un archivo .gitignore para un proyecto Node.js
```

### Verificando el Estado

```
Muéstrame el estado de Git
```

Claude Code ejecutará `git status` y explicará:
- Archivos modificados
- Archivos nuevos sin seguimiento
- Archivos preparados para commit
- El estado de tu rama

---

## Lección 2: Creando Commits

### Commits Básicos

**Forma simple:**
```
Haz commit de todos los cambios
```

**Con mensaje específico:**
```
Haz commit con el mensaje "Añade validación de formulario"
```

### Commits Bien Estructurados

Claude Code puede ayudarte a escribir buenos mensajes:

```
Revisa los cambios actuales y crea un commit con un mensaje descriptivo
```

Claude Code:
1. Analizará qué cambió
2. Generará un mensaje que describe los cambios
3. Creará el commit

### Anatomía de un Buen Mensaje de Commit

```
tipo: descripción corta (máx 50 caracteres)

Cuerpo opcional que explica:
- Qué se cambió
- Por qué se cambió
- Cualquier consideración importante
```

**Tipos comunes:**
- `feat:` - Nueva característica
- `fix:` - Corrección de bug
- `docs:` - Documentación
- `style:` - Formato (sin cambios de código)
- `refactor:` - Refactorización
- `test:` - Añadir o modificar tests
- `chore:` - Tareas de mantenimiento

### Ejemplos de Buenos Commits

```
Crea commits separados para:
1. Los cambios en el modelo de usuario
2. Las nuevas rutas de API
3. Los tests que añadí
```

Claude Code creará commits organizados y descriptivos.

---

## Lección 3: Trabajando con Ramas

### Crear una Nueva Rama

```
Crea una nueva rama llamada feature/login-social
```

Claude Code ejecutará:
```bash
git checkout -b feature/login-social
```

### Cambiar de Rama

```
Cambia a la rama main
```

```
Vuelve a la rama en la que estaba trabajando
```

### Ver Ramas

```
Muéstrame todas las ramas del proyecto
```

### Convenciones de Nombres de Ramas

**Patrones comunes:**
- `feature/nombre-caracteristica` - Nuevas características
- `fix/descripcion-bug` - Correcciones
- `hotfix/problema-urgente` - Correcciones urgentes
- `refactor/que-se-mejora` - Refactorizaciones

**Pedir ayuda con nombres:**
```
Sugiere un nombre de rama para implementar sistema de notificaciones
```

---

## Lección 4: Revisando Cambios

### Ver Cambios Antes de Commit

```
Muéstrame qué ha cambiado desde el último commit
```

Claude Code ejecutará `git diff` y explicará los cambios.

### Revisión Detallada

```
Revisa mis cambios y verifica que:
- No hay console.log de debug
- No hay credenciales hardcodeadas
- El código sigue las convenciones del proyecto
```

### Revisar Archivos Específicos

```
Muéstrame los cambios solo en los archivos de autenticación
```

### Descartar Cambios

Si no quieres mantener cambios:

```
Descarta los cambios en config.js
```

```
Descarta todos los cambios no guardados (¡cuidado!)
```

---

## Lección 5: Pull Requests

### Crear un Pull Request

Después de hacer commits en tu rama:

```
Crea un pull request para mis cambios
```

Claude Code:
1. Verificará que estés en la rama correcta
2. Hará push si es necesario
3. Creará el PR con descripción automática

### Pull Request Detallado

```
Crea un pull request con:
- Título: "Añade sistema de autenticación OAuth"
- Descripción de los cambios
- Pasos para probar
- Screenshots si aplica
```

### Estructura de un Buen PR

Claude Code puede generar PRs con esta estructura:

```markdown
## Resumen
Breve descripción de qué hace este PR

## Cambios
- Lista de cambios principales
- Archivos modificados importantes

## Cómo Probar
1. Paso 1
2. Paso 2
3. Resultado esperado

## Checklist
- [ ] Tests pasan
- [ ] Documentación actualizada
- [ ] Sin warnings del linter
```

### Ver PRs Existentes

```
Muéstrame los pull requests abiertos
```

```
Dame información sobre el PR #42
```

---

## Lección 6: Resolviendo Conflictos

### Entendiendo Conflictos

Los conflictos ocurren cuando:
- Dos personas modifican la misma línea
- Una rama elimina algo que otra modifica
- Cambios incompatibles se intentan fusionar

### Detectando Conflictos

```
Intenta hacer merge de la rama main a mi rama actual
```

Si hay conflictos, Claude Code te lo dirá.

### Resolviendo con Claude Code

```
Ayúdame a resolver los conflictos de merge
```

Claude Code:
1. Mostrará los archivos con conflictos
2. Explicará qué está en conflicto
3. Sugerirá resoluciones
4. Te dejará elegir

### Ejemplo de Resolución

```
Hay un conflicto en auth.js.
El código de main tiene una implementación diferente.
¿Quiero mantener mi código, el de main, o combinar ambos?
```

**Opciones:**
```
Mantén mi versión del código
```

```
Usa la versión de main
```

```
Combina ambas versiones de forma que [explicación]
```

---

## Lección 7: GitHub CLI (gh)

### Comandos Útiles

Claude Code puede usar `gh` para GitHub:

**Ver issues:**
```
Muéstrame los issues abiertos en este repositorio
```

**Crear issue:**
```
Crea un issue para reportar el bug que encontré
```

**Ver estado de CI:**
```
¿Pasaron los checks del último commit?
```

**Revisar PRs:**
```
Muéstrame los comentarios en el PR #15
```

### Trabajo con Issues

```
Muéstrame el issue #23 y ayúdame a implementar la solución
```

```
Cierra el issue #45 con un commit que lo referencia
```

---

## Lección 8: Flujos de Trabajo Comunes

### Flujo de Feature Branch

1. **Crear rama:**
   ```
   Crea una rama para implementar la característica de exportar a PDF
   ```

2. **Hacer cambios:**
   ```
   [Implementar la característica]
   ```

3. **Commits incrementales:**
   ```
   Haz commit de los cambios actuales
   ```

4. **Actualizar con main:**
   ```
   Actualiza mi rama con los últimos cambios de main
   ```

5. **Crear PR:**
   ```
   Crea un pull request para esta característica
   ```

### Flujo de Hotfix

1. **Crear rama desde main:**
   ```
   Crea una rama hotfix/corregir-login desde main
   ```

2. **Hacer la corrección:**
   ```
   [Corregir el problema]
   ```

3. **Commit y PR urgente:**
   ```
   Crea un commit y PR para esta corrección urgente
   ```

---

## Ejercicio Práctico

### Ejercicio 1: Flujo Completo

1. Crea una rama nueva:
   ```
   Crea una rama feature/mejoras-readme
   ```

2. Haz cambios:
   ```
   Mejora el README con mejor documentación
   ```

3. Revisa los cambios:
   ```
   Muéstrame qué cambió
   ```

4. Haz commit:
   ```
   Haz commit con un mensaje descriptivo
   ```

5. Crea PR:
   ```
   Crea un pull request
   ```

### Ejercicio 2: Resolver Conflicto Simulado

Pide a Claude Code que te guíe:
```
Simula un escenario de conflicto y ayúdame a practicar resolverlo
```

---

## Mejores Prácticas

### Para Commits

1. **Commits pequeños y frecuentes** - Más fácil de revisar y revertir
2. **Mensajes descriptivos** - Explica el "por qué", no solo el "qué"
3. **Un cambio por commit** - No mezcles características diferentes
4. **Verifica antes de commit** - Ejecuta tests, revisa cambios

### Para Ramas

1. **Nombres descriptivos** - `feature/login-google` no `rama1`
2. **Ramas cortas** - Merge frecuente a main
3. **Actualiza regularmente** - Evita conflictos grandes
4. **Elimina ramas merged** - Mantén el repo limpio

### Para PRs

1. **Descripción clara** - Explica qué y por qué
2. **PRs pequeños** - Más fáciles de revisar
3. **Incluye tests** - Demuestra que funciona
4. **Responde a comentarios** - Colabora con revisores

---

## Comandos Git Rápidos

| Acción | Cómo Pedirlo |
|--------|--------------|
| Ver estado | "Muéstrame el estado de git" |
| Crear rama | "Crea rama [nombre]" |
| Cambiar rama | "Cambia a rama [nombre]" |
| Ver cambios | "Muéstrame el diff" |
| Hacer commit | "Haz commit de los cambios" |
| Ver historial | "Muéstrame los últimos commits" |
| Crear PR | "Crea un pull request" |
| Ver PRs | "Muéstrame los PRs abiertos" |

---

## Lista de Verificación del Módulo 7

Verifica que puedas:

- [ ] Inicializar repositorios y crear .gitignore
- [ ] Crear commits con mensajes descriptivos
- [ ] Trabajar con ramas efectivamente
- [ ] Revisar cambios antes de commit
- [ ] Crear pull requests bien documentados
- [ ] Resolver conflictos de merge
- [ ] Usar comandos básicos de GitHub CLI

---

## ¿Qué Sigue?

¡Excelente trabajo dominando Git con Claude Code!

En el **Módulo 8**, aprenderemos sobre depuración y testing - cómo encontrar bugs, corregirlos, y escribir tests para prevenir regresiones.

---

*¡Módulo 7 Completado!*
