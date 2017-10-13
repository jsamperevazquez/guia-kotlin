# :clock9: Inicialización en diferido

A veces no queremos inicializar una propiedad en el mismo momento que la declaramos. En estos casos podemos utilizar el modificador _lateinit_.

```kotlin
class BolosTest {

    lateinit var partida : Partida

    @BeforeEach
    fun crearPartida() {
        partida = Partida()
    }
```

Vemos como no tiene sentido que la propiedad _partida_ se inicialice en el momento de la declaración ya que de ello se encarga la función _crearPartida_ (que será llamada antes de cada test unitario).

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/properties.html#late-initialized-properties