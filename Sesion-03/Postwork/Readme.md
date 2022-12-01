## Sesión 4: Aplicación de línea de comandos

### 🎯 OBJETIVO

- Estructura inciial del proyecto

### DESARROLLO

En esta sesión aprendimos qué es Spring Framework y cómo Spring Boot facilita aún más el desarrollo de aplicaciones backend.

Recuerda que todo lo trabajado en tu prework, así como durante la sesión, puede ser aplicado a tu proyecto personal. 

### Asegúrate de comprender:

1. Cómo utilizar el Spring Initializr para crear un proyecto
2. Cómo configurar un proyecto de Maven
3. Cómo crear un código base de Spring Boot


### Indicaciones generales
Para este postwork se generará el esqueleto inicial del proyecto que estaremos realizando a lo largo de estos dos módulos. Este proyecto es una API REST, por lo que los primeros pasos son definir la estructura inicial del proyecto. Es importante notar que los datos que se usan en el entregable de esta sesión son de prueba  y sin persistencia ya que aún no contamos con una base de datos.
Deberás realizar las siguientes tareas:

- Generación del proyecto a partir de Spring initializr.
- Identificar las entidades presentes en tu proyecto (los actores de este, que eventualmente se convertirán en tablas en la base de datos)
- Creación de controladores siguiendo el patrón MVC para cada una de las entidades con los siguientes métodos:
   - Consulta de información 
   - Guardado de información
   - Actualización de información
   - Eliminación de la información

En cada controlador será necesario contar con una fuente de datos, como un arreglo que simule los registros de cada entidad para que este pueda fungir como Base de Datos temporal en el proyecto

No olvides consultar la checklist de tu avance de postwork de la sesión en la sección correspondiente de la app Bedu.