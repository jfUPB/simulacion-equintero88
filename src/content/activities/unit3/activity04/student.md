### En la unidad anterior tu definías la aceleración mediante algún algoritmo. ¿Cuáles eran?

En la unidad anterior etníamos la posibilidad de definir la aceleración de tres formas distintas: aceleración constante, aceleración aleatoria y aceleración con el mouse. 
Aquí el ejemplo de la defnición de la aceleración en alguno de los ejercicios de la unidad anterior:

```js
this.acceleration = createVector();
let randomAcc = p5.Vector.random2D();
this.acceleration.add(randomAcc);
```

### En esta unidad tu vas a calcular la aceleración. ¿Qué tiene que ver esto con las leyes de movimiento de Newton?

La segunda ley de Newton (como lo dicen en el capítulo del libro) se define de la siguiente manera:

> Force equals mass times acceleration.

Allí la reescriben como: A = F * M. Entonces vamos a calcular la aceleración a partir de todas las fuerzas que pensemos añadir para nuestros sistemas simulados.
