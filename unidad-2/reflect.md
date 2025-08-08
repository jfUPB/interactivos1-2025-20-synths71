# Unidad 2


## 🤔 Fase: Reflect

### Actividad 06  

Parte 1: recuperación de conocimiento (Retrieval Practice)

#### 1. Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?

Una maquina de estados es donde se pone en forma de diagrama como funciona el programa que se va a hacer y los posibles caminos que pueda tomar, en caso de fallar se dice que el vector fallo y se le tiene que buscar una solución en el codigo.

los componentes claves de una maquina de estados son:
- Estados
- Eventos
- Acciones
- Vectores

#### 2. Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender un temporizador y botones “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit. ¿Qué problema soluciona en comparación con usar funciones como sleep()?

Es util para detectar los posibles caminos que pueda tener el programa dependiendo de que se presione en el micro:bit en este caso y sea facíl de identificar cuando ocurrio un error, además de esto usando funciones como utime ticks es facíl de controlar 
