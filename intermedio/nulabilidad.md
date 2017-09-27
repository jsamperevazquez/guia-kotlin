# :mailbox_with_no_mail: Nulabilidad

En Kotlin, al declarar una variable hay que definir explicitamente si puede contener valores nulos o no.

```kotlin
    val primerApellido: String = "raul"
    val segundoApellido: String?  = "villares"
    println(primerApellido.length) // Nunca será nulo, no hace falta comprobarlo
    println(segundoApellido.length) // Error de compilación
```

Hay varias opciones para tratar los nulos y evitar el error de compilación anterior:

### Comprobar explícitamente los casos nulos

```kotlin
    val segundoApellido: String?  = "villares"
    val longitud = if(segundoApellido != null) segundoApellido.length else -1
```

### Llamadas seguras

```kotlin
    val segundoApellido: String?  = null
    val longitud = segundoApellido?.length
    println(longitud)
```
```
Salida: null
```

Devuelve _null_ si el objeto es _null_.

```kotlin
    val segundoApellido: String?  = null
    println(segundoApellido?.length ?: "nula")
```
```
Salida: nula
```

## Provocar un NullPointer Exception

No es fácil en Kotlin. La única manera es utilizar el operador !!

```kotlin
    val segundoApellido: String?  = null
    println(segundoApellido!!.length)
```
```
Salida: Exception in thread "main" kotlin.KotlinNullPointerException
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/null-safety.html