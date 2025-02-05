## ¿Cómo funciona la suma de dos vectores?

Si para la creación de vectores se usa el método nativo de p5 *createVector()* se puede usar el método, también ya incluido en p5.js, *add()*.
Lo único que hay que hacer es acceder a este método desde el vector al que le queremos añadir el otro. En el caso del ejemplo es: 

```js
position.add(velocity);
```
Lo que hace *add()* es acceder a position y velocity, que tienen almacenadas las direcciones de memoria de los vectores.

## ¿Por qué esta línea position = position + velocity; no funciona?

Yo suponía que no funcionaba porque no se estaba accediendo a los componentes internos de cada objeto, pero le pregunté a ChatGPT y esta fue su respuesta:

>La razón por la que position = position + velocity; no funciona en p5.js (ni en JavaScript en general para objetos) es porque los objetos en JavaScript no soportan operaciones aritméticas directas. JavaScript intenta convertir los objetos a strings antes de sumarlos, lo que da un resultado inesperado.
