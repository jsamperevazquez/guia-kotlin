# :link: Llamadas _infix_

Las funciones con un único parámetro puede llamarse de manera infija:

```kotlin
infix fun Int.mas(n: Int) = this + n

fun main(args : Array<String>) {
    val resultado = 2 mas 5
    println(resultado)
}
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/functions.html#infix-notation