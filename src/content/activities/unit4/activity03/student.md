 ```js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

class Vehicle {
  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.topspeed = 4;
  }

  update() {
    if (keyIsDown(RIGHT_ARROW)) {
      this.acceleration.add(0.1, 0);
    }
    if (keyIsDown(LEFT_ARROW)) {
      this.acceleration.add(-0.1, 0);
    }
    
    this.velocity.add(this.acceleration);
    this.velocity.limit(this.topspeed);
    this.position.add(this.velocity);
    

    this.acceleration.mult(0);
  }

  display() {
    let angle = this.velocity.heading();
    
    push();
    translate(this.position.x, this.position.y);
    rotate(angle);
    fill(127);
    stroke(0);
    strokeWeight(2);
    beginShape();
    vertex(15, 0);
    vertex(-15, -10);
    vertex(-15, 10);
    endShape(CLOSE);
    
    pop();
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

let car;

function setup() {
  createCanvas(640, 240);
  car = new Vehicle();
}

function draw() {
  background(255);
  car.update();
  car.checkEdges();
  car.display();
}
```
![image](https://github.com/user-attachments/assets/519c6525-b992-464b-97ed-d772f710569f)
![image](https://github.com/user-attachments/assets/5af0f831-14e5-4abe-81be-2b8edbf70488)


