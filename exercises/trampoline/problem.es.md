La plantilla incluye una definición de `repeat`. `repeat` tomará una operación de la función y una variable *num* de tipo número _Number_ e invocará la operación *num* veces:

```js
var count = 0
repeat(function() {
  count++
}, 100)

console.log('executed %d times.', count)
// => ejecutado 100 veces.
```

PERO hay que notar que ejecutar `repeat` con un número grande `num` causa un desbordamiento en la pila de almacenamiento o como se le llama en inglés _stack overflow_:

```
var count = 0
repeat(function() {
  count++
}, 100000)

console.log('executed %d times', count)
// => RangeError: Se excedió el número máximo de llamadas a la pila

```

# Tarea

Modifique la plantilla colocada en la parte de abajo de tal manera que use un trampolín para llamarse a sí misma continuamente de forma sincrónica.

Puedes suponer que la operación que se pase para repetir no toma argumentos (o ya están enlazados a la función) y el valor que devuelva no es importante.

## Condiciones

* No cambies la implementación de _repeat_ para incluir alguna estructura de control
(Puedes cambiarlo de otras maneras).

## Pistas

* Modifica `repeat` para que devuelva el 'paso siguiente', si lo hay.
* Un trampolín sigue ejecutando pasos de forma síncrona, obteniendo nuevos pasos, hasta que no haya más pasos. ¡Aquí puedes usar un bucle!
* Si tu programa tarda mucho tiempo en ejecutarse, probablemente algo esté incorrecto. Utilice Control-C para matar el proceso del nodo.

## Plantilla

```js
function repeat(operation, num) {
  // Modificar esto para que no cause desbordamiento en la pila o como se le llama en inglés _stack overflow_
  if (num <= 0) return
  operation()
  return repeat(operation, --num)
}

function trampoline(fn) {
  // ¡Probablemente quieras implementar un trampolín!
}

module.exports = function(operation, num) {
  // ¡Probablemente quieras hacer un llamado a tu trampolín!
  return repeat(operation, num)
}
```
