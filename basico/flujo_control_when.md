# :abcd: Flujo de control: la expresión _when_

Se puede considerar a _when_ como una versión mejorada de conocido _switch_ de Java (y otros lenguajes). 

```kotlin
fun mostrarComunidad(provincia : String)  {
    when(provincia) {
        "Tarragona" -> println("Cataluña")
        "Sevilla" -> println("Andalucía")
        "Lugo" -> println("Galicia")
        else -> println("Desconocida o no implementado")
    }
}
```

Al igual, que _if_, _when_ puede utilizarse como una expresión.

```kotlin
fun obtenerComunidad(provincia : String) : String  =
    when(provincia) {
        "Tarragona" -> "Cataluña"
        "Sevilla" -> "Andalucía"
        "Lugo" -> "Galicia"
        else -> "Desconocida o no implementado"
    }
```

las ramas admiten varias condiciones, separadas por comas:

```kotlin
fun obtenerComunidad(provincia : String) : String  =
    when(provincia) {
        "Tarragona", "Barcelona", "Lleida", "Girona" -> "Cataluña"
        "Badajoz", "Cáceres" -> "Extremadura"
        else -> "Desconocida o no implementado"
    }
```

El parámetro de _when_ no tienen porque ser constantes, strings a números. Puede ser cualquier tipo de objeto. Así mismo, las condiciones de las ramas pueden ser cualquier expresión:

```kotlin
fun mezclarColores(color1 : String, color2: String) =
    when (setOf(color1, color2)) {
        setOf("ROJO", "AMARILLO") -> "NARANJA"
        setOf("AZUL", "AMARILLO") -> "VERDE"
        setOf("AZUL", "ROJO") -> "MORADO"
        else -> "DESCONOCIDO"
    }
```

Si no se le pasa ningún parámetro, se evaluarán las distintas ramas independientemente. Puede utilizarse como un sustituto más limpio de _if_ _elseif_ _else_:

```kotlin
fun compararEnteros(a : Int, b : Int) {
    when {
        a > b -> println("a es mayor que b")
        b > a -> println("b es mayor que a")
        else -> println("a y b son iguales")
    }
}
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/control-flow.html#when-expression