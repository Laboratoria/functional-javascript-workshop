# Tarea


Modificar la función recursiva `repeat` mostrada en la plantilla, editarla de manera tal que no bloquee el blucle del evento (por ejemplo los temporizadores y manejadores de entrada/salida se pueden disparar).  Esto requiere que la repectición sea asíncrona.

Un temporizador se pone en cola para ser activado después de 100 milisegundos, este imprimirá los resultados de la prueba y saldrá del proceso. La función `repeat` debería liberar el control del lazo del evento para permitir que el temporizador se interrumpa antes que todas las operaciones sean completadas.

Intenta jecutar tantas operaciones como sea posible, ¡ antes que el temporizador se dispare!

## Condiciones

* No usar lazos _for/while_ o _Array#forEach_.
* No crear funciones innecesarias como por ejemplo _helpers_.

## Pistas

* Si tu programa está tardando mucho tiempo en ejecutarse, probablemente algo está mal.

  Usa Control - C para terminar el proceso.

## Recursos

* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Timers

## Plantilla

```js
function repeat(operation, num) {
  // modificar esto para que pueda ser interrumpido
  if (num <= 0) return
  operation()
  return repeat(operation, --num)
}

module.exports = repeat
```
