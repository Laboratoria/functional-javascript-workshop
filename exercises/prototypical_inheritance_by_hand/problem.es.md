Vamos a implementar un programa análogo de la herencia prototípica de JavaScript a mano, para asegurarnos que entendemos exactamente cómo funciona la herencia prototípica

# Tarea

Implementar las funciones `New`, `Create` y `Lookup` para simular las funciones de JavaScript `new`, `Object.create` y las propiedades de búsqueda respectivamente.

A través de este ejercicio, debes evitar usar las funciones de herencia de JavaScript.  en vez de usar las funciones predeterminadas, debes usar tus propias  funciones _New_, _Create_ y _Lookup_ así como `__PROTO__` para representar el prototipo de la instancia, y `PROTOTYPE` para representar el prototipo del constructor.

Por ejemplo:

* New(Apple, 1,2,3) == new Apple(1,2,3)
* `obj.__PROTO__` == obj.__proto__ || Object.getPrototypeOf(obj)
* `Constructor.PROTOTYPE` == `Constructor.prototype`

## Parte 1: Lookup

`Lookup` simulará el comportamiento del mecanismo de búsqueda de propiedades de JavaScript, o _"Getters"_. Cuando se hace referencia a la propiedad de cualquier objeto en JavaScript, "subirá la cadena de prototipos" para encontrar la propiedad, si se encuentra, devolverá su valor, de lo contrario volverá `undefined`.

A la función `Lookup` se le pasará un objeto de contexto, y la propiedad _String_ que estamos buscando. Si la propiedad se encuentra en el contexto actual, se devuelve esa propiedad, de lo contrario verifique el prototipo del contexto, `__PROTO__`.

Si no se puede encontrar una propiedad en la cadena de prototipos del objeto, simplemente devuelve `undefined`.

```js

var cat = {
  color: 'black'
}

var kitten = {
  size: 'small'
}

var otherKitten = {
  size: 'small',
  color: 'grey'
}

kitten.__PROTO__ = cat
otherKitten.__PROTO__ = cat

Lookup(kitten, 'color')  // => 'black'
Lookup(otherKitten, 'color')  // => 'grey'

Lookup(kitten, 'wings')  // => undefined

// cambiar las propiedades en los prototipos debería
// afectar cualquier instancia que herede los prototipos de la misma.
cat.color = 'blue'

Lookup(kitten, 'color')  // => 'blue'

// las propiedades anuladas deberían funcionar
Lookup(otherKitten, 'color')  // => 'grey'

```
Nota al margen: en JavaScript, cuando se obtiene una propiedad usando _'get'_ (es decir, _lookup_), el motor sube a la cadena de prototipos para encontrar el valor, pero si se "establece" una propiedad ignora la cadena de prototipos y simplemente establece el valor en la propiedad del objeto actual. Podríamos haber implementado un _'Setter'_ como ejercicio, pero la realidad es que es bastante trivial:

```js

function Setter(context, property, value) {
  return context[property] = value
}

```

## Parte 2: Create

`Create` simulará el comportamiento de `Object.create`.

A `Create` se le pasará un objeto, usted debe retornar un nuevo objeto con su prototipo (`__PROTO__`) establecido en el objeto suministrado.

```js
fuction Cat() {

}

Cat.PROTOTYPE.speak = function() {
  return 'Miau!'
}

function Kitten() {
  Cat.apply(this, arguments)
}

Kitten.PROTOTYPE = Create(Cat.PROTOTYPE)

var kitten = New(Kitten)
Lookup(kitten, 'speak')() // => 'Miau!'

```

## Final: New

`New` simulará el comportamiento de la palabra clave `new` en JavaScript.

El primer argumento que se le pasará a `New` será el constructor de la función (por ejemplo un tipo _type_).  Los parámetros posteriores deben ser pasados a la función constructor cuando se crea el nuevo objeto.

`New` devolverá nuevos objetos utilizando la función de constructor suministrada.

```js

function Cat(color) {
  this.color = color
}

var blackCat = New(Cat, 'black')
blackCat.color // => black

var brownCat = New(Cat, 'brown')
brownCat.color // => brown

```
La función constructor pasada a `New` puede tener una propiedad `.PROTOTYPE`. Todos los objetos creados con este constructor tendrán su `__PROTO__` establecido por defecto en la propiedad `.PROTOTYPE` del constructor.

```js

function Cat(color) {
  this.color = color
}

Cat.PROTOTYPE.speak = function() {
  return 'Meow!'
}

function Kitten() {
  Cat.apply(this, arguments)
}

Kitten.PROTOTYPE = Create(Cat)

Kitten.PROTOTYPE.speak = function() {
  return 'Mew.'
}

var blackCat = New(Cat, 'black')
blackCat.color // => black

var brownCat = New(Cat, 'brown')
brownCat.color // => brown

```

Las propiedades del prototipo deben estar disponibles en el constructor:

```js
function Cow() {
  // _lookup this.moo:_
  console.log('moo', Lookup(this, 'moo'));
}

// este paso está listo automaticamente hecho en 'verdadero' javascript.
Cow.PROTOTYPE = {}

Cow.PROTOTYPE.moo = true
var cow = New(Cow) // 'moo' verdadero

```

También necesitamos simular otro comportamiento de la palabra clave `new`: Si el propio constructor devuelve un valor,` New` devolverá ese mismo valor.

```js

function Cat(){
  return 3
}
var cat = new Cat() // 3
var cat = New(Cat) // 3

```

## Condiciones

* No utilice ninguna de las funcionalidades de herencia prototipal que incluye JavaScript.
* No haga llamadas a `new`
* No utilice `__proto__`, `Object.getPrototypeOf` o `Object.setPrototypeOf`

## Pistas

* Use `hasOwnProperty` para descubrir si el objeto tiene alguna propiedad.


## Plantilla

```js

/**
 * @param context {Object} Objeto inicial para comenzar a buscar propiedad `property`
 * @param property {String} nombre de la propiedad que está tratando de encontrar.
 * @return {Mixed} El valor de la propiedad `property` en el contexto `context` o en alguna parte de la cadena de prototipo.
 */

function Lookup(context, property) {

}

/**
 * @param proto {Object} El prototipo a usar para el objecto creado.
 * @return Un nuevo objeto cuyo prototipo está puesto como `proto`
 */

function Create(proto) {

}

/**
 * @param Constructor {Function} Constructor para un nuevo tipo.
 * @return nueva instancia del tipo definido por `Constructor`.
 */

function New(Constructor) {

}

module.exports = {
  Lookup: Lookup,
  Create: Create,
  New: New
}

```
