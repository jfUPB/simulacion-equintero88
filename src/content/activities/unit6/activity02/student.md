### Explica brevemente la estructura de datos usada para el campo de flujo y cómo se generan sus vectores.

Para crear el campo de flujo se utilizan dos elementos claves: la resolución, que dice cada cuántos pixeles se genera un nuevo vector. El otro, es el tamaño de la
ventana, según el cual se generarán las columnas y filas correspondientes. Una vez resueltos estos elementos y creado el campo, los vectores que llenan la malla
se generan recorriendo cada fila y columna y en este ejemplo se crean a partir de una variación tipo Perlin Noise:

```js
for (let i = 0; i < this.cols; i++) {
      let yoff = 0;
      for (let j = 0; j < this.rows; j++) {
        //{.code-wide} In this example, use Perlin noise to create the vectors.
        let angle = map(noise(xoff, yoff), 0, 1, 0, TWO_PI);
        this.field[i][j] = p5.Vector.fromAngle(angle);
        yoff += 0.1;
      }
      xoff += 0.1;
    }
```

### Describe con tus palabras cómo un agente utiliza el campo para calcular su fuerza de dirección.

El vehículo tiene en principio una posición aleatoria. Lo que hace el vehículo es leer el la dirección del vector en la que está parado y según esto define su 
dirección deseada y, a partir de eso, resta eso a su velocidad actual y tiene el _steering_, su dirección. Esta fuerza se limita con _maxForce_ y luego se suma a 
aceleración del vehicle.

### Lista los parámetros clave identificados.

- Resolution
- Rows y Cols
- Lookup()
- Follow()
- Desired
- Steer

### Describe la modificación que realizaste al código y explica detalladamente el efecto que tuvo en el movimiento y comportamiento colectivo de los agentes. Incluye una captura de pantalla o GIF si ilustra bien el cambio. Muestra el fragmento de código modificado.


Modifiqué el código para que las celdas fueran más distintas entre sí. Es decir, modifiqué la variación del Perlin Noise (xoff y yoff). También modifiqué el _steer_ que es el vector de dirección. Lo multipliqué para exagerar su efecto.

# [Link de la simulación](https://editor.p5js.org/natureofcode/full/egribz8WV)
