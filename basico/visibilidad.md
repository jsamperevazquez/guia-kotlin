# :eyes: Visibilidad

Los siguientes elementos pueden tener modificadores de visibilidad:

* Clases
* Propiedades
* Constructores
* Funciones
* Interfaces
* Objetos
* Los _accesors_ _set_ a propiedades

:bulb: Los _accesors_ _get_ a propiedades siempre tienen la misma visibilidad que su propiedad.

Los tipos de modificadores de visibilidad son:

* private
* protected
* internal
* public

La visibilidad por defecto (si no se indica ninguna otra) es _public_.

>:coffee: En Java la visiblidad por defecto es _package-private_. Pueden acceder los miembros del mismo paquete (no la subclases). Ver [Controlling Access to Members of a Class](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html)

## Efecto de modificadores de visibilidad a nivel de **paquete**

Hay 4 elementos que se pueden definir a nivel de paquete: propiedades, funciones, clases y objetos. Asi les afectan los modificadores de visibilidad en este nivel:

* public: visible de manera global.
* internal: visible para los elementos del mismo paquete.
* private: visible solo en el mismo fichero.
* protected: no permitido a este nivel.

## Efecto de modificadores de visibilidad a nivel de **clase e interface**

* public: visible para cualquier cliente que ve la clase.
* internal: visible para cualquier cliente **dentro del módulo** que ve la clase.
* private: visible dentro de la clase.
* protected: private + visible para las subclases

>:ru: **Referencia oficial:** https://kotlinlang.org/docs/reference/visibility-modifiers.html