
# Evidencias de la unidad 7

## Actividad 1

**¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?**

La URL que obtuve en este caso es la siguiente https://zjtbj0cm-3000.use2.devtunnels.ms/, está URL la necesitamos porque localhost o la IP local solo funcionan dentro de la misma red o dispositivo, entonces no podemos acceder a el link desde el celular que es lo que nos pide los pasos de la actividad.

**Describe brevemente qué hace npm install y npm start**

npm install lo que hace es descargar las dependencias que necesita el servidor para que pueda correr con normalidad, el npm start inicia el servidor.

**¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?**

Observe estos mensajes al mirar la terminal:

```
New client connected
New client connected
Received message => { type: 'touch', x: 97, y: 230 }
Received message => { type: 'touch', x: 88, y: 229 }
Received message => { type: 'touch', x: 81, y: 224 }
Received message => { type: 'touch', x: 81, y: 216 }
```

los identificadores de cliente son iguales y no diferencia si son el del desktop o el del mobile, así mismo no les asigna un id distitivo como en la unidad anterior, solamente muestra los valores en los que se mueve el circulo en este caso y los clientes que se acaban de conectar.

**Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?** 

Cuando conectamos ambos clientes, el segundo puede mover el circulo que esta en la primera que tiene el desktop, cuando hacemos esto, se actualizan en cada momento los valores a los que movemos el circulo. Se nota un retraso pero no afecta mucho, es solo un poco de retraso que hay.

## Actividad 2

**Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?**








