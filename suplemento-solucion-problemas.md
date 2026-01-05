# Guía de Solución de Problemas

**Problemas comunes y cómo resolverlos**

---

## Problemas de Instalación

### Problema: "command not found: claude"

**Síntomas:**
```bash
$ claude
zsh: command not found: claude
```

**Causas:**
- Claude Code no instalado globalmente
- Terminal no reiniciada después de instalación
- Ruta de bin global de npm no está en PATH

**Soluciones:**

**Solución 1: Instalar globalmente**
```bash
npm install -g claude-code
```

**Solución 2: Reiniciar tu terminal**
Cierra y vuelve a abrir tu aplicación de terminal

**Solución 3: Verificar ruta global de npm**
```bash
npm config get prefix
```

Añade a tu PATH en `.bashrc`, `.zshrc`, o similar:
```bash
export PATH="$PATH:$(npm config get prefix)/bin"
```

---

### Problema: "Permission denied" durante instalación

**Síntomas:**
```bash
npm install -g claude-code
# Error: EACCES: permission denied
```

**Soluciones:**

**Solución 1: Usar npx (recomendado)**
```bash
npx claude-code
```

**Solución 2: Corregir permisos de npm**
```bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
export PATH=~/.npm-global/bin:$PATH
```

Añade la línea export a tu perfil de shell

**Solución 3: Usar sudo (no recomendado)**
```bash
sudo npm install -g claude-code
```

---

### Problema: Versión de Node.js muy antigua

**Síntomas:**
```
Error: Claude Code requiere Node.js 18 o superior
```

**Solución:**

Actualiza Node.js a versión 18+:

**Usando nvm (recomendado):**
```bash
# Instala nvm primero si es necesario
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash

# Instala última versión de Node.js
nvm install node
nvm use node
```

**O descarga desde nodejs.org:**
Visita [nodejs.org](https://nodejs.org) y descarga la versión LTS

---

## Problemas de API Key

### Problema: "API key not found"

**Síntomas:**
```
Error: Variable de entorno ANTHROPIC_API_KEY no configurada
```

**Soluciones:**

**Solución 1: Configurar variable de entorno (sesión actual)**
```bash
export ANTHROPIC_API_KEY="tu-api-key-aqui"
```

**Solución 2: Configurar en perfil de shell (persistente)**

Añade a `~/.bashrc`, `~/.zshrc`, o `~/.bash_profile`:
```bash
export ANTHROPIC_API_KEY="tu-api-key-aqui"
```

Luego recarga:
```bash
source ~/.zshrc  # o ~/.bashrc
```

**Solución 3: Usar config de Claude Code**
```bash
claude config set apiKey "tu-api-key-aqui"
```

---

### Problema: "Invalid API key"

**Síntomas:**
```
Error: API key inválida
```

**Causas:**
- Error tipográfico en API key
- API key revocada o expirada
- Formato de API key incorrecto

**Soluciones:**

1. **Obtener nueva API key:**
   - Ve a [console.anthropic.com](https://console.anthropic.com)
   - Crea una nueva API key
   - Copia la key completa (empieza con `sk-ant-`)

2. **Verificar errores tipográficos:**
   - Las keys deben empezar con `sk-ant-`
   - Sin espacios antes/después
   - Sin comillas dentro de la key

3. **Verificar que está configurada correctamente:**
   ```bash
   echo $ANTHROPIC_API_KEY
   ```

---

### Problema: "Insufficient credits"

**Síntomas:**
```
Error: Créditos insuficientes en tu cuenta
```

**Soluciones:**

1. **Verificar tu balance:**
   - Visita [console.anthropic.com](https://console.anthropic.com)
   - Revisa sección "Usage"

2. **Añadir créditos:**
   - Añade método de pago
   - Compra créditos

3. **Esperar reset mensual:**
   - Créditos de nivel gratuito se resetean mensualmente
   - Verifica cuándo es tu próximo reset

---

## Problemas en Tiempo de Ejecución

### Problema: Claude Code se congela o cuelga

**Síntomas:**
- Sin respuesta después de enviar prompt
- Cursor no parpadea
- Sin output por minutos

**Soluciones:**

**Solución 1: Verificar conexión a internet**
```bash
ping anthropic.com
```

**Solución 2: Aumentar timeout (si está disponible)**
```bash
# En tu solicitud, especifica timeout más largo
claude --timeout 300
```

**Solución 3: Matar y reiniciar**
Presiona `Ctrl+C` para detener, luego inicia de nuevo

**Solución 4: Verificar procesos en segundo plano**
```bash
# Lista tareas en segundo plano
/tasks

# Matar si es necesario
```

---

### Problema: "Rate limit exceeded"

**Síntomas:**
```
Error: Límite de tasa excedido. Por favor intenta más tarde.
```

**Causas:**
- Demasiadas solicitudes en poco tiempo
- Límites de API alcanzados

**Soluciones:**

1. **Esperar y reintentar:**
   - Espera 60 segundos
   - Intenta de nuevo

2. **Reducir frecuencia de solicitudes:**
   - Combina múltiples solicitudes pequeñas
   - Haz solicitudes más grandes y menos frecuentes

3. **Verificar tu uso:**
   - Visita console.anthropic.com
   - Revisa límites de uso

---

### Problema: Cambios no se guardan

**Síntomas:**
- Archivos muestran como modificados pero no cambiaron realmente
- Código desaparece después de cerrar

**Soluciones:**

**Solución 1: Verificar permisos de archivo**
```bash
ls -la [nombre_archivo]
```

Si no tienes permiso de escritura:
```bash
chmod u+w [nombre_archivo]
```

**Solución 2: Verificar directorio de trabajo**
```
Muéstrame el directorio de trabajo actual
Lista todos los archivos aquí
```

**Solución 3: Guardar explícitamente**
```
Por favor escribe los cambios a [nombre_archivo]
Muéstrame [nombre_archivo] para verificar
```

---

### Problema: Herramientas no funcionan

**Síntomas:**
- Herramientas Read/Write/Edit fallan
- Comandos Bash no se ejecutan
- Error: "Ejecución de herramienta fallida"

**Soluciones:**

**Para herramientas de archivo (Read/Write/Edit):**
1. **Verificar rutas de archivo:**
   - Usa rutas absolutas: `/home/usuario/proyecto/archivo.js`
   - O asegúrate de estar en el directorio correcto

2. **Verificar permisos:**
   ```bash
   ls -la
   ```

3. **Verificar espacio en disco:**
   ```bash
   df -h
   ```

**Para herramienta Bash:**
1. **Verificar sintaxis del comando:**
   ```
   Por favor explica este comando antes de ejecutarlo
   ```

2. **Probar comando manualmente:**
   ```bash
   # Sale de Claude Code y prueba
   [tu comando]
   ```

3. **Verificar programas requeridos:**
   ```bash
   which [programa]
   ```

---

## Problemas de Ejecución de Código

### Problema: Errores "Module not found"

**Síntomas:**
```
Error: Cannot find module 'express'
```

**Soluciones:**

**Solución 1: Instalar dependencias**
```
Instala todas las dependencias de package.json
```

O manualmente:
```bash
npm install
# o
pip install -r requirements.txt
```

**Solución 2: Verificar node_modules**
```bash
ls node_modules/
```

Si está vacío o falta:
```bash
rm -rf node_modules package-lock.json
npm install
```

**Solución 3: Verificar rutas de import**
```
Verifica todas las sentencias import en [archivo]
Corrige cualquier ruta incorrecta
```

---

### Problema: Errores de sintaxis después de cambios de Claude Code

**Síntomas:**
```
SyntaxError: Unexpected token
```

**Soluciones:**

**Solución 1: Revisar los cambios**
```
Muéstrame qué cambiaste en [archivo]
```

**Solución 2: Revertir cambios**
```
Por favor deshaz los cambios a [archivo]
```

O con Git:
```bash
git checkout [archivo]
```

**Solución 3: Corregir la sintaxis**
```
Hay un error de sintaxis en [archivo] en línea [X]. Por favor corrígelo.
```

---

### Problema: Tests fallan después de cambios

**Síntomas:**
- Tests pasaban antes
- Tests fallan después de modificaciones de Claude Code

**Soluciones:**

**Solución 1: Verificar qué cambió**
```
Muéstrame el git diff
¿Qué archivos modificaste?
```

**Solución 2: Revisar fallos de tests**
```
Ejecuta los tests y muéstrame el output
Explica por qué estos tests están fallando
```

**Solución 3: Corregir los tests**
```
Corrige el código para que los tests pasen
```

O:
```
Actualiza los tests para que coincidan con la nueva implementación
```

---

## Problemas de Integración Git

### Problema: Comandos Git fallan

**Síntomas:**
```
Error: fatal: not a git repository
```

**Soluciones:**

**Solución 1: Inicializar Git**
```
Inicializa un repositorio git en este directorio
```

O manualmente:
```bash
git init
```

**Solución 2: Verificar instalación de Git**
```bash
git --version
```

Si no está instalado, instala Git:
- **macOS:** `brew install git`
- **Ubuntu:** `sudo apt-get install git`
- **Windows:** Descarga desde git-scm.com

**Solución 3: Verificar que estás en el directorio correcto**
```bash
pwd
ls -la .git
```

---

### Problema: No puede hacer commit de cambios

**Síntomas:**
```
Error: Please tell me who you are
```

**Soluciones:**

**Configurar identidad Git:**
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu.email@ejemplo.com"
```

O pide a Claude Code:
```
Configura git con mi nombre y email
```

---

## Problemas de Rendimiento

### Problema: Claude Code está lento

**Síntomas:**
- Largos retrasos entre solicitud y respuesta
- Herramientas tardan mucho en ejecutarse

**Soluciones:**

**Solución 1: Verificar velocidad de internet**
```bash
speedtest-cli
# o visita fast.com
```

**Solución 2: Simplificar solicitudes**
- Divide tareas complejas en más pequeñas
- Sé más específico para reducir tiempo de procesamiento

**Solución 3: Usar agentes para tareas complejas**
```
Usa un agente para [tarea compleja]
```
Los agentes pueden ser más eficientes para tareas de múltiples pasos

**Solución 4: Cerrar otras aplicaciones**
- Libera memoria y CPU
- Cierra otras sesiones de Claude Code

---

### Problema: Operaciones de archivos grandes son lentas

**Síntomas:**
- Leer archivos grandes tarda mucho
- Editar archivos grandes es lento

**Soluciones:**

**Solución 1: Leer secciones específicas**
```
Lee las líneas 100-200 de [archivo]
Muéstrame solo la [función/clase] en [archivo]
```

**Solución 2: Usar búsqueda en su lugar**
```
Usa grep para encontrar [patrón] en [archivo]
```

**Solución 3: Dividir archivos grandes**
```
Ayúdame a refactorizar este archivo grande en módulos más pequeños
```

---

## Problemas de Servidor MCP

### Problema: Servidor MCP no se conecta

**Síntomas:**
```
Error: No se pudo conectar al servidor MCP
```

**Soluciones:**

**Solución 1: Verificar que el servidor está ejecutándose**
```bash
# Verifica si el proceso del servidor está corriendo
ps aux | grep mcp
```

**Solución 2: Verificar configuración**
Revisa `~/.config/claude/config.json`:
```json
{
  "mcpServers": {
    "nombre-servidor": {
      "command": "ruta-al-servidor",
      "args": []
    }
  }
}
```

**Solución 3: Probar servidor manualmente**
```bash
# Ejecuta el comando del servidor MCP manualmente
/ruta/a/mcp-server
```

**Solución 4: Verificar logs del servidor**
Busca en `~/.config/claude/logs/` por mensajes de error

---

## Obteniendo Más Ayuda

### Cuándo pedir ayuda a Claude Code

Puedes pedir a Claude Code mismo que te ayude a solucionar problemas:

```
Estoy obteniendo este error: [mensaje de error]
¿Puedes ayudarme a entenderlo y corregirlo?
```

```
Algo no está funcionando correctamente. ¿Puedes ayudarme a depurar?
```

```
La [característica] no se está comportando como se espera. Ayúdame a solucionar.
```

### Cuándo revisar documentación

- [GitHub de Claude Code](https://github.com/anthropics/claude-code)
- [Docs de API de Claude](https://docs.anthropic.com)
- [Issues de GitHub](https://github.com/anthropics/claude-code/issues)

### Cuándo preguntar a la comunidad

- Busca issues existentes en GitHub
- Crea nuevo issue con:
  - Descripción clara del problema
  - Pasos para reproducir
  - Mensajes de error
  - Información del sistema

### Información del sistema a proporcionar

Cuando reportes problemas, incluye:

```bash
# Versión de Claude Code
claude --version

# Versión de Node.js
node --version

# Versión de npm
npm --version

# Sistema operativo
uname -a  # macOS/Linux
# o
systeminfo  # Windows
```

---

## Consejos de Prevención

### Mejores Prácticas para Evitar Problemas

1. **Siempre usa control de versiones (Git)**
   - Haz commit de código funcional antes de hacer cambios
   - Fácil de revertir si algo se rompe

2. **Revisa cambios antes de aceptar**
   - Verifica outputs de herramienta Edit
   - Verifica comandos Bash antes de que se ejecuten

3. **Prueba incrementalmente**
   - Prueba después de cada cambio
   - Detecta problemas temprano

4. **Mantén backups**
   - Haz commits a Git regularmente
   - Haz push a repositorios remotos

5. **Sé específico en solicitudes**
   - Reduce malentendidos
   - Obtiene mejores resultados

6. **Pide explicaciones**
   - Entiende qué está haciendo Claude Code
   - Aprende a detectar problemas

7. **Empieza simple, añade complejidad**
   - Haz que lo básico funcione primero
   - Añade características incrementalmente

---

*¡La mayoría de los problemas pueden resolverse con comunicación clara y solución sistemática de problemas!*
