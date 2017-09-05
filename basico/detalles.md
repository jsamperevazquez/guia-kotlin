# :microscope: Detalles

* Comparación: == compara valores, === referencias.

* No es necesario el ; al final de cada statement

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