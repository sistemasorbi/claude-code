# Guía de Referencia Rápida

**Tu hoja de trucos para tareas comunes de Claude Code**

---

## Iniciando y Deteniendo

### Iniciar Claude Code
```bash
claude
```

### Iniciar en directorio específico
```bash
cd /ruta/a/proyecto
claude
```

### Salir de Claude Code
```
/exit
```
O presiona `Ctrl+C`

---

## Comandos Esenciales

### Comandos Slash Integrados

| Comando | Descripción |
|---------|-------------|
| `/exit` | Salir de Claude Code |
| `/help` | Mostrar información de ayuda |
| `/clear` | Limpiar historial de conversación |
| `/tasks` | Mostrar tareas en segundo plano |

---

## Prompts Comunes

### Operaciones de Archivos

**Crear un nuevo archivo:**
```
Crea un archivo llamado [nombre] que [haga qué]
```

**Leer un archivo:**
```
Muéstrame [nombre_archivo]
¿Qué hay en [nombre_archivo]?
```

**Editar un archivo:**
```
En [nombre_archivo], cambia [X] a [Y]
Añade [característica] a [nombre_archivo]
Corrige el [problema] en [nombre_archivo]
```

**Encontrar archivos:**
```
Encuentra todos los archivos [tipo]
Muéstrame todos los archivos que contengan [texto]
Lista todos los archivos de test
```

---

### Operaciones de Código

**Entender código:**
```
Explica qué hace [nombre_archivo/función]
¿Cómo funciona [característica] en esta base de código?
¿Qué hace este código?
```

**Escribir código nuevo:**
```
Crea una [función/clase/componente] que [haga qué]
Escribe una función [tipo] para [propósito]
```

**Corregir problemas:**
```
Corrige el bug en [nombre_archivo]
Depura por qué [problema] está pasando
La app crashea cuando [escenario], ayúdame a corregirlo
```

**Refactorizar:**
```
Refactoriza [código/archivo] para [mejora]
Mejora la estructura de [archivo]
Haz este código más legible
```

---

### Operaciones de Proyecto

**Inicializar proyecto:**
```
Crea un nuevo proyecto [tipo]
Configura una aplicación [framework] con [características]
Inicializa un proyecto [lenguaje] con [dependencias]
```

**Instalar dependencias:**
```
Instala [nombre_paquete]
Añade [librería] a este proyecto
Instala todas las dependencias
```

**Ejecutar comandos:**
```
Ejecuta la aplicación
Inicia el servidor de desarrollo
Ejecuta los tests
Haz build del proyecto
```

---

### Operaciones Git

**Estado y cambios:**
```
Muéstrame el estado de git
¿Qué archivos han cambiado?
Muéstrame el diff
```

**Commit:**
```
Crea un commit con estos cambios
Escribe un mensaje de commit para mis cambios
```

**Pull Request:**
```
Crea un pull request para estos cambios
Escribe una descripción de PR
```

**Ramas:**
```
Crea una nueva rama llamada [nombre]
Cambia a [rama]
```

---

### Entendiendo Bases de Código

**Explorar:**
```
Ayúdame a entender esta base de código
Explica la estructura del proyecto
¿Qué hace este proyecto?
```

**Encontrar código:**
```
¿Dónde está implementada [característica]?
Encuentra todos los usos de [función/clase]
Muéstrame dónde está definido [X]
```

**Dependencias:**
```
¿Qué dependencias usa esto?
¿Qué versión de [paquete] está instalada?
```

---

### Testing y Depuración

**Ejecutar tests:**
```
Ejecuta todos los tests
Ejecuta tests para [archivo/característica]
Crea tests para [código]
```

**Depurar:**
```
Ayúdame a depurar [problema]
¿Por qué está pasando [error]?
Este código no funciona: [descripción]
```

**Errores:**
```
Explica este mensaje de error: [error]
Corrige este error: [error]
```

---

### Documentación

**Crear docs:**
```
Escribe un README para este proyecto
Documenta esta función
Añade comentarios a este código
```

**Generar:**
```
Crea documentación de API
Escribe ejemplos de uso
Genera un changelog
```

---

## Solicitudes Específicas de Herramientas

### Cuando quieres herramientas específicas

**Herramienta Read:**
```
Lee [nombre_archivo] y muéstrame [parte específica]
```

**Herramienta Write:**
```
Escribe un nuevo archivo [nombre_archivo] con [contenido]
```

**Herramienta Edit:**
```
Edita [nombre_archivo] para añadir [característica]
```

**Herramienta Grep:**
```
Busca [texto] en todos los archivos
Encuentra todas las ocurrencias de [patrón]
```

**Herramienta Glob:**
```
Encuentra todos los archivos que coincidan con [patrón]
Lista todos los archivos *.js
```

**Herramienta Bash:**
```
Ejecuta [comando]
Ejecuta [script]
```

**Task/Agente:**
```
Explora esta base de código exhaustivamente
Planifica la implementación para [característica]
Investiga e implementa [solución]
```

---

## Patrones de Prompting Efectivo

### El Patrón Específico
```
En [archivo], añade una [característica] que [haga X] cuando [condición]
```

### El Patrón Exploratorio
```
Ayúdame a entender [concepto/código], luego [acción]
```

### El Patrón Iterativo
```
Crea un [cosa] básico
[Después de revisar] Ahora añade [mejora]
[Después de probar] Corrige [problema]
```

### El Patrón de Contexto
```
Estoy construyendo [proyecto]. Necesito [objetivo].
La estructura actual es [descripción].
Por favor [solicitud específica].
```

---

## Configuración

### Configurar API Key
```bash
export ANTHROPIC_API_KEY="tu-key"
```

### Ubicación del archivo config
```
~/.config/claude/config.json
```

### Configurar valores de config
```bash
claude config set [key] [value]
```

---

## Mejores Prácticas

### Hacer
✅ Sé específico sobre lo que quieres
✅ Proporciona contexto sobre tu proyecto
✅ Revisa cambios antes de aceptar
✅ Pide explicaciones cuando estés aprendiendo
✅ Usa control de versiones (Git)
✅ Prueba cambios incrementalmente
✅ Divide tareas complejas en pasos

### No Hacer
❌ No des instrucciones vagas
❌ No te saltes probar después de cambios
❌ No aceptes ciegamente todos los cambios
❌ No olvides hacer commit de código funcional
❌ No pidas demasiados cambios a la vez
❌ No ignores mensajes de error

---

## Atajos de Teclado

| Atajo | Acción |
|-------|--------|
| `Ctrl+C` | Salir de Claude Code |
| `Ctrl+D` | Terminar entrada |
| `Flecha Arriba` | Comando anterior |
| `Flecha Abajo` | Comando siguiente |

---

## Patrones Comunes de Archivos

### Patrones Glob

```
*.js                 # Todos los archivos .js en directorio actual
**/*.py              # Todos los archivos .py recursivamente
src/**/*.tsx         # Todos los archivos .tsx en src/
**/test/**           # Todos los archivos en directorios test
**/*test*            # Todos los archivos con 'test' en nombre
```

### Patrones Grep (Regex)

```
function.*login      # Funciones conteniendo 'login'
import.*from         # Sentencias import
TODO|FIXME           # Comentarios TODO o FIXME
class\s+\w+          # Definiciones de clase
```

---

## Soluciones Rápidas para Problemas

### Claude Code no inicia
```bash
# Verificar versión
claude --version

# Verificar si Node.js está instalado
node --version

# Reinstalar
npm install -g claude-code
```

### API key no funciona
```bash
# Configurarla de nuevo
export ANTHROPIC_API_KEY="tu-key"

# O usar config
claude config set apiKey "tu-key"
```

### Cambios no se aplican
```
Por favor muéstrame el archivo para verificar los cambios
```

### Comando falló
```
¿Puedes explicar el error e intentar un enfoque diferente?
```

---

## Plantillas Específicas de Proyecto

### Componente React
```
Crea un componente funcional React llamado [Nombre] que:
- Acepte props: [lista props]
- Muestre [elementos UI]
- Maneje [eventos]
```

### Endpoint de API
```
Añade un nuevo endpoint [método HTTP] en [ruta] que:
- Acepte [parámetros]
- Retorne [datos]
- Maneje errores
```

### Modelo de Base de Datos
```
Crea un modelo [ORM] para [entidad] con campos:
- [campo]: [tipo]
- [campo]: [tipo]
Incluye validación y relaciones.
```

### Suite de Tests
```
Crea tests para [función/componente] que verifiquen:
- [caso de test 1]
- [caso de test 2]
- Casos límite y errores
```

---

## Patrones Específicos por Lenguaje

### Python
```
Crea un script Python que [propósito]
Usa [librerías]
Incluye manejo de errores y logging
```

### JavaScript/Node
```
Crea un [tipo] Node.js usando [framework]
Usa sintaxis ES6+
Incluye async/await para operaciones asíncronas
```

### TypeScript
```
Crea un [tipo] TypeScript con tipos apropiados
Usa interfaces para [estructuras de datos]
Habilita modo estricto
```

---

## Lista de Verificación Rápida de Depuración

Cuando algo no funciona:

1. **Lee el error:** `¿Qué significa este error?`
2. **Verifica el archivo:** `Muéstrame [archivo] alrededor de línea [X]`
3. **Encuentra código similar:** `Encuentra otros lugares donde [X] funciona`
4. **Verifica dependencias:** `¿Están todas las dependencias instaladas?`
5. **Prueba aisladamente:** `Crea un test simple para [característica]`
6. **Pide ayuda:** `Ayúdame a depurar [problema específico]`

---

## Recursos

### Documentación Oficial
- [GitHub de Claude Code](https://github.com/anthropics/claude-code)
- [Docs de API de Claude](https://docs.anthropic.com)

### Este Curso
- [README Principal](LEEME.md) - Resumen del curso
- [Guía de Solución de Problemas](suplemento-solucion-problemas.md) - Soluciones detalladas
- [Soluciones de Desafíos](suplemento-soluciones-desafios.md) - Respuestas de práctica

---

*¡Mantén esta referencia a mano mientras trabajas con Claude Code!*
