# Comportamoent
## Separation()

Este comportamiento busca que los boids se mantengan alejados unos de los otros a partir de una distancia (que no se choquen). Para esto, el parámetro clave que se
usa es _desiredSeparation_, que se define en un valor, que representa qué tan alejado debe de estar un boid de otro. Si este umbral se pasa y un boid se acerca más, 
se activa la fuerza de separación.

## Align()

El objetivo del Align() es hacer que el boid se mueva en la misma dirección de los otros boids que están en una distancia determinada, que se define con 
_neighborDistance_ . Solo los boids que estén en ese rango, afectarán el comportamiento. Lo que hace entonces es chequear cuáles están dentro del boid y promediar la
velocidad de todos, para que cada boid adopte la dirección promedio su grupo cercano.

## Cohere()

Este último hace que el boid se acerque al centro de su grupo, de que no se aleje demasiado. En este método también se usa _neighborDistance_ pero en este caso se
promedian las posiciones y no las velocidades.

# Modificación - (Simulación)[https://editor.p5js.org/equintero88/full/nqF7zVEdk]

Puse que los boids siguieran al mouse, y cambié drásticamente el peso de separation (a 10), la de align (a 0) y el de cohere (a 8). 
Lo que pasa es que ahora los boids no se juntan y siempre están todos apuntanto a una misma dirección. Al subir también la cohesión, por ejemplo, y dejar el mouse quieto
los boids entran en un comportamiento caótico de movimiento rotacional.


