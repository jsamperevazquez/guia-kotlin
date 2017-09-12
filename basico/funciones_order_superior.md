# :electric_plug: Programación funcional

## Funciones de orden superior

Una función de orden superior (FOS) es una función que cumple una de las siguientes condiciones:

* recibe una función como parámetro
* devuelve una función

Las FOS están contempladas en Kotlin y permiten tratar a las funciones como cualquier otro valor.

## Funciones anónimas

```kotlin
val multiplicarPorCinco = fun(a : Int) = a * 5
```

## Lambdas

Una lambda es **una función anónima que se utiliza en el mismo momento que se declara**. En Kotlin se declara entre llaves (_{}_) y los parámetros se separan del cuerpo de la función con _->_

Por ejemplo, la función _transforma_ devuelve un entero y recibe dos parámetros: un entero y función que se aplicará a dicho entero.

```kotlin
fun transformar(n : Int, funcion : (Int) -> Int) = funcion(n)

fun main(args : Array<String>) {
    val resultado = transformar(2, { a : Int -> a * 5})
}
```

Si el parámetro de la lambda se puede inferir, podemos prescindir del tipo en la declaración:

```kotlin
val resultado = transformar(2, { a -> a * 5})
```

En este caso además, al ser un único parámetro, podemos ignorarlo en la declaración y utilizar el parámetro estándar _it_:

```kotlin
val resultado = transformar(2, { it * 5})
```

Podemos aprovechar la posibilidad de retornar funciones para hacer funciones que crean funciones:

```kotlin
fun mayorQue(n : Int) = { m : Int -> m > n }

fun main(args : Array<String>) {
    val mayorQue5 = mayorQue(5)
    val mayorQue10 = mayorQue(10)
    println(mayorQue10(1))
    println(mayorQue10(15))
}
```

>:rotating_light: Una lambda no permite especificar el tipo de retorno. Normalmente se puede inferir, pero si necesitamos declararlo explícitamente tenemos que utilizar una función anónima.

## Closures

Las variables locales se vuelven a crear cada vez que una función es llamada. Esto, junto a la capacidad de de tratar a las funciones como cualquier otro valor nos permite hacernos una pregunta interesante:

**¿Qué pasa con estas variables locales cuando la función que las crea ya no está activa?**

Vamos a ver un pequeño código que intenta responder a esta pregunta:

```kotlin
fun crearCaja(n : Int) : () -> Int {
    var variableLocal = n
    return { variableLocal }
}

fun main(args : Array<String>) {
    val caja1 = crearCaja(1)
    val caja2 = crearCaja(2)
    println(caja1())
    println(caja2())
}
```
```
Salida:
1
2
```

**La capacidad de hacer referencia a instancias concretas de variables locales desde una función "interna" se denomina _closure_.**

Otro ejemplo:

```kotlin
fun multiplicador(factor : Int) : (Int) -> Int {
    return { factor * it }
}

fun main(args : Array<String>) {
    val por2 = multiplicador(2)
    println(por2(5))
}
```

Una buena manera de ver las _closures_ es pensar que las funciones que son retornadas contienen una foto de las variables locales a las que hacen referencia.

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/lambdas.html