# Tarea

Escribe una función que permita el uso de `Array.prototype.slice` sin usar `slice.call` o `slice.apply` para invocarlo.

Normalmente deberías usar `slice` junto a `call` o `apply`:

```js
var slice = Array.prototype.slice

function() {
  var args = slice.call(arguments) // esto funciona
}
```

Queremos que esto funcione:

```js
var slice = yourFunction

function() {
  var args = slice(arguments) // esto funciona
}
```

## Ejemplo

Una función, `slice` que muestra el siguiente comportamiento:

```js
var nums = [1,2,3,4,5]

// tu función _slice_ debería emular el comportamiento regular
// de _slice_, exceptuando que toma un arreglo
// como primer argumento

slice(nums, 0, 2) // [1, 2]
slice(nums, 1, 2) // [2]

// comportamiento regular de _slice_ para comparar
nums.slice(0, 2) // [1, 2]
nums.slice(1, 2) // [2]
```

## Condiciones

* No usar ningún lazo for/while o Array#forEach.
* No usar la palabra clave `function` :D

## Pistas

* Es un programa de una sola línea o _one liner_.
* Cada función JavaScript hereda métodos tales como _call_, _apply_ y _bind_ del objeto `Function.prototype`.
* Function#call ejecuta el valor `this` cuando es invocado. Dentro de  `someFunction.call()`, el valor `this` será `someFunction`.
* Function.call es una función por sí misma y hereda de `Function.prototype`.

```js
function myFunction() {
  console.log('called my function')
}

Function.prototype.call.call(myFunction) // => "llamado a mi función"
```

## Plantilla

```js
module.exports = // ¡pon tu solución aquí!
```
