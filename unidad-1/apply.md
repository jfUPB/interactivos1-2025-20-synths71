# Unidad 1

## 🛠 Fase: Apply

### Actividad 05

#### Explica cómo funciona el sistema físico interactivo que acabamos de crear.  

Mediante un micro:bit hicimos un sistema fisico para hacer cambiar un objeto cuando se ejecuta en la pantalla de p5j, pero antes de esto hay que realizar un codigo especifamente el micro:bit para que detecte cuando se esta presionando el boton A. Luego de esto en p5j hacemos un codigo para que cree una interfaz cuando se ejecuta el programa con una figura geometrica, la figura va a tener color verde como predeterminado pero va a cambiar a color rojo cuando se presiona el boton A del micro:bit.  

Esto permite visualizar en tiempo real la interacción física con el micro:bit desde el navegador, integrando hardware y software de forma sencilla.  

### Actividad 06

#### Enlace al editor:  

[Movimiento en X circulo](https://editor.p5js.org/synths71/sketches/Wgz2f4Upj)

#### Codigo del programa: 

``` js
let port;
let connectBtn;
let connectionInitialized = false;
let x = 200;
let y = 200;


function setup() {
  createCanvas(400, 400);
  background(220);
  port = createSerial();
  connectBtn = createButton("Connect to micro:bit");
  connectBtn.position(80, 300);
  connectBtn.mousePressed(connectBtnClick);
}

function draw() {
  background(220);

  if (port.opened() && !connectionInitialized) {
    port.clear();
    connectionInitialized = true;
  }

  if (port.availableBytes() > 0) {
    let dataRx = port.read(1);
    if (dataRx == "A") {
      x-=10;
    } else if (dataRx == "N") {
      x +=10;
    }
  }

  ellipseMode(CENTER);
  ellipse(x, y, 50, 50);
  fill("red");
  

  if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
  } else {
    connectBtn.html("Disconnect");
  }
}

function connectBtnClick() {
  if (!port.opened()) {
    port.open("MicroPython", 115200);
    connectionInitialized = false;
  } else {
    port.close();
  }
}

```
#### Codigo del micro:bit:

``` py
from microbit import *

uart.init(baudrate=115200)
display.show(Image.GHOST)

while True:
        if button_a.is_pressed():
            uart.write('A')

        if button_b.is_pressed():
            uart.write('N')    
      
        sleep(100)  
```
