En la línea 'force.div(10);' se está haciendo paso por referencia, pues 'force' es un objeto complejo (un vector), por lo que su valor está siendo modificado en el
código en general, no solo en el ámbito local de la función applyForce(). La solución a este problema es crear una copia de 'force', modificar la copia y aplicarla
a la aceleración. Así 'force' (sea cual sea) no cambia su valor en todo el código.
