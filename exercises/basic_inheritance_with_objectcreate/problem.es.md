# Tarea

Crear un nuevo tipo "BetterUser" que extienda "User" reemplazando el método `.toString` del usuario.

A la función exportada se le pasará la función constructor para un tipo "User" que se verá así:

```js
/**
 * Usuario Constructor.
 *
 * @param title {String} Título del usuario, por ejemplo 'Sr.', 'Sra.', 'Dr.', etc.
 * @param name {String} Nombre del usuario, por ejemplo 'Juan Ramos'.
 */

function User(title, name) {
  this.title = title
  this.name = name
  console.info('NEW USER: ' + this)
}

/**
 * Crea el nombre completo del usuario a ser mostrado.
 * @return {String} Nombre a mostrar
 */

User.prototype.displayName = function() {
  return this.title + ' ' + this.name
}

/**
 * @return {String} Nombre y título con formato
 */

User.prototype.toString = function() {
  return '[User:'+this.displayName()+']'
}
```
Nota: no necesitas copiar esto en tu solución.

## Ejemplo

Desde tu función exportada, retorna una función constructor `BetterUser` que extienda `User` con un método personalizado `toString` que funcione de la siguiente manera:

```js
var joe = new BetterUser('Sr.', 'Juan Ramos') // pasar el título y nombre
console.log('Hola ' + joe) // 'Hola [BetterUser: Sr. Juan Ramos]'
```

## Condiciones

* ¡No hacer llamadas al constructor User sin necesidad!
* No usar `__proto__`
* No crear funciones innecesarias como por ejemplo helpers.

## Recursos

* http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/
* http://tobyho.com/2011/11/11/js-object-inheritance/
* http://hughfdjackson.com/javascript/2012/01/05/prototypes:-the-short%28est-possible%29-story/

## Plantilla

```js
// User es un constructor
function upgradeUser(User) {

  // EDITAR ESTO COMO SEA NECESARIO
  function BetterUser() {

  }

  return BetterUser
}

module.exports = upgradeUser
```
