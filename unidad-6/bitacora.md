
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













