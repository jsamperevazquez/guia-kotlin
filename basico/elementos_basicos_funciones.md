# :droplet: Elementos básicos: funciones

Las funciones en Kotlin se declaran con la palabra reservada _fun_.

>:coffee: **Diferencia con Java:** No es necesario que una función esté declarada dentro de una clase (estas funciones se denominan _member functions_). Pueden estar definidas a nivel de paquete.

Los parámetros de un función siguen la notación Pascal y pueden tener valores por defecto:

```kotlin
fun saludar(saludo : String = "hola", nombre : String, emoji : String = ":-)") : String {
    return "$saludo $nombre $emoji"
}
```

Los parámetros pueden ser llamados por el nombre:

```kotlin
fun main(args : Array<String>) {
    println(saludar(emoji = ":-D", nombre = "raul"))
}
```

>:rotating_light: Esto solo es válido cuando se llama a funciones Kotlin. Si llamamos a funciónes Java no podemos utilizarlo.

Si el cuerpo de la función consta solo de una expresión (como es el caso anterior) podemos declararla así:

```kotlin
fun saludar(saludo : String = "hola", nombre : String, emoji : String = ":-)") : String = "$saludo $nombre $emoji"
```

Incluso podemos prescindir del tipo de retorno ya que se infiere de la expresión:

```kotlin
fun saludar(saludo : String = "hola", nombre : String, emoji : String = ":-)") = "$saludo $nombre $emoji"
```

Las funciones que no retornan nada tiene el tipo de retorno especial _Unit_ :

```kotlin
fun saludar() : Unit {
    println("hola")
}
```

Que puede ser omitido:

```kotlin
fun saludar() {
    println("hola")
}
```
