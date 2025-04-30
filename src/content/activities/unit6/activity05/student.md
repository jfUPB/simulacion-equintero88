###  ¿Cuál dirías que es la diferencia principal en cómo Flow Fields y Flocking logran el movimiento coordinado o dirigido de los agentes? (piensa en dónde reside la “inteligencia” o las reglas: ¿En el entorno o en las interacciones entre agentes?)

Si bien ambos algoritmos logran un movimiento coordinado, hay unas diferencias claves en cómo está estructurado y cuál es el resultado final. En Flow Fields hay dos
reglas principales que se encargan de parametrizar el movimiento y coordinarlo. El primero es la malla (y las direcciones que tiene cada punto en esta) y el segundo
es la dirección deseada y el _steering _para cada vehículo que va a recorrer esta malla. Con esto último se determina qué tanto se van a desviar los vehículos del
campo que recorren y las direcciones que este tiene.

Con Flocking no es necesario crear un campo que le diga a los agentes por dónde tienen que andar, por dónde deberían. Lo que se hace es que se crea un grupo de objetos
que van a determinar su comportamiento según ciertos parámetros con respecto a esos otros objetos. Modificando esos parámetros, su comportamiento grupal será uno u otro.

### ¿Qué tipo de comportamiento colectivo o patrón visual crees que es más fácil o natural lograr con Flow Fields? ¿Y con Flocking? Da ejemplos.
