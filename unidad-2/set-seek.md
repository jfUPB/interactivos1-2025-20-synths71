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
