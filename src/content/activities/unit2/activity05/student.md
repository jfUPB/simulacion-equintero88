### Código aplicación
```js
unction setup() {
    createCanvas(400, 400);
}

let vLerp = 0;
let direction = true;

function draw() {
    background(200);
    let c1 = color('magenta');
    let c2 = color('orange');
    let v0 = createVector(50, 50);
    let v1 = createVector(250, 50);
    let v2 = createVector(50, 250);
    let v3 = p5.Vector.lerp(v1, v2, varLerp(vLerp));
    let v4 = p5.Vector.sub(v2,v1);
    drawArrow(v0, v1, 'black');
    drawArrow(v0, v2, 'black');
    drawArrow(v0, v3, lerpColor(c1,c2, varLerp(vLerp)));
    drawArrow(v1.add(v0), v4, 'black');
}

function drawArrow(base, vec, myColor) {
    push();
    stroke(myColor);
    strokeWeight(3);
    fill(myColor);
    translate(base.x, base.y);
    line(0, 0, vec.x, vec.y);
    rotate(vec.heading());
    let arrowSize = 7;
    translate(vec.mag() - arrowSize, 0);
    triangle(0, arrowSize / 2, 0, -arrowSize / 2, arrowSize, 0);
    pop();
}

function varLerp(x)
{
  if (direction)
      {
        vLerp = lerp(vLerp, 1, 0.02)
        if (vLerp > 0.99)  direction = false;
      }
  else 
    {
      vLerp = lerp(vLerp, 0, 0.02)
      if (vLerp < 0.01) direction = true;
    }
  return x;
}

```

### ¿Cómo funciona lerp() y lerpColor().

lerp() y lerpColor() son ambas funciones de interpolación que permiten obtener valores intermedios entre dos valores específicos.

### ¿Cómo se dibuja una flecha usando drawArrow()?

El método drawArrow mediante cierta lógica se asegura de que la flecha se dibuje de acuerdo con las referencias pasadas al método que son: base(dónde inicia la 
flecha), vec (la dirección y magnitud del vector) y color.

Por ejemplo, usa rotate() para asegurarse de que la flecha apunte al lugar correcto y translate para ubicar el incio de la flecha en las coordenadas pasadas por base.
