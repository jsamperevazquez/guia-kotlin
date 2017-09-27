# :hatching_chick: Extensiones

Las extensiones permiten añadir funcionalidad (como propiedades o funciones) a las clases, que pueden ser utilizadas posteriormente como si formaran parte de la clase original. Son propiedades y funciones que se definen fuera de la clase para que se pueden utilizar como si formaran parte de ella.

>:rotating_light: Desde las extensiones no se puede acceder a los miembros privados de la clase receptora.

>:rotating_light: Las extensiones deben importarse desde el fichero en el que quieren utilizarse.

```kotlin
fun Int.resto(divisor: Int) = this % divisor

val Int.par
    get() = this.resto(2) == 0

fun main(args : Array<String>) {
    println(10.resto(3))
    println(2.par)
    println(3.par)
}
```

La palabra _this_ hace referencia al objeto **receptor** sobre el que se aplica dicha extensión.

Hemos extendido la clase Int con dos nuevas funcionalidades:

* una función _resto_.
* una propiedad _par_.

Las extensiones son una buena manera de sustituir las clases-utilidades tan comunes en Java. Por ejemplo, la típica clase StringUtils.java que creamos para poder realizar ciertas acciones sobre las cadenas.

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/extensions.html