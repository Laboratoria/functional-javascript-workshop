# Tarea

Sobreescribe un método específico de un objeto con nueva funcionalidad pero
manteniendo el comportamiento anterior.

Crea una función espía que vaya contando cuántas veces se invoca una función.

## Ejemplo

```js
var spy = Spy(console, 'error')

console.error('calling console.error')
console.error('calling console.error')
console.error('calling console.error')

console.log(spy.count) // 3
```

## Argumentos

* target: un objeto con un método llamado `method`
* method: un string con el nombre del método de `target` que espiar.

## Requisitos

* No uses ningún bucle `for/while` o `Array.prototype.forEach`.
* No crees ninguna función extra (helpers, ...).

## Pistas

* Las funciones tienen contexto, input y output. Asegúrate de considerar el
  context, input a *y output de* la función que estás espiando.

## Boilerplate

```js
function Spy(target, method) {
  // TU SOLUCIÓN AQUÍ
}

module.exports = Spy
```
