```js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

let walker;

function setup() {
  createCanvas(640, 240);
  position = createVector();
  walker = new Walker();
  background(255);
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {
  constructor()
  {
    position = createVector(width / 2, height / 2 );
  }

  show() {
    stroke(0);
    point(position.x, position.y);
  }

  step() {
    const choice = floor(random(4));
    if (choice == 0) {
      position.x++;
    } else if (choice == 1) {
      position.x--;
    } else if (choice == 2) {
      position.y++;
    } else {
      position.y--;
    }
  }
}

```

Para realizar el cambio solo tuve que cambiar las posiciones que existían por separado y agruparlas en el vector position, y luego acceder a los componentes con la notación del punto, para poder modificarlo y mostrarlo en pantalla
