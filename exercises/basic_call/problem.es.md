JavaScript implementa un estilo de comprobación de tipos dinámico llamado "duck
typing". En este estilo, los métodos y propiedades de un objeto determinan la
semántica, en vez de usar herencia de una clase o la implementación de una
interfaz. El nombre de este concepto hace referencia a la "prueba del pato",
atribuida a James Whitcomb Riley, y que puede ser articulada así:

> "Cuando veo un pájaro que camina como un pato y nada como un pato y grazna
como un pato, a ese pájaro le llamo pato."

En JavaScript, para poder escribir programas robustos a veces tenemos que
comprobar que un objeto tenga las propiedades o métodos que esperamos.

Usamos `Object#hasOwnProperty` para detectar si un objeto tiene una propiedad
definida directamente sobre sí mismo (y no heredada de su prototipo):

```js
var duck = {
  quack: function() {
    console.log('quack')
  }
}

duck.hasOwnProperty('quack') // => true
```

Nosotros no le dimos un método `.hasOwnProperty` a `duck`, de dónde vino?

El objeto `duck` fue creado con un objeto "literal" usando la sintáxis `{}`, por
lo tanto hereda de `Object.prototype`.


```js
var object = {quack: true}

Object.getPrototypeOf(object) === Object.prototype // => true
object.hasOwnProperty('quack')                     // => true
```

Pero... y su un objeto no hereda de `Object.prototype`?

```js
// crea un objeto con 'null' como prototipo.
var object = Object.create(null)
object.quack = function() {
  console.log('quack')
}

Object.getPrototypeOf(object) === Object.prototype // => false
Object.getPrototypeOf(object) === null             // => true

object.hasOwnProperty('quack')
// => TypeError: Object object has no method 'hasOwnProperty'
```

Sin embargo, todavía podemos usar `hasOwnProperty` directamente de
`Object.prototype`, si la invocamos con el valor de `this` asignado a algo "que
parezca un objeto". `Function#call` nos permite invocar una función y
manualmente asignar el valor de `this`.

```js
// el primer argumento a `call` se convierte en el valor de `this`
// el resto de los argumentos se pasan a la función que estamos llamando

Object.prototype.hasOwnProperty.call(object, 'quack') // => true
```

# Tarea

Escribe una función `duckCount` que retorne el número de argumentos que le han
pasado que tengan una propiedad `quack` definida directamente sobre ellos.
Ignora propiedades heredadas a través de prototipos.

Ejemplo:

```js
var notDuck = Object.create({quack: true})
var duck = {quack: true}
duckCount(duck, notDuck) // 1
```

## Argumentos

* La función recibirá entre 0 y 20 argumentos. Los argumentos pueden ser
  cualquier tipo. Algunos de los argumentos tendrán una propiedad `quack`.

## Requisitos

* No uses ningún bucle `for/while` o `Array.prototype.forEach`.
* No crees variables para contadores ni acumuladores.
* No crees ninguna función extra (helpers, ...).

## Pistas

* La variable `argumentos`, disponible dentro de toda `function`, es un *Object*
  que camina como un *Array*, y nada como un *Array*, ...

```js
{
  0: 'argument0',
  1: 'argument1', // etc
  length: 2
}
```

## Recursos

* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/in
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice#Array-like
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/arguments

## Boilerplate

```js
function duckCount() {
  // TU SOLUCIÓN AQUÍ
}

module.exports = duckCount
```
