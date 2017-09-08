# :card_index: Data classes

Las clases _data_ simplifican la tarea de crear clases que solo contienen datos. Implementan por defecto las siguientes funciones:

* equals()
* toString()
* copy()
* componentN() : Una por cada propiedad de la clase, siendo N 1,2,3,...

```kotlin
data class Persona(val nombre : String, val apellido : String)

fun main(args : Array<String>) {
    val raul = Persona("Raul", "Villares")
    val clon = raul.copy()
    val padre = raul.copy(nombre="Nemesio")
    println(raul == clon) // Está utilizando equals()
    println(raul == padre) // Está utilizando equals()
    println(raul) // Está utilizando toString()
    println(raul.hashCode())
}
```

Para que una clase pueda ser declarada _data_ tiene que cumplir:

* El constructor primario debe tener al menos un parámetro.
* Todos los parámetros del constructor primario deben estar marcados con _val_ o _var_.
* No pueden ser _abstract_, _open_, _sealed_ ni _inner_.

Las funciones de componentes (_componentN()_) permiten deconstruir las clases data:

```kotlin
val raul = Persona("Raul", "Villares")
val (nombre, apellido) = raul
println("nombre : $nombre ; apellido : $apellido")
```

Kotlin tiene dos clases _data_ por defecto: **_Pair_** y **_Triple_**, que admiten 2 y 3 parámetros respectivamente.

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/data-classes.html

