# Unidad 2

## 🔎 Fase: Set + Seek

###  Actividad 01  

#### Describe detalladamente cómo funciona este ejemplo.  

El programa define una clase Pixel que representa un LED del micro:bit controlado por una máquina de estados. Cada pixel tiene una posición (X, Y), un estado inicial (encendido o apagado), y un intervalo de tiempo en milisegundos para cambiar de estado.

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

``` py
from microbit import *
import utime

class Semaforo:
    def __init__(self, pos_rojo, pos_amarillo, pos_verde, tiempo_rojo=3000, tiempo_verde=3000, tiempo_amarillo=1000):
        # posiciones: tupla (x,y) para cada LED que representa un color
        self.pos_rojo = pos_rojo
        self.pos_amarillo = pos_amarillo
        self.pos_verde = pos_verde

        # tiempos en milisegundos para cada color
        self.tiempos = {
            "ROJO": tiempo_rojo,
            "VERDE": tiempo_verde,
            "AMARILLO": tiempo_amarillo
        }

        # estado inicial
        self.estado = "ROJO"        # Estado inicial
        self.inicio_tiempo = utime.ticks_ms()

        # mostrar el estado inicial
        self._mostrar_estado()

    def _encender_led(self, posicion, valor):
        display.set_pixel(posicion[0], posicion[1], valor)

    def _apagar_todos(self):
        display.clear()

    def _mostrar_estado(self):
        # limpia y enciende el LED correspondiente al estado actual
        self._apagar_todos()
        if self.estado == "ROJO":
            self._encender_led(self.pos_rojo, 9)
        elif self.estado == "VERDE":
            self._encender_led(self.pos_verde, 9)
        elif self.estado == "AMARILLO":
            self._encender_led(self.pos_amarillo, 9)

    def actualizar(self):
        # revisar si ya pasó el tiempo del estado actual
        ahora = utime.ticks_ms()
        transcurrido = utime.ticks_diff(ahora, self.inicio_tiempo)
        if transcurrido > self.tiempos[self.estado]:

            # cambiar al siguiente estado

            if self.estado == "ROJO":
                self.estado = "VERDE"
            elif self.estado == "VERDE":
                self.estado = "AMARILLO"
            elif self.estado == "AMARILLO":
                self.estado = "ROJO"

            # reiniciar el temporizador y actualizar el display
            self.inicio_tiempo = ahora
            self._mostrar_estado()

# Usamos la columna central para poner los tres LEDs
pos_rojo = (2, 0)      # arriba
pos_amarillo = (2, 2)  # en el centro
pos_verde = (2, 4)     # abajo

# Crear el objeto semáforo con sus tiempos
semaforo = Semaforo(pos_rojo, pos_amarillo, pos_verde,
                    tiempo_rojo=3000,   # rojo 3 segundos
                    tiempo_verde=3000,  # verde 3 segundos
                    tiempo_amarillo=1000) # amarillo 1 segundo

# Bucle principal
while True:
    semaforo.actualizar()
    utime.sleep_ms(20)  # pequeña pausa para no saturar la CPU
```
Se crea una clase Semaforo que representa el funcionamiento de un semáforo como una máquina de estados. El semáforo tiene tres estados: ROJO, VERDE y AMARILLO. Cada estado dura un tiempo específico en milisegundos. 

#### Estados en el programa

- ROJO: el LED rojo está encendido.

- VERDE: el LED verde está encendido.

- AMARILLO: el LED amarillo está encendido.

#### Evento: 

El paso del tiempo: el evento que activa el cambio de estado es que el tiempo del estado actual se haya cumplido.

#### Acciones:

- Encender el LED del color que corresponda al estado actual.

- Apagar los demás LEDs.

- Cambiar el estado de ROJO a VERDE a AMARILLO a ROJO.

- Reiniciar el tiempo de referencia.


### Actividad 03

#### 1.  Explica por qué decimos que este programa permite realizar de manera concurrente varias tareas.

Decimos que el programa maneja concurrencia porque, aunque el micro:bit no ejecuta dos cosas exactamente al mismo tiempo si va cambiando entre las diferentes tareas y cada objeto funciona como una tarea independiente que va de la mano con el bucle principal.

#### 2.  Identifica los estados, eventos y acciones en el programa. Los estados son condiciones de espera

#### Estados

STATE_INIT - inicializa y pasa a HAPPY.

STATE_HAPPY - muestra Image.HAPPY.

STATE_SMILE - muestra Image.SMILE.

STATE_SAD - muestra Image.SAD.

#### Eventos

Temporizador: utime.ticks_diff(utime.ticks_ms(), start_time) > interval - indica que se acabó el tiempo del estado actual.

Botón A: button_a.was_pressed() - evento presionado por el usuario.

#### Acciones

- cambiar la imagen mostrada.

- reiniciar el temporizador de entrada.

- configurar el intervalo del nuevo estado.

- transitar al siguiente estado.


#### 3.  Describe y aplica al menos 3 vectores de prueba para el programa. Para definir un vector de prueba debes llevar al sistema a un estado, generar los eventos y observar el estado siguiente y las acciones que ocurrirán. Por tanto, un vector de prueba tiene unas condiciones iniciales del sistema, unos resultados esperados y los resultados realmente obtenidos. Si el resultado obtenido es igual al esperado entonces el sistema pasó el vector de prueba, de lo contrario el sistema puede tener un error.

#### Vector 1: Secuencia normal de tiempo

- Condición inicial: El sistema está en STATE_HAPPY mostrando la cara feliz.

- Evento: Pasa el intervalo de 1500 ms sin que se presione ningún botón.

- Resultado esperado: Cambia al estado STATE_SMILE, muestra la cara sonriente y ajusta el temporizador a 1000 ms.

- Resultado obtenido: El programa efectivamente pasa a STATE_SMILE.
El vector de prueba pasa.

#### Vector 2: Interrupción con botón en cara feliz

- Condición inicial: El sistema está en STATE_HAPPY.

- Evento: Se presiona el botón A antes de que termine el intervalo.

- Resultado esperado: El sistema debe cambiar de inmediato a STATE_SAD, mostrar la cara triste y ajustar el intervalo a 2000 ms.

- Resultado obtenido: El programa responde como se espera, cambiando a triste.
El vector de prueba pasa.

#### Vector 3: Interrupción con botón en cara triste

- Condición inicial: El sistema está en STATE_SAD.

- Evento: Se presiona el botón A en cualquier momento.

- Resultado esperado: El programa debe cambiar a STATE_SMILE, mostrar la cara sonriente y ajustar el temporizador a 1000 ms.

- Resultado obtenido: El sistema realiza correctamente la transición.

