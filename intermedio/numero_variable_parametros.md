# :musical_keyboard: Número variable de parámetros

El modificador _vararg_ permite indicar un número variable de parámetros.

```kotlin
fun sumar(vararg elementos: Int) = elementos.reduce { suma, elemento -> suma + elemento }

fun main(args : Array<String>) {
    println(sumar(1,2,3))
}
```

Normalmente se utiliza en el último parámetro de la función. Sin embargo es posible utilizarlo en otro posición y llamar a la función con los nombres de los parámetros.

```kotlin
fun <T> crearCenefa(vararg elementos: T, repeticiones: Int): List<T> {
    val lista = ArrayList<T>()
    for(i in 1..repeticiones)
        lista += elementos
    return lista
}

fun main(args : Array<String>) {
    println(crearCenefa(1, 2, 3, repeticiones=3))
}
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/functions.html#variable-number-of-arguments-varargs