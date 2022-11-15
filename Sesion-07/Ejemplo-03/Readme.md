# Ejemplo 03: Log4J

## OBJETIVO

- Conocer Log4J 
- Entender su configuración
- Hacer un ejemplo sencillo con loggeo usando Log4J

## DESARROLLO

Echemos un vistazo al venerable marco de log de Log4J.

En este punto, por supuesto, está desactualizado, pero vale la pena discutirlo, ya que sienta las bases para sus sucesores más modernos.

Muchos de los detalles de configuración coinciden con Log4j2 que vimos en el ejemplo 1.

### Configuración

1. Creamos un nuevo proyecto en **intelliJ** que use **Maven**.

2. En primer lugar, debe agregar la biblioteca `Log4J` al proyecto agregando la siguiente dependencia al archivo `pom.xml`:

```xml
  <dependency>
    <groupId>log4j</groupId>
    <artifactId>log4j</artifactId>
    <version>1.2.17</version>
  </dependency>
```

3. El archivo de configuración con el **appender** de consola se ve así:

```xml
<!DOCTYPE log4j:configuration SYSTEM "log4j.dtd" >
<log4j:configuration debug="false">

    <!--Console appender-->
    <appender name="stdout" class="org.apache.log4j.ConsoleAppender">
        <layout class="org.apache.log4j.PatternLayout">
            <param name="ConversionPattern" 
              value="%d{yyyy-MM-dd HH:mm:ss} %p %m%n" />
        </layout>
    </appender>

    <root>
        <level value="INFO" />
        <appender-ref ref="stdout" />
    </root>

</log4j:configuration>
```

`<log4j:configuration debug=”false”>` es una etiqueta abierta de toda la configuración que tiene una propiedad: debug . Determina si desea agregar información de depuración de Log4j a los logs.

4. Creamos una clase `Log4jExample` con el código:

```java
import org.apache.log4j.Logger;

public class Log4jExample {
    private static Logger logger = Logger.getLogger(Log4jExample.class);

    public static void main(String[] args) {
        logger.debug("Debug log message");
        logger.info("Info log message");
        logger.error("Error log message");
    }
}
```

5. Lo ejecutamos y observamos el resultado.