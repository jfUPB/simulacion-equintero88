## Primera simulación

En esta simulación se dibujaron unos objetos en el canvas y cada vez que se presiona una tecla el sistema de coordenadas (que fue ubicado en el centro del canvas) 
rota, por lo que rotan también todos los objetos dibujados. Si el eje de coordenadas no se definiera en cada frame en el centro del canvas los objetos rotarían
en el eje de coordenadas original, que es el extremo superior izquierdo del canvas. La función rotate lo que hace es rotar todo el sistema de coordenadas.
Los elementos se dibujan en 0,0 y siguen rotando porque en cada frame el sistema de coordenadas ha rotado tambipen, por lo que en teoría, ese sería el nuevo 0,0.

## Segunda simulación

El motion 101 se aplica dándole al objeto en pantalla una aceleración según el mouse.

