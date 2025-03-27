### ¿Cómo se gestiona la memoria?
En el método run() del emisor se recorre el array de partículas en orden inverso. Para cada partícula se llama a su método run(), y luego se verifica con isDead() si la partícula ha agotado su tiempo de vida (por ejemplo, cuando su propiedad lifespan es menor que 0). Si una partícula ha "muerto", se elimina del array con splice().

Al eliminar una partícula del array, se pierde la única referencia directa a ella. JavaScript cuenta con un garbage collector que se encarga de liberar la memoria de los objetos qua no están referenciados, por lo que, al remover la partícula, se libera la memoria asociada.

---

### Primera simulación
![image](https://github.com/user-attachments/assets/ee00fddc-88dd-4ff4-a310-8f9c4affa8ca)

Para este primer array de partículas apliqué dos conceptos anteriores: fuerzas y aleatoriedad. Apliqué una fueraz de viento para desviar la dirección de las partículas
y la gestión de la vida de las partículas la cambié. Pasé de una en orden de aparición a determinar el ciclo de vida de cada partícula con una distribución 
gaussiana.

---

### Segunda [simulación](https://editor.p5js.org/equintero88/sketches/6T4QJtIpz)
![image](https://github.com/user-attachments/assets/98e001d4-48d0-48dd-97a6-459c7b6a9849)

Agregué de nuevo una fuerza viento que se controla bajo otro concepto de aleatoriedad. También gestioné la vida de las partículas, pero esta vez no de las partículas individualmente sino del emitter en general

--- 

### Tercera [simulación](https://editor.p5js.org/equintero88/sketches/B4YzPzWZQ)

![image](https://github.com/user-attachments/assets/7edc0902-f841-4fd5-9a8b-ef296b8fc8a2)

Para esta simulación volví al concepto de aceleración y modifiqué las partículas "Confeti" para que tuviera más o menos aceleración, y según esto, caerían y rebotarían con mayor o menor intensidad.

### Cuarta [simulación](https://editor.p5js.org/equintero88/sketches/ty6LrlFmw)

![image](https://github.com/user-attachments/assets/4384a704-311e-4f0c-8b33-e7d24c088f0d)

Para este cuarto modelo implementé el modelo del doble péndulo para generar comportamientos impredecibles y abruptos, además de otro "emitter".
