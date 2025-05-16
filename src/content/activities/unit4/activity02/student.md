## Primera simulación

En esta simulación se dibujaron unos objetos en el canvas y cada vez que se presiona una tecla el sistema de coordenadas (que fue ubicado en el centro del canvas) 
rota, por lo que rotan también todos los objetos dibujados. Si el eje de coordenadas no se definiera en cada frame en el centro del canvas los objetos rotarían
en el eje de coordenadas original, que es el extremo superior izquierdo del canvas. La función rotate lo que hace es rotar todo el sistema de coordenadas.
Los elementos se dibujan en 0,0 y siguen rotando porque en cada frame el sistema de coordenadas ha rotado tambipen, por lo que en teoría, ese sería el nuevo 0,0.

## Segunda simulación

El motion 101 se aplica dándole al objeto en pantalla una aceleración según el mouse.

1. El método heading() devuelve el ángulo de un vector respecto al eje x del canvas, es decir, hacia qué dirección apunta el objeto.
2. push() y pop() se usan para manejar el stack, en el que se están almacenando las transformaciones del objeto.
3. rectMode(CENTER) hace que el rectángulo se dibuje desde su centro. Esto permite que el rectángulo, al rotar, gire desde su centro y no desde una esquina.
4. La rotación del rectángulo sigue la dirección del vector de velocidad.
