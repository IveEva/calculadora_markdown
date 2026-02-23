# Calculadora Científica Web
## Guía Didáctica para Estudiantes

---

**Versión:** 1.0  
**Fecha:** Febrero 2026  
**Tecnologías:** HTML5, CSS3, JavaScript ES6  
**Nivel:** Principiante a Intermedio

---

## 📖 Tabla de Contenidos

1. [Introducción](#introducción)
2. [¿Qué hace esta calculadora?](#qué-hace-esta-calculadora)
3. [Estructura del Proyecto](#estructura-del-proyecto)
4. [Conceptos HTML Utilizados](#conceptos-html-utilizados)
5. [Conceptos CSS Utilizados](#conceptos-css-utilizados)
6. [Conceptos JavaScript Utilizados](#conceptos-javascript-utilizados)
7. [Funciones Principales](#funciones-principales)
8. [Flujo de Funcionamiento](#flujo-de-funcionamiento)
9. [Responsive Design](#responsive-design)
10. [Ejercicios Propuestos](#ejercicios-propuestos)
11. [Solución de Problemas](#solución-de-problemas)
12. [Recursos de Aprendizaje](#recursos-de-aprendizaje)

---

## 📋 Introducción

Esta calculadora científica es un proyecto web completo que combina HTML, CSS y JavaScript para crear una aplicación funcional similar a una calculadora física profesional. Es ideal para aprender los fundamentos del desarrollo web front-end.

### ¿Por qué este proyecto es educativo?

- **Integra las tres tecnologías web fundamentales** (HTML, CSS, JS)
- **Enseña manipulación del DOM** (Document Object Model)
- **Muestra manejo de eventos** (clicks, teclado)
- **Implementa lógica matemática** y validaciones
- **Es responsive** (funciona en móviles y desktop)
- **Código bien estructurado** y comentado

---

## 🎯 ¿Qué hace esta calculadora?

### Operaciones Básicas
- ➕ **Suma**: Suma dos números
- ➖ **Resta**: Resta dos números
- ✖️ **Multiplicación**: Multiplica dos números
- ➗ **División**: Divide dos números (con control de división por cero)
- **Módulo (mod)**: Calcula el resto de una división

### Funciones Científicas
- **sin, cos, tan**: Funciones trigonométricas (trabajan en radianes)
- **log**: Logaritmo en base 10
- **ln**: Logaritmo natural (base e)
- **√**: Raíz cuadrada
- **x²**: Elevar al cuadrado
- **1/x**: Inverso multiplicativo
- **%**: Convertir a porcentaje (divide entre 100)

### Sistema de Memoria
- **MC** (Memory Clear): Borra el valor guardado en memoria
- **MR** (Memory Recall): Recupera el valor de la memoria
- **M+** (Memory Add): Suma el número actual a la memoria
- **M-** (Memory Subtract): Resta el número actual de la memoria

### Constantes Matemáticas
- **π (Pi)**: 3.141592653589793
- **e (Euler)**: 2.718281828459045

### Funciones Adicionales
- **±**: Cambia el signo del número (positivo/negativo)
- **AC** (All Clear): Reinicia la calculadora
- **⌫** (Backspace): Borra el último dígito
- **Copiar**: Copia el resultado al portapapeles
- **Soporte de teclado**: Puedes usar tu teclado físico

---

## 🏗️ Estructura del Proyecto

El proyecto está contenido en un **único archivo HTML** que incluye:

```
calculadora.html
├── <head>
│   ├── Metadatos (charset, viewport)
│   ├── Título
│   ├── Enlace a Font Awesome (iconos)
│   └── <style> CSS integrado
└── <body>
    ├── Estructura HTML
    └── <script> JavaScript integrado
```

### ¿Por qué todo en un archivo?

**Ventajas:**
- ✅ Fácil de compartir (un solo archivo)
- ✅ No requiere servidor web
- ✅ Sin dependencias locales
- ✅ Ideal para aprender y prototipar

**Para proyectos grandes:**
Se recomienda separar en archivos:
- `index.html` (estructura)
- `estilos.css` (diseño)
- `script.js` (lógica)

---

## 📄 Conceptos HTML Utilizados

### 1. Etiquetas Principales

#### `<!DOCTYPE html>`
Declara que es un documento HTML5 moderno.

#### `<html lang="es">`
Elemento raíz. `lang="es"` indica idioma español (importante para SEO y accesibilidad).

#### `<head>`
Contiene metadatos que no se ven en pantalla:
- Codificación de caracteres
- Configuración de viewport para móviles
- Título de la pestaña
- Enlaces a recursos externos (CSS, fuentes, iconos)

#### `<body>`
Contiene todo el contenido visible de la página.

### 2. Estructura de Contenedores

#### `<div>`
Contenedor genérico para agrupar elementos. Se usa con clases para aplicar estilos.

**Ejemplo:**
```html
<div class="calculadora">
    <!-- Contenido de la calculadora -->
</div>
```

### 3. Botones Interactivos

#### `<button>`
Elemento clickeable que ejecuta acciones.

**Atributos importantes:**
- `class`: Aplica estilos CSS
- `onclick`: Ejecuta código JavaScript al hacer clic

**Ejemplo:**
```html
<button class="btn btn-numero" onclick="agregarNumero('7')">7</button>
```

### 4. IDs vs Clases

#### ID (`id="nombre"`)
- Identificador **único** en toda la página
- Se usa para acceder desde JavaScript: `document.getElementById('display')`
- Solo puede haber un elemento con ese ID

#### Clase (`class="nombre"`)
- Identificador **reutilizable**
- Múltiples elementos pueden tener la misma clase
- Se usa para aplicar estilos comunes

**Ejemplo:**
```html
<div class="display" id="displayPrincipal">0</div>
<!-- 'display' es la clase, 'displayPrincipal' es el ID único -->
```

### 5. Metaetiqueta Viewport

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**¿Para qué sirve?**
- Hace que la página se vea bien en móviles
- Sin ella, los móviles muestran la versión desktop reducida

---

## 🎨 Conceptos CSS Utilizados

### 1. Selectores

#### Selector Universal `*`
Selecciona TODOS los elementos de la página.

**Uso:** Resetear estilos por defecto del navegador.

#### Selector de Clase `.nombre`
Selecciona elementos con `class="nombre"`.

**Ejemplo:** `.btn` selecciona todos los botones con esa clase.

#### Selector de ID `#nombre`
Selecciona el elemento único con `id="nombre"`.

**Ejemplo:** `#display` selecciona el display principal.

#### Pseudo-clases
Seleccionan estados especiales:
- `:hover` - cuando el cursor está encima
- `:active` - cuando se está clickeando
- `:focus` - cuando el elemento tiene el foco

### 2. Box Model (Modelo de Caja)

Todo elemento HTML es una "caja" con:

```
┌─────────────────────────┐
│       MARGIN            │ ← Espacio exterior
│  ┌──────────────────┐   │
│  │     BORDER       │   │ ← Borde
│  │  ┌───────────┐   │   │
│  │  │  PADDING  │   │   │ ← Espacio interno
│  │  │  ┌─────┐  │   │   │
│  │  │  │CONT.│  │   │   │ ← Contenido
│  │  │  └─────┘  │   │   │
│  │  └───────────┘   │   │
│  └──────────────────┘   │
└─────────────────────────┘
```

#### `box-sizing: border-box`
Hace que `width` incluya padding y border (más intuitivo).

### 3. Flexbox (Diseño Flexible)

Sistema para alinear elementos en una dimensión (horizontal o vertical).

**Propiedades principales:**
- `display: flex` - Activa flexbox
- `justify-content` - Alineación horizontal
- `align-items` - Alineación vertical
- `gap` - Espacio entre elementos

**Uso en la calculadora:**
Centrar la calculadora en la pantalla verticalmente y horizontalmente.

### 4. CSS Grid (Rejilla)

Sistema para layouts bidimensionales (filas y columnas).

**Propiedades principales:**
- `display: grid` - Activa grid
- `grid-template-columns` - Define columnas
- `gap` - Espacio entre celdas
- `grid-column: span N` - Elemento ocupa N columnas

**Uso en la calculadora:**
Organizar los botones en 5 columnas automáticamente.

### 5. Gradientes

Transiciones suaves entre colores.

**Linear Gradient:**
```css
background: linear-gradient(135deg, #1e3c72, #2a5298);
```
- `135deg` - Ángulo (diagonal)
- Colores - De azul oscuro a azul medio

### 6. Sombras

#### Box Shadow (sombra de caja)
```css
box-shadow: 0 4px 0 rgba(0, 0, 0, 0.3);
```
- `0` - desplazamiento horizontal
- `4px` - desplazamiento vertical
- `0` - difuminado
- `rgba(0,0,0,0.3)` - color negro 30% opaco

#### Text Shadow (sombra de texto)
```css
text-shadow: 0 0 10px rgba(72, 187, 120, 0.3);
```
Crea efecto de "brillo LED" en el texto.

### 7. Transiciones

Animan cambios de propiedades CSS.

```css
transition: all 0.2s ease;
```
- `all` - anima todos los cambios
- `0.2s` - duración 0.2 segundos
- `ease` - curva de animación suave

### 8. Transformaciones

Modifican la posición, escala o rotación de elementos.

**Ejemplos:**
- `transform: translateY(2px)` - Mueve 2px hacia abajo
- `transform: scale(0.98)` - Reduce al 98% del tamaño

### 9. Media Queries (Responsive)

Aplican estilos según el tamaño de pantalla.

```css
@media (max-width: 480px) {
    /* Estilos para móviles */
}
```

**Breakpoints usados:**
- Desktop: más de 480px
- Mobile: 480px o menos
- Small Mobile: 360px o menos

---

## 💻 Conceptos JavaScript Utilizados

### 1. Variables

Contenedores que almacenan datos.

#### `let` (variable que puede cambiar)
```javascript
let numeroActual = '0';
numeroActual = '5';  // ✅ Se puede reasignar
```

#### `const` (constante que NO cambia)
```javascript
const PI = 3.14159;
PI = 3.14;  // ❌ ERROR: no se puede reasignar
```

**Uso en la calculadora:**
- `let` para el estado que cambia (número actual, operación)
- `const` para referencias DOM y valores fijos

### 2. Tipos de Datos

#### String (Cadena de texto)
```javascript
let texto = "Hola";
let numero = "123";  // Es texto, no número
```

#### Number (Número)
```javascript
let entero = 42;
let decimal = 3.14;
```

#### Boolean (Verdadero/Falso)
```javascript
let esVerdadero = true;
let esFalso = false;
```

#### Null (Vacío intencionado)
```javascript
let vacio = null;
```

### 3. Operadores

#### Aritméticos
- `+` suma
- `-` resta
- `*` multiplicación
- `/` división
- `%` módulo (resto)

#### Comparación
- `===` igual estricto
- `!==` diferente estricto
- `<` menor que
- `>` mayor que
- `<=` menor o igual
- `>=` mayor o igual

#### Lógicos
- `&&` AND (Y)
- `||` OR (O)
- `!` NOT (NO)

#### Ternario
```javascript
condicion ? siVerdadero : siFalso
```

### 4. Condicionales

#### If-Else
```javascript
if (condicion) {
    // código si es verdadero
} else {
    // código si es falso
}
```

#### Switch
```javascript
switch(variable) {
    case 'opcion1':
        // código
        break;
    case 'opcion2':
        // código
        break;
    default:
        // código por defecto
}
```

### 5. Funciones

Bloques de código reutilizables.

#### Declaración tradicional
```javascript
function nombre(parametro1, parametro2) {
    // código
    return resultado;
}
```

#### Arrow Function (función flecha)
```javascript
const nombre = (parametro) => {
    // código
    return resultado;
};
```

### 6. DOM (Document Object Model)

#### Seleccionar elementos
```javascript
// Por ID (devuelve un elemento)
let elemento = document.getElementById('miId');

// Por clase (devuelve colección)
let elementos = document.querySelectorAll('.miClase');
```

#### Modificar elementos
```javascript
// Cambiar texto
elemento.textContent = 'Nuevo texto';

// Cambiar estilo
elemento.style.color = 'red';

// Añadir clase
elemento.classList.add('activo');

// Quitar clase
elemento.classList.remove('activo');
```

### 7. Eventos

Acciones que ocurren en la página.

#### Event Listener
```javascript
elemento.addEventListener('click', function() {
    // código cuando se hace clic
});
```

#### Inline (en HTML)
```html
<button onclick="miFuncion()">Click</button>
```

### 8. Funciones Matemáticas (Math)

Objeto con funciones matemáticas integradas.

```javascript
Math.sin(x)      // Seno
Math.cos(x)      // Coseno
Math.tan(x)      // Tangente
Math.sqrt(x)     // Raíz cuadrada
Math.pow(x, y)   // x elevado a y
Math.log10(x)    // Logaritmo base 10
Math.log(x)      // Logaritmo natural
Math.round(x)    // Redondear
Math.PI          // Constante Pi
Math.E           // Constante e
```

### 9. Strings (Cadenas de texto)

#### Template Literals
```javascript
let nombre = "Juan";
let saludo = `Hola ${nombre}`;  // "Hola Juan"
```

#### Métodos útiles
```javascript
texto.length          // Longitud
texto.includes('sub') // ¿Contiene?
texto.split('.')      // Dividir en array
texto.slice(0, -1)    // Extraer porción
```

### 10. Conversión de Tipos

```javascript
// String a Number
let num = parseFloat("3.14");  // 3.14

// Number a String
let texto = (42).toString();   // "42"

// Verificar si es número
isNaN(valor)  // true si NO es número
```

### 11. Try-Catch (Manejo de Errores)

```javascript
try {
    // Código que puede fallar
    riesgosoOperation();
} catch (error) {
    // Qué hacer si falla
    console.error('Error:', error);
}
```

### 12. Async/Await (Asincronía)

Para operaciones que toman tiempo.

```javascript
async function miFuncion() {
    try {
        await operacionLenta();
        // continúa después de completarse
    } catch (error) {
        console.error(error);
    }
}
```

---

## 🔧 Funciones Principales

### 1. `actualizarDisplay()`

**¿Qué hace?**
Actualiza lo que se muestra en la pantalla de la calculadora.

**Cuándo se usa:**
Cada vez que cambia el número o la operación.

**Qué actualiza:**
- Display principal (número actual)
- Display secundario (operación en curso: "5 +")
- Elimina el estilo de error si había

---

### 2. `agregarNumero(num)`

**¿Qué hace?**
Añade un dígito (0-9) o punto decimal al número actual.

**Parámetros:**
- `num`: String con el dígito a añadir ('0'-'9' o '.')

**Lógica especial:**
- Si se presionó una operación antes → reemplaza el display
- Si el display muestra "0" → reemplaza por el nuevo número
- Si ya hay un punto decimal → no permite otro
- Si no → concatena el dígito al número actual

**Ejemplo:**
```
Display: "12"
Usuario presiona: "3"
Resultado: "123"
```

---

### 3. `seleccionarOperacion(operacion)`

**¿Qué hace?**
Guarda qué operación matemática se va a realizar.

**Parámetros:**
- `operacion`: String ('suma', 'resta', 'multiplicacion', 'division', 'mod')

**Flujo:**
1. Si hay operación pendiente → la calcula primero
2. Guarda la nueva operación
3. Guarda el número actual como primer operando
4. Marca que el siguiente número debe reemplazar el display

**Ejemplo:**
```
Usuario: "5" → "+" → "3"
Paso 1: numeroActual = "5"
Paso 2: operacionActual = "suma", numeroAnterior = 5
Paso 3: numeroActual = "3"
```

---

### 4. `calcular()`

**¿Qué hace?**
Ejecuta la operación matemática pendiente.

**Flujo:**
1. Verifica que haya operación y número anterior
2. Obtiene ambos números (convierte strings a números)
3. Ejecuta la operación según el tipo (switch)
4. Muestra el resultado
5. Resetea operación y número anterior

**Operaciones disponibles:**
- **suma**: `num1 + num2`
- **resta**: `num1 - num2`
- **multiplicacion**: `num1 * num2`
- **division**: `num1 / num2` (con control de división por cero)
- **mod**: `num1 % num2` (resto de la división)

---

### 5. `aplicarFuncion(funcion)`

**¿Qué hace?**
Aplica funciones científicas (sin, cos, log, etc.) al número actual.

**Parámetros:**
- `funcion`: String con el nombre de la función

**Funciones disponibles:**

#### Trigonométricas
- **sin**: Seno (en radianes)
- **cos**: Coseno (en radianes)
- **tan**: Tangente (en radianes)

#### Logarítmicas
- **log**: Logaritmo base 10
- **ln**: Logaritmo natural (base e)

#### Otras
- **raiz**: Raíz cuadrada (√)
- **potencia**: Elevar al cuadrado (x²)
- **porcentaje**: Dividir entre 100 (%)
- **inverso**: 1/x

**Validaciones:**
- Log y ln: solo números positivos
- Raíz: solo números no negativos
- Inverso: no permite cero (división por cero)

---

### 6. `mostrarResultado(resultado)`

**¿Qué hace?**
Muestra el resultado y calcula información adicional.

**Flujo:**
1. Redondea a 12 decimales (evita errores de punto flotante)
2. Actualiza el display
3. Muestra panel de información adicional:
   - Notación científica (ej: 1.234e+3)
   - Precisión decimal (cuántos decimales tiene)

**¿Por qué redondear?**
JavaScript tiene problemas con decimales:
```
0.1 + 0.2 = 0.30000000000000004  ❌
```
El redondeo elimina estos errores.

---

### 7. Funciones de Memoria

#### `memoriaLimpiar()`
Pone la memoria en 0.

#### `memoriaRecuperar()`
Copia el valor de memoria al display.

#### `memoriaSumar()`
Suma el número actual a la memoria.

#### `memoriaRestar()`
Resta el número actual de la memoria.

**Uso típico:**
```
1. Calculas: 5 + 3 = 8
2. Presionas M+ → memoria = 8
3. Calculas: 2 × 4 = 8
4. Presionas M+ → memoria = 16
5. Presionas MR → display muestra 16
```

---

### 8. Funciones de Utilidad

#### `limpiar()`
Reinicia completamente la calculadora (AC - All Clear).

**Resetea:**
- Número actual a "0"
- Operación a null
- Número anterior a null
- Oculta panel de información

#### `borrarUltimo()`
Elimina el último dígito (Backspace).

**Ejemplos:**
```
"1234" → "123"
"12" → "1"
"1" → "0"
```

#### `cambiarSigno()`
Cambia el signo del número (± toggle).

**Ejemplos:**
```
5 → -5
-5 → 5
0 → 0 (no hace nada)
```

#### `insertarPi()`
Inserta el valor de π (3.141592653589793).

#### `insertarE()`
Inserta el valor de e (2.718281828459045).

#### `copiarResultado()`
Copia el resultado al portapapeles del sistema.

**Nota:** Requiere permisos del navegador y solo funciona en HTTPS o localhost.

---

## 🔄 Flujo de Funcionamiento

### Caso 1: Operación Básica Simple

**Usuario quiere calcular: 5 + 3**

```
Paso 1: Usuario presiona "5"
├─ agregarNumero('5')
├─ numeroActual = "5"
└─ Display: "5"

Paso 2: Usuario presiona "+"
├─ seleccionarOperacion('suma')
├─ operacionActual = "suma"
├─ numeroAnterior = 5
├─ reiniciarDisplay = true
└─ Display: "5 +"

Paso 3: Usuario presiona "3"
├─ agregarNumero('3')
├─ numeroActual = "3" (reemplaza porque reiniciarDisplay=true)
└─ Display: "5 + 3"

Paso 4: Usuario presiona "="
├─ calcular()
├─ resultado = 5 + 3 = 8
├─ numeroActual = "8"
└─ Display: "8"
```

---

### Caso 2: Operaciones Encadenadas

**Usuario quiere calcular: 5 + 3 + 2**

```
Paso 1-3: (igual que antes)
└─ Display: "5 + 3"

Paso 4: Usuario presiona "+" (antes de "=")
├─ seleccionarOperacion('suma')
├─ calcular() primero (hay operación pendiente)
├─ resultado = 5 + 3 = 8
├─ numeroAnterior = 8
├─ operacionActual = "suma"
└─ Display: "8 +"

Paso 5: Usuario presiona "2"
├─ agregarNumero('2')
└─ Display: "8 + 2"

Paso 6: Usuario presiona "="
├─ calcular()
├─ resultado = 8 + 2 = 10
└─ Display: "10"
```

---

### Caso 3: Función Científica

**Usuario quiere calcular: sin(30°)**

```
Nota: La calculadora trabaja en radianes por defecto.
30° = 0.5236 radianes

Paso 1: Usuario presiona "0.5236"
├─ agregarNumero() múltiples veces
└─ Display: "0.5236"

Paso 2: Usuario presiona "sin"
├─ aplicarFuncion('sin')
├─ resultado = Math.sin(0.5236) = 0.5
├─ numeroActual = "0.5"
└─ Display: "0.5"
    Info: "sin(0.5236)"
```

---

### Caso 4: Uso de Memoria

**Guardar y recuperar un valor**

```
Paso 1: Calcular 5 + 3 = 8
└─ Display: "8"

Paso 2: Usuario presiona "M+"
├─ memoriaSumar()
├─ memoria = 0 + 8 = 8
└─ Memoria Display: "Memoria: 8.000000"

Paso 3: Calcular 2 × 4 = 8
└─ Display: "8"

Paso 4: Usuario presiona "M+"
├─ memoriaSumar()
├─ memoria = 8 + 8 = 16
└─ Memoria Display: "Memoria: 16.000000"

Paso 5: Usuario presiona "MR"
├─ memoriaRecuperar()
├─ numeroActual = "16"
└─ Display: "16"
```

---

## 📱 Responsive Design

### ¿Qué es Responsive Design?

Diseño que se adapta a diferentes tamaños de pantalla (móvil, tablet, desktop).

### Técnicas Usadas

#### 1. Viewport Meta Tag
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
Dice al navegador móvil que use el ancho real del dispositivo.

#### 2. Unidades Flexibles

**Viewport Units:**
- `100vh` = 100% de la altura de la pantalla
- `100vw` = 100% del ancho de la pantalla

**Fracciones (fr):**
- En Grid: `1fr 1fr 1fr` = 3 columnas de igual tamaño

**Porcentajes:**
- `width: 100%` = ancho completo del contenedor

#### 3. Media Queries

**Para Mobile (≤ 480px):**
- Padding reducido
- Fuentes más pequeñas
- Botones más compactos
- Gaps más pequeños

**Para Small Mobile (≤ 360px):**
- Ajustes aún más agresivos
- Display más pequeño
- Padding mínimo

#### 4. Flexbox para Centrado

```css
body {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

Centra la calculadora en cualquier pantalla.

#### 5. Max-width

```css
.calculadora {
    width: 100%;
    max-width: 420px;
}
```

**Comportamiento:**
- Desktop: 420px fijo
- Mobile: 100% del ancho (nunca más de 420px)

---

## 💡 Ejercicios Propuestos

### Nivel Básico

#### Ejercicio 1: Cambiar Colores
**Objetivo:** Cambiar la paleta de colores de la calculadora.

**Pasos:**
1. Identifica los colores principales en el CSS
2. Elige una nueva paleta (usa coolors.co)
3. Reemplaza los colores hexadecimales
4. Verifica que haya buen contraste

**Ejemplo:**
```css
/* Cambiar azul por verde */
background: linear-gradient(135deg, #10b981, #059669);
```

---

#### Ejercicio 2: Añadir un Botón
**Objetivo:** Añadir un nuevo botón funcional.

**Ejemplo: Botón de Factorial**

1. **HTML:** Añade el botón
2. **CSS:** Ya tiene los estilos (usa clase `btn-funcion`)
3. **JavaScript:** Añade la función

**Pista:**
```javascript
function factorial(n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```

---

#### Ejercicio 3: Sonidos
**Objetivo:** Añadir sonidos al presionar botones.

**Pasos:**
1. Busca un sonido de click (formato MP3 o WAV)
2. Añade el audio en HTML
3. Reproduce en cada función

**Pista:**
```javascript
let sonido = new Audio('click.mp3');
sonido.play();
```

---

### Nivel Intermedio

#### Ejercicio 4: Historial de Operaciones
**Objetivo:** Mostrar las últimas 5 operaciones realizadas.

**Requisitos:**
- Array para guardar operaciones
- Función para añadir al historial
- Mostrar en un nuevo contenedor
- Limitar a 5 operaciones

---

#### Ejercicio 5: Modo Grados/Radianes
**Objetivo:** Botón para alternar entre radianes y grados.

**Cambios necesarios:**
- Botón RAD/DEG
- Variable global para el modo
- Conversión en funciones trigonométricas
- Indicador visual del modo actual

**Fórmula de conversión:**
```
radianes = grados × π / 180
grados = radianes × 180 / π
```

---

#### Ejercicio 6: Tema Claro/Oscuro
**Objetivo:** Botón para cambiar entre modo claro y oscuro.

**Requisitos:**
- Botón toggle
- Clase `.tema-claro` en CSS
- JavaScript para alternar clase en body
- Guardar preferencia (opcional: localStorage)

---

### Nivel Avanzado

#### Ejercicio 7: Conversión de Bases
**Objetivo:** Convertir entre binario, octal, decimal, hexadecimal.

**Funciones JavaScript útiles:**
```javascript
// Decimal a binario
let binario = numero.toString(2);

// Binario a decimal
let decimal = parseInt(binario, 2);

// Decimal a hexadecimal
let hex = numero.toString(16);
```

---

#### Ejercicio 8: Gráficos de Funciones
**Objetivo:** Graficar funciones matemáticas.

**Librería recomendada:** Chart.js

**Requisitos:**
- Input para la función
- Canvas para el gráfico
- Calcular puntos
- Dibujar con Chart.js

---

#### Ejercicio 9: Modo Programador
**Objetivo:** Operaciones binarias (AND, OR, XOR, NOT, shifts).

**Operadores JavaScript:**
```javascript
a & b    // AND
a | b    // OR
a ^ b    // XOR
~a       // NOT
a << n   // Shift left
a >> n   // Shift right
```

---

#### Ejercicio 10: Reconocimiento por Voz
**Objetivo:** Decir operaciones por voz.

**API:** Web Speech API

**Ejemplo básico:**
```javascript
let recognition = new webkitSpeechRecognition();
recognition.onresult = function(event) {
    let speech = event.results[0][0].transcript;
    // Procesar el texto
};
recognition.start();
```

---

## 🐛 Solución de Problemas

### Problema 1: Los Botones No Funcionan

**Síntomas:** Al hacer clic, no pasa nada.

**Posibles causas:**
1. Error de sintaxis en JavaScript
2. Función no definida
3. Atributo `onclick` mal escrito

**Solución:**
1. Abre la consola (F12 → Console)
2. Busca errores en rojo
3. Verifica que las funciones existen:
```javascript
console.log(typeof agregarNumero);  // Debe decir "function"
```

---

### Problema 2: Display No Se Actualiza

**Síntomas:** El número no cambia en pantalla.

**Posibles causas:**
1. ID incorrecto en HTML o JavaScript
2. JavaScript se carga antes que HTML

**Solución:**
1. Verifica IDs:
```javascript
console.log(display);  // No debe ser null
```

2. Asegura carga después de HTML:
```javascript
document.addEventListener('DOMContentLoaded', function() {
    // Tu código aquí
});
```

---

### Problema 3: Errores de Decimales

**Síntomas:** 0.1 + 0.2 = 0.30000000000000004

**Causa:** Error de punto flotante de JavaScript.

**Solución:** Ya implementada con redondeo:
```javascript
resultado = Math.round(resultado * 1e12) / 1e12;
```

---

### Problema 4: No Funciona en Móvil

**Síntomas:** Se ve mal o los botones son muy pequeños.

**Posibles causas:**
1. Falta meta viewport
2. Media queries no aplicadas

**Solución:**
1. Verifica en `<head>`:
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

2. Prueba en DevTools (F12 → Device Toolbar)

---

### Problema 5: No Copia al Portapapeles

**Síntomas:** Error al presionar "Copiar".

**Causas:**
1. Página no está en HTTPS (excepto localhost)
2. Navegador no soporta la API
3. Permisos denegados

**Solución:**
- Solo funciona en HTTPS o localhost
- Prueba en un servidor local
- Para desarrollo, usa Live Server (extensión VS Code)

---

## 📚 Recursos de Aprendizaje

### Documentación Oficial

**HTML:**
- MDN Web Docs: https://developer.mozilla.org/es/docs/Web/HTML
- HTML Reference: https://htmlreference.io/

**CSS:**
- MDN Web Docs CSS: https://developer.mozilla.org/es/docs/Web/CSS
- CSS Tricks: https://css-tricks.com/
- Flexbox Guide: https://css-tricks.com/snippets/css/a-guide-to-flexbox/
- Grid Guide: https://css-tricks.com/snippets/css/complete-guide-grid/

**JavaScript:**
- MDN JavaScript: https://developer.mozilla.org/es/docs/Web/JavaScript
- JavaScript.info: https://javascript.info/
- Eloquent JavaScript: https://eloquentjavascript.net/

---

### Herramientas Recomendadas

**Editores de Código:**
- Visual Studio Code (recomendado) - https://code.visualstudio.com/
- Sublime Text - https://www.sublimetext.com/
- Atom - https://atom.io/

**Extensiones VS Code útiles:**
- Live Server (servidor local en vivo)
- Prettier (formatea código automáticamente)
- ESLint (encuentra errores de JavaScript)
- Auto Rename Tag (renombra etiquetas HTML emparejadas)

**Navegadores para Desarrollo:**
- Chrome DevTools
- Firefox Developer Edition
- Microsoft Edge DevTools

---

### Cursos Online Gratuitos

- **freeCodeCamp** - https://www.freecodecamp.org/
- **Codecademy** - https://www.codecademy.com/
- **The Odin Project** - https://www.theodinproject.com/
- **MDN Learn** - https://developer.mozilla.org/es/docs/Learn

---

### Comunidades de Ayuda

**Foros:**
- Stack Overflow - https://stackoverflow.com/
- Stack Overflow en Español - https://es.stackoverflow.com/

**Discord:**
- The Programmer's Hangout
- Reactiflux (para React y JavaScript)
- Devcord

**Reddit:**
- r/learnprogramming
- r/webdev
- r/javascript

---

## 🎯 Conclusión

Esta calculadora científica es un proyecto completo que combina:

✅ **HTML** para la estructura  
✅ **CSS** para el diseño responsive  
✅ **JavaScript** para la lógica e interactividad  

### Lo que has aprendido:

1. Estructura de un proyecto web
2. Manipulación del DOM
3. Manejo de eventos
4. Lógica de programación
5. Responsive design
6. Funciones matemáticas
7. Validación de datos
8. Manejo de errores

### Próximos pasos:

1. Experimenta modificando el código
2. Realiza los ejercicios propuestos
3. Comparte tu versión personalizada
4. Aplica estos conceptos en nuevos proyectos

---

**¡Feliz aprendizaje! 🚀**

*Si tienes dudas o encuentras errores, consulta la documentación oficial o busca ayuda en las comunidades mencionadas.*
