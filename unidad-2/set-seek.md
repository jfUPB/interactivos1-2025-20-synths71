# Unidad 2

## 🔎 Fase: Set + Seek

###  Actividad 01  

#### Describe detalladamente cómo funciona este ejemplo.  

Este programa para la micro:bit controla dos LEDs de su matriz 5x5 utilizando una clase llamada Pixel, que permite encender y apagar un LED en intervalos de tiempo definidos. Cada objeto de la clase representa un píxel con una posición, estado (encendido o apagado) y un intervalo. Al iniciar, cada LED se configura y entra en un ciclo donde espera que pase el tiempo definido para cambiar su estado. En el ejemplo, el LED en la esquina superior izquierda (0,0) parpadea cada 1 segundo, mientras que el de la esquina inferior derecha (4,4) lo hace cada 0.5 segundos. El programa corre en un bucle infinito actualizando ambos LEDs continuamente.

#### ¿Cuáles son los estados en el programa?

Los estados son las condiciones en las que estan las condiciones del pixel, esto mientras espera que pase algo. En este caso hay dos estados en esa variable que son: 
- Init
- WaitTimeout

#### ¿Cuáles son los eventos/inputs en el programa?

Los eventos son las condiciones que se revisan constantemente para saber si se debe hacer algo. En este caso hay un evento principal con la siguiente linea de codigo:
 ```
if utime.ticks_diff(utime.ticks_ms(), self.startTime) > self.interval
 ```
#### ¿Cuáles son las acciones en el programa?

Las acciones son las cosas que se hacen cuando ocurre un evento. En este programa las acciones son prender y apagar los leds en unos determinados leds en el micro:bit y luego de esto hacer una espera con un tiempo determinado que en este caso son 1 segundo para un led y 0.5 segundos para otro led, y cuando haga todo esto, lo repita en un bucle infinito. Esto se ejecuta de manera controlada gracias a la clase pixel.

### Actividad 02



### Actividad 03

#### 1.  Explica por qué decimos que este programa permite realizar de manera concurrente varias tareas.

El programa espera 

#### 2.  Identifica los estados, eventos y acciones en el programa. Los estados son condiciones de espera

Los estados son condiciones de espera

#### 3.  Describe y aplica al menos 3 vectores de prueba para el programa. Para definir un vector de prueba debes llevar al sistema a un estado, generar los eventos y observar el estado siguiente y las acciones que ocurrirán. Por tanto, un vector de prueba tiene unas condiciones iniciales del sistema, unos resultados esperados y los resultados realmente obtenidos. Si el resultado obtenido es igual al esperado entonces el sistema pasó el vector de prueba, de lo contrario el sistema puede tener un error.

```
# Imports go at the top
from microbit import *
import utime

STATE_INIT = 0
STATE_HAPPY = 1
STATE_SMILE = 2
STATE_SAD = 3

currentState = STATE_INIT
startTime = 0
intervalHappy= 1500
intervalSmile = 1000
intervalSad = 2000


def tarea1 ():
    global currentState
    global startTime
    if currentState == STATE_INIT:
        display.show(Image.HAPPY)
        startTime = utime.ticks_ms()
        currentState = STATE_HAPPY
    elif currentState == STATE_HAPPY:
        if utime.ticks_diff(utime.ticks_ms(), startTime) > intervalHappy: 
            display.show(Image.SMILE)
            startTime = utime.ticks_ms()
            currentState = STATE_SMILE
        if button_a.was_pressed():
            display.show(Image.SAD)
            startTime = utime.ticks_ms()
            currentState = STATE_SAD
    elif currentState == STATE_SMILE:
        if utime.ticks_diff(utime.ticks_ms(), startTime) > intervalSmile:
            display.show(Image.SAD)
            startTime = utime.ticks_ms()
            currentState = STATE_SAD
    elif currentState == STATE_SAD:
        if utime.ticks_diff(utime.ticks_ms(), startTime) > intervalSad:
             display.show(Image.HAPPY)
             startTime = utime.ticks_ms()
             currentState = STATE_HAPPY
    else: 
        display.show(Image.SKULL)
        



# Code in a 'while True:' loop repeats forever
while True:
    tarea1()
```


Apply: Aplicación 🛠
