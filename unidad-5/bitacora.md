
# Evidencias de la unidad 5

## Actividad 1  


<img width="1916" height="994" alt="Captura de pantalla 2025-09-16 102111" src="https://github.com/user-attachments/assets/4da1139a-58ad-49d9-82de-b18486e16cfc" />

<img width="1918" height="987" alt="Captura de pantalla 2025-09-16 104545" src="https://github.com/user-attachments/assets/539508e7-3d70-4504-afad-41421fe5c603" />


**Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?**

La comunicación entre el micro:bit y el sketch de p5.js se realiza a través del puerto serial (UART).

- xValue: el valor del eje X del acelerómetro.

- yValue: el valor del eje Y del acelerómetro.

- aState: si el botón A está presionado.

- bState: si el botón B está presionado.

**¿Cómo es la estructura del protocolo ASCII usado?**

El protocolo que se utiliza en texto plano o ASCII tiene los siguientes elementos: xValue, yValue, aState, bState\n

**Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.**

Parte del codigo:

```js
if (port.availableBytes() > 0) {
  let data = port.readUntil("\n");
  if (data) {
    data = data.trim();
    let values = data.split(",");
    if (values.length == 4) {
      microBitX = int(values[0]) + windowWidth / 2;
      microBitY = int(values[1]) + windowHeight / 2;
      microBitAState = values[2].toLowerCase() === "true";
      microBitBState = values[3].toLowerCase() === "true";
      updateButtonStates(microBitAState, microBitBState);
    }
  }
}
```
- Se espera a que haya datos disponibles (port.availableBytes()).

- Se lee una línea completa hasta \n.

- Se eliminan espacios extra (trim()).

- Se separan los datos con split(",").

- Se transforman xValue y yValue a enteros y se convierten a coordenadas de pantalla sumando windowWidth / 2 y windowHeight / 2 para centrar el dibujo.

- Los estados de los botones se interpretan como booleanos.

- Finalmente, se llama a updateButtonStates() para manejar eventos basados en los botones.

**¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?**

```js
function updateButtonStates(newAState, newBState) {
  if (newAState === true && prevmicroBitAState === false) {
    lineModuleSize = random(50, 160);
    clickPosX = microBitX;
    clickPosY = microBitY;
    print("A pressed");
  }

  if (newBState === false && prevmicroBitBState === true) {
    c = color(random(255), random(255), random(255), random(80, 100));
    print("B released");
  }

  prevmicroBitAState = newAState;
  prevmicroBitBState = newBState;
}
```
- Evento "A pressed": se detecta cuando el botón A pasa de no estar presionado a estar presionado (false → true). En ese momento:

- Se cambia el tamaño del dibujo.

- Se guarda la posición del clic.

- Evento "B released": se detecta cuando el botón B pasa de estar presionado a no estarlo (true → false). En ese momento:

- Se cambia el color del trazo a un color aleatorio con algo de transparencia.

## Preguntas de la actividad: 

- **Para que sirve la función: function updateButtonStates**:

Esta función sirve para detectar los cambios de estado en los botones del micro:bit y generar las acciones correspondientes.

Es decir que cuando en este caso se presiona el botón A genera un tamaño nuevo para el módulo y guarda la posición, mientras que usando el botón B cambia el color del dibujo a uno aleatorio. Además de esto tiene una especie de historial usando prevmicroBitAState y prevmicroBitBState para que se pueda diferenciar entre presionado actualmente y acaba de cambiar.

## Experimentación:

**mapeo de coordenadas y saturación**

En este experimento probe el mapeo microBitX = int(values[0]) + windowWidth/2 y como se comportara con valores extremos.

Modificando el codigo del microbit un poco para que envie valores artificiales extremos para el eje X y Y. Usando ayuda para realizar el experimento terminamos con este codigo para el microbit:
```py
# microbit_test_extremes.py
from microbit import *
uart.init(115200)
display.set_pixel(0,0,9)

test_values = [0, 2000, -2000, 32767, -32768]
i = 0
while True:
    v = test_values[i % len(test_values)]
    # enviamos v como X e Y (para probar ambos ejes)
    data = "{},{},{},{}\n".format(v, v, False, False)
    uart.write(data)
    # repetimos cada valor varias veces para que se vean en p5
    sleep(200)  # 5 lecturas por segundo
    i += 1
```
Lo que va a pasar aqui es que algunas de las funciones como windowWidth/2, microBitXraw = 0, van a estar siendo sumadas y divididas con el valor artificial que se dio antes pero ahora con el codigo del p5.

*Lo que se logra observar es que los valores ya no se dibujan dentro del canvas o que tiene coordenadas negativas.*

## Análisis y Reflexión:

Lo primero que pasa cuando vamos a ejecutar es lo que sucede dentro del mismo microbit que genera datos crudos por asi decirlo mediante el UART, los cuales viajan como datos en texto en serie hasta que llegan al navegador y ahi los recibe p5 y este los interpreta y los usa para modificar coordenadas de objetos en un canvas.

En el experimento realizado el mayor aprendizaje fue entender que los datos no son neutros, su tamaño, rango y forma de transmisión afectan directamente el rendimiento y la firmeza del sistema. Con esto podemos decir que un valor mal dado puede generar todo tipo de errores.

## Apropiación y Articulación de Conceptos:

En esta actividad lo que se propone entender es que un dato tan simple como el de un acelerometro realmente es un sistema interdependiente, cada parte tiene un rol dentro de la ejecución del ejercicio, es decir, el micro:bit capta señales físicas, el UART las convierte en una secuencia de bytes, el navegador las recibe como texto, y p5.js las interpreta para transformar esas cifras en visuales. En la comunicación seria es en si un flujo de bytes asíncrono y que no necesariamente llegan de la manera más organizada sino que pueden llegar hasta al punto de perderse, en lo que todo esto esta pasando, el micro:bit envía números separados por comas y terminados en \n, el cual es el protocolo que impone el orden para los datos.

## Actividad 2

<img width="1000" height="716" alt="Captura de pantalla 2025-09-16 110246" src="https://github.com/user-attachments/assets/d270b37f-785e-4d51-8bd6-97a6b9fe9983" />

**¿Por qué se ve este resultado?**

Cuando cambiamos de texto plano (ASCII) a formato binario con struct.pack, los datos ya no son números legibles separados por comas y saltos de línea, sino que ya son simples bytes.

<img width="999" height="726" alt="Captura de pantalla 2025-09-16 110405" src="https://github.com/user-attachments/assets/dbe61486-2355-4692-9f33-6859f515cff4" />

**Captura el resultado del experimento anterior. Lo que ves ¿Cómo está relacionado con esta línea de código?**  
```js
data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))
```

La linea de codigo lo que hace es empaquetar datos numéricos en binario en ves de en texto, y cuando ponemos la opción de todo en HEX lo que se ve son esos valores ya convertidos en bytes.

**No te parece que el resultado es un poco más difícil de leer que el texto en ASCII?**

Sí, totalmente. En ASCII podrías ver "x=120,y=34,a=1,b=0", que no es muy dificil de entender pero en binario/HEX sale 00 78 00 22 01 00, que sin decodificar no dice nada claro.

**¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?**

Por lo que investigue es que ocupa menos espacio y hay menos redundancia al no haber unas X o Y ocupando espacio, ahora por las desventajas es que claro, es más dificil de leer y si hay error de sincronización, se daña todo el paquete.

### Ejercicio experimento:  

<img width="995" height="726" alt="Captura de pantalla 2025-09-16 112125" src="https://github.com/user-attachments/assets/e90e8bf4-18dd-48a9-aac4-ed8d5dced5ec" />

**Captura el resultado del experimento. ¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían?**



**Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'?**

### Experimento 2:

<img width="1001" height="734" alt="Captura de pantalla 2025-09-16 112324" src="https://github.com/user-attachments/assets/41c3300d-8ce2-4cd3-a3ee-74aff6b55b76" />


<img width="1916" height="909" alt="Captura de pantalla 2025-09-16 114403" src="https://github.com/user-attachments/assets/0454a132-9714-404d-8feb-5848b9f8b328" />











