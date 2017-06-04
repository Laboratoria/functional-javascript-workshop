# Tarea

Usa `Array#reduce` para implementar una versión simple de `Array#map`.

## Resultado esperado

Una función `map` que aplique una función a cada uno de los elementos de un
array y almacena el resultado en un nuevo array.

```js
var nums = [1,2,3,4,5]

// `map` is your exported function
var output = map(nums, function double(item) {
  return item * 2
})

console.log(output) // => [2,4,6,8,10]
```

## Argumentos

* input: un Array de elementos de cualquier tipo.
* operation: una Function que puede ser "aplicada" a los elementos de `input`.

## Pistas

* No hay necesidad de implementar el `thisArg` opcional de
`Array.prototype.map`, bonus si lo haces!

## Recursos

* https://en.wikipedia.org/wiki/Reduce_(higher-order_function)
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce

## Boilerplate

```js
function arrayMap(arr, fn) {
  // TU SOLUCIÓN AQUÍ
}

module.exports = arrayMap;
```
