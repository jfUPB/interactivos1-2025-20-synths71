# Unidad 3


## 🛠 Fase: Apply

### Actividad 6  

En esta actividad vas a transferir la técnica de programación con máquinas de estado a p5.js.

Crea la bomba versión 2.0 en p5.js. No olvides que al aplicar la técnica de máquinas de estado en micro:bit se evitaba colocar acciones por fuera de los eventos. En el caso de p5.js será necesario que tengas acciones por fuera de eventos porque es necesario dibujar el canvas en cada frame.

```javascript
let count = 20;
let state = "CONFIG"; 
let password = ['A', 'B', 'A'];
let keySequence = [];
let lastTime = 0;

function setup() {
  createCanvas(400, 400);
  textAlign(CENTER, CENTER);
  textSize(20);
}

function draw() {
  background(220);

  if (state === "CONFIG") {
    text("Tiempo inicial", width/2, height/4);
    text("Presiona S para iniciar", width/2, height/2.5);
    textSize(40);
    text(count, width/2, height/2);
    textSize(20);
  } 
  
  else if (state === "ARMED") {
    text("Bomba activada", width/2, height/6);
    text("Tiempo: " + count, width/2, height/2);
    text("Introduce clave: A B A", width/2, height*0.7);

   
    if (millis() - lastTime > 1000) {
      count--;
      lastTime = millis();
      if (count <= 0) {
        state = "EXPLODED";
      }
    }
  } 
  
  else if (state === "EXPLODED") {
    text("BOOM", width/2, height/2.5);
    text("Presiona R para reiniciar", width/2, height*0.65);
  }

  
  drawFixedButtons();
}

function keyPressed() {
  let k = key.toUpperCase();

  if (state === "CONFIG") {
    if (k === "S") {
      lastTime = millis();
      state = "ARMED";
    }
  } 
  
  else if (state === "ARMED") {
    if (k === "A" || k === "B") {
      
      if (k === "A") count = min(count + 1, 99);
      if (k === "B") count = max(count - 1, 1);

      
      keySequence.push(k);
      if (keySequence.length === password.length) {
        if (arraysEqual(keySequence, password)) {
          count = 20;
          state = "CONFIG"; 
        }
        keySequence = []; 
      }
    }
    if (k === "R") {
      count = 20;
      state = "CONFIG";
      keySequence = [];
    }
  } 
  
  else if (state === "EXPLODED") {
    if (k === "R") {
      count = 20;
      state = "CONFIG";
      keySequence = [];
    }
  }
}

function arraysEqual(a, b) {
  if (a.length !== b.length) return false;
  for (let i = 0; i < a.length; i++) {
    if (a[i] !== b[i]) return false;
  }
  return true;
}

function drawFixedButtons() {
  let buttons = ["A", "B", "S", "R"];
  let startX = width/2 - (buttons.length * 60)/2;
  let y = height - 70;

  for (let i = 0; i < buttons.length; i++) {
    let key = buttons[i];
    let x = startX + i * 60;

    fill(240);
    stroke(0);
    rect(x, y, 50, 40, 8);

    fill(0);
    noStroke();
    textSize(18);
    text(key, x+25, y+20);
  }
}
```

