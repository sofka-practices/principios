El principio de Common Closure (CC) es un principio de diseño de software que se enfoca en agrupar las clases y los módulos de tal forma que los que cambian juntos, permanezcan juntos. En otras palabras, este principio establece que las clases y los módulos que tienen una alta tasa de cambio deben estar agrupados juntos para minimizar el impacto de los cambios en otros módulos y reducir el acoplamiento.

En términos de la arquitectura limpia, el principio de Common Closure sugiere que los módulos que dependen de la misma política deberían estar agrupados juntos. Por ejemplo, si un conjunto de módulos están relacionados con el manejo de la autenticación de usuarios, entonces deberían estar agrupados juntos en un solo paquete o módulo. De esta manera, los cambios en las políticas de autenticación se limitan a ese conjunto de módulos y no afectan el resto de la aplicación.

Además, el principio de Common Closure también puede ayudar a mejorar la calidad del software, ya que los módulos con alta tasa de cambio suelen ser aquellos que tienen mayor probabilidad de errores. Al agrupar estos módulos juntos, se facilita su mantenimiento y actualización, lo que puede mejorar la estabilidad y la calidad del software.

En resumen, el principio de Common Closure establece que las clases y los módulos que cambian juntos, permanezcan juntos. Al aplicar este principio en la arquitectura limpia, se busca agrupar los módulos que dependen de la misma política en un solo paquete o módulo para minimizar el impacto de los cambios y mejorar la calidad del software.

## Recomendaciones

1. Identificar las clases y los módulos que tienen una alta tasa de cambio. Esto puede incluir clases relacionadas con la gestión de usuarios, la seguridad, la gestión de errores, entre otras.

2. Agrupar las clases y los módulos que cambian juntos en un mismo paquete o módulo. Por ejemplo, si un conjunto de clases están relacionadas con la gestión de errores, se pueden agrupar en un paquete o módulo dedicado a la gestión de errores.

3. Definir una interfaz pública para cada módulo agrupado. Esta interfaz pública define la funcionalidad ofrecida por el módulo y puede ser utilizada por otros módulos de la aplicación.

4. Establecer las dependencias entre los módulos. Los módulos que dependen de otro módulo deben utilizar la interfaz pública definida para ese módulo.

5. Establecer las restricciones de acceso entre los módulos. Los módulos que no necesiten acceder a un módulo determinado deben tener acceso restringido a ese módulo para reducir el acoplamiento.

Al aplicar el principio de Common Closure en proyectos de Empesariales, se pueden obtener beneficios como una mayor modularidad, una mayor facilidad de mantenimiento, una menor tasa de errores y una mayor facilidad para realizar cambios y actualizaciones.

## ¿Cómo aplicar el principio?
Supongamos que tenemos un proyecto que consta de diferentes módulos, cada uno con una funcionalidad específica, por ejemplo:

* **proyecto-app:** contiene las clases principales del proyecto.
* **proyecto-infra:** contiene las clases relacionadas con los elementos técnicos adaptativos.
* **proyecto-dominio:** contiene las clases que implementan las entidades y casos de uso del proyecto.

Para aplicar el principio de Common Closure, es recomendable agrupar los módulos que cambian juntos en un mismo paquete. En este caso, podríamos agrupar el proyecto-app y el proyecto-infra en un mismo paquete, ya que es probable que si cambiamos algo en el proyecto-app, también tengamos que modificar los dominio que lo utilizan. Además, el proyecto-infra es independiente de los otros dos módulos, por lo que debería estar en un paquete separado.

Para implementar esto en Maven, podemos crear una estructura de directorios como la siguiente:

``` shell
proyecto
|-- proyecto-app
|   |-- src/main/java/com/proyecto/app
|   `-- pom.xml
|-- proyecto-infra
|   |-- src/main/java/com/proyecto/infra
|   `-- pom.xml
|-- proyecto-dominio
|   |-- src/main/java/com/proyecto/dominio
|   `-- pom.xml
`-- pom.xml
```
En cada módulo, debemos especificar el paquete correspondiente en el archivo pom.xml:

``` xml
<parent>
    <groupId>com.proyecto</groupId>
    <artifactId>proyecto</artifactId>
    <version>1.0.0</version>
</parent>

<groupId>com.proyecto</groupId>
<artifactId>proyecto-app</artifactId>
<version>1.0.0</version>
<packaging>jar</packaging>

<modules>
    <module>proyecto-infra</module>
    <module>proyecto-dominio</module>
</modules>


``` 
En este ejemplo, hemos agregado la sección <parent> para indicar que este módulo es un submódulo del proyecto principal (proyecto), que deberá tener su propio pom.xml y estar ubicado en el directorio raíz del proyecto.

De esta manera, podemos asegurar que los módulos que cambian juntos estén agrupados en el mismo paquete y que los cambios en un módulo no afecten a los demás, lo que facilita el mantenimiento y evita posibles errores en el proyecto.

### Ejemplo
``` mermaid
graph TD;
    A[Modulo de ventas] -->|Depende de| B[Modulo de inventario];
    A -->|Depende de| C[Modulo de clientes];
    B -->|Depende de| D[Modulo de compras];
    B -->|Depende de| E[Modulo de proveedores];
    C -->|Depende de| F[Modulo de facturación];

```

En este ejemplo, se tiene una arquitectura de software que consta de diferentes módulos relacionados con ventas, inventario, clientes, compras, proveedores y facturación. Se puede ver que el módulo de ventas depende de los módulos de inventario y clientes, y que estos módulos a su vez dependen de otros módulos.

El principio de Common Closure sugiere que los módulos que cambian juntos deben estar encapsulados juntos. En este caso, los módulos relacionados con ventas, inventario y clientes pueden cambiar juntos, por lo que sería recomendable agruparlos en un mismo módulo, mientras que los módulos de compras, proveedores y facturación pueden cambiar independientemente, por lo que se recomendaría separarlos en otros módulos.

De esta manera, se puede asegurar que los cambios que se realicen en los módulos relacionados con ventas, inventario y clientes afecten únicamente a estos módulos y no a los demás, lo que facilita el mantenimiento y evita posibles errores en el sistema.
