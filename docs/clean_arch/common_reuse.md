El principio de Common Reuse es uno de los principios de la arquitectura limpia que se enfoca en la reutilización de código. Según este principio, los módulos de un sistema deben ser diseñados de tal manera que los componentes reutilizables se agrupen en módulos separados de los componentes específicos del negocio.

El principio de Common Reuse establece que los módulos de un sistema deberían ser diseñados para que se puedan reutilizar en diferentes contextos. Esto significa que el código que se escribe para un módulo debería ser lo más general posible y no estar diseñado específicamente para un caso de uso o requisito en particular.

El objetivo de este principio es fomentar la reutilización de código en todo el sistema, lo que reduce la cantidad de código duplicado y mejora la calidad general del sistema. Además, la reutilización de código también puede reducir el tiempo y los costos de desarrollo, ya que los desarrolladores pueden utilizar código existente en lugar de escribirlo desde cero.

## Recomendaciones

* Identificar los componentes reutilizables del sistema y agruparlos en módulos separados.
* Diseñar los módulos de manera que los componentes reutilizables sean lo más generales posible y no estén específicamente diseñados para un caso de uso en particular.
* Establecer interfaces claras y bien definidas entre los módulos para promover la independencia y la interoperabilidad.
Documentar y publicar los módulos reutilizables para que otros desarrolladores puedan utilizarlos fácilmente.
* Establecer prácticas de control de versiones y actualización de los módulos para garantizar que se mantengan actualizados y sean compatibles con otras partes del sistema.

En resumen, el principio de Common Reuse se enfoca en fomentar la reutilización de código en la arquitectura de un sistema. Al seguir las prácticas recomendadas y diseñar los módulos de manera que los componentes reutilizables sean lo más generales posible, se puede mejorar la calidad general del sistema, reducir los costos de desarrollo y fomentar la colaboración y la interoperabilidad entre los equipos de desarrollo.

## ¿Cómo aplicar el principio?


1. **Identificar el componente común:** Ejemplo, la base de datos es el componente común que se utilizará en todo el proyecto.

2. **Separar el componente común:** Se puede crear un módulo separado en el proyecto para manejar todas las interacciones con la base de datos. Este módulo puede ser un proyecto de  independiente dentro del proyecto principal.

3. **Establecer estándares de codificación:** Para establecer estándares de codificación, ejemplo se puede utilizar un patrón de diseño DAO (Data Access Object) para la capa de acceso a datos. Este patrón de diseño establece una interfaz para el acceso a datos y proporciona una implementación para cada tipo de entidad.

4. **Documentar el componente común:** Es importante documentar la estructura y el funcionamiento del módulo de acceso a datos, de modo que otros desarrolladores puedan comprender cómo usarlo de manera efectiva y eficiente.

5. **Hacer pruebas de regresión:** Es necesario hacer pruebas de regresión en el módulo de acceso a datos para asegurarse de que cualquier cambio en la interacción con la base de datos  no afecte negativamente a otras partes del proyecto.

## Ejemplo

Supongamos que tenemos un proyecto Java que tiene que interactuar con una base de datos MySQL en diferentes partes del código. En lugar de escribir el código para interactuar con la base de datos en cada parte del proyecto, podemos crear un módulo separado que maneje todas las interacciones con la base de datos.

El siguiente diagrama Mermaid ilustra la estructura del proyecto y cómo se relacionan los diferentes módulos:
``` mermaid
graph TD
A[Proyecto Maven] -->|Dependencia| B[myproject-dao]
B -->|Interacciones con BD| C[MySQL Connector]
```

En este diagrama, la caja A representa el proyecto Maven principal, la caja B representa el módulo myproject-dao que maneja todas las interacciones con la base de datos, y la caja C representa la dependencia de MySQL Connector que se utiliza en el módulo myproject-dao.

El siguiente diagrama Mermaid ilustra cómo se utiliza el módulo myproject-dao en el proyecto principal:

``` mermaid
graph TD
A[Proyecto Maven] -->|Utiliza| B[myproject-dao]
B -->|Interacciones con BD| C[MySQL Connector]
```

En este diagrama, la caja A representa el proyecto Maven principal, la caja B representa el módulo myproject-dao que maneja todas las interacciones con la base de datos, y la caja C representa la dependencia de MySQL Connector que se utiliza en el módulo myproject-dao.

Al utilizar la estructura de proyecto ilustrada en estos diagramas, hemos creado un módulo separado que maneja todas las interacciones con la base de datos, lo que nos permite reutilizar el código en diferentes partes del proyecto, mientras mantenemos una estructura clara y estandarizada para nuestro proyecto.


