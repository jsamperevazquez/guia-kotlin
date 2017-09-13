# :microscope: Detalles

* No es necesario el ; al final de cada statement

* Hay 4 elementos principales que se pueden definir **a nivel de paquete**: funciones, propiedades, clases y objetos.

* No existe el concepto _static_. Los miembros se pueden declaran fuera de las clases, directamente a nivel de paquete.

* Comparación: == compara valores, === referencias.

* Es posible utilizar el guión bajo para hacer los constantes numéricas más legibles:

```kotlin
val millon = 1_000_000
```

* Se puede utilizar _const_ para propiedades cuyo valor se conoce en tiempo de compilación. Dichas propiedades han de cumplir:

    * Declaradas a nivel de paquete (top-level) o miembro de un objeto.
    * De tipo String o primitivo
    * Sin una función _get_ personalizada.

## Arrays

* Las arrays se pueden crear con la función _arrayOf_:

```kotlin
var tresPrimeros = arrayOf(1,2,3)
for(i in tresPrimeros) println(i)
```

Se puede acceder a sus miembros utilizando los corchetes [] que equivalen a las funciones _set_ y _get_:

```kotlin
var tresPrimeros = arrayOf(1,2,3)
for(i in 0..tresPrimeros.size-1) println(tresPrimeros[i])
for(i in 0..tresPrimeros.size-1) println(tresPrimeros.get(i))
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/basic-types.html#arrays