# :leftwards_arrow_with_hook: Flujo de control: break, continue y return

## _Break_

Finaliza el bucle más cercano, el más interior:

```kotlin
fun imprimirCincoPrimeros() {
    for (i in 1..10) {
        println(i)
        if(i == 5) break
    }
}
```

Aquí, terminaría el segundo _for_, el de las letras, pero el primero se volvería a ejecutar:

```kotlin
fun imprimirMatriz() {
    for (i in 1..5) {
        for (j in 'a'..'z') {
            print("[$i$j]")
            if (j == 'e') break
        }
        println()
    }
}
```

```
Salida:
[1a][1b][1c][1d][1e]
[2a][2b][2c][2d][2e]
[3a][3b][3c][3d][3e]
[4a][4b][4c][4d][4e]
[5a][5b][5c][5d][5e]
```

Si queremos terminar ambos bucles, podemos utilizar etiquetas:

```kotlin
fun imprimirMatriz() {
    loop@ for (i in 1..5) {
        for (j in 'a'..'z') {
            print("[$i$j]")
            if (j == 'e') break@loop
        }
        println()
    }
}
```

```
Salida:
[1a][1b][1c][1d][1e]
```

## Continue

Salta a la siguiente iteración del bucle más cercano:

```kotlin
fun imprimirPares() {
    for(i in 1..10) {
        if (i % 2 != 0) continue
        print(i)
    }
}
```
```
Salida:
246810
```

También es posible utilizar etiquetas:

```kotlin
fun imprimirVocalNumero() {
    numeros@ for(numero in 1..5) {
        letras@ for(letra in 'a'..'z') {
            when(letra) {
                'a', 'e', 'i', 'o' ->  print("[$numero$letra]")
                'u' ->   {
                    println("[$numero$letra]")
                    continue@numeros
                }
                else -> continue@letras
            }
        }
    }
}
```

```
Salida:
[1a][1e][1i][1o][1u]
[2a][2e][2i][2o][2u]
[3a][3e][3i][3o][3u]
[4a][4e][4i][4o][4u]
[5a][5e][5i][5o][5u]
```

## Return

Sale de la función más cercana en la que se encuentra la instrucción.

```
fun imprimirCincoPrimeros() {
    for(i in 1..10) {
        println(i)
        if(i == 5) return
    }
    println("Esto no se llegará a imprimir")
}
```

Como con _break_ y _continue_ se pueden utilizar etiquetas.