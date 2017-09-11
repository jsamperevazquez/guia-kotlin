# :page_facing_up: Chuleta

## Hola Mundo

```kotlin
fun main(args: Array<String>) {
    println("¡Hola Mundo!")
}
```

## Variables

```kotlin
val nombre = "Kotlin"   // No puede modificarse
var suma = 5            // Puede modificarse
```

## Propiedades

```kotlin
val nombre = "Kotlin"
    get() = field
    set(value) {
        field = value
    }
```

## Expresión If

```kotlin
fun maximo(a : Int, b : Int) = if(a > b) a else b
```

## Expresión When (+ Smart cast)

```kotlin
fun longitud(parametro : Any) =
    when(parametro) {
        is String -> parametro.length       // Smart cast
        is Collection<*> -> parametro.size  // Smart cast
        else -> -1
    }
```

>:link: Inspirada en: https://jaxenter.com/kotlin-cheat-sheet-tips-tricks-136716.html