# calculadora_markdown

```html
<!DOCTYPE html>
<!-- 
  CALCULADORA CIENTÍFICA PROFESIONAL
  ===================================
  Este documento HTML contiene una calculadora científica completa con:
  - Operaciones básicas: suma, resta, multiplicación, división
  - Funciones científicas: seno, coseno, tangente, logaritmos
  - Sistema de memoria: MC, MR, M+, M-
  - Constantes matemáticas: π (Pi) y e (Euler)
  
  EJERCICIO PROPUESTO: Añade funciones trigonométricas inversas (arcsin, arccos, arctan)
-->
<html lang="es">
<!-- 
  La etiqueta <html> es el elemento raíz que contiene todo el documento
  lang="es" indica que el idioma del contenido es español (importante para SEO y accesibilidad)
-->

<head>
<!-- 
  <head> contiene metadatos (información sobre el documento) que no se muestran directamente
  Aquí van: título, enlaces a CSS, scripts, metadatos para navegadores, etc.
-->

    <meta charset="UTF-8">
    <!-- 
      charset="UTF-8" define la codificación de caracteres
      UTF-8 permite usar acentos, ñ, símbolos especiales y emojis
      IMPORTANTE: Sin esto, los caracteres especiales pueden verse mal (Ã±, Ã©, etc.)
    -->

    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 
      viewport controla cómo se ve la página en dispositivos móviles
      width=device-width: ancho de la página = ancho del dispositivo
      initial-scale=1.0: zoom inicial al 100% (sin zoom)
      EJERCICIO: Prueba a eliminar esta línea y ver cómo se ve en móvil
    -->

    <title>Calculadora Científica</title>
    <!-- 
      <title> define el texto que aparece en la pestaña del navegador
      También es importante para SEO (posicionamiento en buscadores)
    -->

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- 
      Enlace a Font Awesome (librería de iconos)
      Permite usar iconos como <i class="fas fa-calculator"></i>
      CDN = Content Delivery Network (servidor externo que aloja la librería)
      ALTERNATIVA: Descargar Font Awesome localmente para no depender de internet
    -->

    <style>
    <!-- 
      La etiqueta <style> contiene el CSS (Cascading Style Sheets)
      CSS define CÓMO se ven los elementos HTML (colores, tamaños, posiciones, etc.)
      ALTERNATIVA: Poner el CSS en un archivo .css separado y enlazarlo con <link>
    -->

        /* ==========================================
           RESET Y CONFIGURACIÓN GLOBAL
           ========================================== */
        * {
            /* 
              El selector * (asterisco) selecciona TODOS los elementos
              Se usa para resetear estilos por defecto del navegador
            */
            margin: 0;      /* Elimina márgenes externos de todos los elementos */
            padding: 0;     /* Elimina espaciado interno de todos los elementos */
            box-sizing: border-box;
            /* 
              box-sizing: border-box hace que padding y border se incluyan en el ancho/alto total
              SIN border-box: width=100px + padding=10px = 110px total
              CON border-box: width=100px (incluye padding) = 100px total
              EJERCICIO: Cambia a content-box y observa cómo se desajustan los elementos
            */
        }

        /* ==========================================
           ESTILOS DEL BODY (FONDO Y CONTENEDOR PRINCIPAL)
           ========================================== */
        body {
            /* 
              <body> es el contenedor de todo el contenido visible de la página
              Aquí configuramos la fuente, el fondo y el centrado
            */
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            /* 
              font-family define la fuente (tipografía) a usar
              Lista de fuentes en orden de preferencia:
              1. Inter (si está instalada)
              2. -apple-system (fuente del sistema en Mac/iOS)
              3. BlinkMacSystemFont (fuente de Chrome en Mac)
              4. Segoe UI (fuente de Windows)
              5. Roboto (fuente de Android)
              6. sans-serif (fuente genérica sin serifa como último recurso)
              EJERCICIO: Cambia a 'Courier New', monospace para ver una fuente monoespaciada
            */

            display: flex;
            /* 
              display: flex convierte el body en un contenedor flexbox
              Flexbox es un sistema de diseño que facilita alinear y distribuir elementos
              ALTERNATIVA: display: grid (sistema de rejilla)
            */

            justify-content: center;
            /* 
              justify-content: center centra horizontalmente el contenido
              Otras opciones: flex-start (izquierda), flex-end (derecha), space-between, etc.
            */

            align-items: center;
            /* 
              align-items: center centra verticalmente el contenido
              Otras opciones: flex-start (arriba), flex-end (abajo), stretch, etc.
            */

            min-height: 100vh;
            /* 
              min-height: 100vh hace que el body ocupe al menos el 100% del viewport height (altura visible)
              vh = viewport height (1vh = 1% de la altura de la pantalla)
              min-height (en lugar de height) permite que crezca si el contenido es muy grande
              EJERCICIO: Cambia a height: 500px y observa qué pasa en pantallas pequeñas
            */

            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            /* 
              background con linear-gradient crea un degradado (transición suave entre colores)
              135deg: ángulo del degradado (de esquina superior izquierda a inferior derecha)
              #1e3c72: color inicial (azul oscuro)
              #2a5298: color final (azul medio)
              0% y 100%: posiciones donde aplican los colores
              EJERCICIO: Cambia el ángulo a 90deg (vertical) o 180deg (horizontal)
              ALTERNATIVA: radial-gradient para degradados circulares
            */

            padding: 20px;
            /* 
              padding: 20px añade espacio interno de 20 píxeles en todos los lados
              Evita que la calculadora toque los bordes en pantallas pequeñas
              Puedes especificar valores diferentes: padding: 10px 20px (vertical horizontal)
            */
        }
        
        /* ==========================================
           CONTENEDOR PRINCIPAL DE LA CALCULADORA
           ========================================== */
        .calculadora {
            /* 
              El punto (.) indica que es una clase CSS
              Selecciona elementos con class="calculadora"
              ALTERNATIVA: usar #calculadora para un ID (solo puede haber uno en la página)
            */

            background: #2d3748;
            /* 
              background: #2d3748 define color de fondo (gris oscuro)
              # indica color hexadecimal: #RRGGBB (Red, Green, Blue)
              #2d3748 = rojo:45, verde:55, azul:72 (en valores 0-255)
              EJERCICIO: Prueba con rgba(45, 55, 72, 0.9) para añadir transparencia
            */

            padding: 25px;
            /* Espacio interno de 25px en todos los lados */

            border-radius: 20px;
            /* 
              border-radius redondea las esquinas
              20px = radio del redondeo
              Puedes usar porcentajes: 50% crea un círculo (si es cuadrado)
              EJERCICIO: Cambia a 0px para esquinas cuadradas o 50px para más redondeadas
            */

            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.4);
            /* 
              box-shadow añade sombra al elemento
              Sintaxis: offset-x offset-y blur-radius spread-radius color
              0: sin desplazamiento horizontal
              25px: desplazamiento vertical (sombra hacia abajo)
              50px: difuminado (blur)
              rgba(0,0,0,0.4): negro con 40% de opacidad
              EJERCICIO: Añade una segunda sombra: 0 25px 50px rgba(0,0,0,0.4), 0 0 100px rgba(255,255,255,0.1)
            */

            width: 100%;
            /* 
              width: 100% hace que ocupe el 100% del contenedor padre
              En este caso, se combina con max-width para ser responsive
            */

            max-width: 420px;
            /* 
              max-width limita el ancho máximo a 420px
              Combinado con width: 100%, se comporta así:
              - En pantallas grandes: 420px de ancho
              - En pantallas pequeñas: 100% del ancho disponible (menos que 420px)
              EJERCICIO: Cambia a 600px y observa cómo se ve en desktop
            */

            border: 3px solid #4a5568;
            /* 
              border añade un borde
              3px: grosor del borde
              solid: estilo del borde (otras opciones: dashed, dotted, double)
              #4a5568: color del borde (gris medio)
            */
        }

        /* ==========================================
           ENCABEZADO DE LA CALCULADORA
           ========================================== */
        .header {
            text-align: center;
            /* Centra el texto horizontalmente */

            margin-bottom: 20px;
            /* 
              margin-bottom: 20px añade espacio EXTERNO de 20px debajo del elemento
              Diferencia con padding: margin separa del elemento siguiente, padding añade espacio interno
            */

            color: #e2e8f0;
            /* Color del texto (gris muy claro, casi blanco) */

            font-size: 14px;
            /* Tamaño de la fuente en píxeles */

            font-weight: 600;
            /* 
              font-weight: grosor de la fuente
              Valores: 100-900 (100=delgada, 900=negrita extrema)
              También: normal (400), bold (700)
            */

            text-transform: uppercase;
            /* 
              text-transform: uppercase convierte todo el texto a MAYÚSCULAS
              Otras opciones: lowercase, capitalize (primera letra mayúscula)
            */

            letter-spacing: 2px;
            /* 
              letter-spacing: espacio adicional entre letras
              2px añade 2 píxeles extra entre cada letra
              Valores negativos (-1px) acercan las letras
            */
        }

        /* ==========================================
           CONTENEDOR DEL DISPLAY (PANTALLA)
           ========================================== */
        .display-container {
            background: #1a202c;
            /* Color de fondo oscuro (casi negro) */

            padding: 20px;
            /* Espacio interno de 20px */

            border-radius: 12px;
            /* Esquinas redondeadas con radio de 12px */

            margin-bottom: 20px;
            /* Espacio debajo del elemento */

            border: 2px solid #4a5568;
            /* Borde de 2px gris medio */

            box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.5);
            /* 
              inset invierte la sombra (hacia dentro en lugar de hacia fuera)
              Crea un efecto de profundidad, como si estuviera hundido
              0: sin desplazamiento horizontal
              2px: desplazamiento vertical
              8px: difuminado
              rgba(0,0,0,0.5): negro con 50% de opacidad
              EJERCICIO: Elimina 'inset' para ver la diferencia
            */
        }

        /* ==========================================
           DISPLAY SECUNDARIO (OPERACIÓN ACTUAL)
           ========================================== */
        .display-operacion {
            color: #718096;
            /* Color gris medio para el texto */

            font-size: 16px;
            /* Tamaño de fuente */

            min-height: 24px;
            /* 
              min-height: altura mínima de 24px
              Asegura que siempre tenga espacio aunque esté vacío
            */

            text-align: right;
            /* Alinea el texto a la derecha (como una calculadora real) */

            margin-bottom: 8px;
            /* Espacio debajo del elemento */

            font-family: 'Monaco', 'Courier New', monospace;
            /* 
              Fuente monoespaciada (todos los caracteres ocupan el mismo ancho)
              Ideal para números y calculadoras
              Ejemplos de fuentes monoespaciadas: Monaco, Courier, Consolas
            */
        }

        /* ==========================================
           DISPLAY PRINCIPAL (RESULTADO)
           ========================================== */
        .display {
            background: transparent;
            /* Sin color de fondo (transparente) */

            color: #48bb78;
            /* 
              Color verde brillante (estilo LED/pantalla LCD)
              Simula las pantallas de calculadoras clásicas
            */

            font-size: 42px;
            /* Tamaño grande para el resultado principal */

            font-weight: 700;
            /* Grosor de fuente (negrita) */

            text-align: right;
            /* Texto alineado a la derecha */

            min-height: 60px;
            /* Altura mínima para evitar saltos cuando cambia el contenido */

            display: flex;
            /* Convierte en contenedor flexbox */

            align-items: center;
            /* Centra verticalmente el contenido */

            justify-content: flex-end;
            /* 
              justify-content: flex-end alinea el contenido al final (derecha)
              Esto mantiene los números alineados a la derecha incluso con flexbox
            */

            word-break: break-all;
            /* 
              word-break: break-all permite romper palabras largas
              Útil para números muy largos que no caben en una línea
              ALTERNATIVA: overflow-wrap: break-word (rompe solo cuando es necesario)
            */

            font-family: 'Monaco', 'Courier New', monospace;
            /* Fuente monoespaciada para números */

            text-shadow: 0 0 10px rgba(72, 187, 120, 0.3);
            /* 
              text-shadow añade sombra al texto (efecto de brillo)
              0 0: sin desplazamiento (sombra centrada)
              10px: difuminado
              rgba(72, 187, 120, 0.3): verde con 30% opacidad
              Crea un efecto de "brillo" LED alrededor del texto
              EJERCICIO: Aumenta el blur a 20px para más brillo
            */
        }

        /* ==========================================
           DISPLAY EN ESTADO DE ERROR
           ========================================== */
        .display.error {
            /* 
              .display.error es un selector combinado
              Selecciona elementos que tienen AMBAS clases: "display" Y "error"
              Se usa cuando: <div class="display error">
            */

            color: #fc8181;
            /* Color rojo claro para mensajes de error */

            font-size: 18px;
            /* Fuente más pequeña para mensajes largos de error */

            text-shadow: 0 0 10px rgba(252, 129, 129, 0.3);
            /* Brillo rojo en lugar de verde */
        }

        /* ==========================================
           DISPLAY DE MEMORIA
           ========================================== */
        .memoria-display {
            background: #1a202c;
            /* Fondo oscuro */

            padding: 8px 12px;
            /* 
              padding: 8px 12px
              8px: padding vertical (arriba y abajo)
              12px: padding horizontal (izquierda y derecha)
            */

            border-radius: 6px;
            /* Esquinas redondeadas */

            margin-bottom: 15px;
            /* Espacio debajo */

            border: 2px solid #4a5568;
            /* Borde gris */

            text-align: right;
            /* Texto alineado a la derecha */

            color: #f6ad55;
            /* 
              Color naranja para diferenciarse del display principal
              Indica que es una función especial (memoria)
            */

            font-size: 12px;
            /* Tamaño pequeño (info secundaria) */

            font-family: 'Monaco', 'Courier New', monospace;
            /* Fuente monoespaciada */

            min-height: 30px;
            /* Altura mínima */

            display: flex;
            /* Flexbox para centrado */

            align-items: center;
            /* Centra verticalmente */

            justify-content: flex-end;
            /* Alinea a la derecha */
        }

        /* ==========================================
           PANEL DE INFORMACIÓN ADICIONAL
           ========================================== */
        .info-panel {
            display: grid;
            /* 
              display: grid convierte en contenedor de rejilla (grid)
              Grid es ideal para layouts bidimensionales (filas y columnas)
            */

            grid-template-columns: 1fr 1fr;
            /* 
              grid-template-columns define las columnas de la rejilla
              1fr 1fr: dos columnas de igual tamaño
              fr = fracción (unidad flexible que se adapta al espacio disponible)
              EJERCICIO: Cambia a "2fr 1fr" para que la primera columna sea el doble
            */

            gap: 10px;
            /* 
              gap: espacio entre elementos del grid
              10px de separación entre las dos columnas
            */

            background: #1a202c;
            /* Fondo oscuro */

            padding: 12px;
            /* Espacio interno */

            border-radius: 8px;
            /* Esquinas redondeadas */

            margin-bottom: 20px;
            /* Espacio debajo */

            border: 2px solid #4a5568;
            /* Borde gris */
        }

        /* ==========================================
           ITEMS INDIVIDUALES DEL PANEL DE INFO
           ========================================== */
        .info-item {
            text-align: center;
            /* Centra el texto */

            color: #a0aec0;
            /* Color gris claro para el texto */

            font-size: 11px;
            /* Tamaño pequeño */
        }

        .info-value {
            display: block;
            /* 
              display: block hace que el elemento ocupe toda la línea
              Los elementos <span> son inline por defecto, esto los convierte a block
            */

            color: #63b3ed;
            /* Color azul claro para el valor */

            font-size: 14px;
            /* Tamaño mayor que el label */

            font-weight: 700;
            /* Negrita */

            margin-top: 4px;
            /* Espacio arriba (separación del label) */

            font-family: 'Monaco', 'Courier New', monospace;
            /* Fuente monoespaciada para valores numéricos */
        }

        /* ==========================================
           GRID DE BOTONES (LAYOUT PRINCIPAL)
           ========================================== */
        .botones-grid {
            display: grid;
            /* Contenedor grid para organizar botones */

            grid-template-columns: repeat(5, 1fr);
            /* 
              repeat(5, 1fr) es una función que repite la definición
              Equivale a: 1fr 1fr 1fr 1fr 1fr (5 columnas iguales)
              EJERCICIO: Cambia a repeat(4, 1fr) para 4 columnas
            */

            gap: 8px;
            /* 
              gap: 8px añade separación de 8px entre todos los botones
              Tanto vertical como horizontalmente
            */

            margin-bottom: 15px;
            /* Espacio debajo de la rejilla */
        }

        /* ==========================================
           ESTILOS BASE PARA TODOS LOS BOTONES
           ========================================== */
        .btn {
            /* Clase base aplicada a TODOS los botones */

            padding: 16px 8px;
            /* 
              16px vertical, 8px horizontal
              Botones más altos que anchos para facilitar el toque en móvil
            */

            border: none;
            /* 
              Elimina el borde por defecto de los botones
              Los botones HTML tienen bordes feos por defecto
            */

            border-radius: 10px;
            /* Esquinas redondeadas */

            font-size: 16px;
            /* Tamaño de fuente */

            font-weight: 600;
            /* Semi-negrita */

            cursor: pointer;
            /* 
              cursor: pointer cambia el cursor a una "manita" al pasar sobre el botón
              Indica que es clickeable
            */

            transition: all 0.2s ease;
            /* 
              transition: anima los cambios de propiedades CSS
              all: anima todos los cambios (color, transform, etc.)
              0.2s: duración de 0.2 segundos
              ease: curva de animación (comienza lento, acelera, termina lento)
              ALTERNATIVA: ease-in, ease-out, ease-in-out, linear
              EJERCICIO: Cambia a 1s para ver una animación lenta
            */

            color: white;
            /* Color del texto */

            box-shadow: 0 4px 0 rgba(0, 0, 0, 0.3);
            /* 
              Sombra que simula profundidad (efecto 3D)
              Parece que el botón está elevado sobre la superficie
            */

            position: relative;
            /* 
              position: relative permite posicionar elementos hijos de forma absoluta
              También permite usar transform sin problemas
            */
        }

        /* ==========================================
           EFECTO AL HACER CLIC EN UN BOTÓN
           ========================================== */
        .btn:active {
            /* 
              :active es un pseudo-selector que se aplica cuando el elemento está siendo clickeado
              Simula que el botón se "hunde" al presionarlo
            */

            transform: translateY(2px);
            /* 
              transform: translateY mueve el elemento verticalmente
              2px hacia abajo simula que el botón se presiona
            */

            box-shadow: 0 2px 0 rgba(0, 0, 0, 0.3);
            /* 
              Reduce la sombra de 4px a 2px
              Esto complementa el efecto de "hundimiento"
            */
        }

        /* ==========================================
           BOTONES NUMÉRICOS (0-9 y punto decimal)
           ========================================== */
        .btn-numero {
            background: linear-gradient(145deg, #4a5568, #3d4553);
            /* 
              Degradado diagonal (145 grados)
              De gris medio a gris oscuro
              Crea profundidad visual
            */

            color: #e2e8f0;
            /* Color del texto (gris claro) */
        }

        .btn-numero:hover {
            /* 
              :hover se aplica cuando el cursor está sobre el elemento
              Proporciona feedback visual al usuario
            */

            background: linear-gradient(145deg, #5a6578, #4d5563);
            /* 
              Degradado más claro al pasar el cursor
              Indica que el botón es interactivo
            */
        }

        /* ==========================================
           BOTONES DE OPERACIÓN (+, -, ×, ÷, mod)
           ========================================== */
        .btn-operacion {
            background: linear-gradient(145deg, #3182ce, #2c5aa0);
            /* Degradado azul */

            font-size: 20px;
            /* Tamaño más grande para símbolos de operación */
        }

        .btn-operacion:hover {
            background: linear-gradient(145deg, #4299e1, #3c6ab0);
            /* Azul más claro al hacer hover */
        }

        .btn-operacion.active {
            /* 
              Clase aplicada cuando una operación está seleccionada
              Muestra visualmente qué operación se está usando
            */

            background: linear-gradient(145deg, #48bb78, #38a169);
            /* Cambia a verde cuando está activa */

            box-shadow: 0 0 15px rgba(72, 187, 120, 0.5);
            /* 
              Sombra brillante alrededor del botón (efecto glow)
              Hace que el botón "brille" cuando está activo
            */
        }

        /* ==========================================
           BOTONES DE FUNCIÓN CIENTÍFICA (sin, cos, √, etc.)
           ========================================== */
        .btn-funcion {
            background: linear-gradient(145deg, #805ad5, #6b46c1);
            /* Degradado morado/púrpura */

            font-size: 13px;
            /* Fuente más pequeña porque los textos son más largos */
        }

        .btn-funcion:hover {
            background: linear-gradient(145deg, #9f7aea, #7c3aed);
            /* Morado más claro al hacer hover */
        }

        /* ==========================================
           BOTONES DE MEMORIA (MC, MR, M+, M-)
           ========================================== */
        .btn-memoria {
            background: linear-gradient(145deg, #d97706, #b45309);
            /* Degradado naranja para diferenciar de otros botones */

            font-size: 13px;
            /* Fuente pequeña */
        }

        .btn-memoria:hover {
            background: linear-gradient(145deg, #f59e0b, #d97706);
            /* Naranja más claro al hacer hover */
        }

        .btn-memoria.active {
            box-shadow: 0 0 15px rgba(245, 158, 11, 0.6);
            /* 
              Brillo naranja cuando hay algo en memoria
              EJERCICIO: Implementar esta funcionalidad en JavaScript
            */
        }

        /* ==========================================
           BOTÓN DE BORRADO TOTAL (AC - All Clear)
           ========================================== */
        .btn-clear {
            background: linear-gradient(145deg, #e53e3e, #c53030);
            /* Degradado rojo para indicar acción destructiva */
        }

        .btn-clear:hover {
            background: linear-gradient(145deg, #fc8181, #e53e3e);
            /* Rojo más claro al hacer hover */
        }

        /* ==========================================
           BOTÓN DE IGUAL (=)
           ========================================== */
        .btn-igual {
            background: linear-gradient(145deg, #48bb78, #38a169);
            /* Degradado verde para indicar acción principal */

            grid-column: span 2;
            /* 
              grid-column: span 2 hace que el botón ocupe 2 columnas
              Esto hace que el botón = sea más grande (más importante)
              EJERCICIO: Cambia a span 3 para que ocupe 3 columnas
            */
        }

        .btn-igual:hover {
            background: linear-gradient(145deg, #68d391, #48bb78);
            /* Verde más claro al hacer hover */
        }

        /* ==========================================
           BOTONES DE ACCIÓN (Copiar, Borrar último)
           ========================================== */
        .acciones-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            /* Dos columnas de igual tamaño */
            gap: 10px;
        }

        .btn-accion {
            padding: 15px;
            background: linear-gradient(145deg, #2d3748, #1a202c);
            color: #e2e8f0;
            border: 2px solid #4a5568;
            border-radius: 10px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s ease;

            display: flex;
            /* Flexbox para alinear icono + texto */

            align-items: center;
            /* Centra verticalmente */

            justify-content: center;
            /* Centra horizontalmente */

            gap: 8px;
            /* Espacio entre icono y texto */

            text-transform: uppercase;
            /* Texto en mayúsculas */

            letter-spacing: 0.5px;
            /* Espaciado entre letras */

            position: relative;
            /* Para posicionar el tooltip */
        }

        .btn-accion:hover {
            background: linear-gradient(145deg, #3d4758, #2a303c);
            border-color: #63b3ed;
            /* Borde azul al hacer hover */
        }

        .btn-accion:active {
            transform: scale(0.98);
            /* 
              scale(0.98) reduce el tamaño al 98% cuando se hace clic
              Efecto alternativo al translateY para botones planos
            */
        }

        /* ==========================================
           TOOLTIP (MENSAJE EMERGENTE)
           ========================================== */
        .tooltip {
            position: absolute;
            /* 
              position: absolute posiciona el elemento respecto a su padre con position: relative
              Permite sacarlo del flujo normal del documento
            */

            background: #1a202c;
            color: #48bb78;
            padding: 8px 14px;
            border-radius: 6px;
            font-size: 11px;

            bottom: 100%;
            /* 
              bottom: 100% posiciona el tooltip justo encima del botón
              100% = altura completa del elemento padre
            */

            left: 50%;
            /* 
              left: 50% lo posiciona al 50% desde la izquierda
              Combinado con transform, centra el tooltip
            */

            transform: translateX(-50%) translateY(-10px);
            /* 
              translateX(-50%) mueve el tooltip 50% de su propio ancho a la izquierda
              Esto lo centra perfectamente sobre el botón
              translateY(-10px) lo separa 10px hacia arriba
            */

            opacity: 0;
            /* 
              opacity: 0 hace el elemento completamente transparente (invisible)
              Valores: 0 (invisible) a 1 (opaco)
            */

            pointer-events: none;
            /* 
              pointer-events: none hace que el elemento ignore eventos del mouse
              Evita que el tooltip bloquee clics o hover de otros elementos
            */

            transition: opacity 0.3s ease;
            /* Anima el cambio de opacidad */

            white-space: nowrap;
            /* 
              white-space: nowrap evita que el texto se divida en varias líneas
              El tooltip siempre será de una sola línea
            */

            z-index: 1000;
            /* 
              z-index controla el orden de apilamiento (qué elemento está encima)
              1000 es un valor alto que asegura que esté sobre otros elementos
            */

            border: 1px solid #48bb78;
            /* Borde verde que combina con el color del texto */
        }

        .tooltip.show {
            /* Clase añadida por JavaScript cuando se quiere mostrar el tooltip */
            opacity: 1;
            /* Hace visible el tooltip con transición suave */
        }

        /* ==========================================
           RESPONSIVE DESIGN - TABLET
           Media query para pantallas de 480px o menos
           ========================================== */
        @media (max-width: 480px) {
            /* 
              @media es una "media query" - aplica estilos solo si se cumple la condición
              max-width: 480px se activa cuando el ancho de pantalla es 480px o menos
              Útil para adaptar el diseño a móviles y tablets pequeñas
              EJERCICIO: Añade un @media (min-width: 768px) para tablets grandes
            */

            .calculadora {
                padding: 20px;
                /* Reduce el padding en pantallas pequeñas (ahorra espacio) */
                max-width: 100%;
                /* Usa todo el ancho disponible */
            }

            .botones-grid {
                grid-template-columns: repeat(5, 1fr);
                /* Mantiene 5 columnas pero más estrechas */
                gap: 6px;
                /* Reduce el espacio entre botones (de 8px a 6px) */
            }

            .display {
                font-size: 36px;
                /* Reduce el tamaño de fuente del display (de 42px a 36px) */
                min-height: 50px;
                /* Reduce la altura mínima */
            }

            .btn {
                padding: 14px 6px;
                /* Reduce el padding de los botones */
                font-size: 14px;
                /* Reduce el tamaño de fuente */
            }

            .btn-operacion {
                font-size: 18px;
                /* Reduce tamaño de símbolos de operación */
            }

            .btn-funcion, .btn-memoria {
                font-size: 11px;
                /* Reduce tamaño de texto en botones de función */
            }
        }

        /* ==========================================
           RESPONSIVE DESIGN - MÓVILES PEQUEÑOS
           Media query para pantallas de 360px o menos
           ========================================== */
        @media (max-width: 360px) {
            /* 
              Móviles muy pequeños (ej: iPhone SE, Galaxy S5)
              Ajustes más agresivos para que todo quepa
            */

            .display {
                font-size: 28px;
                /* Display más pequeño para números largos */
            }

            .btn {
                padding: 12px 4px;
                /* Padding mínimo en botones */
                font-size: 12px;
            }

            .botones-grid {
                gap: 5px;
                /* Espacio mínimo entre botones */
            }

            .btn-funcion, .btn-memoria {
                font-size: 10px;
                /* Tamaño mínimo legible */
            }
        }

        /* ==========================================
           MARCA/BRAND (texto inferior)
           ========================================== */
        .brand {
            text-align: center;
            color: #718096;
            font-size: 10px;
            margin-top: 15px;
            text-transform: uppercase;
            letter-spacing: 1px;
            /* 
              Pequeño texto decorativo en la parte inferior
              EJERCICIO: Añade tu nombre o logo personalizado
            */
        }
    </style>
</head>

<body>
<!-- 
  ========================================
  ESTRUCTURA HTML DE LA CALCULADORA
  ========================================
  A partir de aquí comienza el contenido visible de la página
-->

    <div class="calculadora">
    <!-- 
      Contenedor principal que agrupa toda la calculadora
      La clase "calculadora" aplica los estilos CSS definidos arriba
    -->

        <div class="header">
        <!-- Encabezado/título de la calculadora -->
            <i class="fas fa-calculator"></i>
            <!-- 
              Icono de calculadora de Font Awesome
              fas = Font Awesome Solid (estilo sólido)
              fa-calculator = clase específica del icono
            -->
            CALCULADORA CIENTÍFICA
        </div>

        <div class="display-container">
        <!-- Contenedor del display (pantalla de la calculadora) -->
            <div class="display-operacion" id="displayOperacion">0</div>
            <!-- 
              Display secundario que muestra la operación actual
              id="displayOperacion" permite seleccionarlo desde JavaScript
              El id debe ser único en toda la página
            -->

            <div class="display" id="display">0</div>
            <!-- 
              Display principal que muestra el número actual o resultado
              Empieza mostrando "0"
            -->
        </div>

        <div class="memoria-display" id="memoriaDisplay">
        <!-- Display que muestra el valor guardado en memoria -->
            Memoria: 0
        </div>

        <div class="info-panel" id="infoPanel" style="display: none;">
        <!-- 
          Panel que muestra información adicional (notación científica, precisión)
          style="display: none;" lo oculta inicialmente
          JavaScript lo mostrará cuando haya un resultado
        -->
            <div class="info-item">
                <span>Notación Científica</span>
                <!-- Label del dato -->
                <span class="info-value" id="notacionCientifica">-</span>
                <!-- Valor del dato (actualizado por JavaScript) -->
            </div>
            <div class="info-item">
                <span>Precisión</span>
                <span class="info-value" id="precision">-</span>
            </div>
        </div>

        <div class="botones-grid">
        <!-- 
          Grid (rejilla) que contiene todos los botones
          CSS Grid los organizará automáticamente en 5 columnas
        -->

            <!-- ===== FILA 1: FUNCIONES DE MEMORIA Y BORRADO ===== -->
            <button class="btn btn-memoria" onclick="memoriaLimpiar()">MC</button>
            <!-- 
              MC = Memory Clear (Limpiar memoria)
              onclick="memoriaLimpiar()" ejecuta la función memoriaLimpiar() cuando se hace clic
              La función está definida en JavaScript más abajo
            -->

            <button class="btn btn-memoria" onclick="memoriaRecuperar()">MR</button>
            <!-- MR = Memory Recall (Recuperar de memoria) -->

            <button class="btn btn-memoria" onclick="memoriaSumar()">M+</button>
            <!-- M+ = Memory Add (Sumar a memoria) -->

            <button class="btn btn-memoria" onclick="memoriaRestar()">M-</button>
            <!-- M- = Memory Subtract (Restar de memoria) -->

            <button class="btn btn-clear" onclick="limpiar()">AC</button>
            <!-- 
              AC = All Clear (Borrar todo)
              Reinicia la calculadora al estado inicial
            -->

            <!-- ===== FILA 2: FUNCIONES TRIGONOMÉTRICAS Y LOGARITMOS ===== -->
            <button class="btn btn-funcion" onclick="aplicarFuncion('sin')">sin</button>
            <!-- 
              Botón de función seno
              onclick pasa el parámetro 'sin' a la función aplicarFuncion()
              La función usará este parámetro para saber qué operación realizar
            -->

            <button class="btn btn-funcion" onclick="aplicarFuncion('cos')">cos</button>
            <!-- Coseno -->

            <button class="btn btn-funcion" onclick="aplicarFuncion('tan')">tan</button>
            <!-- Tangente -->

            <button class="btn btn-funcion" onclick="aplicarFuncion('log')">log</button>
            <!-- Logaritmo base 10 -->

            <button class="btn btn-funcion" onclick="aplicarFuncion('ln')">ln</button>
            <!-- Logaritmo natural (base e) -->

            <!-- ===== FILA 3: FUNCIONES MATEMÁTICAS Y DIVISIÓN ===== -->
            <button class="btn btn-funcion" onclick="aplicarFuncion('raiz')">√</button>
            <!-- Raíz cuadrada -->

            <button class="btn btn-funcion" onclick="aplicarFuncion('potencia')">x²</button>
            <!-- Potencia al cuadrado -->

            <button class="btn btn-funcion" onclick="aplicarFuncion('porcentaje')">%</button>
            <!-- Porcentaje (divide entre 100) -->

            <button class="btn btn-operacion" onclick="seleccionarOperacion('mod')">mod</button>
            <!-- Módulo (resto de la división) -->

            <button class="btn btn-operacion" onclick="seleccionarOperacion('division')">÷</button>
            <!-- División -->

            <!-- ===== FILA 4: NÚMEROS 7-9, MULTIPLICACIÓN, CAMBIO DE SIGNO ===== -->
            <button class="btn btn-numero" onclick="agregarNumero('7')">7</button>
            <!-- 
              onclick="agregarNumero('7')" añade el dígito '7' al display
              El parámetro es un string (texto) porque los números en el display son texto
            -->

            <button class="btn btn-numero" onclick="agregarNumero('8')">8</button>
            <button class="btn btn-numero" onclick="agregarNumero('9')">9</button>

            <button class="btn btn-operacion" onclick="seleccionarOperacion('multiplicacion')">×</button>
            <!-- Multiplicación -->

            <button class="btn btn-funcion" onclick="cambiarSigno()">±</button>
            <!-- Cambiar signo (positivo/negativo) -->

            <!-- ===== FILA 5: NÚMEROS 4-6, RESTA, INVERSO ===== -->
            <button class="btn btn-numero" onclick="agregarNumero('4')">4</button>
            <button class="btn btn-numero" onclick="agregarNumero('5')">5</button>
            <button class="btn btn-numero" onclick="agregarNumero('6')">6</button>

            <button class="btn btn-operacion" onclick="seleccionarOperacion('resta')">−</button>
            <!-- Resta (usamos − en lugar de - para claridad visual) -->

            <button class="btn btn-funcion" onclick="aplicarFuncion('inverso')">1/x</button>
            <!-- Inverso multiplicativo (1 dividido entre x) -->

            <!-- ===== FILA 6: NÚMEROS 1-3, SUMA, PI ===== -->
            <button class="btn btn-numero" onclick="agregarNumero('1')">1</button>
            <button class="btn btn-numero" onclick="agregarNumero('2')">2</button>
            <button class="btn btn-numero" onclick="agregarNumero('3')">3</button>

            <button class="btn btn-operacion" onclick="seleccionarOperacion('suma')">+</button>
            <!-- Suma -->

            <button class="btn btn-funcion" onclick="insertarPi()">π</button>
            <!-- Inserta el valor de Pi (3.14159...) -->

            <!-- ===== FILA 7: 0, PUNTO, e, IGUAL ===== -->
            <button class="btn btn-numero" onclick="agregarNumero('0')">0</button>

            <button class="btn btn-numero" onclick="agregarNumero('.')">.</button>
            <!-- Punto decimal -->

            <button class="btn btn-funcion" onclick="insertarE()">e</button>
            <!-- Inserta el número de Euler (2.71828...) -->

            <button class="btn btn-igual" onclick="calcular()" style="grid-column: span 2;">=</button>
            <!-- 
              Botón igual (ejecuta el cálculo)
              style="grid-column: span 2;" hace que ocupe 2 columnas (más grande)
              Este estilo inline sobrescribe el CSS
            -->
        </div>

        <!-- ===== BOTONES DE ACCIÓN ADICIONALES ===== -->
        <div class="acciones-grid">
            <button class="btn-accion" id="btnCopiar" onclick="copiarResultado()">
                <i class="fas fa-copy"></i>
                <!-- Icono de copiar -->
                <span>COPIAR</span>
                <div class="tooltip" id="tooltip">¡Copiado!</div>
                <!-- Tooltip que aparece al copiar (controlado por JavaScript) -->
            </button>

            <button class="btn-accion" onclick="borrarUltimo()">
                <i class="fas fa-backspace"></i>
                <!-- Icono de retroceso/borrar -->
                <span>BORRAR</span>
            </button>
        </div>

        <div class="brand">SCIENTIFIC CALCULATOR PRO</div>
        <!-- Marca/brand en la parte inferior -->
    </div>

    <script>
    <!-- 
      ========================================
      JAVASCRIPT - LÓGICA DE LA CALCULADORA
      ========================================
      JavaScript hace que la calculadora sea interactiva
      Aquí se definen todas las funciones que se ejecutan al hacer clic en los botones
    -->

        // ==========================================
        // VARIABLES GLOBALES (Estado de la calculadora)
        // ==========================================
        // let permite declarar variables que pueden cambiar su valor
        // const se usa para valores que no cambiarán (más abajo)

        let displayOperacion = document.getElementById('displayOperacion');
        // document.getElementById() busca un elemento HTML por su ID
        // Esto nos da acceso al elemento para modificarlo desde JavaScript
        // EJERCICIO: Usa console.log(displayOperacion) para ver el objeto en la consola

        let display = document.getElementById('display');
        // Referencia al display principal

        let infoPanel = document.getElementById('infoPanel');
        // Referencia al panel de información adicional

        let notacionCientifica = document.getElementById('notacionCientifica');
        // Referencia al elemento que muestra la notación científica

        let precision = document.getElementById('precision');
        // Referencia al elemento que muestra la precisión (decimales)

        let tooltip = document.getElementById('tooltip');
        // Referencia al tooltip del botón copiar

        let memoriaDisplay = document.getElementById('memoriaDisplay');
        // Referencia al display de memoria

        // Variables que almacenan el estado actual de la calculadora
        let numeroActual = '0';
        // String que representa el número que se está mostrando
        // Es string (texto) porque puede contener punto decimal y se construye carácter a carácter

        let operacionActual = null;
        // Guarda qué operación se seleccionó ('suma', 'resta', etc.)
        // null significa "sin valor" o "vacío"

        let numeroAnterior = null;
        // Guarda el primer número de la operación
        // Ejemplo: en "5 + 3", numeroAnterior es 5

        let reiniciarDisplay = false;
        // Flag (bandera) booleano que indica si el siguiente número debe reemplazar el display
        // true después de presionar una operación o calcular un resultado

        let memoria = 0;
        // Valor guardado en memoria (usado por MC, MR, M+, M-)

        let anguloEnRadianes = true;
        // Determina si las funciones trigonométricas usan radianes o grados
        // true = radianes, false = grados
        // EJERCICIO: Añade un botón para alternar entre RAD y DEG

        // ==========================================
        // FUNCIÓN: actualizarDisplay()
        // Actualiza lo que se muestra en la pantalla
        // ==========================================
        function actualizarDisplay() {
            // function declara una función (bloque de código reutilizable)
            // Las funciones se "llaman" o "invocan" escribiendo su nombre seguido de ()

            display.textContent = numeroActual;
            // textContent modifica el texto dentro del elemento HTML
            // Equivale a hacer: <div>numeroActual</div>

            display.classList.remove('error');
            // classList.remove() elimina una clase CSS del elemento
            // Esto quita el estilo de error (color rojo) si estaba aplicado

            // Mostrar la operación actual en el display secundario
            if (numeroAnterior !== null && operacionActual) {
                // !== significa "no es estrictamente igual"
                // Esta condición verifica si hay una operación pendiente
                // && es el operador lógico "Y" (ambas condiciones deben cumplirse)

                const simbolos = {
                    // const declara una constante (no se puede reasignar)
                    // Este es un objeto JavaScript (diccionario clave-valor)
                    'suma': '+',
                    'resta': '−',
                    'multiplicacion': '×',
                    'division': '÷',
                    'mod': 'mod'
                };
                // Este objeto mapea nombres de operaciones a sus símbolos visuales

                displayOperacion.textContent = `${numeroAnterior} ${simbolos[operacionActual]}`;
                // Template literal (${}) permite insertar variables en strings
                // simbolos[operacionActual] busca el símbolo correspondiente
                // Ejemplo: si operacionActual='suma', muestra "5 +"
            } else {
                // else se ejecuta si la condición del if es falsa
                displayOperacion.textContent = numeroActual;
                // Si no hay operación pendiente, muestra solo el número actual
            }
        }

        // ==========================================
        // FUNCIÓN: agregarNumero(num)
        // Añade un dígito o punto decimal al display
        // ==========================================
        function agregarNumero(num) {
            // num es un parámetro (valor que recibe la función)
            // Se pasa cuando se llama la función: agregarNumero('7')

            if (reiniciarDisplay) {
                // Si es true, reemplaza el display con el nuevo número
                numeroActual = num;
                reiniciarDisplay = false;
                // Resetea el flag
            } else {
                // Si es false, añade el dígito al número existente
                if (numeroActual === '0' && num !== '.') {
                    // === significa "es estrictamente igual"
                    // !== significa "no es estrictamente igual"
                    // Si el display muestra "0" y se presiona un número (no punto), reemplaza el 0
                    numeroActual = num;
                } else if (num === '.' && numeroActual.includes('.')) {
                    // includes() verifica si un string contiene otro string
                    // Evita que se añadan múltiples puntos decimales
                    return;
                    // return termina la ejecución de la función (no continúa)
                } else {
                    // En cualquier otro caso, concatena (une) el nuevo dígito
                    numeroActual += num;
                    // += es un operador de asignación que concatena strings
                    // Equivale a: numeroActual = numeroActual + num
                }
            }
            actualizarDisplay();
            // Llama a la función para refrescar la pantalla
        }

        // ==========================================
        // FUNCIÓN: seleccionarOperacion(operacion)
        // Selecciona qué operación matemática se realizará
        // ==========================================
        function seleccionarOperacion(operacion) {
            // Recibe el tipo de operación: 'suma', 'resta', etc.

            if (numeroAnterior !== null && !reiniciarDisplay) {
                // ! es el operador NOT (negación lógica)
                // Si hay una operación pendiente y no se ha reiniciado el display,
                // primero calcula el resultado de la operación anterior
                calcular();
            }
            
            operacionActual = operacion;
            // Guarda la operación seleccionada

            numeroAnterior = parseFloat(numeroActual);
            // parseFloat() convierte un string a número decimal
            // "3.14" (string) se convierte en 3.14 (número)
            // Guarda el número actual como el primero de la operación

            reiniciarDisplay = true;
            // Marca que el siguiente número debe reemplazar el display

            // Código para resaltar botón activo (visual feedback)
            document.querySelectorAll('.btn-operacion').forEach(btn => {
                // querySelectorAll() selecciona todos los elementos con esa clase
                // forEach() ejecuta una función para cada elemento
                btn.classList.remove('active');
                // Quita la clase 'active' de todos los botones de operación
            });
            // EJERCICIO: Añade btn.classList.add('active') al botón clickeado
        }

        // ==========================================
        // FUNCIÓN: calcular()
        // Ejecuta la operación matemática pendiente
        // ==========================================
        function calcular() {
            if (operacionActual === null || numeroAnterior === null) {
                // || es el operador lógico "O" (al menos una condición debe cumplirse)
                // Si no hay operación o número anterior, no hace nada
                return;
            }

            const num1 = numeroAnterior;
            // Primer operando

            const num2 = parseFloat(numeroActual);
            // Segundo operando (convierte de string a número)

            let resultado;
            // Variable que guardará el resultado de la operación

            // switch es una estructura que ejecuta código según el valor de una variable
            switch(operacionActual) {
                case 'suma':
                    // case define un caso posible
                    resultado = num1 + num2;
                    // + suma dos números
                    break;
                    // break termina el switch (evita que continúe a los siguientes casos)

                case 'resta':
                    resultado = num1 - num2;
                    // - resta dos números
                    break;

                case 'multiplicacion':
                    resultado = num1 * num2;
                    // * multiplica dos números
                    break;

                case 'division':
                    if (num2 === 0) {
                        // Verifica división por cero
                        display.textContent = 'Error: División por cero';
                        display.classList.add('error');
                        // classList.add() añade una clase CSS (aplica estilos de error)
                        infoPanel.style.display = 'none';
                        // style.display modifica directamente el CSS del elemento
                        // 'none' oculta el elemento
                        numeroActual = '0';
                        numeroAnterior = null;
                        operacionActual = null;
                        displayOperacion.textContent = '0';
                        return;
                        // Termina la función (no continúa ejecutando)
                    }
                    resultado = num1 / num2;
                    // / divide dos números
                    break;

                case 'mod':
                    resultado = num1 % num2;
                    // % es el operador módulo (resto de la división)
                    // Ejemplo: 10 % 3 = 1 (porque 10 ÷ 3 = 3 con resto 1)
                    break;
            }

            mostrarResultado(resultado);
            // Llama a otra función para mostrar el resultado

            operacionActual = null;
            numeroAnterior = null;
            // Resetea las variables (operación completada)

            reiniciarDisplay = true;
            // El siguiente número debe reemplazar el resultado
        }

        // ==========================================
        // FUNCIÓN: aplicarFuncion(funcion)
        // Aplica funciones científicas (sin, cos, log, etc.)
        // ==========================================
        function aplicarFuncion(funcion) {
            const num = parseFloat(numeroActual);
            // Obtiene el número actual del display

            if (isNaN(num)) return;
            // isNaN() verifica si algo NO es un número (Not a Number)
            // Si no es un número válido, termina la función

            let resultado;

            switch(funcion) {
                case 'sin':
                    // Calcula el seno
                    resultado = anguloEnRadianes ? Math.sin(num) : Math.sin(num * Math.PI / 180);
                    // ? : es el operador ternario (if-else condensado)
                    // Si anguloEnRadianes es true, usa Math.sin(num)
                    // Si es false, convierte grados a radianes primero
                    // Math es un objeto con funciones matemáticas integradas
                    displayOperacion.textContent = `sin(${num})`;
                    break;

                case 'cos':
                    // Calcula el coseno
                    resultado = anguloEnRadianes ? Math.cos(num) : Math.cos(num * Math.PI / 180);
                    displayOperacion.textContent = `cos(${num})`;
                    break;

                case 'tan':
                    // Calcula la tangente
                    resultado = anguloEnRadianes ? Math.tan(num) : Math.tan(num * Math.PI / 180);
                    displayOperacion.textContent = `tan(${num})`;
                    break;

                case 'log':
                    // Logaritmo base 10
                    if (num <= 0) {
                        // <= significa "menor o igual que"
                        // El logaritmo solo existe para números positivos
                        display.textContent = 'Error: log(x) requiere x > 0';
                        display.classList.add('error');
                        return;
                    }
                    resultado = Math.log10(num);
                    // Math.log10() calcula el logaritmo base 10
                    displayOperacion.textContent = `log(${num})`;
                    break;

                case 'ln':
                    // Logaritmo natural (base e)
                    if (num <= 0) {
                        display.textContent = 'Error: ln(x) requiere x > 0';
                        display.classList.add('error');
                        return;
                    }
                    resultado = Math.log(num);
                    // Math.log() calcula el logaritmo natural (ln)
                    displayOperacion.textContent = `ln(${num})`;
                    break;

                case 'raiz':
                    // Raíz cuadrada
                    if (num < 0) {
                        // < significa "menor que"
                        // No se puede calcular raíz cuadrada de números negativos (en números reales)
                        display.textContent = 'Error: Raíz de número negativo';
                        display.classList.add('error');
                        return;
                    }
                    resultado = Math.sqrt(num);
                    // Math.sqrt() calcula la raíz cuadrada (square root)
                    displayOperacion.textContent = `√${num}`;
                    break;

                case 'potencia':
                    // Elevar al cuadrado
                    resultado = Math.pow(num, 2);
                    // Math.pow(base, exponente) eleva un número a una potencia
                    // Math.pow(5, 2) = 5² = 25
                    displayOperacion.textContent = `${num}²`;
                    break;

                case 'porcentaje':
                    // Convertir a porcentaje (dividir entre 100)
                    resultado = num / 100;
                    displayOperacion.textContent = `${num}%`;
                    break;

                case 'inverso':
                    // Inverso multiplicativo (1/x)
                    if (num === 0) {
                        display.textContent = 'Error: División por cero';
                        display.classList.add('error');
                        return;
                    }
                    resultado = 1 / num;
                    displayOperacion.textContent = `1/${num}`;
                    break;
            }

            mostrarResultado(resultado);
            reiniciarDisplay = true;
        }

        // ==========================================
        // FUNCIÓN: mostrarResultado(resultado)
        // Muestra el resultado en el display y actualiza info adicional
        // ==========================================
        function mostrarResultado(resultado) {
            resultado = Math.round(resultado * 1000000000000) / 1000000000000;
            // Redondea a 12 decimales para evitar errores de punto flotante
            // JavaScript tiene problemas con decimales: 0.1 + 0.2 = 0.30000000000000004
            // Este truco limita los decimales indeseados

            numeroActual = resultado.toString();
            // .toString() convierte un número a string

            actualizarDisplay();
            // Actualiza la pantalla principal

            // Mostrar información adicional
            infoPanel.style.display = 'grid';
            // Hace visible el panel de información

            notacionCientifica.textContent = resultado.toExponential(4);
            // .toExponential(4) convierte a notación científica con 4 decimales
            // 1234.56 se convierte en "1.2346e+3"
            
            const decimales = resultado.toString().split('.')[1];
            // .split('.') divide el string en un array usando '.' como separador
            // "3.14159".split('.') = ["3", "14159"]
            // [1] selecciona el segundo elemento (los decimales)

            precision.textContent = decimales ? decimales.length + ' dígitos' : '0 dígitos';
            // Operador ternario: si hay decimales, cuenta cuántos; si no, muestra 0
        }

        // ==========================================
        // FUNCIÓN: limpiar()
        // Reinicia la calculadora al estado inicial (AC - All Clear)
        // ==========================================
        function limpiar() {
            numeroActual = '0';
            numeroAnterior = null;
            operacionActual = null;
            reiniciarDisplay = false;
            display.classList.remove('error');
            displayOperacion.textContent = '0';
            infoPanel.style.display = 'none';
            actualizarDisplay();
            // Resetea todas las variables y oculta el panel de info
        }

        // ==========================================
        // FUNCIÓN: borrarUltimo()
        // Borra el último dígito (backspace)
        // ==========================================
        function borrarUltimo() {
            if (numeroActual.length > 1) {
                // .length devuelve la longitud del string
                // Si tiene más de un carácter, borra el último
                numeroActual = numeroActual.slice(0, -1);
                // .slice(inicio, fin) extrae una porción del string
                // (0, -1) desde el inicio hasta el penúltimo carácter
                // "12345".slice(0, -1) = "1234"
            } else {
                // Si solo queda un carácter, lo reemplaza por '0'
                numeroActual = '0';
            }
            actualizarDisplay();
        }

        // ==========================================
        // FUNCIÓN: cambiarSigno()
        // Cambia el signo del número (positivo/negativo)
        // ==========================================
        function cambiarSigno() {
            if (numeroActual === '0') return;
            // No hace nada si el número es 0

            numeroActual = (parseFloat(numeroActual) * -1).toString();
            // Multiplica por -1 para cambiar el signo
            // 5 * -1 = -5
            // -5 * -1 = 5

            actualizarDisplay();
        }

        // ==========================================
        // FUNCIÓN: insertarPi()
        // Inserta el valor de Pi (π)
        // ==========================================
        function insertarPi() {
            numeroActual = Math.PI.toString();
            // Math.PI es la constante Pi (3.141592653589793)
            reiniciarDisplay = true;
            actualizarDisplay();
        }

        // ==========================================
        // FUNCIÓN: insertarE()
        // Inserta el número de Euler (e)
        // ==========================================
        function insertarE() {
            numeroActual = Math.E.toString();
            // Math.E es el número de Euler (2.718281828459045)
            reiniciarDisplay = true;
            actualizarDisplay();
        }

        // ==========================================
        // FUNCIONES DE MEMORIA
        // ==========================================
        
        function memoriaLimpiar() {
            // MC - Memory Clear
            memoria = 0;
            actualizarMemoriaDisplay();
        }

        function memoriaRecuperar() {
            // MR - Memory Recall
            numeroActual = memoria.toString();
            // Copia el valor de memoria al display
            reiniciarDisplay = true;
            actualizarDisplay();
        }

        function memoriaSumar() {
            // M+ - Memory Add
            memoria += parseFloat(numeroActual);
            // += suma al valor existente
            // memoria = memoria + numeroActual
            actualizarMemoriaDisplay();
        }

        function memoriaRestar() {
            // M- - Memory Subtract
            memoria -= parseFloat(numeroActual);
            // -= resta del valor existente
            actualizarMemoriaDisplay();
        }

        function actualizarMemoriaDisplay() {
            // Actualiza el display de memoria
            if (memoria === 0) {
                memoriaDisplay.textContent = 'Memoria: 0';
            } else {
                memoriaDisplay.textContent = `Memoria: ${memoria.toFixed(6)}`;
                // .toFixed(6) redondea a 6 decimales
                // 3.141592653589793.toFixed(6) = "3.141593"
            }
        }

        // ==========================================
        // FUNCIÓN: copiarResultado()
        // Copia el resultado al portapapeles
        // ==========================================
        async function copiarResultado() {
            // async indica que esta función es asíncrona (puede usar await)
            // Las funciones asíncronas no bloquean el código mientras esperan

            if (numeroActual === '0') return;
            // No copia si el display muestra solo 0

            try {
                // try-catch maneja errores
                // try intenta ejecutar el código
                // Si falla, ejecuta el código en catch

                await navigator.clipboard.writeText(numeroActual);
                // await espera a que se complete la operación asíncrona
                // navigator.clipboard.writeText() copia texto al portapapeles
                // Es asíncrona porque requiere permisos del usuario

                tooltip.classList.add('show');
                // Muestra el tooltip "¡Copiado!"

                setTimeout(() => tooltip.classList.remove('show'), 2000);
                // setTimeout ejecuta código después de un tiempo
                // 2000 milisegundos = 2 segundos
                // () => es una arrow function (función flecha)
            } catch (err) {
                // catch captura cualquier error que ocurra en try
                console.error('Error al copiar:', err);
                // console.error() muestra el error en la consola del navegador
            }
        }

        // ==========================================
        // SOPORTE DE TECLADO
        // Permite usar la calculadora con el teclado
        // ==========================================
        document.addEventListener('keydown', (e) => {
            // addEventListener() escucha eventos (clicks, teclas, etc.)
            // 'keydown' se dispara cuando se presiona una tecla
            // (e) => es una arrow function que recibe el evento

            if (e.key >= '0' && e.key <= '9' || e.key === '.') {
                // e.key contiene la tecla presionada
                // >= y <= comparan strings alfabéticamente
                // Si se presiona un número o punto, lo añade
                agregarNumero(e.key);
            } else if (e.key === '+') {
                seleccionarOperacion('suma');
            } else if (e.key === '-') {
                seleccionarOperacion('resta');
            } else if (e.key === '*') {
                seleccionarOperacion('multiplicacion');
            } else if (e.key === '/') {
                e.preventDefault();
                // preventDefault() evita el comportamiento por defecto
                // En este caso, evita que '/' active la búsqueda rápida en Firefox
                seleccionarOperacion('division');
            } else if (e.key === 'Enter' || e.key === '=') {
                e.preventDefault();
                calcular();
            } else if (e.key === 'Escape') {
                // Escape borra todo
                limpiar();
            } else if (e.key === 'Backspace') {
                // Backspace borra el último dígito
                borrarUltimo();
            }
        });

        // ==========================================
        // INICIALIZACIÓN
        // ==========================================
        actualizarDisplay();
        // Llama a actualizarDisplay() al cargar la página
        // Asegura que el display muestre "0" inicialmente

        // ==========================================
        // EJERCICIOS PROPUESTOS PARA AMPLIAR
        // ==========================================
        /*
        1. Añadir funciones trigonométricas inversas (arcsin, arccos, arctan)
        2. Añadir botón RAD/DEG para alternar entre radianes y grados
        3. Añadir historial de cálculos (guardar últimas 10 operaciones)
        4. Añadir función de potencia genérica (x^y)
        5. Añadir factorial (n!)
        6. Añadir conversión entre bases (binario, octal, hexadecimal)
        7. Guardar el estado en localStorage (persiste al recargar)
        8. Añadir temas (modo oscuro/claro)
        9. Añadir sonidos al presionar botones
        10. Añadir gráficos (graficar funciones)
        */
    </script>
</body>
</html>
```

[image_alt](https://github.com/IveEva/calculadora_markdown/blob/655a45f2953484f67e77ab310febc1c9cf826a76/microprocesador%206502.jpg)
# Tareas pendientes:
- [x] Añadir funciones de memoria.
- [ ] Imcluir conversión de binario a hex.
- [ ] Añadir pin de usuario.
