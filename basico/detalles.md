# :microscope: Detalles

* No existe el concepto _static_. Los miembros se pueden declaran fuera de las clases, directamente a nivel de paquete.

* Comparación: == compara valores, === referencias.

* No es necesario el ; al final de cada statement

* Es posible utilizar el guión bajo para hacer los constantes numéricas más legibles:

```kotlin
val millon = 1_000_000
```

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