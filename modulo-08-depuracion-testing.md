# Módulo 8: Depuración y Testing

**Objetivo:** Aprende cómo encontrar y corregir problemas con asistencia de IA

**Tiempo Estimado:** 45-55 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Leer e interpretar mensajes de error
- Usar estrategias sistemáticas de depuración
- Escribir tests unitarios y de integración
- Practicar desarrollo guiado por tests (TDD)
- Identificar y corregir problemas de rendimiento
- Resolver escenarios comunes de depuración

---

## Lección 1: Leyendo Mensajes de Error

### Anatomía de un Error

Los mensajes de error típicamente contienen:

1. **Tipo de error** - Qué clase de error ocurrió
2. **Mensaje** - Descripción del problema
3. **Stack trace** - Dónde ocurrió el error
4. **Archivo y línea** - Ubicación exacta

### Ejemplo de Error

```
TypeError: Cannot read property 'name' of undefined
    at getUserName (/app/src/utils.js:15:20)
    at handleRequest (/app/src/server.js:42:10)
    at processRequest (/app/src/middleware.js:8:5)
```

### Pidiendo Ayuda con Errores

```
Tengo este error: [pegar error completo]

¿Puedes explicarme qué significa y cómo corregirlo?
```

Claude Code:
1. Explicará el tipo de error
2. Identificará la causa probable
3. Mostrará dónde ocurre
4. Sugerirá la corrección

### Errores Comunes y Sus Significados

| Error | Significado |
|-------|-------------|
| `TypeError: undefined is not a function` | Llamando algo que no es una función |
| `ReferenceError: x is not defined` | Variable no existe |
| `SyntaxError` | Error de sintaxis en el código |
| `RangeError` | Valor fuera de rango permitido |
| `Cannot read property of undefined` | Accediendo propiedad de algo que no existe |

---

## Lección 2: Estrategias de Depuración

### El Proceso Sistemático

1. **Reproducir** - Asegúrate de poder recrear el bug
2. **Aislar** - Encuentra dónde ocurre exactamente
3. **Investigar** - Entiende por qué ocurre
4. **Corregir** - Implementa la solución
5. **Verificar** - Confirma que está arreglado
6. **Prevenir** - Añade tests

### Usando Claude Code para Depurar

**Paso 1: Describir el problema**
```
El formulario de login no funciona.
Cuando hago clic en "Enviar", no pasa nada.
En la consola veo este error: [error]
```

**Paso 2: Localizar el problema**
```
Muéstrame el código del formulario de login y la función que maneja el submit
```

**Paso 3: Investigar**
```
¿Por qué podría estar fallando la validación aquí?
```

**Paso 4: Corregir**
```
Corrige el problema que identificaste
```

**Paso 5: Verificar**
```
Ejecuta la aplicación y prueba el login
```

### Técnicas de Depuración

**Añadir logging temporal:**
```
Añade console.logs temporales en la función processPayment para ver los valores de las variables
```

**Simplificar el código:**
```
Simplifica esta función para encontrar qué parte está fallando
```

**Verificar entradas:**
```
Añade validación para verificar que los parámetros son correctos antes de procesarlos
```

---

## Lección 3: Escribiendo Tests Unitarios

### ¿Qué son los Tests Unitarios?

Los tests unitarios verifican que funciones individuales funcionan correctamente.

### Estructura de un Test

```javascript
describe('Función a probar', () => {
  test('debería hacer algo específico', () => {
    // Arrange (preparar)
    const input = 'valor de entrada';

    // Act (actuar)
    const result = funcionAPprobar(input);

    // Assert (afirmar)
    expect(result).toBe('valor esperado');
  });
});
```

### Pidiendo Tests a Claude Code

**Tests para función existente:**
```
Crea tests unitarios para la función calculateTotal en utils.js
```

**Tests comprehensivos:**
```
Escribe tests para la función validateEmail que cubran:
- Emails válidos
- Emails sin @
- Emails sin dominio
- Strings vacíos
- Valores null/undefined
```

### Ejemplo Práctico

**Función:**
```javascript
function calculateDiscount(price, discountPercent) {
  if (discountPercent < 0 || discountPercent > 100) {
    throw new Error('Discount must be between 0 and 100');
  }
  return price - (price * discountPercent / 100);
}
```

**Pedir tests:**
```
Crea tests para la función calculateDiscount que cubran todos los casos
```

**Tests generados:**
```javascript
describe('calculateDiscount', () => {
  test('aplica descuento correctamente', () => {
    expect(calculateDiscount(100, 20)).toBe(80);
  });

  test('retorna precio original con 0% descuento', () => {
    expect(calculateDiscount(100, 0)).toBe(100);
  });

  test('retorna 0 con 100% descuento', () => {
    expect(calculateDiscount(100, 100)).toBe(0);
  });

  test('lanza error con descuento negativo', () => {
    expect(() => calculateDiscount(100, -10)).toThrow();
  });

  test('lanza error con descuento mayor a 100', () => {
    expect(() => calculateDiscount(100, 150)).toThrow();
  });
});
```

---

## Lección 4: Tests de Integración

### Diferencia con Tests Unitarios

- **Unitarios** - Prueban funciones aisladas
- **Integración** - Prueban cómo trabajan juntos los componentes

### Tests de API

```
Crea tests de integración para el endpoint POST /api/users que verifiquen:
- Crear usuario exitosamente con datos válidos
- Rechazar si falta el email
- Rechazar si el email ya existe
- Retornar el formato correcto de respuesta
```

### Tests de Base de Datos

```
Escribe tests de integración para el UserRepository que:
- Creen un usuario y lo recuperen
- Actualicen un usuario existente
- Eliminen un usuario
- Manejen errores de conexión
```

---

## Lección 5: Desarrollo Guiado por Tests (TDD)

### El Ciclo TDD

1. **Red** - Escribe un test que falle
2. **Green** - Escribe el código mínimo para pasar
3. **Refactor** - Mejora el código manteniendo tests verdes

### Practicando TDD con Claude Code

**Paso 1: Definir requisitos**
```
Necesito una función que valide contraseñas.
Requisitos:
- Mínimo 8 caracteres
- Al menos una mayúscula
- Al menos un número
- Al menos un carácter especial
```

**Paso 2: Pedir tests primero**
```
Escribe los tests para esta función ANTES de implementarla
```

**Paso 3: Implementar**
```
Ahora implementa la función para que pase todos los tests
```

**Paso 4: Ejecutar**
```
Ejecuta los tests y muéstrame los resultados
```

---

## Lección 6: Depuración de Rendimiento

### Identificando Problemas

```
La página de dashboard tarda mucho en cargar.
Ayúdame a identificar qué está causando la lentitud.
```

Claude Code puede:
- Analizar el código buscando operaciones costosas
- Identificar consultas de BD ineficientes
- Encontrar renderizados innecesarios
- Detectar memory leaks

### Problemas Comunes de Rendimiento

**Consultas N+1:**
```
Revisa las consultas de base de datos en getUsersWithPosts
y optimiza para evitar el problema N+1
```

**Loops ineficientes:**
```
Esta función es lenta. Analiza los loops y sugiere optimizaciones.
```

**Renderizados excesivos (React):**
```
El componente UserList se renderiza muchas veces.
Identifica la causa y optimiza.
```

### Añadiendo Mediciones

```
Añade medición de tiempo a las funciones principales de la API
para identificar cuáles son las más lentas
```

---

## Lección 7: Escenarios Comunes de Depuración

### Escenario 1: "Funciona en mi máquina"

```
El código funciona localmente pero falla en producción.
El error es: [error]
Las diferencias que conozco son: [diferencias]
```

### Escenario 2: "Funcionaba antes"

```
Esta funcionalidad dejó de funcionar después del último deploy.
Muéstrame qué cambió recientemente que pueda afectar esto.
```

### Escenario 3: "A veces falla"

```
Tengo un bug intermitente: a veces el login falla sin razón aparente.
Ayúdame a identificar posibles condiciones de carrera o problemas de timing.
```

### Escenario 4: "El test pasa pero el código falla"

```
Los tests de la función X pasan, pero en producción falla.
Revisa si los tests cubren el caso real de uso.
```

---

## Ejercicio Práctico

### Ejercicio 1: Depurar un Bug

Dado este código con un bug:

```javascript
function getAverageScore(students) {
  let total = 0;
  for (let i = 0; i <= students.length; i++) {
    total += students[i].score;
  }
  return total / students.length;
}
```

Pide a Claude Code:
```
Este código tiene un bug. Identifícalo, explica el problema, y corrígelo.
```

### Ejercicio 2: Escribir Tests

```
Tengo esta función de carrito de compras.
Escribe tests que cubran:
- Añadir productos
- Eliminar productos
- Calcular total
- Aplicar descuentos
- Validar cantidades
```

### Ejercicio 3: TDD Completo

```
Vamos a practicar TDD.
Necesito una función que formate números de teléfono.
Primero escribe los tests, luego implementa la función.
```

---

## Mejores Prácticas

### Para Depuración

1. **No asumas** - Verifica tus suposiciones
2. **Reproduce primero** - Asegúrate de poder recrear el bug
3. **Un cambio a la vez** - Cambia una cosa y verifica
4. **Usa control de versiones** - Puedes revertir si empeoras las cosas
5. **Documenta** - Anota lo que descubres

### Para Testing

1. **Escribe tests antes** - TDD previene bugs
2. **Cubre edge cases** - Los casos límite causan bugs
3. **Tests independientes** - Un test no debe depender de otro
4. **Nombres descriptivos** - El nombre debe explicar qué se prueba
5. **Mantén tests rápidos** - Tests lentos no se ejecutan

---

## Lista de Verificación del Módulo 8

Verifica que puedas:

- [ ] Leer e interpretar mensajes de error
- [ ] Usar estrategias sistemáticas de depuración
- [ ] Escribir tests unitarios
- [ ] Escribir tests de integración
- [ ] Practicar TDD básico
- [ ] Identificar problemas de rendimiento
- [ ] Resolver escenarios comunes de bugs

---

## Comandos Útiles

| Tarea | Cómo Pedirlo |
|-------|--------------|
| Explicar error | "Explica este error: [error]" |
| Depurar función | "Depura la función X" |
| Escribir tests | "Escribe tests para [función]" |
| Ejecutar tests | "Ejecuta los tests" |
| Añadir logging | "Añade logs para depurar" |
| Optimizar | "Optimiza esta función lenta" |

---

## ¿Qué Sigue?

¡Excelente trabajo aprendiendo depuración y testing!

En el **Módulo 9**, pondremos todo en práctica construyendo un proyecto del mundo real - una aplicación completa desde cero hasta el despliegue.

---

*¡Módulo 8 Completado!*
