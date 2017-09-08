# :mailbox_with_mail: Clases: _inner_ y _nested_

Se puede definir una clase dentro de otra. Esta clase se denomina _nested_ (anidada). Si queremos que dicha clase tengo acceso a la clase externa que la incluye, tenemos que marcarla como _inner_.

```kotlin
class Externa(val propiedad : Int = 1) {
    private class Anidada {
        fun saludar() {
            println("hola")
        }
    }

    private inner class Interna {
        fun imprimirPropiedad() {
            println(this@Externa)
        }
    }
}
```

>:bulb: Hay que recordar que si no se cambia expresamente, las clases internas serán públicas.

