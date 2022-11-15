# Ejemplo 02: LogBack

## OBJETIVO

- Utilizar LogBack en el proceso de logs


## DESARROLLO

En este ejemplo, presentaremos la arquitectura de Logback y examinaremos cómo podemos usarla para mejorar nuestras aplicaciones. Para esto creamos un nuevo proyecto que utilice **Maven** en **intelliJ**.

### Arquitectura

La arquitectura Logback se compone de tres clases: **Logger** , **Appender** y **Layout** .

- Un **Logger** es un contexto para mensajes de log. Esta es la clase con la que interactúan las aplicaciones para crear mensajes de logs.

- Los **Appenders** colocan los mensajes de logs en sus destinos finales. Un **Logger** puede tener más de un **Appender** . Generalmente pensamos en **Appenders** como adjuntos a archivos de texto, pero **Logback** es mucho más potente que eso.

- El **Layout** prepara los mensajes para su salida. **Logback** admite la creación de clases personalizadas para dar formato a los mensajes, así como sólidas opciones de configuración para los existentes.

### Configuración 

**Logback** utiliza **Simple Logging Facade** para Java (SLF4J) como su interfaz nativa. Antes de que podamos comenzar a mandar mensajes, debemos agregar **Logback** y **SLF4J** a nuestro `pom.xml`:

```xml
<dependency>
    <groupId>ch.qos.logback</groupId>
    <artifactId>logback-core</artifactId>
    <version>1.2.6</version>
</dependency>

<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-api</artifactId>
    <version>1.7.30</version>
    <scope>test</scope>
</dependency>
```

**Logback** también requiere `logback-classic.jar`  en el classpath para el tiempo de ejecución.

Agregaremos esto a `pom.xml` como una dependencia de prueba:

```xml
<dependency>
    <groupId>ch.qos.logback</groupId>
    <artifactId>logback-classic</artifactId>
    <version>1.2.6</version>
</dependency>
```

Ahora creamos el archivo de configuración que tiene el nombre `logback.xml`, en este ejemplo crearemos un archivo de configuración sencillo, con el contenido siguiente:

```xml
<configuration>
  <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
    <encoder>
      <pattern>%d{HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
    </encoder>
  </appender>

  <root level="debug">
    <appender-ref ref="STDOUT" />
  </root>
</configuration>
```

Por último creamos una clase `Example` con el siguiente contenido:

```java
public class Example {

    private static final Logger logger 
      = LoggerFactory.getLogger(Example.class);

    public static void main(String[] args) {
        logger.info("Example log from {}", Example.class.getSimpleName());
    }
}
```

Esta clase crea un `logger` y llama a  `info()` para generar un mensaje de log.

Al ejecutarlo obtenemos el siguiente resultado

```bash
20:34:22.136 [main] INFO Example - Example log from Example
```

Resumiendo este ejemplo:

- Tenemos un **appender**  llamado STDOUT que hace referencia al nombre de clase `ConsoleAppender`.
- Hay un **layout** que describe el formato de nuestro mensaje de log.
- Nuestro código crea un  `logger` y le pasamos nuestro mensaje a través de un  método `info()`.