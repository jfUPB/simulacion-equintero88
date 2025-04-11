### Código
```js
// ========================================================
// VARIABLES GLOBALES
// ========================================================
let mover;          // Bola que sigue al mouse
let particles = []; // Array de partículas
let totalParticles = 150; 

// Parámetros para la rejilla de ondas
let xStep = 10;
let yStep = 20;
let gridCols, gridRows;
let waveGrid;             // Almacenará la activación extra para cada vértice
let activationThreshold = 150; // Distancia máxima para activar la onda
let bumpMax = 60;         // Amplitud máxima que se puede sumar (aumentada para mayor intensidad)
let decayFactor = 0.95;   // Factor de decaimiento de la activación
let intensityFactor = 1.5; // Factor adicional para intensificar el efecto de la activación

// ========================================================
// FUNCIÓN SETUP
// ========================================================
function setup() {
  createCanvas(800, 600);
  mover = new Mover();

  // Inicializamos la rejilla para las ondas
  gridCols = Math.floor(width / xStep) + 1;
  gridRows = Math.floor(height / yStep) + 1;
  waveGrid = new Array(gridRows);
  for (let r = 0; r < gridRows; r++) {
    waveGrid[r] = new Array(gridCols).fill(0);
  }

  // Creamos las partículas
  for (let i = 0; i < totalParticles; i++) {
    let x = random(width);
    let y = random(height);
    particles.push(new Particle(x, y));
  }
}

// ========================================================
// FUNCIÓN DRAW
// ========================================================
function draw() {
  // Dibujamos el fondo con ondas que reaccionan a la bola
  drawWavyBackground(mover);

  // Actualizamos y mostramos la bola
  mover.update();
  mover.checkEdges();
  mover.show();

  // Actualizamos y mostramos las partículas
  for (let p of particles) {
    p.update(mover);
    p.checkEdges();
    p.show();
  }
}

// ========================================================
// FUNCIÓN PARA DIBUJAR EL FONDO ONDEANTE CON SOMBRA Y EFECTO RESIDUAL
// ========================================================
function drawWavyBackground(mover) {
  // Fondo amarillo oscuro
  background(200, 200, 50);

  push();
  strokeWeight(3);
  noFill();

  // Recorremos cada fila de la rejilla
  for (let r = 0; r < gridRows; r++) {
    let y = r * yStep;

    // Dibujo de la sombra de la línea
    push();
    stroke(0, 0, 0, 80); // sombra semi-transparente
    beginShape();
    for (let c = 0; c < gridCols; c++) {
      let x = c * xStep;

      // Calculamos la distancia del vértice a la bola
      let d = dist(x, y, mover.position.x, mover.position.y);
      // Si está dentro del umbral, activamos la onda en esa celda
      if (d < activationThreshold) {
        let bump = map(d, 0, activationThreshold, bumpMax, 0, true);
        // Usamos max() para mantener una activación alta reciente
        waveGrid[r][c] = max(waveGrid[r][c], bump);
      }
      // Decaimos la activación de la celda
      waveGrid[r][c] *= decayFactor;

      // Movimiento base mínimo en toda la rejilla
      let baseOffset = sin((x + frameCount * 0.5) * 0.02) * 5;
      // La activación acumulada modula la onda, ahora intensificada con intensityFactor
      let extraOffset = waveGrid[r][c] * intensityFactor * sin((x + frameCount * 2) * 0.02);

      let totalOffset = baseOffset + extraOffset;

      vertex(x + 4, y + totalOffset + 4); // Sombra: se desplaza 4 px
    }
    endShape();
    pop();

    // Ahora la línea principal
    push();
    stroke(160, 80, 0, 150); // color de la onda
    beginShape();
    for (let c = 0; c < gridCols; c++) {
      let x = c * xStep;
      
      let baseOffset = sin((x + frameCount * 0.5) * 0.02) * 5;
      let extraOffset = waveGrid[r][c] * intensityFactor * sin((x + frameCount * 2) * 0.02);
      let totalOffset = baseOffset + extraOffset;
      
      vertex(x, y + totalOffset);
    }
    endShape();
    pop();
  }
  pop();
}

// ========================================================
// CLASE MOVER 
// ========================================================
class Mover {
  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.velocity = createVector();
    this.acceleration = createVector();
    this.topspeed = 5;

    // Para la estela (trail)
    this.trail = [];
    this.maxTrailLength = 15;
  }

  update() {
    // La bola se dirige hacia el mouse
    let mouse = createVector(mouseX, mouseY);
    let dir = p5.Vector.sub(mouse, this.position);
    dir.setMag(0.2);
    this.acceleration = dir;

    this.velocity.add(this.acceleration);
    this.velocity.limit(this.topspeed);
    this.position.add(this.velocity);

    // Guardamos la posición para la estela
    this.trail.push(this.position.copy());
    if (this.trail.length > this.maxTrailLength) {
      this.trail.shift();
    }
  }

  checkEdges() {
    if (this.position.x > width) {
      this.position.x = width;
      this.velocity.x *= -1;
    } else if (this.position.x < 0) {
      this.position.x = 0;
      this.velocity.x *= -1;
    }

    if (this.position.y > height) {
      this.position.y = height;
      this.velocity.y *= -1;
    } else if (this.position.y < 0) {
      this.position.y = 0;
      this.velocity.y *= -1;
    }
  }

  show() {
    // Dibujamos la estela
    push();
    noStroke();
    for (let i = 0; i < this.trail.length; i++) {
      let pos = this.trail[i];
      let alpha = map(i, 0, this.trail.length, 80, 0);
      fill(0, alpha);
      circle(pos.x, pos.y, 60);
    }
    pop();

    // Bola principal (totalmente negra)
    push();
    noStroke();
    fill(0);
    circle(this.position.x, this.position.y, 60);
    pop();
  }
}

// ========================================================
// CLASE PARTICLE 
// ========================================================
class Particle {
  constructor(x, y) {
    this.position = createVector(x, y);
    this.velocity = p5.Vector.random2D(); 
    this.acceleration = createVector();
    this.maxSpeed = 3;

    // Todas serán moradas, pero con variación en tamaño y forma
    this.c = color(150, 0, 200, 180);
    // Tamaño base y factor para la altura de la elipse (varían entre partículas)
    this.baseSize = random(16, 24);
    this.shapeFactor = random(0.5, 1);
  }

  update(mover) {
    this.acceleration.set(0, 0);

    // Movimiento aleatorio
    let randomAcc = p5.Vector.random2D();
    randomAcc.mult(0.1);
    this.acceleration.add(randomAcc);

    // Fuerza de repulsión respecto a la bola
    let repelForce = p5.Vector.sub(this.position, mover.position);
    let distance = repelForce.mag();
    let repelRadius = 100;
    if (distance < repelRadius) {
      repelForce.setMag(1 - distance / repelRadius);
      this.acceleration.add(repelForce);
    }

    this.velocity.add(this.acceleration);
    this.velocity.limit(this.maxSpeed);
    this.position.add(this.velocity);
  }

  checkEdges() {
    if (this.position.x > width) {
      this.position.x = width;
      this.velocity.x *= -1;
    } else if (this.position.x < 0) {
      this.position.x = 0;
      this.velocity.x *= -1;
    }

    if (this.position.y > height) {
      this.position.y = height;
      this.velocity.y *= -1;
    } else if (this.position.y < 0) {
      this.position.y = 0;
      this.velocity.y *= -1;
    }
  }

  show() {
    push();
    translate(this.position.x, this.position.y);
    // Rotamos según la dirección de la velocidad
    let angle = this.velocity.heading();
    rotate(angle);

    let speedFactor = this.velocity.mag() * 8; // Deformación extra según la velocidad
    let w = this.baseSize + speedFactor;
    let h = this.baseSize * this.shapeFactor;

    // Dibujo de la sombra de la partícula
    push();
    translate(3, 3); // Desplazamiento para la sombra
    noStroke();
    fill(0, 80);
    ellipse(0, 0, w, h);
    pop();

    // Dibujo de la partícula (color morado)
    noStroke();
    fill(this.c);
    ellipse(0, 0, w, h);
    pop();
  }
}

```

### Captura
![image](https://github.com/user-attachments/assets/73c5c24f-3239-467a-b225-c07ea797cca3)
