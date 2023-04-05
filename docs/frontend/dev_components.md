El principio "Developing components, not screens" se refiere a una práctica de desarrollo de software que se enfoca en crear componentes reutilizables en lugar de crear soluciones  orientadas a una sola pantalla o vista.

Este principio se basa en la idea de que, al crear componentes independientes y modulares, es posible crear una arquitectura de software más flexible y escalable, que permite una mayor reutilización del código y una mayor facilidad para realizar cambios y actualizaciones en el sistema.

Al desarrollar componentes en lugar de soluciones orientadas a la pantalla, se pueden crear módulos que sean independientes del contexto en el que se utilicen, lo que permite que puedan ser reutilizados en diferentes partes del sistema sin necesidad de realizar cambios significativos en el código.

Este enfoque también permite una mayor separación de preocupaciones y una mayor cohesión entre los diferentes componentes del sistema, lo que mejora la mantenibilidad del código y reduce la complejidad general del sistema.

En resumen, el principio "Developing components, not screens" promueve una arquitectura de software modular y reutilizable que se enfoca en la creación de componentes independientes en lugar de soluciones monolíticas orientadas a una sola pantalla o vista.

## ¿Cómo aplicar el principio?

A continuación, se presenta un ejemplo para ilustrar este principio:

``` mermaid
graph TD
A[MainApp] --> B[Header]
A --> C[MainContent]
A --> D[Footer]
C --> E[ArticleList]
C --> F[SideBar]
E --> G[ArticleCard]
F --> H[SearchBar]
```

En este ejemplo, se muestra una estructura básica de una aplicación con un encabezado, contenido principal y un pie de página. El contenido principal se divide en una lista de artículos y una barra lateral. Tanto la lista de artículos como la barra lateral se construyen como componentes reutilizables, donde la lista de artículos se compone de una serie de tarjetas de artículos y la barra lateral incluye un componente de barra de búsqueda.

De esta manera, el enfoque está en la creación de componentes reutilizables y modulares que se pueden utilizar en diferentes partes de la aplicación en lugar de construir pantallas monolíticas que sean difíciles de mantener y extender.