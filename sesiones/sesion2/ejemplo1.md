# Sesión 02: Agregando la barra de navegación

## Introducción
Durante esta sesión vamos a implementar a nuestro clon de la página de Matcha uno de los elementos más usados en una página web, la barra de navegación. Aquí aprenderemos el uso de etiquetas semánticas disponibles en HTML5 y conoceremos cómo administrar correctamente la posición de elementos mediante el modelo de cajas de HTML.

## Objetivos

En esta sesión aprenderás:

- Agregar `etiquetas semánticas` de HTML que den una mejor estructura a lo que
  estamos creando.
- Aplicar conceptos de `modelo de caja` y `display` en `CSS` para agregar la
  apariencia de nuestra `barra de navegación`.
- Agregar nuestros cambios de códigos al historial de cambios en Git y subirlos a GitHub.

## Requisitos

- Git  instalado
- Navegador web
- Tener instalado Sublime Text.
- Cuenta de Github

## Organización de la clase

- [Ejemplo 01: HTML de la barra de navegación ( 10 minutos ) ]

- [Ejemplo  02: Cambiando el modelo de caja del menú de navegación ( 25 minutos ) ]

- [Reto  02: Aplica el margen utilizando el atajo de la propiedad `margin` ( 15 minutos ) ]

- [Reto  03: Alineación de texto en la barra de navegación ( 15 minutos ) ]

- [Reto  04: Agregando estilos restantes ( 25 minutos ) ]

<br/>

# Ej. 01 HTML de la barra de navegación
 ## Objetivo
 - Crear la estructura de HTML que contenga nuestra barra de navegación.

---
<br/>

## Requisitos
- Tener instalado Sublime Text.

---
<br/>

## Desarrollo

Para nuestra barra de navegación usaremos la etiqueta `header` ya que es la
cabecera de nuestra página. Dentro de esta etiqueta pondremos otros 3
contenedores: un link con el logo dentro, el menú de navegación y el contenedor
de acciones de usuario.

```html
<header>
  <!-- Logo con link a la página principal -->
  <a>
    <img />
  </a>
  <!-- Menú de navegación -->
  <nav></nav>
  <!-- Contenedor de acciones de usuario -->
  <div></div>
</header>
```

> TIP: La etiqueta `a` sirve para agregar un enlace interno o externo. Para
> indicar la dirección de dicho enlace se usa el atributo `href` y su contenido
> interno puede ser un texto, una imagen o combinación de estos u otros
> elementos. En nuestro caso, queremos que el link apunte a la página inicial,
> esto se puede lograr escribiendo `/` (barra diagonal) que hace referencia a la
> raíz (punto de partida) de la página.

<br/>

# Reto 01 - Etiquetas semánticas para barra de navegación
## Objetivos
- Utilizar etiquetas semánticas en la barra de navegación.
- Agregar los estilos correctos para ajustar el posicionamiento de la barra de navegación.

---
<br/>

### REQUISITOS
- Tener conocimientos básicos de HTML y CSS

---
<br/>

### INSTRUCCIONES

Viendo la barra de navegación del sitio original de [Matcha](https://getmatcha.com),
¿qué etiquetas semánticas consideras que serían buenas usar?

Tomando en cuenta el contenido actual de nuestra web, ¿consideras bueno que se
ponga dentro de un contenedor? Si tu respuesta es positiva, ¿qué contenedor
semántico usarías?

<br/>

Teniendo en cuenta lo siguiente:

- El link de la imagen del logo es: `https://getmatcha.com/wp-content/uploads/2020/01/Icon-green.png`
- El menú de navegación se puede lograr con una lista desordenada que en HTML se
  representa a través de la etiqueta [`<ul></ul>`](https://developer.mozilla.org/es/docs/Web/HTML/Elemento/ul).
- La acción `Sign In` es un link que apunta a la dirección `/login` y la acción
  de `Start free trial` es un botón.

¿Cómo agregarías el contenido de la barra de navegación?

> Ten en cuenta que no se verá igual que la página, y eso está bien, ya que nos
> estamos enfocando solo en la estructura y luego le daremos los estilos
> necesarios para darle la apariencia esperada.

<br/>

<details><summary>Posible solución</summary>
<p>

```html
<header class="header">
  <!-- Logo con link a la página principal -->
  <a href="/">
    <img src="https://getmatcha.com/wp-content/uploads/2020/01/Icon-green.png" alt="Matcha"/>
  </a>
  <!-- Menú de navegación -->
  <nav>
    <ul>
      <li>Platform</li>
      <li>Pricing</li>
      <li>Customers</li>
      <li>Resources</li>
      <li>About</li>
    </ul>
  </nav>
  <!-- Contenedor de acciones de usuario -->
  <div>
    <a>Sign In</a>
    <button>Start free trial</button>
  </div>
</header>
```

</p>
</details>

<br/>

### NOTA:
Vemos que la barra de navegación en la página original no está pegada al borde superior del navegador. En cambio, esta se encuentra a una distancia fija y el contenido de igual manera se encuentra a una distancia específica de la barra de navegación.

Para agregar este tipo de espaciados, podemos usar la propiedad margin, que nos permite poner un margen de separación entre elementos, ya sea en cualquiera de los 4 lados de la caja (arriba, derecha, abajo e izquierda).

Para el caso de la barra de navegación agregaremos un margen superior de 40px y un margen a cada lado de 20px. Ya que este margen queremos dárselo a toda la barra, se lo aplicaremos al elemento header. Para evitar que en caso agreguemos algún otro header en alguna sección de la página, vamos a agregarle un atributo de clase a la etiqueta header y aplicar el estilo a dicha etiqueta a través del selector de clase:

```html
<header class="header">
  <!-- Contenido del header -->
</header>
```

```css
.header {
  margin-top: 40px;
  margin-left: 20px;
  margin-right: 20px;
}
```

# Ej. 02 - Cambiando el modelo de caja del menú de navegación

## Objetivo
- Identificar elementos de bloque y de línea.
- Usar etiquetas semánticas para mejor legibilidad del código.
- Definir conjunto de propiedades de CSS para alinear correctamente el contenido de la barra de navegación.

---
<br/>

## Requisitos
- Tener instalado Sublime Text
- Conocer la diferencia entre elemento de bloque y elemento de línea

---
<br/>

## Desarrollo

En este punto ya tenemos las separaciones deseadas entre los bloques más grandes
de contenido, sin embargo nuestro menú de navegación aun no tiene la apariencia
del sitio original, ya que se muestran de forma vertical (uno debajo del otro),
mientras que el diseño original lo muestra horizontalmente.

## Concepto: Display `block` vs `inline`

¿Por qué se muestra por defecto uno debajo de otro? Esto es debido a los estilos
que las etiquetas tienen asignadas por defecto, y este comportamiento está
relacionado a la propiedad `display`. El navegador asigna a las etiquetas de HTML
la propiedad `display` con valores `block` o `inline`. Los elementos con
`display: block;` usan todo el ancho disponible de su contenedor, es decir, si
nosotros creamos 4 etiquetas `<p></p>`, una seguida de la otra, vamos a ver que
cada texto que pongamos se mostrará uno debajo de otro porque por defecto su
ancho será del 100%. Mientras que los elementos con `display: inline;` usan solo
el espacio necesario para mostrar su contenido.

Algunos ejemplos de elementos con display `block` son: `div`, `p`, `ul`, `h1`,
`header`, `section`, `aside`, `nav`, y muchos más.

Y algunos ejemplos de elementos con display `inline` son: `img`, `a`, `span`,
`strong`, entre otros.

Teniendo en cuenta esta información, nuestro menú de navegación está basado de
las etiquetas `ul` y `li` que tienen display `block` y `list-item` (se comporta
como display `block` si no hay un valor especificado, puedes leer más al respecto
[aquí](https://developer.mozilla.org/en-US/docs/Web/CSS/display-listitem))
respectivamente.

Una solución podría ser reemplazar el display de los `li` a `inline`.

```css
li {
  display: inline;
}
```

Si aplicamos este estilo, nuestro menú se verá ahora de manera horizontal, pero
se seguirían viendo 3 filas: una para el logo, otra para el menú y la última
para las acciones de usuario.

Para evitar las 3 filas, tendríamos que poner a cada elemento contenedor (`a`,
`nav` y `div`) el display `inline`, sin embargo, al cambiar a este valor de
`display` nos encontramos que perdemos ciertas propiedades como `margin-top`,
`margin-bottom`, `height`, es decir, por más que le pongamos un valor, este no
se ve reflejado, y este es el comportamiento correcto que se define para los
elemento scon `display: inline;`. Ante esto, podemos usar otro valor llamado
`inline-block` que mezcla lo mejor de `block` e `inline`, permitiendo cambiar
el layout a un comporamiento como el `inline` pero permitiendo cambiar los
márgenes verticales y la altura como cualquier elemento con display `block`.

Pongamos a prueba este nuevo display, asignándolo a todos los hijos directos de
la etiqueta header:

```css
.header > * {
  display: inline-block;
}
```

¡Muy bien! Con esto conseguimos que estén alineados. ¿Qué tal si le damos un poco
de espacio a cada parte de la barra de navegación? Si tomamos el contenedor (la
etiqueta `header` para la barra de navegación) como un todo equivalente al 100%
y a cada uno de sus hijos les damos un porcentaje de ancho. Podríamos decir que
el logo va a usar un 15% del tamaño de su contenedor, el menú de navegación un
70% y las acciones de usuario el 15% restante. Para aplicar estos estilos podemos
ponerle atributos de clase para que sean más fáciles de identificar:

```html
<header class="header">
  <!-- Logo con link a la página principal -->
  <a href="/" class="logo"></a>
  <!-- Menú de navegación -->
  <nav class="navbar"></nav>
  <!-- Contenedor de acciones de usuario -->
  <div class="actions"></div>
</header>
```

```css
.logo {
  width: 15%;
}

.navbar {
  width: 70%;
}

.actions {
  width: 15%;
}
```

¿Viste lo que pasó? Las acciones de usuario se fueron debajo de los demás
elementos de la barra de navegación. ¿Por qué te imaginas que esto pasó? ¿Serán
nuestras matemáticas (15 + 75 + 15 = 100) :thinking:?

Tranquilxs, esto se debe a que cuando le dijimos que le ponga el `display: inline-block`
a cada uno de los hijos del `header`, los espacios entre cada etiqueta tomaron
un tamaño también, sí, leíste bien, los espacios, aquellas teclas ENTER que
presionamos para que nuestro código se vea más bonito, puedes hacer la prueba
quitando las separaciones:

```html
<header class="header">
  <!-- Logo con link a la página principal -->
  <a href="/" class="logo"></a
  ><!-- Menú de navegación -->
  <nav class="navbar"></nav>
  <!-- Contenedor de acciones de usuario -->
  <div class="actions"></div>
</header>
```

Resulta que al darle un display `inline-block` a los espacios de nuestro código
le damos la posibilidad de tener un tamaño porque al final representan un texto
vacío, el tamaño variará dependiendo del tamaño de fuente que tenga su contenedor.
Si bien, quitando los espacios entre cada etiqueta soluciona el problema, no es
una solución escalable, puesto que si agregamos algo más dentro de la etiqueta
`header` tendríamos el mismo problema y terminaríamos con una sola línea de
código muy larga. [Otras soluciones](https://css-tricks.com/fighting-the-space-between-inline-block-elements/)
implican agregarle son utilizar comentarios entre los saltos de línea, poner un
margin negativo a cada elemento, quitar la etiqueta de cierre y demás.

En nuestro caso usaremos el _hack_ del `font-size`, resulta que si lo que le da
tamaño a los espacios en blanco es el tamaño de la fuente, podemos darle un
tamaño de fuente 0 al contenedor y luego asignar el tamaño de fuente correcto
en cada elemento hijo. Hagamos una prueba, teniendo en cuenta que el tamaño de
la fuente será de 16px para el menú de navegación:

```css
.header {
  margin-top: 40px;
  margin-left: 20px;
  margin-right: 20px;
  font-size: 0;
}

.header > * {
  display: inline-block;
  font-size: 16px;
}
```

¡Eso es magia! En realidad no, es sufrir con CSS :sweat:.

<br/>

# Alineamiento vertical

Resulta que para alinear al centro verticalmente, debemos hacer uso de la
propiedad `vertical-align: middle`, sin embargo, si aplicamos solo esta propiedad
no nos quedará centrado correctamente, esto debido a que cada elemento tiene un
tamaño diferente. Para solucionar esto, podemos sacar provecho que el contenedor
tiene un tamaño fijo (`.header` con `height:45px;`) y podemos decir que cada hijo
del elemento `header` tenga un height del `100%`. Por último, después de aplicar
ambas propiedades nos daremos con la sorpresa de que no queda verticalmente
centrado ya que a pesar que los elementos tienen el mismo tamaño, no comparten
el mismo espacio que el texto debería ocupar, para esto existe la propiedad
`line-height` que nos permite indicar cuánto es el tamaño de altura que ocupará
cada línea de texto, en este caso debería ser igual al tamaño del contenedor
(45px), quedando así:

```css
.header > * {
  display: inline-block;
  font-size: 16px;
  vertical-align: middle;
  height: 100%;
  line-height: 45px;
}
```

Con esto quedaría centrado nuestro menú de navegación, pero si somos
perfeccionistas, nos daremos cuenta que el logo no está centrado verticalmente,
lo podemos solucionar agrandando su altura al 100% del contendor:

```css
.logo > img {
  width: 15%;
}
```

El último de los detalles sería cambiar el peso de la fuente en los textos del
menú de navegación y los botones ya que aunque no parezcan son distintos en la
web original:

```css
.navbar {
  width: 70%;
  text-align: center;
  color: #025157;
  font-weight: 500;
}

.actions {
  width: 15%;
  text-align: right;
  font-size: 14px;
  font-weight: 600;
}
```

Wohoo!! Finalmente hemos terminado nuestra barra de navegación. ¿Qué te pareció?
Interesante todo lo que tienes que hacer para poder darle la forma que deseas,
¿no?. Como mencionado anteriormente, existen otras técnicas que hacen esto de
una manera mucho más sencilla pero la discutiremos en su momento. No olvides
subir tus cambios a Github y realizar el deploy en Netlify.

<br/>

# Reto 02 - Aplica el margen utilizando el atajo de la propiedad `margin`
## Objetivos
- Utilizar las propiedades abreviadas ("shortcuts") de margen.

---
<br/>

## Requisitos
- Tener Git Bash si usas Windows.
- Tener conocimientos básicos de HTML y CSS

---
<br/>

## Instrucciones

¿Sabías que la propiedad `margin` puede asignar el valor de los 4 lados en una
sola línea? Si es la primera vez que escuchas esto, no dudes en _googleaerlo_ y
experimentar cambiando las 3 propiedades que hemos escrito previamente por una
sola. Luego imagina, pregunta e investiga que otras propiedades tienen el mismo
atajo.

<br/>

El contenido que agregamos en la sesión anterior también tiene una separación de
la barra de navegación. Esto podríamos solucionarlo agregando un margen a la
primera etiqueta de nuestro contenido (que sería el `h1`), sin embargo, esto no
sería óptimo porque si en algún momento insertáramos algo antes del `h1` nuestro
margen no funcionaría como deseamos. Para evitar esto, podemos usar un contenedor
que englobe a todo nuestro contenido y aplicar el margen a dicho contenedor.


<br/>

<details><summary>Posible solución</summary>

```html

<!-- Aquí va la barra de navegación -->
 <section class="main">
    <h1>Build your blog. Build your business.</h1>

    <h4>Instantly publish articles, drive more traffic, grow your email list, and see your blog’s impact on sales.</h4>

    <form>
      <input type="email">
      <button type="submit" class="texto-boton">
        Try it now &rarr;
      </button>
    </form>

    <p class="texto-promocional">Start publishing today with a <strong>free 7-day trial.</strong></p>
    <p class="texto-promocional"><strong>No credit card</strong> required.</p>

    <img src="https://ignos.blog/wp-content/uploads/2021/04/capterra.png" alt="Captcha de Capterra">
  </section>

```

<br/>

Ahora agregaremos el CSS que necesitamos.
<br/>
Para nuestro `<header>`, una clase `.header`. Nota que estamos usando una versión abreviada (atajo) de la propiedad `margin`, ahora de tres números:

```css
.header {
  margin: 40px 20px 0;
  font-size: 0;
}
```
<br/>

Este es el estilo y margen para el contenedor `<section>` con clase `.main`:

```css
.main {
  margin-top: 140px;
  text-align: center;
}
```

Con este cambio en el CSS, así como incorporando un **contenedor** en nuestra sección inicial, logramos un mejor control de nuestros elementos en pantalla.

</details>

<br/>

# Reto 03 - Alineación de texto en la barra de navegación

## Objetivos
- Utilizar conjunto de propiedades para alinear textos

---
<br/>

## REQUISITOS
- Tener Git Bash si usas Windows.
- Tener conocimientos básicos de HTML y CSS

---
<br/>

## INSTRUCCIONES

Nuestra barra de navegación va tomando forma, pero, ¿qué tal si vamos alineando el texto?, considerando que el menú de navegación debería tener el texto y las acciones alineadas a la izquierda. ¿Qué propiedad vas a usar para alinear el texto? ¿A qué elementos aplicarás el alineado?

<br/>

<details><summary>Posible solución</summary>


```css
.navbar {
  width: 70%;
  text-align: left;
  color: #025157;
  font-weight: 500;
}

.actions {
  width: 15%;
  text-align: left;
  font-size: 14px;
  font-weight: 600;
}
```


</details>

<br/>

# Reto 04 - Agregando estilos restantes
## Objetivos
- Agregar clases y estilos a la barra de navegación.
- Subir los cambios a GitHub

---
<br/>

## Requisitos
- Tener Git Bash si usas Windows.

---
<br/>

## Instrucciones

A continuación completa los siguientes requerimientos:

1. Todos los textos dentro de la barra de navegación deben usar la fuente
   `sans-serif` y el alto de la barra debe ser de `45px`.
2. El texto del menú de navegación debe tener una separación a los costados de
   `25px`, además debe ser del color `#025157`.
3. El tamaño de fuente para las acciones debe ser de `14px` y cada una de las
   acciones debe tener una separación hacia los lados de `10px`. El color del
   texto `Sign In` debe ser `#67b54b` y el botón de `Start free trial` debe tener
   color de texto blanco, color de fondo `#67b54b`, un  relleno de `14px` hacia
   los costados y `12px` en la parte inferior y superior. Por último el botón
   no debe tener borde, pero un radio de borde de `5px` para tener esquinas
   redondeadas.

<br/>

<details>
  <summary>Posible solución</summary>

  ### Posible solución

  ```css
  .header {
    margin-top: 40px;
    margin-left: 20px;
    margin-right: 20px;
    font-size: 0;
    height: 45px;
    font-family: sans-serif;
  }

  .navbar {
    width: 70%;
    text-align: center;
    color: #025157;
  }

  .menu-item {
    display: inline;
    margin-right: 25px;
    margin-left: 25px;
  }

  .actions {
    width: 15%;
    text-align: right;
    font-size: 14px;
  }

  .actions > * {
    margin-right: 10px;
    margin-left: 10px;
  }

  .actions a {
    color: #67b54b;
  }

  .actions button {
    color: white;
    background-color: #67b54b;
    padding-left: 14px;
    padding-right: 14px;
    padding-top: 12px;
    padding-bottom: 12px;
    border: 0;
    border-radius: 5px;
  }
  ```
</details>

<br/>

No olvides subir tus cambios a Github y realizar el deploy en Netlify.

<br/>

