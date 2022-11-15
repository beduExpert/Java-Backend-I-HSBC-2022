## Reto 01: Log4J2

### OBJETIVO

- Prácticar el uso de la herramienta de mensajes de log.

### DESARROLLO

El objetivo del reto es crear un programa con las siguiente características:

1. Tener una clase `Sort` con un método `sorting` que recibe un arreglo y regresa el arreglo ordenado.
2. En dado caso de recibir un arreglo ordenado imprimir como log el mensaje `"el arreglo ya está ordenado"`
3. Si el arreglo es vacío, mandar como log en forma de error el mensaje `"El arreglo es vacío"`
4. Si no cumple las condiciones anteriores, entonces cuando termine el proceso de ordenamiento del arreglo imprimir como log `"se terminó de ordenar el arreglo"`
5. Todos estos mensajes deben generarse con un formato diferente.
6. Generar los logs con `Log4J2`
7. Modificar el archivo de configuración de `Log4J2` para que guarde estos logs en un archivo.
