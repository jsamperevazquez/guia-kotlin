# :bulb: Casting inteligente

Si ya hemos validado el tipo de un objeto (de alguna de las varias maneras posibles) no es necesario volver a comprobarlo, pudiendo utilizar directamente las funciones que son propias de dicho tipo.

```kotlin
fun <T> mostrarInfo(elemento: T) {
    when (elemento) {
        is String -> println(elemento.length) // Smart cast
        else -> println(elemento)
    }
}
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/typecasts.html#smart-casts