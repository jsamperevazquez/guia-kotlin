# :memo: Cadenas

Respecto a Java, son dos las novedades que presenta Kotlin en el tratamiento de cadenas: templates y cadenas raw.

## Tipos de cadenas: _escaped_ y _raw_

### Cadenas _escaped_

Las cadenas escaped son equivalentes a las cadenas de Java. 

```kotlin
val cadenaEscapable = "Hola, mundo!\n"
```

Los carácteres escapables por defecto son: \t , \b , \n , \r , \' , \" , \\ \$ 

### Cadenas _raw_

A diferencia de las _escaped_, las cadenas _raw_ no contienen caracteres escapables y pueden contener saltos de linea:

```kotlin
val cadena =    """
                |Un viejo estanque
                |una rana salta
                |el sonido del agua
                """.trimMargin()
println(cadena)
```

La función trimMargin se utiliza para eliminar los espacios en blanco y como prefijo por defecto se utiliza "|". Pero se puede utilizar cualquier otra cadena:

```kotlin
val cadena =    """
                *Un viejo estanque
                *una rana salta
                *el sonido del agua
                """.trimMargin("*")
println(cadena)
```
Las cadenas raw pueden ser útiles en situaciones en las que sea necesario definiar cadenas largas separadas en varias lineas, como por ejemplo en consultar SQL:

```kotlin
val consulta =   """
                |SELECT
                |   *
                |FROM
                |   dbo.TRABAJADORES
                |WHERE
                | idTrabajador = 100
                """.trimMargin()
```

## String templates

Las cadenas en Kotlin pueden contener expresiones, que serán evaluadas en el momento de ejecución y cuyo resultado será encadenado a la cadena:

```kotlin
val lenguaje = "Kotlin"
println("Hola desde $lenguaje!") // La salida es: "Hola desde Kotlin!"
```

Las expresiones más complejas se incluyen dentro de llames ({}):

```kotlin
val a = 2
val b = 5
println("la suma de a y b es ${a+b}")
```

Los _string templates_ se pueden utilizar también en cadenas _raw_:

```kotlin
val a = 2
val b = 5
val cadena =    """
                | a
                |+
                | b
                |__
                |${a+b}
                """.trimMargin()
    println(cadena)
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/basic-types.html#strings