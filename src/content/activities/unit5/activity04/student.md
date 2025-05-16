## ¿Cómo se gestiona la creación y la desaparición de las partículas y cómo se gestiona la memoria?

En el método run() del emisor se recorre el array de partículas en orden inverso. Para cada partícula se llama a su método run(), y luego se verifica con isDead() si la partícula ha agotado su tiempo de vida (por ejemplo, cuando su propiedad lifespan es menor que 0). Si una partícula ha “muerto”, se elimina del array con splice().
El tiempo de vida de las partículas se reduce con cada iteración del código.

## Cómo se aplica el marco de movimiento motion 101 en los sistemas de partículas que analizaste en la actividad anterior?

Se recorre el array en el que están las partículas dentro del ciclo for se aplica el método applyForce() a cada una de estas.

## ¿Cómo se aplican fuerzas externas a los sistemas de partículas que trabajaste en la unidad? ¿Qué fuerzas se aplicaron y cómo están modeladas?

Con el mismo marco que expliqué anteriormente, solo que se aplica a cada partícula individualmente.

## ¿Cómo se aplicaste los conceptos de herencia y polimorfismo en los sistemas de partículas que trabajaste en la unidad?

De la clase Particle hereda RotatingParticle. Para cada uno de ellos se ejecuta un run() pero dibuja cosas diferenters.




