# SASS EDTEAM

## Sintaxis

### Variables
* Se declaran con **$**
* Tiene un scope si estan dentro de llaves { } solo podrán usarse en esa parte, por ello mayormente se declaran de forma global (fuera de llaves). 
* Se pueden hacer operaciones sin necesidad de colocar la unidad (px, em,rem).

*Ejemplo*

~~~
$size: 200px

body { padding-top: $size + 10; }
~~~

Una opción de las variables es que se pueden sobreescribir usando `!default` tomando el valor que no tiene default. Ej:

~~~
$width: 20px !default;

// En otro archivo, ubicado antes o después

$width: 50px;
~~~

Se puede interpolar la variable por ejemplo para crear un selector con nombre de variable. Ej:

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

Permite agregar selectores dentro de otros, una buena practica es tener como máximo 02-03 anidamientos o ninguno para no generar un anidamiento extremo. Ej:

~~~
.header {
  ul { padding: 10px; }
  li { display: flex; }
  a { color: blue; }
}
~~~

Otro caso a usar es en media query. Ej:
~~~
.header {
  padding: 20px;
  @media screen and (min-width: 1024px) {
    padding: 10px;
  }
}
~~~

### Tipos de datos

### @import

## 
