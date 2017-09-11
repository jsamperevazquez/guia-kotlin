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

## Closure

```kotlin
fun crearContador() : () -> Int {
    var contador = 0
    return fun() : Int {
        contador += 1
        return contador
    }
}

fun main(args : Array<String>) {
    val contador = crearContador()
    println(contador()) // 1
    println(contador()) // 2
}
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/lambdas.html