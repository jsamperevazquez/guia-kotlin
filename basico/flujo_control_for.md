# :repeat: Flojo de control: El bucle _for_ (y los rangos)

La única forma del bucle _for_ en Kotlin es del tipo 'for-each', que itera sobre cualquier objeto que implemente la _interface iterator_ que se utiliza normalmente para recorrer colecciones de elementos.

```kotlin
val lista = listOf(1,2,3)
for(i in lista) println(i)
```

Para conseguir el mismo resultado que los bucles _for_ de Java que inicializan una variable y la van modificando en cada iteración, Kotlin manjea el concepto de **rango**.

Un rango es un intervalo de datos entre dos valores, utilizando el operador dos puntos (_.._).

```kotlin
val rango = 1..3
for(i in rango) println(i)
```

_in_ e _!in_ se utilizan para comprobar si un determinado valor pertenece a un rango:

```kotlin
val letras = 'a'..'z'
if('a' in letras) println("es una letra")
if('1' !in letras) println("no es una letra")
```

Por defecto, los rangos son "cerrados". Es decir, el último elemento forma parte del rango. Para cambiar esto es necesario utilizar el operador _until_:

```kotlin
val rango1 = 1..3
val rango2 = 1 until 4
println(rango1 == rango2)
```

Para cambiar el salto de la iteración se utiliza el operador _step_ que por defecto tiene valor 1:

```kotlin
val cincoPrimerosPares = 2..10 step 2
```

Es posible iterar sobre un rango al revés, utilizando _downTo_:

```kotlin
val rango = 3 downTo 1
for(i in rango) println(i)
```

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/control-flow.html#for-loops