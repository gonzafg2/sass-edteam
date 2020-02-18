# SASS EDTEAM

[https://ed.team/cursos/sass](https://ed.team/cursos/sass)

## Compilar sass con Node

~~~
/* node-sass archivo-entrada archivo-salida */

// Se ejecuta una vez
node-sass styles.scss styles.css

// con --watch, para cada cambio se ejecuta 
node-sass --watch styles.scss styles.css

// para carpetas
~~~

## Tabla de contenidos

1. [Sintaxis](#Sintaxis)
    - [Variables](#Variables)
    - [Anidamiento](#Anidamiento)
    - [Tipos de datos](#Tipos-de-datos)
    - [@import](#import)
## Sintaxis

### Variables
* Se declaran con `$`
* Tiene un scope si estan dentro de llaves `{ }` solo podrán usarse en esa parte, por ello mayormente se declaran de forma global (fuera de llaves). 
* Se pueden hacer operaciones sin necesidad de colocar la unidad (px, em,rem).

*Ejemplo*
~~~
$size: 200px

body { padding-top: $size + 10; }
~~~

Una opción de las variables es que se pueden sobreescribir usando `!default` tomando el valor que no tiene default.

*Ejemplo*
~~~
$width: 20px !default;

// En otro archivo, ubicado antes o después

$width: 50px;
~~~

Se puede interpolar la variable por ejemplo para crear un selector con nombre de variable. 

*Ejemplo*
~~~
$color: red;

#{color} {
  color: $color;
}

.#{color} {
  color: $color;
}

/* Resultado */

red {
  color: red;
}

.red {
  color: red;
}
~~~

Otro ejemplo de interpolación es para la propiedad css `calc` porque esta propiedad espera dos valores, no espera algo para ser compilado

~~~
$size: 200px;

div {
  width: calc(100% - $size);  
}

section {
  width: calc(100% - #{$size});  
}

/* Resultado */
div {
  width: calc(100% - $size);  
}

section {
  width: calc(100% - 200px);  
}

~~~

### Anidamiento

Permite agregar selectores dentro de otros, una buena practica es tener como máximo 02-03 anidamientos o ninguno para no generar un anidamiento extremo.

*Ejemplo*
~~~
.header {
  ul { padding: 10px; }
  li { display: flex; }
  a { color: blue; }
}
~~~

**Casos de uso**

* Media query.
*Ejemplo*
~~~
.header {
  padding: 20px;
  @media screen and (min-width: 1024px) {
    padding: 10px;
  }
}
~~~

* Animaciones.
*Ejemplo*
~~~
.chat-image {
  animation: rotacion 1s;
  @keyframes rotacion {
    //
  }
}
~~~

* Selector padre con pseudo-elemento, utilizando `&`
*Ejemplo*
~~~
.link {
  &:hover { color: green; }
}
~~~

**Nota**: Una mala practica sería usar con selectores normales
*Ejemplo*
~~~
// mala practica
.link {
  & li { color: green; }
}
~~~

* Clases.
*Ejemplo*
~~~
.menu {
  display: flex;
  &-item { color: blue; }
}

/* Resultado */

.menu {
  display: flex;
  .menu-item { color: blue; }
}
~~~

* Propiedad.
*Ejemplo*
~~~
.main {
  font: {
    family: arial;
    size: 18px;
    weigth: 700;
  }
  grid-template: {
    columns: 100px 100px;
    rows: auto;
  }
}

/* Resultado */

.main {
  font-family: arial;
  font-size: 18px;
  font-weigth: 700;
  grid-template-columns: 100px 100px;
  grid-template-rows: auto;
  }
}
~~~

### Tipos de datos

Es importante porque aveces nos toca validar el tipo de dato pasado ej. en mixis. 

`type-of`: permite saber el tipo de dato

*Ejemplo*
~~~
$var: hola;
type-of($var)
~~~

* String: Se utiliza con comillas o sin comillas

*Ejemplo*
~~~
$var: 'hola';

.header { content: $var; }
~~~

* Números: Son números con unidades (px, em, rem, s)

*Ejemplo*
~~~
$var1: 1em;
$var2: 12px;
$time: 5s;

.animacion { animation-duration: $time; }
~~~

* Colores: 

*Ejemplo*
~~~
$var1: blue;
$var2: darken(red,20);

body {
  background: $var2;
  color: $var1;
}

~~~

* Booleans

*Ejemplo*
~~~
$var: false;
~~~

* List: Son valores de propiedades separadas con espacio o comas
*Ejemplo*
~~~
$var: 1px solid red;
~~~

* Maps: Su sintaxis es parecida a objetos de js
*Ejemplo*
~~~
$colores: (
  primario: red,
  secundario: blue,
  terciario: yellow
);

body {
  color: map-get($colores, secundario);
}
~~~

### @import

Permite estructurar distintos archivos sass y luego unificarlos en uno solo, pero para ello es importante que los archivos secundarios sean archivos parciales `_archivo`
*Ejemplo*
~~~
// Tenemos un archivo parcial _variables.scss y otro archivo styles.scss
@import "variables"

body { background: $color; }
~~~
## 
