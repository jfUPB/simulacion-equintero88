# ¿Qué pasa si hago que la posición sea una variable aleatoria que se actualiza con draw()?

### ¿Qué te imaginas que pasará? ¿Qué pasó?

Pensé que, evidentemente, la bola iba a estar cambiando su trayectoria y velocidad de manera abrupta, y esto fue lo que pasó. En un principio la bola se mantenía muy estática,
aunque con un movimiento parecido a una vibración. Me di cuenta que esto sucedía porque el rango de generación de números aleatorios era muy pequeño. Comencé a ampliar este rango
y pude identificar que los movimientos eran cada vez más abruptos, y que se podía identificar con mayor facilidad cuando el número aleatorio generado era uno pequeño, pues
los saltos eran mucho mayores.

```js
let mover;

function setup() {
  createCanvas(640, 240);
  // Create the Mover object.
  mover = new Mover();
}

function draw() {
  background(255);
  // Call methods on the Mover object.
  mover.update();
  mover.velocity.x = (random(-50,50));
  mover.velocity.y = (random(-50,50));
  mover.checkEdges();
  mover.show();
}

class Mover {
  constructor() {
    // The object has two vectors: position and velocity.
    this.position = createVector(random(width), random(height));
    this.velocity = createVector(random(-10, 10), random(-10, 10));
  }

  update() {
    // Motion 101: position changes by velocity.
    this.position.add(this.velocity);
  }

  show() {
    stroke(0);
    strokeWeight(2);
    fill(127);
    circle(this.position.x, this.position.y, 48);
  }

  checkEdges() {
    if (this.position.x > width) {
      this.position.x = 0;
    } else if (this.position.x < 0) {
      this.position.x = width;
    }

    if (this.position.y > height) {
      this.position.y = 0;
    } else if (this.position.y < 0) {
      this.position.y = height;
    }
  }
}
```
