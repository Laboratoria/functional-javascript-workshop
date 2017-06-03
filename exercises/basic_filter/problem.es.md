# Tarea

Usa `Array#filter` para implementar una función llamada `getShortMessages`.

`getShortMessages` recibe un arreglo de objetos con una propiedad `.message` y
retorna un arreglo de `messages` que son de *menos de < 50 caracteres*.

La función debe retornar un array con los mensajes, *sin el objeto que los
contiene*.

## Argumentos

* messages: un Array de 10 a 100 objects con una estructura así:

```js
{
  message: 'Esse id amet quis eu esse aute officia ipsum.' // random
}
```

## Requisitos

* No uses `for/while` ni `Array#forEach`.
* No crees ninguna función adicional (helpers).

## Pistas

* Trata de "encadenar" (chain) algunos métodos de `Array`!

## Ejemplo

```js
[
  'Tempor quis esse consequat sunt ea eiusmod.',
  'Id culpa ad proident ad nulla laborum incididunt.',
  'Ullamco in ea et ad anim anim ullamco est.',
  'Est ut irure irure nisi.'
]
```

## Recursos

* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map

## Boilerplate

```js
function getShortMessages(messages) {
  // TU SOLUCIÓN AQUÍ
}

module.exports = getShortMessages
```
