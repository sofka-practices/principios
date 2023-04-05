El principio "Keeping a changelog" se refiere a la práctica de mantener un registro detallado y actualizado de los cambios que se realizan en un proyecto. Este registro se conoce como "changelog" y sirve como una herramienta importante para la comunicación y el seguimiento de los cambios a lo largo del tiempo.

Un changelog típicamente incluye información como la fecha de la actualización, una descripción breve y clara de los cambios realizados, y cualquier otra información relevante para el equipo de desarrollo y los usuarios finales.

Mantener un changelog ayuda a garantizar que todos los miembros del equipo estén al tanto de los cambios realizados en el proyecto, lo que puede ayudar a evitar conflictos y errores en el futuro. Además, un changelog claro y detallado puede ayudar a los usuarios a comprender mejor las nuevas funcionalidades y a encontrar soluciones rápidas a los problemas.

En general, mantener un changelog es una buena práctica en cualquier proyecto de software, independientemente de si se trata de un proyecto frontend o backend.

## Recomendaciones
En un proyecto frontend, el principio de mantener un changelog se puede aplicar siguiendo los siguientes pasos:

1. Establecer una convención para nombrar las versiones: Es importante establecer una convención clara para nombrar las diferentes versiones del proyecto. Por ejemplo, se puede utilizar el formato "vX.Y.Z", donde "X" representa una versión mayor, "Y" representa una versión menor y "Z" representa una revisión.

2. Crear un archivo para el changelog: El changelog se puede mantener en un archivo separado en el repositorio del proyecto. Es recomendable utilizar un formato claro y estructurado, como Markdown o plain text, para que sea fácil de leer y actualizar.

3. Registrar los cambios de forma regular: Cada vez que se realice una actualización o se agregue una nueva funcionalidad al proyecto, es importante registrarla en el changelog. Es recomendable incluir la fecha de la actualización, una descripción breve y clara de los cambios realizados, y cualquier otra información relevante para el equipo de desarrollo y los usuarios finales.

4. Comunicar los cambios a los usuarios: Es importante comunicar los cambios a los usuarios del proyecto. Esto se puede hacer a través de notas de lanzamiento, actualizaciones en redes sociales o en la documentación del proyecto.

5. Mantener el changelog actualizado: Es importante mantener el changelog actualizado a medida que se realizan cambios en el proyecto. Esto ayuda a garantizar que todos los miembros del equipo estén al tanto de los cambios realizados en el proyecto y que los usuarios finales puedan comprender mejor las nuevas funcionalidades y solucionar rápidamente los problemas.

En resumen, mantener un changelog en un proyecto frontend es una buena práctica que ayuda a mantener un registro detallado y actualizado de los cambios realizados en el proyecto, lo que puede ayudar a evitar conflictos y errores en el futuro y permitir una comunicación clara y transparente entre los miembros del equipo y los usuarios finales.

## ¿Cómo aplicar el principio?
El principio de "Keeping a changelog" se trata de mantener un registro de todos los cambios y actualizaciones que se realizan en el proyecto. Esto permite a los desarrolladores y usuarios tener una mejor comprensión de los cambios que se han realizado, lo que se ha solucionado y las mejoras agregadas.

Un ejemplo de cómo se podría aplicar este principio en un proyecto frontend sería:

Supongamos que estamos trabajando en un proyecto de desarrollo de una aplicación web y se ha realizado una nueva actualización. Para mantener un registro de los cambios realizados, se podría crear un archivo de registro de cambios (changelog) en el directorio raíz del proyecto.

El archivo podría tener una estructura similar a esta:

``` shell
## [2.0.0] - 2023-04-01

### Added
- Nuevo componente de búsqueda.

### Changed
- Mejoras en el rendimiento del componente de inicio.

### Fixed
- Solución de errores menores en el componente de perfil.

## [1.0.0] - 2023-03-01

### Added
- Componentes de inicio, perfil y registro.
- Integración con la API RESTful.

```

En este ejemplo, se puede ver que se han registrado todos los cambios realizados desde la versión 1.0.0 hasta la versión 2.0.0 del proyecto, incluyendo la fecha de la actualización y las modificaciones realizadas en el código.

Con esta información, tanto los desarrolladores como los usuarios pueden comprender rápidamente qué cambios se han realizado y cuándo se han implementado. Esto ayuda a mantener el proyecto organizado y facilita la comunicación y colaboración entre los miembros del equipo de desarrollo.

### Usar los logs de Git

Una forma común de aplicar este principio en un proyecto de frontend es mediante el uso de los logs de git. En git, es posible crear un registro de los cambios realizados en el repositorio del proyecto utilizando el comando git log. Este comando muestra una lista de los commits realizados en orden cronológico inverso, es decir, los cambios más recientes aparecen primero.

Para mantener un changelog adecuado en git, es recomendable seguir ciertas convenciones en el mensaje de cada commit. Una forma común de hacerlo es utilizando el formato "tipo: mensaje". El tipo puede ser una de las siguientes opciones:

* feat: Nueva funcionalidad
* fix: Corrección de un error
* docs: Cambios en la documentación
* style: Cambios en el estilo de código (sin cambios en la funcionalidad)
* refactor: Cambios en el código que no afectan la funcionalidad
* test: Agregado o modificación de pruebas
* chore: Cambios en el proceso de construcción o en herramientas auxiliares

Por ejemplo, un mensaje de commit adecuado podría ser:
``` shell
feat: Agregada nueva funcionalidad de búsqueda
```

También es recomendable incluir más detalles en el mensaje del commit, como la razón detrás de los cambios realizados y cualquier impacto que puedan tener en el proyecto.

Al mantener un changelog adecuado utilizando los logs de git, los desarrolladores pueden fácilmente revisar los cambios realizados en el proyecto y mantener a los colaboradores y usuarios informados sobre las actualizaciones y mejoras.

Para obtener los registros (logs) de Git necesarios para crear un changelog, se puede utilizar el comando git log. Este comando muestra el historial de confirmaciones en un repositorio de Git. Aquí hay algunos ejemplos de cómo utilizar este comando para obtener los registros necesarios:

* Para ver las confirmaciones entre dos etiquetas (tags) en particular:
    ``` shell
    git log <tag1>...<tag2> --pretty=format:"%h %s"
    ```
    Este comando muestra las confirmaciones entre <tag1> y <tag2> y se muestra en el formato hash commit mensaje.

* Para ver las confirmaciones en una rama específica:
    ``` shell
    git log <branch> --pretty=format:"%h %s"
    ```
    Este comando muestra las confirmaciones en la rama especificada y se muestra en el formato hash commit mensaje.

* Para ver las confirmaciones entre dos fechas específicas:
    ``` shell
    git log --after="<fecha1>" --before="<fecha2>" --pretty=format:"%h %s"
    ```
    Este comando muestra las confirmaciones entre <fecha1> y <fecha2> y se muestra en el formato hash commit mensaje.

Después de obtener los registros de Git necesarios, se puede crear un archivo de changelog utilizando esta información y formatearla de una manera fácil de leer y entender para los usuarios finales. Por lo general, los archivos de changelog incluyen información sobre las características nuevas, mejoras y correcciones de errores implementadas en cada versión del software.



