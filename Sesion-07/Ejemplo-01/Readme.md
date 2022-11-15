# Ejemplo 01: Log4J2

## OBJETIVO

- Conocer Log4J2
- Entender su configuración
- Hacer un ejemplo sencillo con loggeo usando Log4J2

## DESARROLLO

Log4j 2 es una versión nueva y mejorada del marco de registro de Log4j. La mejora más convincente es la posibilidad de log asíncrono. Log4j 2 requiere las siguientes bibliotecas:

- `log4j-api`
- `log4j-core`

Para este ejemplo inicializamos un proyecto con **Maven** desde **intelliJ**

### Configuración

1. En primer lugar, debe agregar la biblioteca `Log4J2` al proyecto agregando la siguiente dependencia al archivo `pom.xml`:

```xml
<dependency>
    <groupId>org.apache.logging.log4j</groupId>
    <artifactId>log4j-api</artifactId>
    <version>2.6.1</version>
</dependency>
<dependency>
    <groupId>org.apache.logging.log4j</groupId>
    <artifactId>log4j-core</artifactId>
    <version>2.6.1</version>
</dependency>
```
2. La configuración de `Log4j2` se basa en el archivo de configuración principal `log4j2.xml`. Lo primero que hay que configurar es el agregador.

Estos determinan dónde se enrutará el mensaje de log. El destino puede ser una consola, un archivo, un socket, etc.

Log4j2 tiene muchos appenders para diferentes propósitos, puede encontrar más información en el sitio oficial de `Log4j2`.

Echemos un vistazo a un ejemplo de configuración simple.

3. Creamos el archivo `log4j2.xml` con el siguiente contenido:

```xml
<Configuration status="debug" name="baeldung" packages="">
    <Appenders>
        <Console name="stdout" target="SYSTEM_OUT">
            <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss} %p %m%n"/>
        </Console>
    </Appenders>
</Configuration>
```

Puede establecer un nombre para cada agregador, por ejemplo, use la consola de nombres en lugar de la salida estándar .

Observe el elemento PatternLayout: esto determina cómo debe verse el mensaje. En nuestro ejemplo, el patrón se establece en función del parámetro de patrón , donde %d determina el patrón de fecha, %p : salida del nivel de registro, %m : salida del mensaje registrado y %n : agrega un nuevo símbolo de línea.

4. Finalmente, para habilitar un agregador (o varios), debe agregarlo a la sección `<Root>`:

```xml
<Root level="error">
    <AppenderRef ref="STDOUT"/>
</Root>
```

### Login en archivos

A veces necesitará guardar el log en un archivo, por lo que agregaremos **fout logger** a nuestra configuración:

```xml
<Appenders>
    <File name="fout" fileName="baeldung.log" append="true">
        <PatternLayout>
            <Pattern>%d{yyyy-MM-dd HH:mm:ss} %-5p %m%nw</Pattern>
        </PatternLayout>
    </File>
</Appenders>
```

El agregador de archivos tiene varios parámetros que se pueden configurar:

- **file** : determina el nombre de archivo del archivo de registro
- **append** : el valor predeterminado para este parámetro es verdadero, lo que significa que, de manera predeterminada, un agregador de archivos se agregará a un archivo existente y no lo truncará.
- **PatternLayout** que se describió en el ejemplo anterior.

Para habilitar el agregador de archivos , debe agregarlo a la sección `<Root>`:

```xml
<Root level="INFO">
    <AppenderRef ref="stdout" />
    <AppenderRef ref="fout"/>
</Root>
```

### Log Asíncrono

Si desea que su Log4j2 sea asincrónico, debe agregar la biblioteca **LMAX disruptor** a su `pom.xml`. **LMAX disruptor** es una biblioteca de comunicación entre subprocesos sin bloqueo.

Agregar **disruptor** a `pom.xml`:

```xml
<dependency>
    <groupId>com.lmax</groupId>
    <artifactId>disruptor</artifactId>
    <version>3.3.4</version>
</dependency>
```

Si desea usar el **LMAX disruptor**, debe usar `<asyncRoot>` en lugar de `<Root>` en la configuración.

```xml
<AsyncRoot level="DEBUG">
    <AppenderRef ref="stdout" />
    <AppenderRef ref="fout"/>
</AsyncRoot>
```

### Uso

Ahora probemos los logs.

1. Creamos una nueva clase en el proyecto llamada **Log4jExample** con el siguiente contenido.

```java
import org.apache.logging.log4j.Logger;
import org.apache.logging.log4j.LogManager;

public class Log4jExample {

    private static Logger logger = LogManager.getLogger(Log4jExample.class);

    public static void main(String[] args) {
        logger.debug("Debug log message");
        logger.info("Info log message");
        logger.error("Error log message");
    }
}
```

al ejecutarlo nos debe imprimir lo siguiente en la consola:

```bash
2016-06-16 17:02:13 INFO  Info log message
2016-06-16 17:02:13 ERROR Error log message
```

