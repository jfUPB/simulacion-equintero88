### ¿Para qué sirve el método mag()? Nota que hay otro método llamado magSq(). ¿Cuál es la diferencia entre ambos? ¿Cuál es más eficiente?

El método mag() devuelve la magnitud de un vector, utilizando el Teorema de Pitágoras. El método magSq solo suma el cuadrado de los componentes, pero no 
hace la operación de raiz cuadrada. El más eficiente es mag(), pues devuelve la magnitud real del vector, magSq() se puede usa para comparar longitudes entre vectores
sin tener que usar la operación de raiz cuadrada que es un poco costosa en términos de rendimiento.

### ¿Para qué sirve el método normalize()?

El método normaliza() sirve para volver el vector un vector unitario, pero respetando la dirección a la que apunta.

### ¿Para qué sirve el método dot()? ¿Qué le responderías en un frase?

El método dot() sirve para calcular el producto punto entre dos vectores.

Le pregunté a ChatGPT qué cosas pueden indicar los resultados del producto punto:
> ![image](https://github.com/user-attachments/assets/dec96ab6-e19e-42d4-af50-f804b69000cb)

### El método dot() tiene una versión estática y una de instancia. ¿Cuál es la diferencia entre ambas?

El método dot() de instancia se usa cuando ya hay unos objetos p5.Vector creados, y se llama desde el mismo objeto (v1.dot(v2);). El método estático se 
llama desde la clase p5.Vector y no necesita haber creado objetos p5.Vector.


### ¿Cuál es la interpretación geométrica del producto cruz de dos vectores? Tu respuesta debe incluir qué pasa con la orientación y la magnitud del vector resultante.

El producto cruz entre dos vectores da como resultado un nuevo vector que es perpendicular a los dos vectores originales, y su magnitud representa el área 
del paralelograma formado por los dos vectores. Esto representa lo siguiente
> - Si los vectores son paralelos, el área del paralelogramo es cero.
> -  Si forman un ángulo de 90°, el área es máxima.
> - Si están en un ángulo intermedio, el área depende de cuánto se separan los vectores.

> El producto cruz no solo nos da un nuevo vector, sino que su magnitud nos dice cuánto espacio ocupan los dos vectores juntos en el plano

### ¿Para que te puede servir el método dist()?

Para calcular la distancia que hay entre dos vectores.

### ¿Para qué sirven los métodos normalize() y limit()?

El método normaliza() sirve para volver el vector un vector unitario, pero respetando la dirección a la que apunta. El método limit() para limitar la 
magnitud de un vector a un valor determinado.
