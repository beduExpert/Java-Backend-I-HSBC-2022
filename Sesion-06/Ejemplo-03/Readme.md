## Ejemplo 03: Diferencia entre AMQP y JMS

### OBJETIVO

- Entender las diferencias entre AMQP y JMS


### DESARROLLO

1. Protocolo de cola de mensajes avanzado (AMQP): 

Es un protocolo que se utiliza para la comunicación entre aplicaciones. Es un protocolo ligero que soporta las aplicaciones para su transferencia de datos. Este protocolo se utiliza por su escalabilidad y modularidad con las tecnologías. 

2. Servicio de mensajes de Java (JMS): 

Es una interfaz de programa de aplicación (API) que admite la comunicación de la computadora en una red. Es una poderosa API utilizada para recibir los mensajes generados durante la comunicación. 

#### AMQP

- Protocolo avanzado de colas de mensajes.
- Fue desarrollado por JPMorgan Chase.
- Todos los clientes compatibles con AMQP pueden comunicarse entre sí.
- Utiliza Direct, Fanout, Topic y Headers.
- AMQP es un protocolo.
- AMQP solo usa y admite tipos de datos binarios.
- La seguridad es compatible con la capa de seguridad y autenticación simple (SASL).
- Son los productores los que envían el mensaje y luego se pone en cola.
- Es flexible con muchas tecnologías.

#### JMS 

- Servicio de mensajes de Java.
- Fue desarrollado por Sun Microsystems.
- La aplicación debe utilizar la API de JMS para comunicarse.
- Utiliza Publicación/Suscripción y P2P (Punto a Punto).
- JMS es una API estándar.
- JMS admite cinco tipos de datos denominados MapMessage, ObjectMessage, Text message, StreamMessage y BytesMessage.
- No se proporciona seguridad y depende del proveedor de JMS.
- Es manejado por los productores y envía directamente al tema.
- No es una tecnología flexible, ya que está hecha solo para Java.

