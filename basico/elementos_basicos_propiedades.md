# :mailbox_with_mail: Elementos básicos: propiedades

No debemos confundir una propiedad con una variable. Una propiedad es un elemento de máximo nivel (puede estar definida a nivel de clase pero **también a nivel de paquete**) a la que no se accede directamente, si no a través de unos _accesors_. Estos _accesors_ son una función _get_ (para leer el valor) y una función _set_ (para cambiar el valor).

Por ejemplo:

```kotlin
package com.raulvillares.guiakotlin.elementosbasicos

var propiedad = 0

fun main(args : Array<String>) {
    propiedad = 1
    println(propiedad)
}
```

Aunque _propiedad_ parezca una variable normal y corriente en realidad estamos accediendo a ella a través de las funciones get y set que aunque no se vean están definidas y siendo utilizas para acceder al valor de _propiedad_. En realidad, el código anterior es equivalente a:

```kotlin
package com.raulvillares.guiakotlin.elementosbasicos

var propiedad = 0
    get() = field
    set(value) {
        field = value
    }

fun main(args : Array<String>) {
    propiedad = 1
    println(propiedad)
}
```

Ahora se ven los _accesors_ _get_ y _set_ que antes estaban "ocultos". 

>:eyes: Con la palabra reservada field accedemos valor de la propiedad directamente, ya que si utilizamos _propiedad_ estaremos llamador al _accesor_ get y tendríamos un error en tiempo de ejecución al llamar una y otra vez a la función get.

Esto daría error en tiempo de ejecución:

```kotlin
package com.raulvillares.guiakotlin.elementosbasicos

var propiedad = 0
    get() = propiedad

fun main(args : Array<String>) {
    println(propiedad)
}
```

ya que _get_ se está llamando recursivamente. 

>:rotating_light: En Kotlin, a una propiedad nunca se accede directamente, SIEMPRE se hace a través de sus accesors (estén estos codificados explícitamente o no).

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/properties.html


