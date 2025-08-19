# Unidad 3


## 🛠 Fase: Apply

### Actividad 6  

```
let port;
let connectBtn;
let connectionInitialized = false;
let count = 20;
let validChars = "ABST"; 

function setup() {
  createCanvas(400, 400);
  background(220);
  port = createSerial();
  let sendBtnA = createButton('A', 300,300);
  let sendBtnB = createButton('B');
  let sendBtnS = createButton('S');
  let sendBtnT = createButton('T');
}

function draw() {
  background(220);
 textAlign(CENTER);
  text("Press A,B,S,T to simulate micro:bit keys", width / 2, height / 1.7);
  
  textAlign(CENTER);
  text(count, width / 2, height / 2);


function keyPressed() {
  keyValue = key.toUpperCase();
  if(validChars.includes(keyValue)){
    console.log(keyValue);
    port.write(keyValue);
  }

}
}
```
