# Unidad 2


## 🛠 Fase: Apply

### Actividad 04

<img width="631" height="676" alt="Actividad04" src="https://github.com/user-attachments/assets/d811eb7d-d57b-4294-80eb-b97ac6f61945" />

### Actividad 05

Implementa el código para la bomba temporizada usando mycropython y el micro:bit, incluyendo la funcionalidad básica: configuración del tiempo, cuenta regresiva y detonación.

#### 1. El código que implementa la bomba temporizada.

```
from microbit import *
import utime

STATE_INIT = 0
STATE_CONFIG = 1
STATE_ACTIVO = 2
STATE_EXPLOSION = 3

TIEMPO_MIN = 10
TIEMPO_MAX = 60
TIEMPO_INICIAL = 10
INTERVALO_SEGUNDO = 1000  

current_state = STATE_INIT
start_time = 0
tiempo = TIEMPO_INICIAL

while True:
  
    if current_state == STATE_INIT:
        tiempo = TIEMPO_INICIAL
        display.show(str(tiempo % 10))
        current_state = STATE_CONFIG

    elif current_state == STATE_CONFIG:
        if button_a.was_pressed():  
            tiempo = min(tiempo + 1, TIEMPO_MAX)
            display.show(str(tiempo % 10))

        if button_b.was_pressed():  
            tiempo = max(tiempo - 1, TIEMPO_MIN)
            display.show(str(tiempo % 10))

        if accelerometer.was_gesture("shake"):  
            start_time = utime.ticks_ms()
            current_state = STATE_ACTIVO

    elif current_state == STATE_ACTIVO:
        if utime.ticks_diff(utime.ticks_ms(), start_time) >= INTERVALO_SEGUNDO:
            start_time = utime.ticks_ms()

            if tiempo > 0:  
                tiempo -= 1
                display.show(str(tiempo % 10))

            if tiempo <= 0:
                current_state = STATE_EXPLOSION

        if pin_logo.is_touched():  
            current_state = STATE_CONFIG
            tiempo = TIEMPO_INICIAL

    elif current_state == STATE_EXPLOSION:
        display.show(Image.SKULL)
        utime.sleep_ms(300)
        display.clear()
        utime.sleep_ms(200)

        if pin_logo.is_touched():
            current_state = STATE_CONFIG
            tiempo = TIEMPO_INICIAL
```

#### 2. La definición de los vectores de prueba básicos que permiten verificar el correcto funcionamiento del programa.  

- Desde STATE_IDLE, si se detecta Shake, pasa a STATE_CONFIGURACION e inicia el conteo mostrando el tiempo inicial en pantalla.
- Desde STATE_CONFIGURACION, si se presiona Botón UP, permanece en STATE_CONFIGURACION pero incrementa el tiempo configurado y actualiza la pantalla.
- Desde STATE_CONFIGURACION, si se presiona Botón DOWN, permanece en STATE_CONFIGURACION pero disminuye el tiempo configurado y actualiza la pantalla.
- Desde STATE_ACTIVO, cuando transcurre 1 segundo, permanece en STATE_ACTIVA, disminuye el contador en 1 y actualiza la pantalla.
- Desde STATE_ACTIVO, cuando el tiempo llega a 0, pasa a STATE_EXPLOSION.
- Desde STATE_EXPLOSION, si se presiona Botón TOUCH, vuelve a STATE_CONFIGURACION.


