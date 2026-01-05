# Módulo 5: Prompting Efectivo para Tareas de Programación

**Objetivo:** Domina el arte de comunicar tareas de programación a la IA

**Tiempo Estimado:** 30-40 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Escribir prompts claros y específicos
- Proporcionar el contexto necesario para mejores resultados
- Usar desarrollo iterativo para refinar soluciones
- Aplicar patrones de prompts probados
- Hacer las preguntas correctas para clarificar requisitos

---

## Lección 1: El Arte de Ser Específico

### Por Qué la Especificidad Importa

**Prompt vago:**
```
Haz una función para usuarios
```

**Problemas:**
- ¿Qué tipo de función?
- ¿Qué lenguaje?
- ¿Qué debe hacer exactamente?

**Prompt específico:**
```
Crea una función en Python llamada validar_usuario que:
- Reciba un diccionario con 'email' y 'password'
- Verifique que el email tenga formato válido
- Verifique que la contraseña tenga al menos 8 caracteres
- Devuelva True si es válido, False si no
- Lance ValueError si faltan campos
```

### Elementos de un Buen Prompt

1. **Acción clara** - ¿Qué quieres que haga?
2. **Contexto** - ¿Dónde se usará?
3. **Especificaciones técnicas** - Lenguaje, framework, etc.
4. **Comportamiento esperado** - ¿Qué debe pasar?
5. **Casos límite** - ¿Qué hacer en situaciones especiales?

### Ejemplos de Mejora

**Antes:** "Añade validación al formulario"

**Después:**
```
En el componente RegistroForm.jsx, añade validación que:
- Muestre error si el email no tiene formato válido
- Muestre error si la contraseña tiene menos de 8 caracteres
- Muestre error si las contraseñas no coinciden
- Deshabilite el botón de enviar hasta que todo sea válido
- Los mensajes de error deben aparecer debajo de cada campo
```

---

## Lección 2: Proporcionando Contexto

### Tipos de Contexto Útil

**Contexto del proyecto:**
```
Estoy trabajando en una aplicación de e-commerce con React y Node.js.
El backend usa Express con PostgreSQL.
```

**Contexto de la tarea:**
```
Necesito implementar el carrito de compras.
Ya existe el modelo de Producto y la autenticación de usuarios.
```

**Contexto de restricciones:**
```
Debe funcionar sin librerías externas adicionales.
Necesita ser compatible con navegadores IE11.
```

### Cómo Proporcionar Contexto

**Estructura recomendada:**

```
[Contexto del proyecto]
Estoy trabajando en [tipo de aplicación] usando [tecnologías].

[Estado actual]
Ya tengo implementado [lo que existe].
El archivo principal es [archivo].

[Lo que necesito]
Necesito [descripción clara de la tarea].

[Restricciones/Requisitos]
Debe [requisitos específicos].
No debe [restricciones].
```

### Ejemplo Completo

```
Contexto: Estoy construyendo una API REST para un blog con Node.js y Express.
Ya tengo los modelos de Usuario y Post funcionando con MongoDB.

Necesito: Implementar un sistema de comentarios.

Requisitos:
- Los comentarios pertenecen a un post y a un usuario
- Se pueden responder (comentarios anidados, máximo 2 niveles)
- Solo usuarios autenticados pueden comentar
- El autor del post puede eliminar cualquier comentario
- Los usuarios solo pueden editar sus propios comentarios

Restricciones:
- Usar el mismo patrón de controladores que ya existe
- Seguir la misma estructura de respuesta de la API
```

---

## Lección 3: Desarrollo Iterativo

### El Enfoque Paso a Paso

En lugar de pedir todo de una vez, divide en pasos:

**Paso 1: Estructura básica**
```
Crea el modelo de Comentario con los campos básicos
```

**Paso 2: Funcionalidad CRUD**
```
Añade las rutas y controladores para crear y listar comentarios
```

**Paso 3: Características adicionales**
```
Implementa la funcionalidad de respuestas anidadas
```

**Paso 4: Validación y seguridad**
```
Añade validación y verificación de permisos
```

### Beneficios del Enfoque Iterativo

1. **Más control** - Revisas cada paso antes de continuar
2. **Menos errores** - Detectas problemas temprano
3. **Mejor aprendizaje** - Entiendes cada parte
4. **Más flexibilidad** - Puedes cambiar dirección fácilmente

### Refinando Resultados

Después de cada paso, puedes refinar:

```
Esto está bien, pero:
- Añade validación del campo email
- Cambia el nombre de la función a validateInput
- Usa async/await en lugar de callbacks
```

---

## Lección 4: Patrones de Prompts Efectivos

### Patrón: Crear Desde Especificación

```
Crea [tipo de componente/función] llamado [nombre] que:
- [Requisito 1]
- [Requisito 2]
- [Requisito 3]

Usa [lenguaje/framework].
Sigue [patrón/estilo].
```

### Patrón: Modificar Existente

```
En [archivo/función], modifica para que:
- [Cambio 1]
- [Cambio 2]

Mantén [lo que no debe cambiar].
```

### Patrón: Depurar

```
Tengo este error: [mensaje de error]

El código relevante está en [archivo].
Sucede cuando [condiciones].
Esperaba que [comportamiento esperado].
```

### Patrón: Explicar y Mejorar

```
Explica qué hace [código/función] y sugiere mejoras para:
- Legibilidad
- Rendimiento
- Manejo de errores
```

### Patrón: Crear Como Otro

```
Mira cómo está implementado [componente/función existente].
Crea [nuevo componente/función] siguiendo el mismo patrón.
```

### Patrón: Revisar Código

```
Revisa [archivo/código] y busca:
- Vulnerabilidades de seguridad
- Problemas de rendimiento
- Código duplicado
- Mejores prácticas que no se siguen
```

---

## Lección 5: Haciendo las Preguntas Correctas

### Cuándo Preguntar

Es mejor que Claude Code pregunte antes de asumir:

```
Quiero implementar autenticación en mi aplicación
```

Claude Code puede preguntar:
- ¿JWT o sesiones?
- ¿Qué proveedor de identidad?
- ¿Necesitas OAuth social?
- ¿Qué nivel de seguridad?

### Fomentando Preguntas

Puedes pedir explícitamente clarificación:

```
Quiero añadir un sistema de pagos.
Antes de implementar, hazme preguntas sobre mis requisitos.
```

### Preguntas que Tú Debes Hacer

**Antes de implementar:**
```
¿Cuáles son las diferentes formas de implementar esto?
¿Cuáles son los pros y contras de cada enfoque?
```

**Después de recibir código:**
```
¿Por qué elegiste este enfoque?
¿Qué alternativas consideraste?
¿Qué limitaciones tiene esta solución?
```

**Para aprender:**
```
Explica cada línea de este código
¿Qué pasaría si cambio X por Y?
¿Cómo puedo probar que esto funciona correctamente?
```

---

## Lección 6: Evitando Errores Comunes

### Error 1: Demasiado Vago

❌ "Mejora este código"

✅ "Mejora este código añadiendo:
- Manejo de errores con try-catch
- Validación de entrada
- Comentarios que expliquen la lógica"

### Error 2: Demasiado a la Vez

❌ "Crea una aplicación completa de e-commerce con autenticación, carrito, pagos, inventario, reportes y panel de admin"

✅ Divide en múltiples solicitudes, empezando por:
"Crea la estructura básica del proyecto y el modelo de Producto"

### Error 3: Asumir Conocimiento

❌ "Usa la función X que creamos antes"

✅ "En el archivo utils.js hay una función llamada formatDate. Úsala para..."

### Error 4: No Verificar

❌ Aceptar código sin revisarlo

✅ "Muéstrame el código que vas a crear primero" o revisar lo generado

### Error 5: Olvidar el Contexto

❌ Después de varios intercambios: "Ahora añade validación"

✅ "En la función createUser que acabamos de crear, añade validación para el email"

---

## Ejercicio Práctico

### Ejercicio 1: Escribir Buenos Prompts

Convierte estos prompts vagos en prompts específicos:

**Vago:** "Haz un login"

**Tu versión mejorada:** (piénsalo antes de ver la respuesta)

<details>
<summary>Ver ejemplo de mejora</summary>

```
Crea un sistema de login para mi aplicación React que:
- Tenga un formulario con campos email y contraseña
- Valide el formato del email
- Muestre mensajes de error si las credenciales son incorrectas
- Redirija a /dashboard después de login exitoso
- Guarde el token JWT en localStorage
- Tenga estilos básicos con CSS modules
```
</details>

### Ejercicio 2: Desarrollo Iterativo

Practica pidiendo algo en pasos:

**Paso 1:** "Crea la estructura HTML de un formulario de contacto"

**Paso 2:** "Añade estilos CSS al formulario"

**Paso 3:** "Añade validación con JavaScript"

**Paso 4:** "Conecta el formulario a una API"

### Ejercicio 3: Usar Patrones

Usa el patrón "Crear Como Otro":

```
Mira el componente UserCard.jsx.
Crea ProductCard.jsx siguiendo la misma estructura y estilo.
```

---

## Plantillas de Prompts

### Para Nuevas Funcionalidades

```
Necesito implementar [funcionalidad].

Contexto:
- Proyecto: [tipo y tecnologías]
- Ya existe: [lo que está implementado]
- Debe integrarse con: [sistemas existentes]

Requisitos:
- [Requisito 1]
- [Requisito 2]

Restricciones:
- [Restricción 1]
- [Restricción 2]
```

### Para Corrección de Bugs

```
Bug: [descripción del problema]

Error: [mensaje de error si hay]

Para reproducir:
1. [Paso 1]
2. [Paso 2]

Esperado: [lo que debería pasar]
Actual: [lo que está pasando]

Código relevante: [archivo/función]
```

### Para Refactorización

```
Refactoriza [código/archivo] para:
- [Objetivo 1]
- [Objetivo 2]

Mantén:
- [Lo que no debe cambiar]

El código actual: [descripción o referencia]
```

---

## Lista de Verificación del Módulo 5

Verifica que puedas:

- [ ] Escribir prompts específicos con todos los detalles necesarios
- [ ] Proporcionar contexto relevante
- [ ] Dividir tareas grandes en pasos manejables
- [ ] Usar patrones de prompts efectivos
- [ ] Hacer preguntas para clarificar requisitos
- [ ] Evitar errores comunes de prompting

---

## Resumen de Mejores Prácticas

1. **Sé específico** - Incluye todos los detalles relevantes
2. **Da contexto** - Explica el proyecto y la situación actual
3. **Itera** - Divide en pasos y refina
4. **Usa patrones** - Aplica estructuras probadas
5. **Pregunta** - Clarifica antes de implementar
6. **Verifica** - Revisa el código generado
7. **Aprende** - Pide explicaciones para entender mejor

---

## ¿Qué Sigue?

¡Excelente trabajo dominando el prompting efectivo!

En el **Módulo 6**, aprenderemos sobre agentes en segundo plano - cómo usar agentes especializados para tareas complejas como exploración de código y planificación de implementaciones.

---

*¡Módulo 5 Completado!*
