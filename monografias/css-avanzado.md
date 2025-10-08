---
layout: default
title: "Monografía — CSS Avanzado"
---
<h1 align="center">UNIVERSIDAD NACIONAL DEL CENTRO DEL PERÚ</h1>

<div align="center">   
    <img width="400" height="350" src="https://upload.wikimedia.org/wikipedia/commons/9/92/Escudo_UNCP.png" />
</div>

<h2 align="center">
    <p>FACULTAD DE INGENIERÍA DE SISTEMAS</p>
    <p>DESARROLLO DE APLICACIONES WEB</p>
</h2>

<h2 align="center">
     Conocimientos avanzados del lenguaje de diseño CSS
</h2>

**PRESENTADO POR:**

◼️Cerrón Pizarro Sebastián José

◼️Huaire Maravi Edison Orlando

◼️Huaman Huaynatez Jean Franco

◼️Janampa Choccelahua Gian Alessandro

◼️Mateo Cabello Raúl Julián

◼️Ramirez Buitrón Kenyo Wilder

<h2 align="center">
    <p>HUANCAYO -- PERÚ</p>
    <p>2025</p>
</h2>

---

# ÍNDICE


[ÍNDICE]

[INTRODUCCIÓN]

[CAPITULO 1 - Variables CSS y Custom Properties]

[CAPITULO 2 - Funciones CSS (calc(), clamp(), min(), max())]

[CAPITULO 3 - Grid Layout Avanzado (Áreas de grid, auto-fit, auto-fill)]

[CAPITULO 4 - Flexbox avanzado (Alineaciones, distribución dinámica)]

[CAPITULO 5 - Diseño responsivo (Media Queries y Mobile-first)]

[CAPITULO 6 - Scroll Snap y Técnicas de Scroll]

[CAPITULO 7 - Clipping y Masking con CSS]

[CAPITULO 8 - Container Queries]

[CAPITULO 9 - Filtros y Efectos Visuales avanzados]

[CAPITULO 10 - Técnicas de Performance y Optmización en CSS]

[CONCLUSIÓN]

[REFERENCIA BIBLIOGRÁFICA]

# INTRODUCCIÓN

La siguiente monografía profundiza el tema del lenguaje de diseño CSS,
conocido como Cascading Style Sheets, la cual aplicar estilos a
documentos, en su mayoría documentos HTML. Este lenguaje permite que la
información de los documentos HTML tenga un aspecto que sea organizado,
llamativo e interesante para los usuarios añadiendo el diseño de los
bloques, los colores de las letras o fondos de los bloques, las formas
que pueden tomar algunos bloques, entre otras funciones (Manz, s. f.).
Por la funcionalidad que tiene este lenguaje, es muy importante para un
desarrollador de páginas web el tener conocimientos sobre CSS al ser un
tema fundamental para las páginas web.

Por lo tanto, se tiene como objetivo el conocer temas más avanzados
relacionados con CSS. Para ello se buscará información de fuentes
fiables para los temas seleccionados que se mostrarán en los capítulos
para luego mostrar ejemplos aplicables de los temas utilizando códigos y
sus resultados.

Esta investigación resulta pertinente debido al aumento de la
importancia de las páginas web en la actualidad, ya que para las
organizaciones al intentar captar la atención de los usuarios buscan que
su página web, aparte que tenga la información relevante sobre ellos,
también buscan que sea llamativo, atractivo y tenga una buena
optimización de rendimiento, por lo cual beneficia a las organizaciones
utilizar CSS. También es importante para el aspecto académico, ya que,
al ser importante para las organizaciones, es muy demandado por el
mercado laboral, la cual servirá para los front-end, diseñadores
gráficos y especialistas en experiencia de usuario.

El tipo de esta investigación será de Investigación documental y
descriptiva, ya que se buscará información revisando documentos,
artículos, cursos y recursos web especializados. también es exploratoria
ya que busca profundizar en temas avanzas relacionados con CSS.

# CAPITULO 1 - Variables CSS y Custom Properties

Ambos términos representan lo mismo, el Custom Properties es la forma
oficial de decirle a las variables, el término fue dado por W3C, la cual
es una organización internacional que desarrolla los estándares y
directrices para la web (World Wide Web Consortium, s. f.). Las
variables se consideran como un mecanismo que sirve personalizar las
propiedades CSS, se usa para evitar escribir un valor en varias
ocasiones. Permitiendo que sea fácil de entender y de configurar (Manz,
s. f.).

Para declarar una propiedad personalizada, primero se crea la clase,
luego se escribe dos guiones ( - ), después el nombre de la variable y
al final un valor admitido en CSS. Para admitir una variable de manera
global al documento html se utiliza el pseudo-clase ":root". Para el uso
de la variable, se escoge la clase que tendra esta variable, luego de
poner el nombre de la propiedad, se coloca "var()" y dentro del
paréntesis se pone el nombre de la variable.

```css
:root {
  --background-color: yellow;
}
body {
  background: var(--background-color);
}
```

Una característica que tiene la función var() es que se puede escoger
una opción de respaldo si en el caso de la variable que ingresaste
dentro del paréntesis aun no ha sido definida. A esta alternativa se le
conoce como Fallback, Si se desea que la opción de respaldo también sea
una variable, se ingresa otra función var() y luego su variable.

```css
/* Primer Código*/
body {
  background: var(--background-color, green);
}
```

```css
/* Segundo Código*/
body{
background-color: var( --my-var, var(--my-background, pink) );
}
```

Se puede utilizar :root para hacer de manera global, pero también se
puede hacer de manera local, utilizando una clase padre.

```css
/* Código CSS*/
.parent {
  --background-color: black;
  background: indigo;
  padding: 1rem;
  display: flex;
  gap: 1rem;
}
.child {
  width: 100px;
  height: 100px;
  background: var(--background-color);
}
.first {
  --background-color: gold;
}
```

Como se muestra, en la clase parent se tiene una variable, para
utilizarlas en las demás clases, estas tienen que estar dentro de la
clase en el codigo HTML.

```css
<div class="parent">
  <div class="first child">First child</div>
  <div class="second child">Second child</div>
  <div class="third child">Third child</div>
</div>
```

Como se muestra en el código, al estar dentro de la clase "parent",
puede utilizar la variable que tiene su clase padre. En el caso de la
clase "firts" se priorizará su variable, cambiando de blanco a negro.

**Ventajas**

-   Reutilización de código: permite aplicar el mismo valor en múltiples
    lugares sin repetirlo.

-   Facilidad de mantenimiento: un cambio en la variable se refleja
    automáticamente en todos los elementos donde fue utilizada.

-   Diseños dinámicos: posibilitan cambiar estilos de forma más sencilla
    en proyectos grandes.

-   Compatibilidad con JavaScript: se pueden modificar en tiempo real,
    favoreciendo la construcción de interfaces interactivas.



# CAPITULO 2 - Funciones CSS (calc(), clamp(), min(), max())

Las funciones en CSS forman parte de las herramientas modernas que permiten definir valores dinámicos sin necesidad de JavaScript. Su propósito es calcular y ajustar automáticamente propiedades de diseño, lo que hace que las páginas sean más flexibles y responsivas (MDN Web Docs, s. f.).

Estas funciones se interpretan directamente en el navegador y pueden trabajar con unidades mixtas (px, %, vw, rem, etc.), lo que antes requería cálculos manuales o media queries adicionales. Entre las más usadas tenemos:

calc(): permite realizar operaciones matemáticas (+, −, ×, ÷).

min(): selecciona el valor más pequeño entre dos o más opciones.

max(): selecciona el valor más grande entre dos o más opciones.

clamp(): fija un rango mínimo, preferido y máximo en una sola línea.

Estas funciones, combinadas con variables CSS, dan mayor control y eficiencia en proyectos grandes de diseño web.

## 🔹 Ventajas

Adaptabilidad: ajustan medidas de forma automática según el tamaño del dispositivo.

Simplicidad: reducen la necesidad de usar JavaScript o varias media queries.

Flexibilidad: permiten mezclar diferentes unidades (ejemplo: px con %).

Mantenimiento fácil: facilitan cambios en proyectos grandes y responsivos.

🔹 Ejemplos de código

Ejemplo con calc()
```css
div {
  width: calc(100% - 50px);
}
```
➡ El div ocupará todo el ancho de la página menos 50 píxeles.

Ejemplo con min()
```css
div {
  width: min(70%, 400px);
}
```
➡ El ancho será el menor valor: 70% de la pantalla o 400px.

Ejemplo con max()
```css
p {
  font-size: max(16px, 2vw);
}
```
➡ El texto nunca será más pequeño que 16px, pero crecerá en pantallas grandes.

Ejemplo con clamp()
```css
h1 {
  font-size: clamp(16px, 5vw, 40px);
}
```
➡ El título (h1) será como mínimo 16px, crecerá de forma dinámica (5vw), pero nunca más de 40px.

# CAPITULO 3 - Grid Layout Avanzado (Áreas de grid, auto-fit, auto-fill)

El CSS Grid Layout es un sistema de diseño en dos dimensiones (filas y columnas) que facilita la construcción de interfaces web organizadas y responsivas. A diferencia de Flexbox, que trabaja en una sola dirección (fila o columna), Grid permite controlar simultáneamente ambas dimensiones, ofreciendo mayor precisión y flexibilidad (W3C, s. f.).

Dentro de sus características avanzadas destacan:

grid-template-areas: permite asignar nombres a secciones del layout, lo que mejora la legibilidad y semántica del código.

auto-fit y auto-fill: permiten crear cuadrículas dinámicas donde los elementos se ajustan automáticamente al espacio disponible, sin necesidad de usar múltiples media queries.

Estas propiedades hacen de Grid una herramienta fundamental en proyectos modernos de diseño web, especialmente en páginas con estructuras complejas como dashboards, plantillas de noticias, portfolios o aplicaciones web.

🔹 Ventajas

Organización clara: usar nombres en las áreas facilita la lectura y mantenimiento.

Diseño responsivo: auto-fit y auto-fill ajustan automáticamente el número de columnas.

Mayor control: permite distribuir espacio, alineaciones y relaciones entre elementos de forma precisa.

Escalabilidad: útil para proyectos grandes donde la estructura puede crecer fácilmente.

🔹 Ejemplos de código
1. Uso de grid-template-areas

Permite asignar nombres a diferentes secciones del layout.

```css
.container {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  grid-template-columns: 1fr 2fr;
  gap: 10px;
}

.header  { grid-area: header;  background: lightblue; }
.sidebar { grid-area: sidebar; background: lightgreen; }
.main    { grid-area: main;    background: lightcoral; }
.footer  { grid-area: footer;  background: lightgray; }

```
➡ Resultado: el diseño queda dividido en header, sidebar, main y footer de forma clara y ordenada.

2. Uso de auto-fit y auto-fill

Sirven para crear grids responsivos que se adaptan automáticamente.
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 15px;
}
.item {
  background: lightseagreen;
  height: 100px;
  border-radius: 8px;
  text-align: center;
  line-height: 100px;
  color: white;
  font-weight: bold;
}

```
➡ Resultado: las tarjetas se ajustan solas al espacio disponible, evitando el uso de múltiples media queries.

En pantallas grandes → varias columnas.

En pantallas pequeñas → se reducen a 1 o 2 columnas automáticamente.

# CAPÍTULO 4 – Flexbox avanzado (Alineaciones, distribución dinámica)

Flexbox, o **Flexible Box Layout**, es un sistema de diseño unidimensional en CSS que permite organizar elementos en filas o columnas de forma más flexible y eficiente que los métodos tradicionales como `float` o `inline-block` (MDN Web Docs, s. f.).

En su nivel avanzado, Flexbox ofrece herramientas poderosas para la **alineación, distribución dinámica y adaptabilidad**, permitiendo que los elementos se acomoden automáticamente al espacio disponible.

---

## 🔹 Propiedades avanzadas más relevantes

- **justify-content**: controla la alineación horizontal dentro del contenedor.  
  Valores útiles: `space-between`, `space-around`, `space-evenly`, `center`, `flex-start`, `flex-end`.

- **align-items**: define la alineación vertical de los elementos.  
  Valores: `stretch`, `center`, `flex-start`, `flex-end`.

- **align-content**: controla el espacio entre filas cuando hay múltiples líneas (wrap).  
  Ejemplo: `align-content: space-between;`.

- **flex-grow / flex-shrink / flex-basis**: permiten distribuir espacio dinámicamente.  
  - `flex-grow`: qué tanto crece un ítem.  
  - `flex-shrink`: qué tanto se reduce un ítem.  
  - `flex-basis`: tamaño base inicial.  

- **order**: cambia el orden visual de los elementos sin alterar el HTML.

---

## 🔹 Ejemplo de alineaciones dinámicas
```css
.container {
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 200px;
  background: lightgray;
}

.item {
  width: 80px;
  height: 80px;
  background: steelblue;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
}
````

➡ En este ejemplo, los elementos se distribuyen con **espacio alrededor** y quedan **centrados verticalmente** en el contenedor.

## 🔹 Ejemplo de distribución dinámica

```css
.container {
  display: flex;
  gap: 10px;
}

.item {
  flex-grow: 1;
  background: lightseagreen;
  height: 100px;
  text-align: center;
  line-height: 100px;
  color: white;
  font-weight: bold;
}
```

➡ Aquí, todos los ítems ocupan el **mismo ancho disponible**, adaptándose de manera **automática y proporcional** al espacio de la pantalla.

---

## ✅ Ventajas del uso avanzado de Flexbox

* Permite **alineaciones complejas** sin necesidad de hacks con `float`.
* Facilita el **diseño adaptable** en diferentes resoluciones.
* Mejora la **legibilidad y mantenimiento** del código.
* Junto con **Media Queries**, es clave en el diseño web moderno y responsivo.

---

# CAPÍTULO 5 – Diseño responsivo (Media Queries y Mobile-first)

El **diseño responsivo** busca que las páginas web se adapten automáticamente a diferentes dispositivos (computadoras, tablets, celulares).
Esto se logra principalmente con **Media Queries**, reglas en CSS que aplican estilos según el tamaño de pantalla o características del dispositivo (W3C, s. f.).

La estrategia más utilizada es **Mobile-first**, que consiste en diseñar primero para pantallas pequeñas y luego ir ampliando estilos con media queries.

---

## 🔹 Sintaxis de Media Queries

```css
@media (condición) {
  /* Estilos aplicados solo si se cumple la condición */
}
```

Ejemplos de condiciones comunes:

* `max-width`: aplica estilos cuando el ancho de la pantalla es **menor o igual** al valor indicado.
* `min-width`: aplica estilos cuando el ancho es **mayor o igual** al valor indicado.


## 🔹 Ejemplo Mobile-first

```css
/* Estilo base → para móviles */
.container {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

/* Pantallas medianas (tablets) */
@media (min-width: 768px) {
  .container {
    flex-direction: row;
  }
}

/* Pantallas grandes (desktop) */
@media (min-width: 1024px) {
  .container {
    gap: 20px;
  }
}
```

➡ **En móvil**: los elementos se muestran en columna.
➡ **En tablet**: cambian a una fila horizontal.
➡ **En desktop**: aumenta el espacio entre ellos.



## ✅ Ventajas del diseño responsivo con Media Queries

* Garantiza que la web funcione bien en dispositivos móviles.
* Permite cargar **estilos ligeros** para pantallas pequeñas.
* Es **escalable y fácil de mantener** en proyectos grandes.
* Favorece la **usabilidad y experiencia del usuario** en cualquier dispositivo.

# CAPÍTULO 6 - Scroll Snap y Técnicas de Scroll

## Concepto

El **Scroll Snap** es una propiedad introducida en el estándar de CSS con el objetivo de proporcionar un control más refinado sobre el desplazamiento de los elementos dentro de un contenedor. Esta técnica se basa en la capacidad de "anclar" o "encajar" los elementos de una interfaz en posiciones predeterminadas al realizar un desplazamiento horizontal o vertical. 

De acuerdo con la documentación de Mozilla Developer Network (MDN, 2022), el Scroll Snap pertenece al módulo de CSS denominado *CSS Scroll Snap Module*, el cual fue diseñado por el World Wide Web Consortium (W3C) como respuesta a la necesidad de mejorar la experiencia de desplazamiento en interfaces modernas, especialmente en dispositivos móviles donde el desplazamiento táctil es más común.  

En términos prácticos, esta característica permite que, al desplazarse sobre un contenedor que posee múltiples elementos, cada uno de ellos se alinee automáticamente con los bordes visibles de la pantalla o área del contenedor. Esto se aplica frecuentemente en carruseles de imágenes, listas horizontales, presentaciones interactivas y páginas con secciones extensas.

## Ventajas

- **Optimización de la experiencia de usuario**: facilita la navegación al asegurar que los elementos se ubiquen siempre en posiciones consistentes, reduciendo el esfuerzo visual del lector.  
- **Compatibilidad con la web responsiva**: resulta particularmente eficaz en dispositivos móviles y pantallas táctiles.  
- **Simplicidad en el desarrollo**: elimina la necesidad de scripts adicionales en JavaScript para lograr efectos de alineación en carruseles o sliders.  
- **Estandarización**: al ser una especificación de CSS, mantiene un comportamiento consistente entre navegadores modernos.  
- **Versatilidad**: puede aplicarse tanto en desplazamientos horizontales como verticales, ampliando sus posibilidades de uso.  

## Ejemplo de código

```css
/* CSS */
.container {
  scroll-snap-type: x mandatory;
  display: flex;
  overflow-x: auto;
  width: 100%;
}

.item {
  scroll-snap-align: center;
  flex: 0 0 100%;
  height: 200px;
}
```

```html
<!-- HTML -->
<div class="container">
  <div class="item" style="background: lightblue;">Sección 1</div>
  <div class="item" style="background: lightgreen;">Sección 2</div>
  <div class="item" style="background: lightcoral;">Sección 3</div>
</div>
```

## Resultado

El código anterior genera un contenedor desplazable horizontalmente en el que cada sección ocupa el 100 % del ancho de la pantalla. Al realizar scroll, los elementos se alinean automáticamente al centro del área visible, produciendo un efecto similar a un carrusel de diapositivas.

# CAPÍTULO 7 - Clipping y Masking con CSS

## Concepto

Dentro de las técnicas avanzadas de diseño web, el **Clipping** y el **Masking** en CSS representan recursos fundamentales para la manipulación visual de los elementos. Ambas técnicas tienen como finalidad alterar las áreas visibles de un elemento, aunque lo hacen mediante mecanismos distintos:

- **Clipping**: se basa en la utilización de la propiedad `clip-path`, la cual permite definir una región geométrica (círculos, elipses, polígonos, entre otros) que delimita la parte del elemento que será visible. El contenido fuera de la forma definida se oculta sin modificar realmente el DOM.  
- **Masking**: emplea una imagen o un gradiente como máscara mediante la propiedad `mask-image` (o `-webkit-mask-image` en algunos navegadores). La máscara determina qué partes del elemento serán visibles en función de la opacidad o transparencia de la imagen aplicada.  

Según Coyier (2021), estas herramientas amplían considerablemente la creatividad del diseñador, dado que permiten crear interfaces más dinámicas, con efectos visuales modernos sin necesidad de editar previamente las imágenes en un software externo.

## Ventajas

- **Mayor expresividad visual**: posibilitan el uso de formas y patrones personalizados que enriquecen el diseño de interfaces.  
- **Flexibilidad**: mientras el clipping se orienta a recortes geométricos, el masking admite imágenes complejas y gradientes.  
- **Optimización de recursos**: evita la necesidad de generar imágenes editadas previamente, ya que los efectos se logran directamente con código.  
- **Compatibilidad moderna**: ampliamente soportado en navegadores actuales, aunque en algunos casos se requiere prefijos específicos.  
- **Aplicaciones dinámicas**: se pueden integrar con transiciones y animaciones para efectos interactivos en páginas web.  

## Ejemplo de código

```css
/* CSS */
.clipped {
  width: 300px;
  height: 300px;
  background: url('https://picsum.photos/400') no-repeat center/cover;
  clip-path: circle(50% at 50% 50%);
}

.masked {
  width: 300px;
  height: 300px;
  background: url('https://picsum.photos/400') no-repeat center/cover;
  -webkit-mask-image: linear-gradient(to bottom, black 70%, transparent 100%);
  -webkit-mask-repeat: no-repeat;
  -webkit-mask-size: cover;
}
```

```html
<!-- HTML -->
<div class="clipped"></div>
<br>
<div class="masked"></div>
```

## Resultado

El primer ejemplo aplica un recorte circular a la imagen de fondo del elemento, mostrándola como si estuviera contenida en un círculo perfecto. El segundo ejemplo utiliza un degradado como máscara, de modo que la parte inferior de la imagen se desvanece progresivamente hasta volverse transparente.

# CAPITULO 8 - Propiedades y Contenedores CSS (Container Queries)
Los CSS Container Queries son el mismo concepto de las Media Queries, pero en lugar de estar orientados a modificar los estilos dependiendo del tamaño de la página o dispositivo (viewport), lo hace dependiendo de un contenedor padre (o ancestro). De esta forma, podemos cambiar el tamaño de ciertos elementos y hacer que tengan una forma o unos estilos dependiendo del contexto donde se encuentren.

------------

### ELEMENTO CONTENEDOR
Para empezar tenemos que determinar cuál será el elemento contenedor al que vamos a hacer referencia. En dicho elemento, necesitaremos establecer las siguientes propiedades:

#### PROPIEDADES

**Propiedad container-name:** La propiedad container-name le da un nombre de contenedor al elemento en el que nos encontramos. Sin este nombre no podremos hacer referencia luego, en la regla @container.

**ejemplo:**

```css
.container {
  container-name: titulo;
}
```

**Propiedad container-type:** La propiedad container-type, establece el tipo de tamaño que va a tener el contenedor en cuestión, donde puede ser:
 - size: Elementos de tipo bloque (alto y ancho).
 -  inline-size: Elementos de tipo linea (solo ancho).
 
**ejemplo**
```css
 .container {
  container-name: titulo;
  container-type: inline-size;
}
```
**Propiedad container:** En esta propiedad podemos indicar **dos valores**, el valor de la propiedad **container-name** y el valor de la propiedad **container-type**, pero siempre separadas por un **/**.

**ejemplo**

```css
 .container {
  container: titulo / inline-size;
}
```
------------
### REGLA CONTAINER
Una vez tenemos nuestro contenedor definido, debemos establecer una regla @container que es muy parecido a las reglas @media, pero en este caso establece una condición para aplicar estilos a un contenedor en concreto.

**SINTAXIS**
```css
@container <nombre del contenedor> (<condición>)
```
**Ejemplo**
```css
.container {
  border: 1px solid red;
  color: black;
  container: titulo;
}

@container logo (width <= 550px) {
  .h1 {
    color: blue;
  }
}
```

------------

### UNIDADES DE CONTENEDORES
Cuando nos encontramos en el interior de una regla @container podemos utilizar ciertas unidades especiales como cqw, cqh, cqi, cqb, cqmin o cqmax.
Los componentes que usan unidades de longitud relativas a su contenedor son más flexibles para su uso en diferentes contenedores sin tener que recalcular valores de longitud concretos.

**Las unidades de longitud de la consulta del contenedor son:**
- cqw: 1% del ancho de un contenedor de consulta
- cqh: 1% de la altura de un contenedor de consulta
- cqi: 1% del tamaño en línea de un contenedor de consulta
- cqb: 1% del tamaño del bloque de un contenedor de consulta
- cqmin: El valor más pequeño de uno cqi o cqb
- cqmax: El valor mayor de uno cqi u otro cqb

```css
@container (width > 700px) {
  .card h2 {
    font-size: max(1.5em, 1.23em + 2cqi);
  }
}
```
# CAPITULO 9 - Filtros y Efectos Visuales avanzados

Los filtros en CSS permiten añadir efectos visuales, como sepia, ajustes de brillo, contraste u otros, directamente desde el navegador y de manera instantánea, sin modificar de forma permanente la imagen original.

Se pueden aplicar desde dos propiedades CSS diferentes:

Propiedad  | Descripción
------------- | -------------
Filter  | Aplica un filtro concreto a un elemento HTML y todos los de su interior.
backdrop-filter  | 	Aplica un filtro concreto al fondo de un elemento HTML, sin que afecte a su interior.

### PROPIEDAD FILTER
filter acepta funciones de filtrado (por ejemplo, blur(), brightness(), contrast(), grayscale(), sepia()) que modifican la representación visual del elemento en el renderizado final de la página.
```css
img {
  filter: grayscale(100%);
  transition: filter 1s;
  width: 200px;
}

img:hover {
  filter: grayscale(0%);
}
```
#### FUNCIONES DE FILTROS
Función  | Significado | Valor
------------- | ------------- | -------------
grayscale  | Escala de blanco y negro | percent - number
blur | 	Desenfoque Gausiano | size
sepia | Grado de color sepia | percent - number
saturate | Grado de saturación | percent - number
opacity | Grado de transparencia | percent - number
brightness | Brillo | percent - number
contrast | Contraste | percent - number
hue-rotate | Rotación de color (matiz) | angle
invert | Invertir | percent - number
drop-shadow | Sombra idéntica | posx posy size color

**PORCENTAJES O NÚMEROS**
- PERCENT: Valor porcentual (0%, 50%,100%,....)
- NUMBER: Valor númerico (0, 0.5, 1,.....)

**ejemplo grayscale**
```css
#img1 {
    filter: grayscale(100%);
}
```
**ejemplo blur**
```css
#img2 {
    filter: blur(5px);
}
```
**ejemplo sepia**
```css
#img3 {
    filter: sepia(100%);
}
```
**ejemplo saturate**
```css
#img4 {
    filter: saturate(200%);
}
```
**ejemplo opacity**
```css
#img5 {
    filter: opacity(50%);
}
```
**ejemplo brigthness **
```css
#img6 {
    filter: brightness(230%);
}
```
**ejemplo contrast**
```css
#img7 {
    filter: contrast(250%);
}
```
**ejemplo invert**
```css
#img8 {
    filter: invert(80%);
}
```
**ejemplo hue-rotate**
```css
#img9 {
    filter: hue-rotate(230deg);
}
```
**ejemplo drop-shadow**
```css
#img10 {
    filter: drop-shadow(5px 5px 10px black);
}
```

### PROPIEDAD BACKDROP-FILTER
La propiedad backdrop-filter en CSS sirve para aplicar efectos visuales (como desenfoque, brillo, contraste, etc.) al fondo que hay detrás de un elemento, sin alterar el contenido interno de ese mismo elemento.

Es decir, mientras que filter afecta directamente al elemento y a todo lo que contiene, backdrop-filter solo modifica la parte del fondo que se ve a través del elemento.

**ejemplo**
```css
#img11 {
    backdrop-filter: blur(10px);
}
```

# CAPITULO 10 - Técnicas de Performance y Optimización en CSS

## Concepto
Según Vázquez Sanisidro (2017), el **CSS es un recurso crítico de bloqueo de renderizado**, es decir, mientras el navegador no procese las hojas de estilo, la página no puede mostrarse al usuario. Por ello, la optimización de CSS busca **reducir el tiempo de renderizado inicial** aplicando técnicas como:

- Uso de **CSS crítico (Critical CSS)** para cargar primero los estilos mínimos necesarios en la parte visible.  
- **Minificación** de archivos para reducir su tamaño eliminando espacios y comentarios.  
- **Carga diferida o asíncrona** del CSS no crítico para evitar bloquear la renderización.  
- Evitar el uso de **estilos inline**, ya que son más lentos de procesar y no se pueden cachear.  
- Optimización de **fuentes web** con `@font-face` y la propiedad `font-display` para evitar pantallas en blanco mientras se descargan.  

En palabras del autor:  
> “Lo ideal es identificar los estilos críticos para el diseño de la parte superior de la página y cargarlos junto al html (…) y retrasar la carga del resto de los recursos CSS después del html necesario para mostrar la parte superior de la página” [1].

## Ventajas
- Mejora perceptible en el tiempo de carga inicial de la página.  
- Evita que el usuario vea una página en blanco mientras se cargan los estilos.  
- Reduce el tamaño de los archivos CSS y acelera su descarga.  
- Permite aprovechar nuevas capacidades de los navegadores modernos (como `preload` y `font-display`).  
- Incrementa la retención de usuarios y el posicionamiento en buscadores (SEO).  

## Ejemplo de Código
| Código No optimizado |
```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Ejemplo sin optimización</title>

  <!-- ❌ Múltiples hojas de estilo que bloquean el renderizado -->
  <link rel="stylesheet" href="reset.css">
  <link rel="stylesheet" href="layout.css">
  <link rel="stylesheet" href="theme.css">
  <link rel="stylesheet" href="fonts.css">

  <!-- ❌ Fuente sin font-display (puede mostrar pantalla en blanco mientras carga) -->
  <style>
    @font-face {
      font-family: 'MiFuente';
      src: url('mifuente.woff2') format('woff2');
    }
  </style>

  <!-- ❌ Estilos inline dispersos -->
</head>
<body style="margin:0; padding:0; background:#f4f4f4;">
  <h1 style="color:#333; text-align:center; margin-top:50px;">
    Bienvenido a mi sitio sin optimización
  </h1>
  <p style="font-size:18px; color:#555; text-align:center;">
    Este texto tarda más en cargarse debido a malas prácticas en el uso de CSS.
  </p>
</body>
</html>
```
| Código Optimizado |
```html
<style>
  /* ✅ CSS crítico inline (se carga primero) */
  body { font-family: Arial, sans-serif; margin:0; padding:0; background:#f4f4f4; }
  h1 { font-size: 2em; color: darkblue; text-align: center; margin-top: 50px; }
</style>

<!-- ✅ Carga diferida de CSS no crítico -->
<link rel="preload" href="styles.min.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
<noscript><link rel="stylesheet" href="styles.min.css"></noscript>

<!-- ✅ Fuente optimizada con font-display -->
<style>
  @font-face {
    font-family: 'MiFuente';
    src: url('mifuente.woff2') format('woff2'),
         url('mifuente.woff') format('woff');
    font-display: swap; /* Muestra texto con fuente del sistema mientras carga */
  }
</style>
```

# CONCLUSIÓN

El estudio realizado permite establecer que la optimización de CSS constituye un componente fundamental en el proceso de mejora del rendimiento de los sitios web. Tal como sostiene Vázquez Sanisidro (2017), el uso inadecuado de las hojas de estilo puede generar un bloqueo en el renderizado de la página, retrasando la visualización de los contenidos y afectando de manera directa la experiencia del usuario. En este sentido, la investigación demuestra que la optimización de CSS no debe entenderse únicamente como una cuestión estética, sino como una práctica estratégica que influye en la eficiencia técnica y en la percepción global de calidad de un sitio web.

Entre las técnicas analizadas, destacan la aplicación de CSS crítico, que permite mostrar de inmediato los elementos esenciales de la página; la carga diferida de estilos no prioritarios, que evita bloqueos en el renderizado inicial; y la minificación de archivos, que reduce el peso de los recursos y acelera su descarga. De igual forma, la exclusión de estilos inline favorece tanto la eficiencia del renderizado como la mantenibilidad del código, y la optimización de fuentes web mediante la propiedad font-display contribuye a garantizar que el contenido textual sea accesible desde el primer momento, incluso en conexiones limitadas.

Los beneficios derivados de estas prácticas abarcan distintas dimensiones: desde la mejora en los tiempos de carga y la reducción de la tasa de abandono, hasta un mayor posicionamiento en motores de búsqueda y una mejor accesibilidad en entornos de baja capacidad. Además, al promover un código más estructurado y modular, la optimización facilita la escalabilidad y el mantenimiento de proyectos a largo plazo, consolidándose como un estándar de calidad en el desarrollo web moderno.

En conclusión, la optimización de CSS no representa una acción opcional, sino un requisito indispensable para el diseño de aplicaciones y sitios web eficientes, accesibles y competitivos. La incorporación de estas prácticas desde las etapas iniciales del desarrollo asegura no solo un mejor desempeño técnico, sino también una experiencia de usuario más satisfactoria, lo cual constituye un factor decisivo en el actual entorno digital caracterizado por la inmediatez y la alta exigencia de los usuarios.

# REFERENCIA BIBLIOGRÁFICA

- Manz. (s. f.). ¿Qué es CSS? En LenguajeCSS.com. https://lenguajecss.com/css/introduccion/que-es-css/
- ManzDev. (2017, 5 de abril). Variables CSS: CSS Custom Properties. https://lenguajecss.com/css/variables-css/css-custom-properties/
- World Wide Web Consortium (s. f.). About us. W3C. https://www.w3.org/about/
- A. Vázquez Sanisidro, Optimización de Páginas Web: Visión teórica y análisis práctico, Tesis de Grado, Dpto. de Ingeniería Telemática, Univ. de Sevilla, Sevilla,     España, 2017.
- Coyier, C. (2021). *Clipping and Masking in CSS*. CSS-Tricks. Recuperado de https://css-tricks.com/clipping-masking-css/  
- Meyer, E. A. (2018). *CSS: The Definitive Guide* (4.ª ed.). O’Reilly Media.  
- Mozilla Developer Network (MDN). (2022). *clip-path*. Mozilla Foundation. Recuperado de https://developer.mozilla.org/es/docs/Web/CSS/clip-path  
- Mozilla Developer Network (MDN). (2022). *mask-image*. Mozilla Foundation. Recuperado de https://developer.mozilla.org/es/docs/Web/CSS/mask-image
- Keith, J. (2020). *A complete guide to CSS Scroll Snap*. CSS-Tricks. Recuperado de https://css-tricks.com/practical-guide-to-scroll-snap/  
- Mozilla Developer Network (MDN). (2022). *CSS Scroll Snap*. Mozilla Foundation. Recuperado de https://developer.mozilla.org/es/docs/Web/CSS/CSS_Scroll_Snap  
- W3C. (2019). *CSS Scroll Snap Module Level 1*. World Wide Web Consortium. Recuperado de https://www.w3.org/TR/css-scroll-snap-1/
- Manz. (s. f.).  Filtros CSS En LenguajeCSS.com.https://lenguajecss.com/css/efectos/filtros-css/
- Manz. (s. f.). CSS Container Queries En LenguajeCSS.com.https://lenguajecss.com/css/responsive-web-design/css-container-queries/
