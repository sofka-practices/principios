El principio de Having a common user input strategy se refiere a la necesidad de mantener una estrategia de entrada de datos coherente en toda la aplicación. Esto significa que los usuarios deben ser capaces de introducir información de la misma manera en todas las secciones de la aplicación, lo que facilita la interacción y la usabilidad de la misma.

Un ejemplo de una estrategia común de entrada de datos podría ser el uso de formularios en toda la aplicación. Los formularios permiten a los usuarios introducir información de manera estructurada y coherente, y también ofrecen una serie de características útiles, como validación de datos, sugerencias de autocompletado, entre otros.

Además de los formularios, existen otras formas de mantener una estrategia común de entrada de datos en toda la aplicación. Por ejemplo, el uso de controles de entrada de datos estándar, como casillas de verificación, botones de opción y menús desplegables, puede ayudar a los usuarios a sentirse más cómodos y confiados al interactuar con la aplicación.

Al mantener una estrategia común de entrada de datos en toda la aplicación, se pueden mejorar la usabilidad y la experiencia del usuario, lo que a su vez puede conducir a una mayor satisfacción del usuario y una mayor retención. Además, también puede ayudar a los desarrolladores a mantener un código más limpio y organizado, ya que se puede utilizar una biblioteca común de componentes de entrada de datos en toda la aplicación.

## UX y Sistema de Diseño

Tener una estrategia común para la entrada de datos puede mejorar la experiencia de usuario en una aplicación al proporcionar una forma consistente y fácil de entender los componetes visuales teniendo asi una linea base grafica común. Además, esto puede reducir el tiempo y el esfuerzo necesarios para desarrollar y mantener la aplicación, permitiendo que los desarrolladores se centren en mejorar la experiencia del usuario y la funcionalidad de la aplicación de una manera centrada.

Un sistema de diseño puede ayudar a establecer y mantener una estrategia común de entrada de usuario mediante la definición de patrones de diseño estandarizados para elementos de entrada comunes, como campos de texto, botones, menús desplegables, etc. Estos patrones de diseño pueden incluir la ubicación, el estilo, el tamaño y la interacción de los elementos de entrada.

Al seguir una estrategia común de entrada de usuario, se puede mejorar la coherencia de la experiencia del usuario en toda la aplicación. Los usuarios pueden entender y utilizar más fácilmente los diferentes componentes de la interfaz de usuario, lo que puede mejorar la satisfacción del usuario y la usabilidad de la aplicación. Además, seguir una estrategia común de entrada de usuario puede simplificar el proceso de desarrollo, ya que se puede reutilizar código y patrones de diseño existentes en lugar de tener que crearlos desde cero para cada componente de la interfaz de usuario.

## ¿Cómo aplicar el principio?

``` mermaid
graph LR
A[app] -->|UI library| B[design-system]
A[app] -->|logic components| C[components]
C[components] --> D[component-1.js]
C[components] --> E[component-2.js]
B[design-system] --> F[forms.js]
B[design-system] --> G[validations.js]

```

En este diagrama, se muestra cómo la aplicación se divide en dos paquetes principales: design-system y components. El paquete design-system contiene la biblioteca de interfaz de usuario (UI) y se utiliza para estandarizar la apariencia y la interacción en toda la aplicación. El paquete components contiene los componentes lógicos de la aplicación, que se construyen utilizando la biblioteca de interfaz de usuario.

La aplicación app está conectada a ambos paquetes, y cada paquete está conectado a los componentes que lo utilizan. Por ejemplo, el componente-1.js utiliza la biblioteca de botones en design-system para estandarizar la apariencia de los botones en la aplicación.

Este enfoque de separación de responsabilidades permite una mayor modularidad y reutilización de componentes en la aplicación, lo que puede mejorar la calidad del código y reducir el tiempo de desarrollo.