## Reto 01: Compilación y generación de JAR con Maven

### OBJETIVO

- Compilar y generar un archivo JAR a partir de un código Java con Maven

### DESARROLLO

Crear un programa en Java que convierta un número entero a binario, dicho programa deberá compilarse con Maven.

<details>
  <summary>Solución</summary>

  Afortunadamente Java cuenta con un método estático en la clase Integer que convierte un número entero en binario:

  ```java
  public class IntegerToBinary {
    public static void main(String [] args) {
      int number = 20;

      String binary = Integer.toBinaryString(number);

      System.out.println("El número entero " + number + " en binario es: " + binary);
    }
  }
  ```

  Por último, basados en el Ejemplo 02 y 03 podemos crear el siguiente archivo de Maven:

  ```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>reto01</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>18</maven.compiler.source>
        <maven.compiler.target>18</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

</project>
  ```

  Así al ejecutar el comando `mvn compile` generará el JAR correspondiente.
</details>