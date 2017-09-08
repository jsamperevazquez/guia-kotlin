# :factory: Clases: creación

La forma más simple de crear y utilizar una clase es:

```kotlin
class Clase

fun main(args : Array<String>) {
    val vacia = Clase()
}
```

Si no se indica nada, se genera automáticamente un **constructor primario**. El anterior código es equivalente a:

```kotlin
class Clase constructor() {}

fun main(args : Array<String>) {
    val vacia = Clase()
}
```


Las clases pueden recibir parámetros en su **constructor primario**:

```kotlin
class Persona constructor(nombre : String) {
    val nombre = nombre
}
```

Si el contructor primario no tiene modificadores de visibilidad ni anotaciones se puede prescindir de la palabra _constructor_:

```kotlin
class Persona(nombre : String) {
    val nombre = nombre
}
```

Hay una manera más directa de crear [propiedades](./elementos_basicos_propiedades.md):

```kotlin
class Persona(val nombre : String)
```

El código de inicialización de la clase, de existir, tiene que ir dentro de un bloque _init_:

```kotlin
class Persona(val nombre : String) {
    init {
        println("Se ha creado un objeto de la clase Persona con nombre ${this.nombre}")
    }
}
```

## Constructores secundarios

Se utiliza la palabra reservada _constructor_ para constructores adicionales al primario. **Es necesario llamar al primario desde el secundario** (de manera directo o indirecta a través de otro constructor secundario):

```kotlin
class Persona(val nombre : String) {
    constructor(nombre : String, apellido : String) : this("$nombre $apellido")
    constructor(nombre : String, apellido1 : String, apellido2 : String) : this("$nombre $apellido1", apellido2)
}

val persona1 = Persona("Raul")
val persona2 = Persona("Raul", "Villares")
val persona3 = Persona("Raul", "Villares", "Sanchez")
```

Hay que tener en cuenta que el bloque _init_ se ejecuta cada vez que se crea un objeto, **desde cualquier constructor** (ya que todos los constructores acaban llamando al primario):

```kotlin
class Persona(val nombre : String) {
    init {
        println("Se ha creado un objeto de la clase Persona")
    }
    constructor(nombre : String, apellido : String) : this("$nombre $apellido")
}
```

De manera similar a Java, si una clase implementa constructores secundarios, no se generará automáticamente un constructor primario:

```kotlin
class Persona {
    var nombre = ""
    constructor(nombre : String) {
        this.nombre = nombre
    }
}

val persona = Persona() // Error de compilación
```

:bulb: Este código está forzado para mostrar el ejemplo. La manera lógica de hacerlo sería:
```kotlin
class Persona(val nombre : String = "")
```

Desde los constructores secundarios no se pueden definir propiedades:

```kotlin
class Persona {
    constructor(val nombre : String) // Error de compilación
}
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/classes.html