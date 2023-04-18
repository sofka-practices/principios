## Ejercicio práctico para el principio de "The Reuse/Release Equivalence":

Supongamos que estamos desarrollando una aplicación en Java que tiene una funcionalidad para crear y enviar correos electrónicos. Queremos asegurarnos de que la funcionalidad de envío de correos electrónicos sea fácilmente reutilizable en otros proyectos. Para aplicar el principio de "The Reuse/Release Equivalence", debemos crear un paquete independiente para la funcionalidad de envío de correos electrónicos, con una API clara y bien definida. Luego, podemos publicar este paquete como una biblioteca independiente, que otros proyectos pueden utilizar fácilmente.

Para implementar este ejercicio en Java y Maven, podemos seguir los siguientes pasos:

1. Crear un nuevo proyecto de Maven para nuestra funcionalidad de envío de correos electrónicos:

    ``` bash
    mvn archetype:generate -DgroupId=com.example.email -DartifactId=email-sender -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
    ```

2. Definir la API pública para nuestra funcionalidad de envío de correos electrónicos en un paquete separado:

    ``` java
    package com.example.email.sender;

    public interface EmailSender {
        void send(String to, String subject, String body);
    }
    ```

3. Implementar la funcionalidad de envío de correos electrónicos en una clase separada:
    ``` java
    package com.example.email.sender.impl;

    import com.example.email.sender.EmailSender;

    public class EmailSenderImpl implements EmailSender {
        @Override
        public void send(String to, String subject, String body) {
            // implementación de la funcionalidad de envío de correos electrónicos
        }
    }
    ```

4. Empaquetar nuestra funcionalidad de envío de correos electrónicos en un JAR independiente:
    ``` bash
    mvn package
    ```

5. Instalar el JAR en nuestro repositorio local de Maven:
    ```bash
    mvn install
    ```

6. Ahora, otros proyectos pueden utilizar nuestra funcionalidad de envío de correos electrónicos simplemente agregando la dependencia en su archivo pom.xml:
    ```xml
    <dependency>
        <groupId>com.example.email</groupId>
        <artifactId>email-sender</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
    ```


## Ejercicio práctico para el principio de "Common Closure":

Supongamos que estamos desarrollando una aplicación que permite a los usuarios registrarse y acceder a una plataforma para comprar productos. Queremos aplicar el principio de Common Closure para asegurarnos de que cada módulo de nuestro proyecto tenga responsabilidades coherentes y estén enfocados en funcionalidades similares.

Para ello, podemos crear dos módulos: uno para la autenticación y registro de usuarios, y otro para la gestión de compras. Estos dos módulos tendrán responsabilidades claramente definidas y no se mezclarán las funcionalidades.

A continuación, te muestro cómo estructuraríamos nuestro proyecto usando este principio:

``` sh
- my-project
  - pom.xml
  - authentication-registration-module
    - pom.xml
    - src
      - main
        - java
          - com.myproject.auth
            - AuthenticationService.java
            - RegistrationService.java
  - purchase-management-module
    - pom.xml
    - src
      - main
        - java
          - com.myproject.purchase
            - PurchaseService.java
            - Product.java
```

En este ejemplo, cada módulo tiene su propio pom.xml y su propia estructura de paquetes. El módulo de autenticación y registro tiene sus clases en el paquete "com.myproject.auth", mientras que el módulo de gestión de compras tiene sus clases en el paquete "com.myproject.purchase". De esta manera, cada módulo tiene una responsabilidad claramente definida.

Para asegurarnos de que estos módulos no estén acoplados, podemos definir interfaces para cada uno de ellos y hacer que se comuniquen a través de estas interfaces. Por ejemplo, podemos definir una interfaz "UserRepository" en el módulo de autenticación y registro, y hacer que el módulo de gestión de compras use esta interfaz para acceder a los datos del usuario.

``` sh
- my-project
  - pom.xml
  - authentication-registration-module
    - pom.xml
    - src
      - main
        - java
          - com.myproject.auth
            - AuthenticationService.java
            - RegistrationService.java
            - UserRepository.java (interfaz)
  - purchase-management-module
    - pom.xml
    - src
      - main
        - java
          - com.myproject.purchase
            - PurchaseService.java
            - Product.java
            - UserRepository.java (interfaz)
```

De esta manera, estamos aplicando el principio de Common Closure para asegurarnos de que cada módulo tenga una responsabilidad coherente y que esté enfocado en funcionalidades similares. También estamos aplicando el principio de Dependency Inversion para reducir el acoplamiento entre módulos y aumentar la reutilización de código.

## Ejercicio práctico para el principio de "Common Reuse":

En este ejercicio, se aplicará el principio de Common Reuse de la Arquitectura Limpia en un proyecto Java usando Maven. El objetivo es crear una estructura de proyecto que permita reutilizar el código en diferentes proyectos.

1. Crear un proyecto Java básico usando Maven:
``` sh
mvn archetype:generate -DgroupId=com.example.commonreuse -DartifactId=myproject -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

2. En el archivo pom.xml, agregar las siguientes dependencias de Apache Commons:
``` xml
<dependencies>
    <!-- Apache Commons Lang -->
    <dependency>
        <groupId>org.apache.commons</groupId>
        <artifactId>commons-lang3</artifactId>
        <version>3.12.0</version>
    </dependency>
    
    <!-- Apache Commons Math -->
    <dependency>
        <groupId>org.apache.commons</groupId>
        <artifactId>commons-math3</artifactId>
        <version>3.6.1</version>
    </dependency>
</dependencies>
```
3. Crear una clase de utilidad en el paquete com.example.commonreuse.util:
```java
package com.example.commonreuse.util;

import org.apache.commons.lang3.StringUtils;

public class StringUtil {
    public static boolean isEmpty(String str) {
        return StringUtils.isEmpty(str);
    }

    public static boolean isNotEmpty(String str) {
        return StringUtils.isNotEmpty(str);
    }
}
```
4. Crear una clase de cálculo en el paquete com.example.commonreuse.math:
``` java
package com.example.commonreuse.math;

import org.apache.commons.math3.stat.StatUtils;

public class MathUtil {
    public static double[] calculateStatistics(double[] values) {
        double mean = StatUtils.mean(values);
        double variance = StatUtils.variance(values, mean);
        double stdDev = Math.sqrt(variance);

        return new double[]{mean, stdDev};
    }
}
```

5. Empaquetar el proyecto en un archivo JAR usando Maven:
``` sh
mvn package
```

6. Crear un nuevo proyecto Java que use el código de utilidad y de cálculo creados anteriormente. Para hacerlo, agregar la siguiente dependencia en el archivo pom.xml:
```xml
<dependency>
    <groupId>com.example.commonreuse</groupId>
    <artifactId>myproject</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
```
7. Crear una nueva clase en el nuevo proyecto que use el código de utilidad y de cálculo:
```java
package com.example.commonreuse.app;

import com.example.commonreuse.math.MathUtil;
import com.example.commonreuse.util.StringUtil;

public class App {
    public static void main(String[] args) {
        double[] values = {1, 2, 3, 4, 5};

        double[] stats = MathUtil.calculateStatistics(values);
        System.out.println("Mean: " + stats[0]);
        System.out.println("Std dev: " + stats[1]);

        String str = "   ";
        System.out.println("Is empty: " + StringUtil.isEmpty(str));
    }
}
```

8. Empaquetar el proyecto en un archivo JAR usando Maven:
```sh
mvn package
```

Con esto, se ha creado una estructura de proyecto que permite reutilizar el código de utilidad y de cálculo en diferentes proyectos. Esto se logra mediante el uso del principio Common Reuse


## Ejercicio práctico para el principio de "Stable Abstractions":

Para aplicar el principio Stable Abstractions en un proyecto Java con Maven, se pueden seguir los siguientes pasos:

1. Crear una estructura de paquetes que refleje la arquitectura del sistema y que permita separar las capas o módulos de la aplicación.

2. Definir interfaces y abstracciones que permitan desacoplar las capas o módulos de la aplicación y que se puedan usar para establecer contratos entre ellos.

3. Definir clases concretas que implementen las interfaces y abstracciones definidas en el paso anterior, y que se encarguen de realizar las operaciones específicas de cada capa o módulo.

4. Organizar los paquetes de tal forma que los paquetes de nivel superior dependan únicamente de los paquetes de nivel inferior, y no al revés. De esta forma, se garantiza que los paquetes más estables (de nivel inferior) no dependan de los menos estables (de nivel superior).

5. Aplicar el principio de inversión de dependencias para que los paquetes de nivel superior dependan solo de las abstracciones e interfaces, y no de las clases concretas.

A continuación, se presenta un ejemplo de cómo aplicar el principio Stable Abstractions en un proyecto Java con Maven:

Supongamos que se tiene una aplicación de gestión de ventas que consta de tres capas: una capa de presentación, una capa de lógica de negocio y una capa de acceso a datos. Para aplicar el principio Stable Abstractions en esta aplicación, se pueden seguir los siguientes pasos:

1. Crear una estructura de paquetes que refleje la arquitectura del sistema:
    ``` sh
    com.example.ventas
    ├── presentation
    ├── business
    └── dataaccess
    ```
2. Definir interfaces y abstracciones:
    ``` java
    // En el paquete business
    public interface VentasService {
        List<Venta> listarVentas();
        void registrarVenta(Venta venta);
    }

    // En el paquete dataaccess
    public interface VentasRepository {
        List<Venta> listarVentas();
        void registrarVenta(Venta venta);
    }
    ```
3. Definir clases concretas:
    ``` java
    // En el paquete business
    public class VentasServiceImpl implements VentasService {
        private VentasRepository ventasRepository;
        public VentasServiceImpl(VentasRepository ventasRepository) {
            this.ventasRepository = ventasRepository;
        }
        public List<Venta> listarVentas() {
            return ventasRepository.listarVentas();
        }
        public void registrarVenta(Venta venta) {
            ventasRepository.registrarVenta(venta);
        }
    }

    // En el paquete dataaccess
    public class VentasRepositoryImpl implements VentasRepository {
        public List<Venta> listarVentas() {
            // Implementación específica de acceso a datos
        }
        public void registrarVenta(Venta venta) {
            // Implementación específica de acceso a datos
        }
    }
    ```

4. Organizar los paquetes de tal forma que los paquetes de nivel superior dependan únicamente de los paquetes de nivel inferior:

    ```sh
    com.example.ventas
    ├── presentation
    │   └── business
    ├── business
    │   └── dataaccess
    └── dataaccess

    ```

5. Aplicar el principio de inversión de dependencias para que los paquetes de nivel superior dependan solo de las abstracciones e interfaces para registrar las ventas. 

    ``` java
    Venta venta = new Venta(/* información de la venta */);
    ventasService.registrarVenta(venta);
    ```


## Preguntas de Repaso

1. ¿Cuáles son los principios de arquitectura limpia?
2. ¿Qué es el principio de Common Closure? ¿Cómo se aplica en la arquitectura de software?
3. ¿Qué es el principio de Common Reuse? ¿Cómo se aplica en la arquitectura de software?
4. ¿En qué consiste el principio de Release/Reuse Equivalence?
5. ¿Qué es el principio de Acyclic Dependencies? ¿Cómo se aplica en la arquitectura de software?
6. ¿En qué consiste el principio de Stable Dependencies? ¿Cómo se aplica en la arquitectura de software?
7. ¿Qué es el principio de Stable Abstractions? ¿Cómo se aplica en la arquitectura de software?
8. ¿Cómo se relacionan los principios de arquitectura limpia con el diseño de software orientado a objetos?
9. ¿Por qué es importante seguir los principios de arquitectura limpia en el desarrollo de software?
10. ¿Qué herramientas o técnicas se pueden utilizar para aplicar los principios de arquitectura limpia en el desarrollo de software?