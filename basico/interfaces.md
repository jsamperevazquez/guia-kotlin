# :busts_in_silhouette: Interfaces

Las _interfaces_ funcionan de manera similar a Java:

```kotlin
interface Interfaz {
    fun saludar()
}

class Concreta : Interfaz {
    override fun saludar() {
        println("hola")
    }
}
```

Puedes tener propiedades pero o bien deben ser abstractas o bien deben implementar _accesor_ (que no tienen _backing fields_):

```kotlin
interface Interfaz {
    abstract var p1 : Int
    val doble : Int
        get() = p1*2
}
```

La _interfaces_ admiten implementación:

```kotlin
interface Interfaz {
    fun saludar() {
        println("hola")
    }
}
```

Una clase puede implementar varias interfaces (o derivar de una clase) que definan una función con la misma signatura. En ese caso, es necesario referirse a la función especificando a que interfaz o clase base nos referimos:

```kotlin
interface Interfaz1 {
    fun saludar() {
        println("hola")
    }
}

interface Interfaz2 {
    fun saludar()
}

open class Base {
    open fun saludar() {
        println("ei!")
    }
}

class Concreta : Base(), Interfaz1, Interfaz2 {
    override fun saludar() {
        super<Interfaz1>.saludar() // Hay que espeficifarlo ya que saludar() existe en 2 interfaces y una clase
        println("soy una clase concreta")
    }
}
```


