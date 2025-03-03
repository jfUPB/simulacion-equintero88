### ¿En qué consiste motion 101?

Motion 101 es un modelo de movimiento en el que un objeto tiene una posición (la posición es un vector) y mediante otro vector, que en el caso de la explicación
es la velocidad, se determinará como se moverá el objeto mediante la suma de vectores: sumándole a la posición la velocidad. Si se quieren movimientos más dinámicos
a la velocidad se le puede añadir, por ejemplo, el vector de aceleración.

### Ejemplo ilustrado

```js
let mover;
let mover2;

function setup() {
  createCanvas(640, 240);
  mover = new Mover();
  mover2 = new Mover2();
}

function draw() {
  background(255);

  mover.update();
  mover2.update();
  mover2.checkEdges();
  mover.show();
  mover2.show();
}



class Mover {
  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.velocity = createVector();
    this.acceleration = createVector();
    this.topspeed = 5;
  }

  update() {

    let mouse = createVector(mouseX, mouseY);
    // Step 1: Compute direction
    let dir = p5.Vector.sub(mover2.position, this.position);

    // Step 2: Normalize
    dir.normalize();

    // Step 3: Scale
    dir.mult(0.2);
    
    // Steps 2 and 3 could be combined into:
    // dir.setMag(0.2);

    // Step 4: Accelerate
    this.acceleration = dir;

    this.velocity.add(this.acceleration);
    this.velocity.limit(this.topspeed);
    this.position.add(this.velocity);

  }

  show() {
    stroke(0);
    strokeWeight(2);
    fill(127);
    circle(this.position.x, this.position.y, 48);
  }
}



class Mover2{
  constructor(){
    this.position = createVector(width/2,height/2);
    this.velocity = createVector();
    this.acceleration = createVector();
    this.topSpeed = 5;
  }

  update() {
    // The random2D() function returns a unit vector pointing in a random direction.
    this.acceleration = p5.Vector.random2D();
    this.acceleration.mult(random(2));

    this.velocity.add(this.acceleration);
    this.velocity.limit(this.topSpeed);
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
    }
    else if (this.position.x < 0) {
      this.position.x = width;
    }

    if (this.position.y > height) {
      this.position.y = 0;
    }
    else if (this.position.y < 0) {
      this.position.y = height;
    }
  }

}
```
