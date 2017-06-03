# Tarea

Retorna una función que reciba una lista de usuarios válidos, y retorne una
función que retorne `true` si todos los usuarios que le pasen existen en la
lista original de usuarios.

Sólo necesitas comprobar que los ids coincidan.

## Ejemplo

```js
var goodUsers = [
  { id: 1 },
  { id: 2 },
  { id: 3 }
]

// `checkUsersValid` es una función que tú implementarás
var testAllValid = checkUsersValid(goodUsers)

testAllValid([
  { id: 2 },
  { id: 1 }
])
// => true

testAllValid([
  { id: 2 },
  { id: 4 },
  { id: 1 }
])
// => false
```

## Argumentos

* goodUsers: una lista de usuarios válidos

Usa `Array#some` y `Array#every` para comprobar cada usuario pasado a la función
que retornes existe en el array pasado a la función exportada.

## Requisitos

* No uses bucles `for/while` ni `Array#forEach`.
* No crees ninguna función adicional (helpers).

## Recursos

* https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/every
* https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/some

## Boilerplate

```js
function checkUsersValid(goodUsers) {
  return function allUsersValid(submittedUsers) {
    // TU SOLUCIÓN AQUÍ
  };
}

module.exports = checkUsersValid
```
