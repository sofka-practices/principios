El principio de bounded contexts, o contextos delimitados en español, es un principio de diseño de software que se utiliza en arquitecturas de software basadas en el patrón de diseño Domain-Driven Design (DDD). Este principio establece que los límites de un contexto del negocio deben ser explícitamente definidos y que cada contexto debe ser independiente y tener un lenguaje ubicuo propio.

En otras palabras, el principio de bounded contexts sugiere que un sistema complejo se puede dividir en múltiples contextos delimitados, cada uno de los cuales representa una parte del negocio. Cada contexto delimitado debe tener su propio modelo de datos, reglas de negocio y lenguaje específico que se utiliza en la comunicación entre los diferentes miembros del equipo de desarrollo, los stakeholders y los usuarios del sistema.

El principio de bounded contexts ayuda a mantener la claridad y la coherencia en el diseño del software al separar el modelo de dominio en diferentes contextos y alentar a que cada uno de ellos tenga su propio lenguaje específico. Esto evita confusiones y malentendidos en el equipo de desarrollo, ya que cada contexto tiene su propio significado específico para los términos y conceptos utilizados en el negocio.

Por ejemplo, en una aplicación de comercio electrónico, se pueden definir dos contextos delimitados: uno para la gestión de pedidos y otro para la gestión de clientes. Cada uno de estos contextos tendría su propio modelo de datos, sus propias reglas de negocio y su propio lenguaje específico. Los términos utilizados en el contexto de gestión de pedidos, como "estado del pedido" o "fecha de entrega", pueden tener un significado diferente al contexto de gestión de clientes.

Al definir contextos delimitados, se puede mantener una estructura clara y coherente en el diseño del software, lo que hace que el sistema sea más fácil de entender, mantener y escalar. Además, la independencia entre los diferentes contextos permite que cada uno pueda evolucionar de manera independiente sin afectar a otros contextos, lo que hace que el sistema sea más flexible y adaptable.

## Casos o Escenarios

Tomando como ejemplo la aplicación de comercio electrónico mencionada anteriormente, podríamos definir los siguientes contextos delimitados:

1. **Contexto de gestión de pedidos:** Este contexto se encargaría de la gestión de los pedidos realizados por los clientes. En este contexto se definirían los modelos de datos para representar los pedidos y se implementarían las reglas de negocio relacionadas con la gestión de pedidos, como la validación de datos del pedido, la actualización del estado del pedido y la generación de facturas. El lenguaje específico de este contexto podría incluir términos como "estado del pedido", "fecha de entrega" o "número de seguimiento".

2. **Contexto de gestión de clientes:** Este contexto se encargaría de la gestión de los clientes de la tienda en línea. En este contexto se definirían los modelos de datos para representar los clientes y se implementarían las reglas de negocio relacionadas con la gestión de clientes, como la validación de datos del cliente, la gestión de direcciones de envío y la autenticación de los clientes. El lenguaje específico de este contexto podría incluir términos como "dirección de envío", "historial de compras" o "credenciales de acceso".

Cada uno de estos contextos tendría su propia lógica de negocio, sus propios modelos de datos y su propio lenguaje específico. Además, cada contexto tendría su propia capa de servicios y controladores para exponer su funcionalidad a otras partes de la aplicación. Esto permite que cada contexto se pueda evolucionar de manera independiente, sin afectar a otros contextos, lo que hace que el sistema sea más flexible y escalable.

## ¿Cómo se aplicaría este principio?

``` mermaid

graph TD
  subgraph Contexto del Dominio
    A[Agencia]
    E[Empleado]
    C[Cliente]
    P[Paquete]
  end

  subgraph Contexto de la Logística
    LP[Logística Paquetería]
    LS[Logística Servicio Postal]
    T[Transportista]
  end

  subgraph Contexto del Financiero
    F[Facturación]
    CC[Cuentas por Cobrar]
    CP[Cuentas por Pagar]
  end

  A -- Conoce --> E
  A -- Conoce --> C
  A -- Conoce --> P
  A --> LP
  A --> LS
  LP --> T
  LS --> T
  A --> F
  F -- Conoce --> CC
  F -- Conoce --> CP

```

En este ejemplo, se pueden ver tres contextos claramente definidos: el Contexto del Dominio, el Contexto de la Logística y el Contexto del Financiero. Cada uno tiene un conjunto de entidades relacionadas que se agrupan dentro de ese contexto. Además, hay algunas conexiones entre los diferentes contextos, como que la Agencia conoce tanto a los Empleados como a los Clientes, y que el Contexto de la Logística se comunica con la Agencia a través de Transportistas. Esto ilustra cómo diferentes contextos pueden interactuar entre sí en un sistema de software.