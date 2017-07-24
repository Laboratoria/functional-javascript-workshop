# Tarea

Hacer exactamente la misma tarea que en "Basic Inheritance with Object.create", con la condición de no usar Object.create.

Los detalles están copiados debajo de estas líneas para su referencia.

## Condiciones

* ¡No hacer llamadas al constructor User sin necesidad!
* No usar `Object.create`.
* No usar `__proto__`

## Pistas

* Los prototipos son siempre objetos.
* Tu instancia `BetterUser` necesita 'heredar' desde `User.prototype`
* No hay razón para no crear objetos ficticios en el árbol de herencias
* Debe entender lo que hace `Object.create` does.

## Recursos

* http://www.bennadel.com/blog/2184-Object-create-Improves-Constructor-Based-Inheritance-In-Javascript-It-Doesn-t-Replace-It.htm

## Definición de la tarea anterior

Crear un "BetterUser" que extienda "User" reemplazando el método `.toString`.

Su función exportada será  pasada de la función constructor para un tipo "User" que se parece a esto:

```js


/**
 * Usuario Constructor.
 *
 * @param title {String} Título del usuario, por ejemplo 'Sr.', 'Sra.', 'Dr.', etc.
 * @param name {String} Nombre del usuario, por ejemplo 'Juan Ramos'.*
 *
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
  return '[User: '+this.displayName()+']'
}
```

Nota: no necesitas copiar esto en tu solución.

## Ejemplo

Desde tu función exportada, retorna una función constructor `BetterUser` que extienda `User` con un método personalizado `toString` que funcione de la siguiente manera:

```js
var joe = new BetterUser('Sr.', 'Juan Ramos') // pasar el título y nombre
console.log('Hola ' + joe) // 'Hola [BetterUser: Sr. Juan Ramos]'
```

## Plantilla

```js

// User es un constructor
function upgradeUser(User) {

  // EDITAR ESTO COMO SEA NECESARIO
  function BetterUser() {

  }

  return BetterUser
}

module.exports = upgradeuser
```
