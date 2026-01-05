# Módulo 1: Bienvenida a Claude Code - Tus Primeros Pasos

**Objetivo:** Familiarizarte con Claude Code y entender lo que puede hacer

**Tiempo Estimado:** 20-30 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Entender qué es la "Programación en Pareja con IA" y por qué es revolucionaria
- Saber cómo instalar Claude Code en tu sistema
- Estar familiarizado con la interfaz de línea de comandos
- Entender el flujo básico de conversación
- Conocer la terminología esencial que necesitas

---

## Lección 1: ¿Qué es la "Programación en Pareja con IA"?

### Entendiendo el Concepto

**Programación en Pareja con IA** es un enfoque revolucionario para el desarrollo de software. Vamos a desglosarlo de la manera más simple posible:

**Programación Tradicional (La Forma Antigua):**
- Escribes cada línea de código tú mismo
- Buscas documentación durante horas
- Depuras errores manualmente
- Necesitas recordar sintaxis y APIs
- Pequeños errores pueden tomar horas en encontrar

**Programación en Pareja con IA (La Forma de Claude Code):**
- Describes lo que quieres lograr
- La IA te ayuda a implementarlo paso a paso
- La IA puede leer tu código, entender el contexto y hacer cambios
- La IA explica lo que está haciendo para que aprendas
- La depuración es colaborativa y más rápida

### Ejemplo del Mundo Real

**En lugar de hacer esto manualmente:**
```bash
# Buscar en Google "cómo crear servidor HTTP en Node.js"
# Leer documentación
# Copiar y pegar ejemplos
# Depurar por qué no funciona
# Corregir errores de sintaxis
# Probar manualmente
```

**Simplemente dices:**
> "Crea un servidor HTTP simple en Node.js que devuelva 'Hola Mundo' en el puerto 3000"

Y Claude Code:
1. Crea el archivo
2. Escribe el código
3. Explica lo que hizo
4. ¡Incluso puede ejecutarlo por ti!

Ese es el poder de la Programación en Pareja con IA.

---

## Lección 2: Instalando Claude Code

### Requisitos del Sistema

Antes de instalar, asegúrate de tener:
- Una computadora con macOS, Linux o Windows (WSL)
- Conexión a internet
- Acceso a terminal/línea de comandos
- Una clave API de Claude (la obtendremos)

**Consejo para Principiantes:** Si estás en Windows, necesitarás WSL (Subsistema de Windows para Linux). ¡No te preocupes - te guiaremos!

### Instalación Paso a Paso

#### Paso 1: Instalar Node.js (si no lo tienes)

Claude Code requiere Node.js versión 18 o superior.

**Verifica si tienes Node.js:**
```bash
node --version
```

**Si ves un número de versión como `v18.x.x` o superior, ¡estás listo!**

**Si no, instala Node.js:**
1. Ve a [nodejs.org](https://nodejs.org)
2. Descarga la versión LTS (Soporte a Largo Plazo)
3. Ejecuta el instalador
4. Sigue las instrucciones de instalación

#### Paso 2: Obtén Tu Clave API de Claude

1. Ve a [console.anthropic.com](https://console.anthropic.com)
2. Regístrate o inicia sesión
3. Navega a "API Keys"
4. Haz clic en "Create Key"
5. Copia tu clave API (empieza con `sk-ant-...`)
6. **¡Guárdala segura!** No la compartas con nadie

**Consejo para Principiantes:** Tu clave API es como una contraseña - ¡mantenla secreta y segura!

#### Paso 3: Instalar Claude Code

Abre tu terminal y ejecuta:

```bash
npm install -g @anthropic-ai/claude-code
```

**Lo que está pasando:**
- `npm` es el Gestor de Paquetes de Node (instala software)
- `install` le dice a npm que instale algo
- `-g` significa "globalmente" (disponible en todas partes)
- `@anthropic-ai/claude-code` es el nombre del paquete

**Espera a que la instalación se complete.** Verás un indicador de progreso.

#### Paso 4: Configura Tu Clave API

Necesitas decirle a Claude Code tu clave API. Hay dos formas:

**Opción A: Configurarla como variable de entorno (recomendado)**

**En macOS/Linux:**
```bash
export ANTHROPIC_API_KEY="tu-clave-api-aquí"
```

**En Windows (PowerShell):**
```powershell
$env:ANTHROPIC_API_KEY="tu-clave-api-aquí"
```

Para hacerlo permanente, añádelo a tu archivo de configuración de shell (`.bashrc`, `.zshrc`, etc.)

**Opción B: Crear un archivo de configuración**

Claude Code también puede leer de un archivo de configuración:
```bash
claude config set apiKey "tu-clave-api-aquí"
```

#### Paso 5: Verificar la Instalación

Ejecuta este comando para asegurarte de que todo funciona:

```bash
claude --version
```

¡Deberías ver el número de versión de Claude Code!

**Consejo para Principiantes:** Si obtienes un error, asegúrate de que reiniciaste tu terminal después de la instalación.

---

## Lección 3: Entendiendo la Interfaz de Claude Code

### ¿Qué es una CLI (Interfaz de Línea de Comandos)?

Una **CLI** es una forma basada en texto de interactuar con software. En lugar de hacer clic en botones, escribes comandos.

**¡No te intimides!** Claude Code hace que la CLI sea amigable y conversacional.

### Tu Primera Vista de Claude Code

#### Iniciando Claude Code

En tu terminal, simplemente escribe:

```bash
claude
```

**Lo que verás:**
```
╭───────────────────────────────────────────────────╮
│                                                   │
│   Claude Code v1.0.0                             │
│   Asistente de desarrollo potenciado por IA      │
│                                                   │
╰───────────────────────────────────────────────────╯

Directorio de trabajo: /home/usuario/proyectos

¿Cómo puedo ayudarte hoy?
>
```

**¡Esta es tu interfaz de conversación!** El `>` es donde escribes.

### Entendiendo la Interfaz

#### El Encabezado
Muestra:
- Versión de Claude Code
- Tu directorio de trabajo actual
- Información de estado

#### El Prompt (`>`)
Aquí es donde escribes tus solicitudes, como si chatearas con un amigo.

#### Área de Respuesta
Encima del prompt, verás:
- Las respuestas de Claude
- Uso de herramientas (cuando Claude lee archivos, ejecuta comandos, etc.)
- Resultados y salidas

### Tu Primera Conversación

Probemos algo simple. En el prompt `>`, escribe:

```
¡Hola! ¿Puedes explicar qué puedes hacer?
```

¡Presiona Enter y observa a Claude Code responder!

**Verás:**
- Un saludo amigable
- Una explicación de capacidades
- Sugerencias de qué probar

**Consejo para Principiantes:** Claude Code es conversacional. ¡Puedes hacer preguntas en español simple!

---

## Lección 4: Terminología Básica Que Necesitas Conocer

Aprendamos las palabras esenciales que verás en Claude Code. ¡No te preocupes - explicaremos todo en términos simples!

### Términos Esenciales

**Sesión**
- **Qué significa:** Una conversación con Claude Code, de principio a fin
- **Piénsalo como:** Una conversación de chat que termina cuando cierras la terminal
- **Ejemplo:** Inicias Claude Code, le pides ayuda para construir un sitio web, luego sales

**Directorio de Trabajo**
- **Qué significa:** La carpeta en la que Claude Code está trabajando actualmente
- **Piénsalo como:** Tu ubicación actual en tu computadora
- **Ejemplo:** `/home/usuario/mi-proyecto` es donde están tus archivos del proyecto

**Herramienta (Tool)**
- **Qué significa:** Una capacidad que tiene Claude Code (como leer archivos, ejecutar comandos)
- **Piénsalo como:** Diferentes habilidades o capacidades
- **Ejemplo:** La herramienta "Read" permite a Claude leer tus archivos de código

**Prompt**
- **Qué significa:** Tu mensaje o solicitud a Claude Code
- **Piénsalo como:** Una instrucción o pregunta que haces
- **Ejemplo:** "Crea un script de Python que imprima Hola Mundo"

**Uso de Herramienta / Llamada de Herramienta**
- **Qué significa:** Cuando Claude Code usa una de sus herramientas para hacer algo
- **Piénsalo como:** Claude realizando una acción
- **Ejemplo:** Usar la herramienta Write para crear un nuevo archivo

**Agente**
- **Qué significa:** Un asistente de IA especializado para tareas complejas
- **Piénsalo como:** Llamar a un experto para un trabajo específico
- **Ejemplo:** El agente "Explore" te ayuda a entender grandes bases de código

**Contexto**
- **Qué significa:** La información que Claude Code tiene sobre tu proyecto
- **Piénsalo como:** Lo que Claude "sabe" sobre tu código
- **Ejemplo:** Archivos que ha leído, comandos que ha ejecutado

**Servidor MCP**
- **Qué significa:** Una extensión que da a Claude Code nuevas capacidades
- **Piénsalo como:** Un plugin o complemento
- **Ejemplo:** Un servidor MCP de base de datos permite a Claude Code trabajar con bases de datos

**Consejo para Principiantes:** ¡No intentes memorizar todos estos ahora! Los aprenderás naturalmente mientras usas Claude Code. Solo vuelve a esta lista si ves una palabra que no entiendes.

---

## Práctica: Tu Primera Sesión de Claude Code

¡Ahora vamos a construir algo! Esto será muy simple - solo estamos haciendo que te sientas cómodo con el proceso.

### Proyecto de Práctica: Un Script Simple de Python

#### Paso 1: Crear un Directorio de Proyecto

Primero, creemos una carpeta para tu proyecto. En tu terminal (antes de iniciar Claude Code):

```bash
mkdir hola-claude
cd hola-claude
```

**Lo que hiciste:**
- `mkdir` = crear directorio (crear una carpeta)
- `cd` = cambiar directorio (entrar en la carpeta)

#### Paso 2: Iniciar Claude Code

Ahora inicia Claude Code en este directorio:

```bash
claude
```

¡Ahora estás en una sesión de Claude Code!

#### Paso 3: Tu Primera Solicitud

En el prompt `>`, escribe:

```
Crea un script de Python llamado hola.py que pregunte el nombre del usuario y lo salude
```

Presiona Enter.

**Lo que verás:**
- Claude Code reconociendo tu solicitud
- Usando la herramienta Write para crear el archivo
- El código siendo escrito
- Confirmación de que está hecho

#### Paso 4: Verificar Lo Que Se Creó

Veamos el archivo. Escribe:

```
¿Puedes mostrarme qué hay en hola.py?
```

¡Claude Code usará la herramienta Read y mostrará el contenido!

#### Paso 5: Ejecutar el Programa

¡Ahora ejecutémoslo! Escribe:

```
Ejecuta el script hola.py
```

Claude Code:
- Usará la herramienta Bash para ejecutar `python hola.py`
- El script preguntará por tu nombre
- Escribe tu nombre y presiona Enter
- ¡Verás el saludo!

#### Paso 6: Hacer un Cambio

Practiquemos hacer cambios. Escribe:

```
Haz el saludo más entusiasta con signos de exclamación
```

Observa cómo Claude Code:
- Usa la herramienta Edit
- Te muestra el cambio
- Actualiza el archivo

**¡Felicidades!** Acabas de:
- Crear un archivo con IA
- Ejecutar un programa
- Hacer modificaciones
- ¡Todo a través de conversación!

---

## Entendiendo Lo Que Acaba de Pasar

Desglosemos lo que Claude Code hizo:

### Cuando pediste crear un script:
1. **Entendió tu solicitud** - Analizó lo que querías
2. **Eligió la herramienta correcta** - Decidió usar Write
3. **Creó el archivo** - Escribió el código Python
4. **Confirmó la finalización** - Te informó que estaba hecho

### Cuando pediste ver el archivo:
1. **Usó la herramienta Read** - Abrió y leyó el archivo
2. **Mostró el contenido** - Te mostró el código
3. **Explicó lo que hace** - Te ayudó a entender

### Cuando pediste ejecutarlo:
1. **Usó la herramienta Bash** - Ejecutó el comando
2. **Mostró la salida** - Mostró los resultados
3. **Manejó la interacción** - Te dejó escribir tu nombre

### Cuando pediste cambios:
1. **Usó la herramienta Edit** - Hizo modificaciones precisas
2. **Mostró la diferencia** - Resaltó lo que cambió
3. **Preservó el otro código** - Solo cambió lo necesario

¡Este es el flujo de trabajo básico que usarás para todas las tareas de Claude Code!

---

## Lista de Verificación del Módulo 1

Antes de pasar al Módulo 2, asegúrate de poder:

- [ ] Explicar qué es la "Programación en Pareja con IA" en tus propias palabras
- [ ] Instalar exitosamente Claude Code en tu sistema
- [ ] Iniciar una sesión de Claude Code en tu terminal
- [ ] Entender términos básicos como "herramienta", "prompt" y "sesión"
- [ ] Crear un archivo simple usando Claude Code
- [ ] Hacer cambios a un archivo
- [ ] Ejecutar un programa con la ayuda de Claude Code

---

## Preguntas Comunes (FAQ)

### P: ¿Necesito saber programar?
**R:** ¡No! Claude Code puede ayudarte a aprender programación. Sin embargo, algo de entendimiento básico te ayuda a guiar mejor a Claude Code.

### P: ¿Claude Code es gratis?
**R:** Claude Code en sí es gratis, pero necesitas una clave API de Claude que tiene costos de uso. Los nuevos usuarios típicamente obtienen créditos gratis para empezar.

### P: ¿Qué pasa si cometo un error en mi solicitud?
**R:** ¡No hay problema! Puedes clarificar, pedir a Claude Code que deshaga cambios, o simplemente hacer una nueva solicitud. Nada es permanente.

### P: ¿Claude Code puede trabajar con cualquier lenguaje de programación?
**R:** ¡Sí! Claude Code puede ayudar con Python, JavaScript, Java, Go, Rust, y muchos más lenguajes.

### P: ¿Qué pasa si Claude Code hace algo mal?
**R:** Siempre tienes el control. Revisa los cambios antes de aceptarlos, y siempre puedes pedir a Claude Code que corrija o revierta cosas.

### P: ¿Cómo salgo de Claude Code?
**R:** Escribe `/exit` o presiona Ctrl+C. Tus archivos se guardan automáticamente.

---

## ¿Qué Sigue?

¡Excelente trabajo completando el Módulo 1! Ahora entiendes:
- Qué es Claude Code y cómo funciona
- Cómo instalarlo y configurarlo
- Cómo iniciar una sesión y tener una conversación
- Cómo crear y modificar archivos

**¿Listo para el Módulo 2?** En el próximo módulo, aprenderemos diferentes formas de iniciar proyectos con Claude Code - ¡desde cero, desde plantillas, y desde bases de código existentes!

---

## Consejos Pro para Principiantes

1. **Sé conversacional** - Habla con Claude Code naturalmente, como con un colega

2. **Sé específico** - Cuantos más detalles proporciones, mejores los resultados

3. **Haz preguntas** - Si no entiendes algo, pide a Claude Code que explique

4. **Revisa los cambios** - Siempre verifica lo que Claude Code hace para que aprendas

5. **Experimenta** - Prueba diferentes solicitudes y ve qué pasa. ¡No puedes romper nada!

6. **Guarda tu trabajo** - Usa Git (lo aprenderemos después) para rastrear cambios

7. **Lee la salida** - Claude Code explica lo que está haciendo - esto te ayuda a aprender

---

## Solución de Problemas Comunes

### "Command not found: claude"
**Solución:** Asegúrate de instalar globalmente con `-g` y reiniciar tu terminal.

### "API key not found"
**Solución:** Configura tu variable de entorno `ANTHROPIC_API_KEY` o usa `claude config set apiKey`.

### "Permission denied"
**Solución:** Puede que necesites usar `sudo` en macOS/Linux: `sudo npm install -g @anthropic-ai/claude-code`

### Claude Code parece lento
**Solución:** Esto es normal. El procesamiento de IA toma tiempo. Solicitudes complejas toman más que las simples.

### No veo ninguna salida
**Solución:** Asegúrate de presionar Enter después de escribir tu solicitud. Verifica tu conexión a internet.

---

*¡Módulo 1 Completado!*
