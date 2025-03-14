## [Enlace de la simulación](https://editor.p5js.org/natureofcode/sketches/CQ19Yw0iT)

```js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

let angleOffset = 9; // Desplazamiento de la onda
let angleVelocity = 0.2;
let amplitude = 120;

function setup() {
  createCanvas(640, 240);
}

function draw() {
  background(255);
  stroke(0);
  strokeWeight(2);
  fill(127, 127);

  let angle = angleOffset; // Usamos un ángulo base que cambia con el tiempo

  for (let x = 0; x <= width; x += 24) {
    let y = amplitude * sin(angle);
    circle(x, y + height / 2, 48);
    angle += angleVelocity; // Incremento del ángulo para formar la onda
  }

  angleOffset += 0.05; 
}

```
