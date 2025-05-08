## Explicación

Escogí la palabra "CALOR". El comportamiento que le otorgué fue el de algo que se está derritiendo. La palabra se derrite de abajo hacia arriba. La animación se puede
asociar fácilmente a una consecuencia del significado de la palabra (que haga calor). Las gotas se relacionan directamente con algo que se está derritiendo como un
helado, o con gotas de sudor.

## Aspectos técnicos

Se crea una palabra y con textToPoints se crean puntos. A cada punto se le asigna un Bodies.rectangle, y se almacenan en un arreglo. La palabra en primer lugar está 
estática (todos los elementos). Cuando se presiona click se vuelven objetos dinámicos, y se eliminan de abajo hacia arriba. Tienen efecto restitution para generar
elasticidad y se usa la gravedad por defecto para que caigan.

Se usan restricciones para el efecto de estiramiento. Cada bloque dinámicocuelga con un resorte corto (length:10, stiffness:0.002) que se rompe cuando se estira >30 px.

## Link [simulación](https://editor.p5js.org/equintero88/sketches/2U3eY1VY3)

![ScreenRecording2025-05-08132444-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/6732654d-e748-4bb2-8642-2e2267f3430f)
