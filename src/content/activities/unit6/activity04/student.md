## Concepto

Pensé en la posibilidad de crear un FlowField que no interviniera en todo el canvas, sino en partes específicas de este, las que el usuario quisiera. Pienso que la 
forma más convencional de crear un FlowField sería teniendo en cuenta todo el canvas, ya con la posibilidad de crear ciertas variaciones, zonas de mayor o menor acción.
Pero creo que el pensarlo como un elemento que puede funcionar solo para ciertas partes en específico puede abrir un mundo de posibilidades. Lo que quise hacer era un
efecto simple, modificar una imagen con un FlowField en un área en específico. La interacción, es decir, el área en específico, se crea arrastrando el mouse.

## Del concepto a la implementación

Pensando el FlowField como un campo que define la influencia (dirección, magnitud) de ciertos puntos en un espacio, en la simulación que pensé este campo de influencia
se crea a partir de arrastrar el mouse de un lugar de la pantalla a otro. Tengo que hacer la claridad de que creé dos simulaciones. Una, en la que desde la posición 
inicial en la que se arrastra el mouse (StartX y StartY) a la posición final (EndX, EndY) se traza una línea recta y en la otra se rastrea la trayectoria completa, 
incluso si hay curvas. En las dos, la forma de hacer la distorsión en la imagen es similar, y es que se crea una función que calcula los píxeles de la imagen, qué cerca
están de esta trayectoria (las dos). Mientras más cerca estén de la línea, más distorsión habrá, y hay un punto una distancia máxima en que ya no hay influencia.

Cabe recalcar que en la primera simulación puede evidenciarse el funcionamiento, aunque con un rendimiento muy pobre. La segunda simulación es mucho más costosa en 
términos computacionales y casi que ni se puede percibir ningún efecto. Es más costosa porque la región de influencia es mucho más grande, por lo que para más puntos se
hace el cálculo de la distancia respecto a los pixeles.

### [Primera simulación](https://editor.p5js.org/equintero88/sketches/3gC5Ep6mX)
### [Segunda simulación](https://editor.p5js.org/equintero88/sketches/6pR5YbST8n)
