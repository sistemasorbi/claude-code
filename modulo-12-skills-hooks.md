# Módulo 12: Skills y Hooks - Personalizando Claude Code

**Objetivo:** Personaliza el comportamiento de Claude Code con skills y hooks

**Tiempo Estimado:** 30-40 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Entender qué son skills y hooks
- Crear comandos slash personalizados (skills)
- Configurar hooks para automatización
- Personalizar ajustes de Claude Code
- Integrar con tu IDE
- Crear flujos de trabajo personalizados

---

## Lección 1: Entendiendo Skills

### ¿Qué son los Skills?

Los **Skills** son comandos slash personalizados que puedes crear para automatizar tareas comunes.

**Ejemplos de skills integrados:**
- `/commit` - Crear un commit de git
- `/review-pr` - Revisar un pull request
- `/help` - Mostrar información de ayuda

**Puedes crear los tuyos:**
- `/deploy` - Desplegar tu aplicación
- `/test-all` - Ejecutar todos los tests y mostrar resultados
- `/review-code` - Revisar código con los estándares de tu equipo

---

### Creando Tu Primer Skill

**Los skills se definen en:**
```
~/.config/claude/skills/
```

**Crea un skill simple:**

```typescript
// ~/.config/claude/skills/hello.ts
export default {
  name: 'hello',
  description: 'Decir hola',
  run: async (context) => {
    return '¡Hola desde mi skill personalizado!';
  }
};
```

**Úsalo:**
```
/hello
```

---

### Ejemplos Prácticos de Skills

**Ejemplo 1: Skill de Deploy**

```typescript
// ~/.config/claude/skills/deploy.ts
export default {
  name: 'deploy',
  description: 'Despliega aplicación a producción',
  run: async (context) => {
    // Ejecuta script de despliegue
    await context.bash('npm run build');
    await context.bash('./scripts/deploy.sh');

    return '¡Despliegue completado!';
  }
};
```

---

**Ejemplo 2: Skill de Revisión de Código**

```typescript
// ~/.config/claude/skills/review.ts
export default {
  name: 'review',
  description: 'Revisa código contra estándares del equipo',
  run: async (context) => {
    // Obtiene diff de git actual
    const diff = await context.bash('git diff');

    // Revisa contra estándares
    const review = await context.agent({
      type: 'general',
      prompt: `Revisa este código contra nuestros estándares:\n${diff}\n\nVerifica:
      - Problemas de seguridad
      - Problemas de rendimiento
      - Violaciones de estilo de código
      - Tests faltantes`
    });

    return review;
  }
};
```

---

## Lección 2: Entendiendo Hooks

### ¿Qué son los Hooks?

Los **Hooks** son scripts que se ejecutan automáticamente cuando ocurren ciertos eventos.

**Hooks disponibles:**
- `user-prompt-submit-hook` - Antes de enviar tu mensaje
- `tool-use-hook` - Antes de usar una herramienta
- `response-hook` - Después de que Claude responda

---

### Creando Hooks

**Los hooks se definen en config.json:**

```json
{
  "hooks": {
    "user-prompt-submit-hook": "~/.config/claude/hooks/before-prompt.sh",
    "tool-use-hook": "~/.config/claude/hooks/before-tool.sh"
  }
}
```

---

### Ejemplos Prácticos de Hooks

**Ejemplo 1: Auto-formatear Antes de Commit**

```bash
#!/bin/bash
# ~/.config/claude/hooks/before-tool.sh

# Si la herramienta es Edit o Write, formatea el archivo
if [ "$TOOL_NAME" = "Edit" ] || [ "$TOOL_NAME" = "Write" ]; then
  # Ejecuta prettier en archivos JavaScript
  if [[ "$FILE_PATH" == *.js ]] || [[ "$FILE_PATH" == *.ts ]]; then
    npx prettier --write "$FILE_PATH"
  fi
fi
```

---

**Ejemplo 2: Hook de Verificación de Seguridad**

```bash
#!/bin/bash
# ~/.config/claude/hooks/security-check.sh

# Verifica datos sensibles antes de commit
if [[ "$PROMPT" == *"commit"* ]]; then
  # Busca claves API, contraseñas, etc.
  if git diff | grep -i "api_key\|password\|secret"; then
    echo "¡ADVERTENCIA: Se encontraron datos sensibles potenciales!"
    exit 1  # Bloquea la acción
  fi
fi
```

---

## Lección 3: Personalizando Ajustes

### Configuración de Claude Code

**Archivo de configuración principal:**
```
~/.config/claude/config.json
```

**Ejemplo de configuración:**

```json
{
  "apiKey": "tu-clave-api",
  "model": "claude-sonnet-4-20250514",
  "mcpServers": {
    ...
  },
  "hooks": {
    ...
  },
  "settings": {
    "autoCommit": false,
    "defaultBranch": "main",
    "editor": "code",
    "theme": "dark"
  }
}
```

---

### Personalizando Comportamiento

**Pide ayuda a Claude Code:**

```
Ayúdame a personalizar mis ajustes de Claude Code:
- Cambiar modelo por defecto a Haiku para tareas simples
- Configurar auto-formateo antes de commits
- Configurar mi editor preferido
- Establecer directorio de trabajo personalizado
```

---

## Lección 4: Integración con IDE

### Integración con VS Code

**Instala extensión de Claude Code:**
1. Abre VS Code
2. Busca "Claude Code"
3. Instala la extensión

**Características:**
- Asistencia de código inline
- Correcciones rápidas
- Explicaciones de código
- Sugerencias de refactorización

---

### Atajos de Teclado

**Configura atajos personalizados:**

**En VS Code:**
```json
// keybindings.json
[
  {
    "key": "ctrl+shift+c",
    "command": "claude.explain"
  },
  {
    "key": "ctrl+shift+r",
    "command": "claude.refactor"
  }
]
```

---

## Lección 5: Flujos de Trabajo Personalizados

### Creando Flujos de Trabajo Específicos del Proyecto

**Ejemplo: Flujo de Trabajo de Desarrollo de Características**

```typescript
// ~/.config/claude/skills/new-feature.ts
export default {
  name: 'new-feature',
  description: 'Inicia nueva característica con flujo de trabajo completo',
  run: async (context, featureName) => {
    // 1. Crea rama de característica
    await context.bash(`git checkout -b feature/${featureName}`);

    // 2. Crea lista de tareas
    await context.todo([
      { content: 'Escribir tests', status: 'pending' },
      { content: 'Implementar característica', status: 'pending' },
      { content: 'Actualizar documentación', status: 'pending' },
      { content: 'Crear PR', status: 'pending' }
    ]);

    // 3. Configura estructura de característica
    await context.bash(`mkdir -p src/features/${featureName}`);

    return `¡Característica ${featureName} inicializada! Listo para empezar desarrollo.`;
  }
};
```

**Úsalo:**
```
/new-feature autenticacion-usuarios
```

---

### Flujo de Trabajo de Testing

```typescript
// ~/.config/claude/skills/test-all.ts
export default {
  name: 'test-all',
  description: 'Ejecuta todos los tests y verificaciones',
  run: async (context) => {
    const results = [];

    // Ejecuta tests unitarios
    results.push(await context.bash('npm test'));

    // Ejecuta linter
    results.push(await context.bash('npm run lint'));

    // Ejecuta verificación de tipos
    results.push(await context.bash('npm run type-check'));

    // Ejecuta auditoría de seguridad
    results.push(await context.bash('npm audit'));

    return results.join('\n\n');
  }
};
```

---

## Práctica Práctica

### Ejercicio 1: Crear un Skill Útil

**Tarea:** Construye un skill personalizado para tu flujo de trabajo

```
Crea un skill que:
1. Ejecute todos los tests
2. Si los tests pasan, cree un commit
3. Haga push a la rama actual
4. Abra PR si está en rama de característica

Nómbralo /ship
```

---

### Ejercicio 2: Configurar Hooks de Automatización

**Tarea:** Crea hooks para calidad de código

```
Configura hooks que:
1. Auto-formateen código antes de guardar
2. Ejecuten linter antes de commit
3. Verifiquen TODOs antes de push
4. Prevengan commits con console.log
```

---

### Ejercicio 3: Flujo de Trabajo Personalizado

**Tarea:** Crea un flujo de trabajo completo

```
Construye un flujo de trabajo /release que:
1. Verifique que todos los tests pasen
2. Actualice número de versión
3. Genere changelog
4. Cree tag de git
5. Haga push a remoto
6. Cree release de GitHub
```

---

## Lista de Verificación del Módulo 12

- [ ] Entender skills y hooks
- [ ] Poder crear skills personalizados
- [ ] Poder configurar hooks de automatización
- [ ] Saber cómo personalizar ajustes
- [ ] Poder integrar con IDE
- [ ] Poder crear flujos de trabajo personalizados

---

## Mejores Prácticas

**Skills:**
- Mantén skills enfocados en una tarea
- Añade descripciones claras
- Maneja errores con gracia
- Hazlos reutilizables

**Hooks:**
- No hagas hooks demasiado lentos
- Añade manejo de errores
- Registra lo que hacen los hooks
- Hazlos opcionales/configurables

**Flujos de Trabajo:**
- Prueba flujos de trabajo exhaustivamente
- Documenta lo que hacen
- Hazlos flexibles
- Versiona tus configuraciones

---

## ¿Qué Sigue?

¡Ahora puedes personalizar Claude Code para que coincida exactamente con tu flujo de trabajo!

**¿Listo para el Módulo 13?** A continuación, exploraremos el uso de Claude Code con diferentes lenguajes de programación y frameworks.

---

*¡Módulo 12 Completado!*
