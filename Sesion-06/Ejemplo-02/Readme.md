## Ejemplo 02: Diferencia entre P2P y Publish/subscribe

### OBJETIVO

- Entender las diferencias entre el modelo Punto a Punto y Publish/Suscribe


### DESARROLLO

El modelo de mensajería punto a punto y el modelo de mensajería de publicación y suscripción son los dos tipos de módulos/tipos/dominios de mensajería admitidos por Java Message Service (JMS) .

Estos dos son modelos de programación que admiten mensajería asincrónica entre sistemas heterogéneos.

Hay algunos términos importantes que nos ayudarán a comprender mejor la diferencia entre los dos tipos de modelos de mensajería:

- El destino JMS es un área de ensayo que actúa como origen de los mensajes consumidos por un cliente y como destino/objetivo para los mensajes producidos.
- El productor JMS es un cliente JMS que envía un mensaje.
- El consumidor JMS es un cliente JMS que recibe un mensaje.
- Un cliente JMS puede ser tanto un productor como un consumidor de mensajes.
- La dependencia del tiempo simplemente significa que si un productor ha publicado algunos mensajes sobre un tema al que un consumidor no se ha suscrito, entonces el consumidor no recibirá los mensajes sobre ese tema.

Veamos la diferencia entre estos dos tipos de modelos de mensajería:

#### P2P
- Aquí el destino JMS es la cola.
- Aquí el productor JMS es el remitente.
- Aquí el consumidor JMS es el receptor.
- Aquí el mensaje lo recibe solo 1 consumidor JMS.
- Aquí, el consumidor JMS envía un reconocimiento al productor al recibir el mensaje.
- Aquí existe una dependencia del tiempo para que el receptor reciba el mensaje.
- Este modelo está basado en extracción, lo que significa que el receptor es responsable de solicitar que un remitente envíe nuevos mensajes.
- por ej. enviar un fax/mensaje de voz.

#### Pub Sub

- Mientras que JMS Destination en Pub sub es un tema.
- Mientras que el productor de JMS en Pub sub es un editor.
- Mientras que el consumidor de JMS en Pub sub es un suscriptor.
- Mientras está en Pub sub, varios consumidores de JMS pueden recibir un mensaje.
- Mientras está en Pub sub, el consumidor de JMS no envía ningún reconocimiento al recibir el mensaje.
- Mientras que en Pub sub, no existe una dependencia de tiempo establecida entre el productor y el consumidor.
- Si bien este modelo se basa en notificaciones automáticas, lo que significa que los mensajes se entregan automáticamente a los consumidores sin que tengan que solicitar nuevos mensajes.
- por ej. periódicos

