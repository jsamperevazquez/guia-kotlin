# :package: Estructura interna: _package_ e _import_

Los ficheros de código fuente Kotlin utilizan la extensión .kt

:coffee: **Diferencia con Java:** No es necesario que el nombre del fichero se corresponda con el nombre de la clase.
De hecho, en un mismo fichero Kotlin, pueden haber varias clases (además de funciones y propiedades).

```kotlin
package com.raulvillares.guiakotlin.paquete1

class Cosa1 {}
class Cosa2 {}
```

Un fichero de código Kotlin puede comenzar con la palabra reservada _package_, que indicará el paquete al que pertenecen
todos los elementos declarados en dicho fichero.

Los elementos de este fichero serán accesibles desde todos los ficheros del mismo paquete. Por ejemplo:

```kotlin
package com.raulvillares.guiakotlin.paquete1

var cosa = Cosa1()
```

Pero si queremos acceder desde otro otro paquete ser necesario importarlo utilizando _import_:

```kotlin
package com.raulvillares.guiakotlin.paquete2
import com.raulvillares.guiakotlin.paquete1.*

var cosa = Cosa1()
```

En lugar de importar todos los elementos del paquete (con el asterisco *) podemos importar solo los que necesitemos:

```kotlin
package com.raulvillares.guiakotlin.paquete2
import com.raulvillares.guiakotlin.paquete1.Cosa1

var cosa = Cosa1()
```


:coffee: **Diferencia con Java:** No es necesario que la declaración del paquete se corresponda con el sistema de archivos.
Es decir, podemos tener un fichero .kt que se declara como parte del paquete _com.raulvillares.guiakotlin.utilidades_ dentro del
sistema de archivos _/src/cadenas.kt_ (en lugar de _/src/com/raulvillares/guiakotlin/utilidades/cadenas.kt_).

:coffee: **Diferencia con Java:** No existe la [importación estática](https://docs.oracle.com/javase/8/docs/technotes/guides/language/static-import.html). Todas la importaciones se realizan con _import_.

:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/packages.html
