# SASS EDTEAM

## Sintaxis

### Variables
Se declaran con $, teniendo un scope si estan dentro de llaves { } solo podrán usarse en esa parte, por ello mayormente se declaran de forma global (fuera de llaves). Se pueden hacer operaciones sin necesidad de colocar la unidad (px, em,rem). Ej:
~~~
$size: 200px

body { padding-top: $size + 10; }
~~~

Una opción de las variables es que se pueden sobreescribirse usando `!default` tomando el valor la que no tiene default. Ej:

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

Como resultado:

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

### Tipos de datos

### @import

## 
