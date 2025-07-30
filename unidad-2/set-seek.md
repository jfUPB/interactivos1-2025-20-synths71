# Unidad 2

## 🔎 Fase: Set + Seek

###  Actividad 01  

#### Describe detalladamente cómo funciona este ejemplo.  

dwsd

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

Las acciones son las cosas que se hacen cuando ocurre un evento.


