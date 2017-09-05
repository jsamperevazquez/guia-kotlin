# :microscope: Variables

La inicialización de una variable local en Kotlin es de a forma:

```kotlin
var a : Int = 0
```

Es posible prescindir del tipo si puede ser inferido de la asignación:

```kotlin
var a = 0
```

El símbolo de interrogación después del tipo indica que admite valores nulos, que es _nullable_. Por lo tanto, esto no es válido:

```kotlin
var a : Int = null
```

Sin embargo, esto sí:

```kotlin
var a : Int? = null
```

>:rotating_light: Por defecto, la inferencia de tipos no considera tipos _nullables_. Es decir, esto daría error de compilación:

```kotlin
var a = 0
a = null
```

ya que sería equivalente a:

```kotlin
var a : Int = 0
a = null
```

En Kotlin existen dos tipos de variables locales: mutables e inmutables.

## Variables mutables

se definen con la palabra reservada _var_ (de **variable**). Su valor puede ser reasignado.

```kotlin
var mutable = 1
mutable = 2
```

## Variables inmutables

se definen con la palabra reservada _val_ (de **value**)

>:rotating_light: La referencia a la que apuntan no puede ser cambiada, lo cual no quiere decir que el objeto al que hacen referencia no pueda cambiar. 

En tipos primitivos (números, booleanos,...) esto no afecta:

```kotlin
package com.raulvillares.guiakotlin.elementosbasicos

fun main(args : Array<String>) {
    var a = 1
    val b = a
    a = 2
}
```

En este caso, la variable b conserva el valor 1. Pero con elementos complejos (como las clases), en los que en la variable se almacena la referencia y no el valor, hay que tener cuidado.

```kotlin
package com.raulvillares.guiakotlin.elementosbasicos

class Cosa(var valor : Int)

fun main(args : Array<String>) {
    var cosa = Cosa(1)
    val inmutable = cosa
    cosa.valor = 2
    // ahora, inmutable.valor contiene un 2
}
```

Lo que no se puede hacer con una variable inmutable es reasignar su valor. Por ejemplo, y siguiendo el código anterior, esto está prohibido:

```kotlin
inmutable = Cosa(3)
```

lo cual si estaría permitido si hubiésemos definido la variable _inmutable_ de la siguiente manera:

```kotlin
var inmutable = cosa
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/basic-syntax.html#defining-local-variables
