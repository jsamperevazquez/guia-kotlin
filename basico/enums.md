# :1234: Enums

Los _enums_ funcionan en Kotlin de manera equivalente a Java:

```kotlin
enum class RGB {
    ROJO, VERDE, AZUL;

    fun resto() : List<RGB> {
        val resto = mutableListOf<RGB>()
        for(color in enumValues<RGB>()) {
            if(color != this) resto.add(color)
        }
        return resto
    }
}

fun mezclar(color1 : RGB, color2 : RGB) =
    when (setOf(color1, color2)) {
        setOf(RGB.ROJO, RGB.AZUL) -> "MORADO"
        setOf(RGB.ROJO, RGB.VERDE) -> "AMARILLO"
        setOf(RGB.VERDE, RGB.AZUL) -> "CELESTE"
        else -> "DESCONOCIDO"
    }

fun main(args : Array<String>) {
    println(mezclar(RGB.ROJO, RGB.VERDE))
    println(RGB.ROJO.resto())
    println(RGB.valueOf("ROJO"))
}
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/enum-classes.html