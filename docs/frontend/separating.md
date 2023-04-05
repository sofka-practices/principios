El principio Separating presentational and business/controller layer (Separación de la capa de presentación y la capa de negocio/controlador) en frontend se refiere a la separación clara de las responsabilidades entre la capa de presentación y la capa de negocio o controlador en la aplicación web o móvil. En términos simples, este principio sugiere que la lógica empresarial y de controlador no debe mezclarse con la capa de presentación, como HTML, CSS y JavaScript.

La separación de la capa de presentación y la capa de negocio/controlador permite una mayor modularidad y reutilización del código. También facilita la tarea de realizar cambios y actualizaciones en la lógica empresarial sin tener que modificar la capa de presentación.

En la práctica, esto se logra utilizando patrones de diseño como MVC (Modelo-Vista-Controlador) o MVVM (Modelo-Vista-Modelo de vista). En estos patrones, la capa de presentación se encarga de mostrar los datos y eventos de usuario a la capa de controlador o modelo, que procesa y manipula los datos según la lógica empresarial. Los cambios en los datos se reflejan en la vista a través del modelo o del controlador.

## Ejemplo

Para aplicar el principio de Separating presentational and business/controller layer en un SPA, se puede utilizar el patrón de arquitectura de Componentes Container y Componentes Presentacionales.

Los Componentes Presentacionales se encargan únicamente de la presentación y la visualización de la información, mientras que los Componentes Container se encargan de la lógica de negocio y la integración con los servicios y API.

A continuación, se muestra un ejemplo de cómo se podría estructurar una aplicación de ReactJS aplicando este principio:

``` mermaid
graph LR
A[App] --> B[Container 1]
B --> C[Presentation Component 1]
B --> D[Presentation Component 2]
B --> E[API Service]
A --> F[Container 2]
F --> G[Presentation Component 3]
F --> H[Presentation Component 4]
F --> E[API Service]
```

En este ejemplo, la aplicación se divide en dos Componentes Container principales (B y F), cada uno con sus propios Componentes Presentacionales (C, D, G y H) y utilizando un único servicio de API compartido (E).

Los Componentes Presentacionales se centran en la presentación de datos y se pueden reutilizar en múltiples Componentes Container, mientras que los Componentes Container se centran en la lógica de negocio y la integración con los servicios externos.

De esta manera, se logra una separación clara entre la capa de presentación y la capa de negocio/controlador, lo que permite una mayor flexibilidad y facilidad de mantenimiento a largo plazo.

## Gestión de estados

Los estados centralizados favorece el principio de Separating presentational and business/controller layer en frontend ya que promueve la separación de la lógica de presentación y la lógica de negocio mediante el uso de un store global para manejar el estado de la aplicación.

La lógica de negocio se puede maneja en con reducers y acciones, mientras que la lógica de presentación se maneja con estados locales. Los componentes solo acceden al estado de la aplicación a través de argumentos o propiedades y disparan acciones para actualizar el estado.


## ¿Cómo aplicar el principio?

Aquí te dejo un ejemplo de cómo se podría representar este principio de Separating presentational and business/controller layer:

### Sincrono
``` mermaid
graph LR;
  A[Componente Presentacional] -->|Eventos| B[Componente de Controlador]
  B --> |Actualiza| A
  B --> |Acciones| C(Logica/store global)
  C --> |Estados| B
```

### Asincrono

``` mermaid
graph LR;
  A[Componente Presentacional] -->|Eventos| B[Componente de Controlador]
  B --> |Actualiza| A
  C(Logica/store global) --> |Estados| B
  B --> |Llamadas| D(Servicio de API)
  D --> |Acciones|C
```

En este caso particular, el componente de presentación envía eventos al componente controlador, cuya función es ejecutar acciones para actualizar el almacenamiento de estados que maneja la lógica de negocio. La lógica  devuelve nuevos estados que se actualizan en la presentación según las decisiones del controlador. Además, el controlador realiza llamadas a los servicios de API y espera su respuesta para luego ejecutar acciones hacia la lógica o almacenamiento de estados, lo que permite actualizar los estados a nivel de representación.

De esta forma, se separa claramente la lógica de presentación de la lógica de negocio y se favorece el principio de Separating presentational and business/controller layer.
