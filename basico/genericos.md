# :bust_in_silhouette: Genéricos

Al igual que en Java, en Kotlin las clases (además de las funciones) pueden tener un tipo. Aquí podemos ver un ejemplo básico con la implementación y utilización de de una pila:

```kotlin
class Pila<T>() {
    private val elementos = mutableListOf<T>()

    private fun size() : Int = this.elementos.size

    fun put(elemento : T) {
        this.elementos.add(elemento)
    }

    fun pop() : T = this.elementos.removeAt(this.elementos.lastIndex)

    override fun toString() = this.elementos.toString()
}

fun main(args : Array<String>) {

    val pilaEnteros = Pila<Int>()
    pilaEnteros.put(1)
    pilaEnteros.put(3)
    pilaEnteros.put(2)
    println(pilaEnteros.pop())
    println(pilaEnteros)

    val pilaStrings = Pila<String>()
    pilaStrings.put("hola")
    pilaStrings.put("que")
    pilaStrings.put("tal")
    println(pilaStrings.pop())
    println(pilaStrings)

}
```

## Limitación de tipos

Se puede restringir los subtipos que puede admitir un tipo génerico. Por ejemplo podríamos redefinir nuestra Pila de la siguiente manera:

```kotlin
class Pila<T : Comparable<T>>() {
    ...
}
```

Las pilas de enteros y de _Strings_ definidas anteriormente seguirían funcionando (ya que implementan la _interface_ _Comparable_) pero no podríamos crear la siguiente pila:

```kotlin
val pilaNoValida = Pila<HashMap<Int, String>>()
```

Las funciones también pueden tener tipos genéricos:

```kotlin
fun  <T> imprimir(lista : List<T>) {
    println(lista.joinToString(separator = ",", prefix = "[", postfix = "]"))
}

fun main(args : Array<String>) {
    imprimir(listOf(1,2,3,4,5))
    imprimir(listOf("hola", "que", "tal"))
}
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/generics.html