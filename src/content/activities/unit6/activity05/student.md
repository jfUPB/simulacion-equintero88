###  ¿Cuál dirías que es la diferencia principal en cómo Flow Fields y Flocking logran el movimiento coordinado o dirigido de los agentes? (piensa en dónde reside la “inteligencia” o las reglas: ¿En el entorno o en las interacciones entre agentes?)

Si bien ambos algoritmos logran un movimiento coordinado, hay unas diferencias claves en cómo está estructurado y cuál es el resultado final. En Flow Fields hay dos
reglas principales que se encargan de parametrizar el movimiento y coordinarlo. El primero es la malla (y las direcciones que tiene cada punto en esta) y el segundo
es la dirección deseada y el _steering _para cada vehículo que va a recorrer esta malla. Con esto último se determina qué tanto se van a desviar los vehículos del
campo que recorren y las direcciones que este tiene.

Con Flocking no es necesario crear un campo que le diga a los agentes por dónde tienen que andar, por dónde deberían. Lo que se hace es que se crea un grupo de objetos
que van a determinar su comportamiento según ciertos parámetros con respecto a esos otros objetos. Modificando esos parámetros, su comportamiento grupal será uno u otro.

### ¿Qué tipo de comportamiento colectivo o patrón visual crees que es más fácil o natural lograr con Flow Fields? ¿Y con Flocking? Da ejemplos.

Creo que es mucho más fácil simular sistemas más aleatorios con el Flocking, pues la variación de los parámetros puede generar resultados más distintos entre sí y con transiciones más marcadas. En cambio, Flow Fields puede ser más adecuado para movimientos continuos pero con direcciones determinadas, y trayectorias especialmente curvas.

- Flow Fields: Movimientos parecidos a huracanes, tornados, humo o viento
- Flocking: Para interacciones entre muchas partículas (comportamientos grupales). Por ejemplo simular grupos de insectos, aves, peces.

### ¿Cuáles podrían ser las ventajas o desventajas de usar uno u otro algoritmo para ciertos tipos de efectos visuales o simulaciones?

- **Flow Fields:** Se pueden lograr efectos interesantes solamente pensando en una forma ingeniosa de crear el campo de acción, además de que genera trayectorias que al recorrerse se ven muy fluidas y orgánicas. La desventaja es que las partículas no interactúan entre sí, sino que todo está guiado por el campo. 
- **Flocking:**  Una gran ventaja es que solo variando los pesos se pueden generar comportamientos realmente complejos, diferentes entre sí y visualmente muy interesantes. Pueden crearse combinaciones ingeniosas entre los boids, o entre diferentes grupos para crear simulaciones complejas, con poco. Una gran desventaja es que es muy costoso computacionalmente, especialmente como lo usamos, ejecutando todo desde la CPU.

### ¿Cómo te ayudaron estos dos ejemplos (Flow Fields y Flocking) a entender mejor el concepto de “agente autónomo”? ¿Qué características definen a un agente en estos sistemas?

Entiendo a el agente autónomo como un ente que percibe su entorno y a partir de este se comporta de cierta forma. Creo que la palabra "autónomo" puede generar confusión, pues el agente toma ciertas decisiones pero no es completamente autónomo, pues nosotros definimos qué preponderancia van a tener unos tipos de comportamientos u otros.

### ¿En qué momento observaste “comportamiento emergente” (complejidad o patrones no programados explícitamente) al trabajar con estos algoritmos?

Creo que esto se ve reflejado en todo momento cuando se simula con estos patrones. Como dije hace un momento, nosotros como diseñadores pensamos en cómo nos gustaría que funcionase, pero sin duda en todo momento, al trabajar con tantos objetos (o vectores en los FlowFields) no podemos tener control de todos ellos, y surgirán comportamientos que no esperábamos.
