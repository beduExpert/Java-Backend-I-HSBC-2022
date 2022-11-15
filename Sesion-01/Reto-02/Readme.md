## Reto 02: Ejecución de una aplicación Java con Maven

### OBJETIVO

- Compilar y ejecutar un programa en Java utilizando Maven como herramienta de construcción

### DESARROLLO

Crear un programa que imprima en pantalla la suma de los primeros 100 números y que pueda ser ejecutado a través de IntelliJ.

<details>
  <summary>Solución</summary>

  Comenzaremos escribiendo la solución en Java que será crear un ciclo for desde 1 hasta 100 para ir sumando la variable de iteración:

  ```java
  public class SumOfFirst100Numbers {
    public static void main(String [] args) {
      int total = 0;
      
      for (int i = 1; i <= 100; i++) {
        total += i;
      }

      System.out.println("La suma de los primeros 100 números es: " + total);
    }
  }
  ```

  Por último bastará con ejecutar con el botón de play.
</details>