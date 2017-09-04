# ::twisted_rightwards_arrows:: Flujo de control: if

En Kotlin, _if_ es una expresión que **siempre retorna un resultado**.

```kotlin
fun maximo(a : Int, b : Int) : Int {
    return if(a > b) a else b
}
```

>:coffee: **Diferencia con Java:** En Java _if_ es una declaración (_statement_) y no devuelve ningún resultado.

El hecho de que _if_ sea una expresión nos permite escribir la anterior función de la siguiente manera:

```kotlin
fun maximo(a : Int, b : Int) = if(a > b) a else b
```

Por lo tanto, en Kotlin no existe el [operador ternario](https://es.wikipedia.org/wiki/Operador_ternario#Java.2C_JSP) ya que al ser _if_ una expresión cumple perfectamente con este cometido y de manera más clara. Donde en Java haríamos:

```java
int maximo = (a > b) ? a : b
```

en Kotlin podemos hacer:

```kotlin
val max = if(a > b) a else b
```

Si las ramas de la expresión _if_ están contenidas en llaves (_{}_) el resultado de la expresión _if_ será **la última expresión de cada llave**:

```kotlin
val maximo = if (a > b) {
        println("a es mayor que b")
        a
    } else {
        println("b es mayor que a")
        b
    }
}
```



