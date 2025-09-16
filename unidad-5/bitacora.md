
# Evidencias de la unidad 5

## Actividad 1  


<img width="1916" height="994" alt="Captura de pantalla 2025-09-16 102111" src="https://github.com/user-attachments/assets/4da1139a-58ad-49d9-82de-b18486e16cfc" />

<img width="1918" height="987" alt="Captura de pantalla 2025-09-16 104545" src="https://github.com/user-attachments/assets/539508e7-3d70-4504-afad-41421fe5c603" />


### Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?

La comunicación entre el micro:bit y el sketch de p5.js se realiza a través del puerto serial (UART).

- xValue: el valor del eje X del acelerómetro.

- yValue: el valor del eje Y del acelerómetro.

- aState: si el botón A está presionado.

- bState: si el botón B está presionado.

### ¿Cómo es la estructura del protocolo ASCII usado?

El protocolo que se utiliza en texto plano o ASCII tiene los siguientes elementos: xValue, yValue, aState, bState\n

### Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.

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

### ¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?

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

## Actividad 2

<img width="1000" height="716" alt="Captura de pantalla 2025-09-16 110246" src="https://github.com/user-attachments/assets/d270b37f-785e-4d51-8bd6-97a6b9fe9983" />

### Captura el resultado del experimento anterior. ¿Por qué se ve este resultado?

<img width="999" height="726" alt="Captura de pantalla 2025-09-16 110405" src="https://github.com/user-attachments/assets/dbe61486-2355-4692-9f33-6859f515cff4" />

### Captura el resultado del experimento anterior. Lo que ves ¿Cómo está relacionado con esta línea de código?  
```js
data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))
```

No te parece que el resultado es un poco más difícil de leer que el texto en ASCII?

### ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?  

### Ejercicio experimento:  

<img width="995" height="726" alt="Captura de pantalla 2025-09-16 112125" src="https://github.com/user-attachments/assets/e90e8bf4-18dd-48a9-aac4-ed8d5dced5ec" />

### Captura el resultado del experimento. ¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían?

### Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'?

### Experimento 2:

<img width="1001" height="734" alt="Captura de pantalla 2025-09-16 112324" src="https://github.com/user-attachments/assets/41c3300d-8ce2-4cd3-a3ee-74aff6b55b76" />







