
# Evidencias de la unidad 6

## Actividad 1

**¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito?**

La terminar se puso a instalar unos paquetes y se demoro 11 segundos aproximadamente, los paquetes me imagino serviran para abrir el servidor que luego podremos mover en los links que se nos dan en la unidad. 

**¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?**

El mensaje que aparecio es el siguiente:

nodejs-test-1@1.0.0 start
> node server.js

Server is listening on http://localhost:3000

Este mensaje indica que el servidor esta conectado en el computador y esta esperando peticiones por así decirlo en el puerto 3000 del computador.

**Describe lo que ves inicialmente en page1 y page2 en tu navegador.**

Lo que veo son dos circulos de color rojo con una linea negra que sale de estos y esta sigue una linea entre el page1 y page2 que incluso si muevo la pestaña del navegador estás van a seguir en linea recta.

**¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?**

los mensajes iniciales son los siguiente:

A user connected - ID: ZnjqybfzCVqrtYyFAAAB
Received win1update from ID: ZnjqybfzCVqrtYyFAAAB Data: { x: 204, y: 0, width: 1034, height: 712 }
Debug - Connected clients: 1, Page1: 1, Page2: 0, Synced: 0
Sync status: pages=false, synced=false, clients=1
Debug - Connected clients: 1, Page1: 1, Page2: 0, Synced: 1
Sync status: pages=false, synced=true, clients=1
A user connected - ID: gjZq7wLdI0gxE_gHAAAD

Esto me imagino es que el puerto 3000 reconoce que me conecte y luego pone las posiciones de los circulos o de la ventana donde están los circulos ahí mismo en la consola.

**Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?**

Cuando muevo las ventanas la linea que se dibuja en los dos circulos se mueve, incluso si las ventanas no están unidas para que siga siendo en linea recta y sigue así no importa como los mueva.

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page 1</title>
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
    <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
    <style>
        body {
            margin: 0;
            overflow: hidden;
        }
    </style>
</head>
<body>
    <!-- <h1>Welcome to Page 1</h1> -->
    <script defer src="page1.js"></script>
</body>
</html>
```
Esto es lo que sale en la consola del navegador pero no los entiendo muy bien.

## Actividad 2

**Piensa en cómo te conectas a Internet en casa o en la Universidad. ¿Usas Wi-Fi? ¿Un cable de red? Eso es simplemente tu “rampa de acceso” a la gran red de carreteras. ¿Qué pasaría si esa rampa se corta? Anota tus ideas.**

Generalmente me conecto con Wi-Fi y algunas veces con cable en mi casa si así lo requiero para tener conexión mejor y más estable y como se explica en la actividad, eso vendría a ser mi rampa de acceso.

Si se corta mi rampa de acceso mi computador ya no podría entrar a la red de carreteras que es Internet, lo que no me va a dejar acceder a ninguna pagina web ni revisar correos y tampoco comunicarme con servidores ni otros dispositivos y quedaría aislado.

**¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega?**

Un ejemplo del dia a dia puede ser a la hora de cojer transporte publico, hablando especificamente de un bus, el cliente es el pasajero y el servidor es el bus mismo o el conductor, lo que se pide es subirse para ir a cierto lugar y la entrega es ir hasta ese destino.

**Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor?**

la url que escogi es la siguiente: https://live.warthunder.com/feed/camouflages

El protocolo es https:// que indica que el navegador y el servidor se van a comunicar usando HTTPS.

El nombre del dominio es live.warthunder.com.

La ruta es /feed/camouflages que es la sección especifica dentro de ese servidor.

Si solo escribo https://live.warthunder.com el servidor me envía la página de inicio que ahí muestra todas las diferentes rutas y también como es la pagina de incio por defecto, muestra todo el contenido de las diferentes rutas ya que así es como esta puesta la pagina por defecto.

**Compara HTTP con los protocolos seriales que usaste. ¿Qué similitudes encuentras? ¿Qué diferencias clave ves? ¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?**


Las similitudes es que ambos son protocolos de comunicación y además de esto viajan en mensajes bien estructurados. Las diferencias clave pueden ser que los protocolos seriales son mucho más simples y directos mientras que HTTP tiene reglas más avanzadas y además el protocolo serial por lo general tiene un canal directo mientras que HTTP es una red mundial.

Es más complejo porque HTTP no solo manda bytes sino que necesita más elementos como el servidor y el cliente y también necesita flexibilidad para que el mismo protocolo funcione para recursos y dispositivos diferentes.

**Piensa en una página web simple, como un formulario de login. ¿Qué parte crees que es HTML (ej. los campos de texto, el botón)? ¿Qué parte es CSS (ej. el color del botón, el tipo de letra)? ¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?**

El HTML sería los campos de texto donde se pone el login y la contraseña y el botón de ingresar, el CSS por otro lado sería lo que le da el aspecto visual a la estructura así como el color del y tamaño del boton asi como el tipo de letra y los margenes y como están posicionados los campos en la pantalla, el JavaScript es lo que valida que no se dejen espacios vacios, deja que aparezcan los mensajes sin tener que recargar la pagina y manda los datos al servidor cuando se presione el botón.

**Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”. ¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web? ¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?**

La ventaja de este modelo es que es mucho más eficiente para interfaces de usuario, porque no necesita estar volviendo a hacer los dibujos ni volviendo a calcular todo constantemente sino que reacciona solo cuando hay una interacción o un cambio que vendría siendo el estado, esto da a entender que cuando se un bucle draw() se estaría gastando procesamiento innecesario y los recursos del navegador se estarían usando mal porque no hay cambios en si constantes o al menos cuando no hay cambios visibles.

**¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores?**

Node.js permite que JavaScript se use no solo en el navegador, sino también en el servidor, esto podría ser beneficioso para los desarrolladores porque así no tendrían que aprender un lenguaje distinto para cada cosa y podrían ser más eficientes en el trabajo en equipo ya que desarrollar sería mucho más facil, también se pueden compartir conocimientos, librerías e incluso fragmentos de código entre el cliente y el servidor.

**Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?**

La diferencia es que HTTP es como un intercambio de cosas, por ejemplo de juegos de consola o cartas, el cliente pide algo y el servidor le responde y esto pasa cada vez que el cliente pide algo. Mientras que con WebSockets/Socket.IO se establece una conexión directa y constante, así como si se estuviera haciendo una llamada de telefono o FaceTime y en la que ambos se pueden enviar mensajes sin necesidad de iniciar de 0 cada vez que se va a hablar.

## Actividad 3

**Experimento 1**
<img width="1919" height="1011" alt="image" src="https://github.com/user-attachments/assets/55f695bb-9410-4f9b-9cf9-a76263b48615" />

Al usar Intenta acceder a http://localhost:3000/page1, ya no funciona el servidor y me dice que no se puede obtener pero cuando usamos  http://localhost:3000/pagina_uno ahora si deja meterme al servidor.

Esto nos demuestra que el servidor asocia de forma estricta la URL con la respuesta que devuelve y si no coinciden entonces no va a mostrar nada y va a soltar un error.

**Experimento 2**

Al ver la terminal del page1 tenemos este ID: tRn2L03TIrKczAYYAAAB, además de esto dice que un usuario se conecto con ese id.

Cuando abro el page2 me sale el mismo mensaje de que se conecto un usuario con el ID: hucd3f1CiqHEiobtAAAD

Cierro page1 y aparece este mensaje en la terminal: User disconnected - ID: tRn2L03TIrKczAYYAAAB, y de igual manera cierro page2 y sale el siguiente mensaje en la terminal: User disconnected - ID: hucd3f1CiqHEiobtAAAD

Cuando los clientes se desconectan el servidor sabe exactamente cúal cliente se desconecto, eso muestra que el servidor asocia la conexión a un cliente específico y único mediante su socket.id

**Experimento 3**

Cuando muevo page1 se mueve win1update con sus coordenadas y direcciones y así mismo al mover page2 se mueve win2update ahora con los datos de la segunda pagina.

<img width="740" height="171" alt="image" src="https://github.com/user-attachments/assets/8619e77f-b6f6-47b6-a04f-9cd238bdf09b" />

Experimento clave: 

Al mover la ventana de page1 no se actualizó la visualización en page2 y viendo más lo que aparece en la terminal encontre que socket.emit envía el mensaje solo al mismo cliente que lo generó cosa que el broadcast lo envía a los demás.

**Experimento 4**

Al hacer el cambio del puerto al 3001 me sale el siguiente mensaje: Server is listening on http://localhost:3001

Ahora abriendo el servidor:

<img width="1855" height="1001" alt="image" src="https://github.com/user-attachments/assets/7705c0a2-a51c-429c-b3d6-38fef01bfb15" />

Vemos que solo funciona cuando pongo http://localhost:3001/page1 

Esto muestra que la variable port define la “puerta” en la que el servidor escucha, y que la función listen usa ese número para decidir en qué dirección aceptar conexiones.

## Actividad 4

**Experimento 1**

Al hacer el proceso indicado llegamos hasta este punto:

<img width="1919" height="1017" alt="image" src="https://github.com/user-attachments/assets/53294c34-b7ec-4c05-9f87-a44b2673b037" />

Esto indica que el cliente page2.html está intentando conectarse con el servidor usando Socket.IO, pero como el servidor está apagado entonces no encuentra la dirección para establecer la conexión.

Habiendo abierto el archivo de page2.html que se encuentra en la carpeta de views no se resuelven los errores y sigue apareciendo los mismos pero abriendo el link normal si se resuelven.

**Experimento 2**

Al hacer los cambios necesarios se logra ver lo siguiente: 

<img width="1757" height="861" alt="image" src="https://github.com/user-attachments/assets/c73c561e-3907-4b44-90d0-c9bd0bfb68d1" />

<img width="1868" height="984" alt="Captura de pantalla 2025-10-03 011847" src="https://github.com/user-attachments/assets/5e7998b4-ee28-4a62-be5e-af70deb760c4" />

Con esto lo que pasa es que page1 y page2 logran conectarse al servidor pero cuando se mueve page2 no se comparten los datos de posición/estado y se ve como en la consola de page1 aparece NOT SYNCED hasta que en algún momento logra un SYNCED con datos viejos o vacíos, pero no se mantiene actualizado.

Esto paso porque al comentar la linea de codigo que se pedía que es la línea que enviaba los datos iniciales al servidor cuando page2 se conectaba, Sin ese emit, el servidor nunca reenvía esos datos a page1, y por eso no hay actualización.

**Experimento 3**

Haciendo lo que se pide en el experimento tenemos:

<img width="1732" height="879" alt="image" src="https://github.com/user-attachments/assets/9b699dba-225a-4e98-940a-a828c4024051" />

Lo que vemos en las consolas es una sincronización en tiempo real entre las dos páginas usando Socket.IO, esto se muestra en la forma que cada vez que una ventana se mueve, envía su posición y tamaño al servidor con socket.emit y así el servidor recibe esa información y la reenvía a la otra ventana y eso es lo que aparece en la consola.

**Experimento 4**

Modifique el codigo del if para que fuera de la siguiente forma añadiendo un consol.log, esto no va a cambiar el comportamiento sino que va a mostrar un pequeño mensaje en la consola.

<img width="1833" height="997" alt="image" src="https://github.com/user-attachments/assets/aa53f402-5a4c-4293-af45-2f0659307719" />

Haciendo un console.log para que aparezca en la consola de page2 se ve que aparece un mensaje que dice "cambio la ventana a:" para luego dar las posiciones normalmente. Haciendo esta actividad comprobamos que el if se ejecuta solo cuando hay un cambio en la posición o tamaño de la ventana, entonces el codigo está diseñado para evitar envios y datos innecesarios.

**Experimento 5**

Haciendo el experimento del cambio de color llegamos a lo siguiente:

<img width="1916" height="1005" alt="Captura de pantalla 2025-10-03 015933" src="https://github.com/user-attachments/assets/7e4d7f21-d1d6-479e-8a07-8716fb9a206e" />

<img width="1919" height="1015" alt="image" src="https://github.com/user-attachments/assets/3830fd0d-154b-4785-b5c9-41026d0c49ca" />

Realizando otra modificación se me ocurrio hacer que el circulo en la page2 fuera más grande o pequeño dependiendo de la distancia y resulto de la siguiente forma:

<img width="1918" height="981" alt="image" src="https://github.com/user-attachments/assets/8b6c79f0-0f54-472c-8c94-6b3d73548cc6" />

<img width="1872" height="1011" alt="image" src="https://github.com/user-attachments/assets/a078d1ae-b1b3-461a-954b-508d684c84d3" />

## Actividad 5

**Explica tu idea y realiza algunos bocetos**

La idea para esta aplicación interactiva surgio mientras estaba trabajando una actividad de esta misma materia que involucraba un semaforo, me parece que es una buena forma de interacción porque cuando presiono el boton de pedir paso para el peaton, el semaforo para los vehiculos pasa por el amarillo y luego en el rojo, mientras que el de peatones pasa a verde por unos segundos con cierto intervalo de tiempo, el page1 es el que tiene el semaforo para los vehiculos y el de peatones en page2, el boton para pedir paso esta solo en el de page2, así como están ese tipo de botones en algunos semaforos de la ciudad.

**Implementa tu idea**

<img width="1903" height="975" alt="Captura de pantalla 2025-10-03 024701" src="https://github.com/user-attachments/assets/481ac79c-3c09-46c0-9e2a-588224e89296" />

<img width="1907" height="1056" alt="Captura de pantalla 2025-10-03 024707" src="https://github.com/user-attachments/assets/2f170df3-7a4f-4959-9e46-f8d03b110371" />

<img width="1881" height="985" alt="Captura de pantalla 2025-10-03 024717" src="https://github.com/user-attachments/assets/102ebd60-4f9a-4ac8-b8a2-e157ef6cbf49" />

**Incluye todos los códigos (servidor y clientes) en tu bitácora**

server.js:

```js
const express = require('express');
const app = express();
const http = require('http').createServer(app);
const io = require('socket.io')(http);

const port = 3000;

// Servir carpeta "views"
app.use(express.static('views'));

// Ruta principal → abre page1
app.get('/', (req, res) => {
  res.sendFile(__dirname + '/views/page1.html');
});

app.get('/page1', (req, res) => {
  res.sendFile(__dirname + '/views/page1.html');
});

app.get('/page2', (req, res) => {
  res.sendFile(__dirname + '/views/page2.html');
});


// Estado inicial del semáforo
let carLight = "green"; // rojo - amarillo - verde
let pedLight = "red";   // rojo - verde

io.on("connection", (socket) => {
  console.log(`Usuario conectado - ID: ${socket.id}`);

  // Enviar estado actual al conectarse
  socket.emit("lightUpdate", { carLight, pedLight });

  // Cuando peatón pide cruce
  socket.on("requestCross", () => {
    console.log("Botón de peatón presionado!");

    // Carros a amarillo primero
    carLight = "yellow";
    pedLight = "red";
    io.emit("lightUpdate", { carLight, pedLight });

    // Después de 2s → carros en rojo, peatón en verde
    setTimeout(() => {
      carLight = "red";
      pedLight = "green";
      io.emit("lightUpdate", { carLight, pedLight });

      // Después de 4s → volver al estado normal (carros verde, peatón rojo)
      setTimeout(() => {
        carLight = "green";
        pedLight = "red";
        io.emit("lightUpdate", { carLight, pedLight });
      }, 4000);

    }, 2000);
  });

  socket.on("disconnect", () => {
    console.log(`Usuario desconectado - ID: ${socket.id}`);
  });
});

http.listen(port, () => {
  console.log(`Servidor escuchando en http://localhost:${port}`);
});
```

page1.html:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Semáforo - Carros</title>
  <script src="/socket.io/socket.io.js"></script>
  <script src="page1.js"></script>
</head>
<body>
  <h1> Semáforo - Carros</h1>
  <canvas id="carSemaforo" width="200" height="400"></canvas>
</body>
</html>
```

page1.js:

```js
<!DOCTYPE html>
<html>
<head>
  <title>Semáforo - Carros</title>
  <script src="/socket.io/socket.io.js"></script>
  <script src="page1.js"></script>
</head>
<body>
  <h1> Semáforo - Carros</h1>
  <canvas id="carSemaforo" width="200" height="400"></canvas>
</body>
</html>
```

page2.html:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Semáforo - Peatón</title>
  <script src="/socket.io/socket.io.js"></script>
  <script src="page2.js"></script>
</head>
<body>
  <h1> Semáforo - Peatón</h1>
  <canvas id="pedSemaforo" width="200" height="400"></canvas>
  <br>
  <button onclick="requestCross()"> Pedir cruce</button>
</body>
</html>
```

page2.js:

```js
let socket = io();
let pedLight = "red";

socket.on("lightUpdate", (data) => {
  pedLight = data.pedLight;
  drawPedLight();
});

function requestCross() {
  socket.emit("requestCross");
}

function drawPedLight() {
  let c = document.getElementById("pedSemaforo");
  let ctx = c.getContext("2d");

  ctx.fillStyle = "black";
  ctx.fillRect(0, 0, 200, 400);

  ctx.fillStyle = (pedLight === "red") ? "red" : "darkred";
  ctx.beginPath();
  ctx.arc(100, 100, 70, 0, 2 * Math.PI);
  ctx.fill();

  ctx.fillStyle = (pedLight === "green") ? "lime" : "darkgreen";
  ctx.beginPath();
  ctx.arc(100, 300, 70, 0, 2 * Math.PI);
  ctx.fill();
}
```

## Autoevaluación 

En esta unidad aprendimos como se manejan los servidores, que es la internet y como funciona para poder conectarnos a ella, así como hacer diversos experimentos con los recursos que se dieron en la unidad.

- Actividad 1: En la actividad 1 considero que merezco 5, ya que realice la instalación del servidor en mi computador y además resolvi las dudas que se proponían con mis propias palabras y con lo que veía que me soltaba la terminal de git bash y con lo que veía que pasaba en la pantalla del servidor cuando la movia o hacia el ejercicio que me proponian.

- Actividad 2: En la actividad 2 considero que merezco 5, esto porque leí todos los textos de información detenidamente para entender que era lo que me estaban diciendo y el porque, así como responder las preguntas y ejercicios que proponían con los conocimientos que daban en el parrafo de información de ese ejercicio propuesto ya que era así como parrafo de infomación y luego un ejercicio propuesto y así varias veces durante está actividad, y en algunas de las preguntas que no sabía exactamente la respuesta la intento explicar con mis propias palabras.

- Actividad 3: En está actividad considero que merezco 4.0, ya que realice todos los ejercicios de experimentación y poniendo pruebas en foma de fotos y realizando todos los pasos que me proponían pero en algunos de los experimentos pude haber indagado un poco más para entender mejor algunos de los experimentos y no solo limitarme a poner lo minimo para completar lo que me proponían.

- Actividad 4: En está actividad considero que merezco 4.2, ya que relice todos los experimentos, indagando en estos sobretodo en la parte de codigo para entender que era lo que se estaba cambiando pero no mucho, solo para entender lo más esencial que necesitaba saber para así dar por completado el experimento, también claro poniendo pruebas de los ejercicios.

- Actividad 5: En esta actividad considero que merezco 3.8, ya que la aplicación interactiva me la pense detenidamente para que fuera algo original y que a la vez nosotros pudieramos ver en el día a día, asi como asegurarme de que estuviera funcionando sin ningún problema en el servidor que se nos dio, solo cambiando los codigos del servidor y cliente para que cambiara a la aplicación interactiva que quería proponer pero para poder implementar los codigos me apoye un poco en la IA, ya que aún no sabía exactamente como implementar todo el codigo en un nuevo lenguaje como html y javascript y por este motivo no me puedo poner más alto en la nota.


Con la parte de la defensa terminada, la nota de la autoevaluación promediadia es: **4.4**





























