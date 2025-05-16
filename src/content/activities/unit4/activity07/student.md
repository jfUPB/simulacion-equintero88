### [Enlace a la simiulación](https://editor.p5js.org/equintero88/sketches/bA07joq2N)

```js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

class Oscillator {
  constructor() {
    this.angle = createVector();
    this.angleVelocity = createVector(random(-0.05, 0.05), random(-0.05, 0.05));
    this.amplitude = createVector(random(20, width / 2), random(20, height / 2));
    this.acceleration = createVector(0,0);
    this.wind = createVector(randomGaussian(5,0.5), randomGaussian(5,0.5));
  }

  update() {
    this.angle.add(this.angleVelocity);
    this.angleVelocity.add(this.acceleration);
    this.acceleration.add(this.wind);
    this.acceleration.mult(0);
  }

  show() {
    let x = sin(this.angle.x) * this.amplitude.x;
    let y = sin(this.angle.y) * this.amplitude.y;

    push();
    translate(width / 2, height / 2);
    stroke(0);
    strokeWeight(2);
    fill(127);
    line(0, 0, x, y);
    circle(x, y, 32);
    pop();
  }
}

```

Modifiqué la clase Oscillator y le agregué una fuerza _wind_, que actúa según una distribución Gaussiana.
