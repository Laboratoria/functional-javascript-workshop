# Tarea

Dado un arreglo de strings, usa `Array#reduce` para crear un objeto que contenga
el número de veces que ocurre cada string en el arreglo. Retorna el objeto
directamente, no hay necesidad de usar `console.log`.

## Ejemplo

```js
var inputWords = ['Apple', 'Banana', 'Apple', 'Durian', 'Durian', 'Durian']

console.log(countWords(inputWords))

// =>
// {
//   Apple: 2,
//   Banana: 1,
//   Durian: 3
// }
```

## Argumentos

* inputWords: Un Array de Strings.

## Requisitos

* No uses bucles `for/while` ni `Array#forEach`.
* No crees ninguna función adicional (helpers).

## Resources

* https://en.wikipedia.org/wiki/Reduce_(higher-order_function)
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce

## Boilerplate

```js
function countWords(inputWords) {
  // TU SOLUCIÓN AQUÍ
}

module.exports = countWords
```
