### Iamgen del resultado

![image](https://github.com/user-attachments/assets/a40757b3-0ca9-4143-818a-916790176e5f)

### Código

Solo modifiqué esta línea: **let phase = 0.2;** por lo que el círculo empezó un poco más a la derecha, yu puede verse la diferencia con el gris, que empieza en fase 0.


### Código de la aplicación  e imagen
```js
let amplitudeSlider, periodSlider, phaseSlider;
let amplitude = 100;
let period = 200;
let phase = 0;
let time = 0;

function setup() {
  createCanvas(600, 300);
  
  // Crear sliders
  amplitudeSlider = createSlider(10, 150, amplitude);
  amplitudeSlider.position(10, height + 10);
  
  periodSlider = createSlider(50, 400, period);
  periodSlider.position(10, height + 40);
  
  phaseSlider = createSlider(0, TWO_PI, phase, 0.1);
  phaseSlider.position(10, height + 70);
}

function draw() {
  background(255);
  
  amplitude = amplitudeSlider.value();
  period = periodSlider.value();
  phase = phaseSlider.value();
  
  let frequency = TWO_PI / period;
  time += 0.05; // Hace que la onda se mueva con el tiempo
  
  stroke(0);
  noFill();
  beginShape();
  for (let x = 0; x < width; x++) {
    let y = height / 2 + amplitude * sin(frequency * x + phase + time);
    vertex(x, y);
  }
  endShape();
}
```
![image](https://github.com/user-attachments/assets/6ae6fea5-8a76-43e2-99d6-60291463d72a)
