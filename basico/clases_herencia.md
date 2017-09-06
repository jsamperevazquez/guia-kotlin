# :family: Clases: herencia

>:coffee: **Diferencia con Java:** Por defecto, de las clases Kotlin no se puede heredar ya que son _final_. Hay que marcarlo explícitamente con la palabra _open_ en la declaración de la clase:

```kotlin
open class Base
class Derivada : Base()
```

:bulb: Todas las clases heredan de una clase _Any_ similar a _Object_ de Java.

Si una clase derivada no tiene constructor primario, sus constructores secundarios tienen que llamar al contructor primario de la clase base directa a indirectamente (a través de constructores secundarios de la clase base) utilizando la palabra _super_:

```kotlin
open class Base

class Derivada : Base {
    var a = 0
    constructor(a : Int) : super() {
        this.a = a
    }
}
```

:bulb: De nuevo este código está forzado para mostrar el ejemplo. La manera lógica de hacerlo sería:
```kotlin
open class Base
class Derivada(val a : Int = 0) : Base()
```

## Métodos

Al igual que con las clases, los métodos en Kotlin son _final_ por defecto, y si quieren sobreescribirse es necesario marcalos con _open_.

```kotlin
open class Base {
    open fun saludar() {
        println("hola, soy Base!")
    }
}

class Derivada() : Base() {
    override fun saludar() {
        println("hola, soy Derivada!")
    }
}
```

>:coffee: **Diferencia con Java:** Es obligatorio marcar con _override_ los métodos de una clase derivada que sobreescriban métodos de la clase base.

## Propiedades

Se sobreescriben de manera análoga a los métodos:

```kotlin
open class Entero protected constructor(val signo : Char = '+', valor : Int) {
    open val valor = if(signo == '-') valor *-1 else valor
}

open class Negativo(valor : Int) : Entero('-', valor)
open class Positivo(override val valor : Int) : Entero('+', valor)
```

## Acceder a miembros de la clase base

Para acceder a miembros (funcones, propiedades,...) de una clase base desde una clase derivada se utiliza _super_:

```kotlin
open class Base(val valor : Int) {
    open fun saludar() {
        println("hola!")
    }
}

class Derivada(valor : Int) : Base(valor) {
    override fun saludar() {
        super.saludar()
        println("tengo el valor ${super.valor}")
    }
}
```

