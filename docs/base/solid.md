# SOLID

Los principios SOLID en el desarrollo de software son un conjunto de principios de diseño orientados a objetos que buscan promover la claridad, la simplicidad y la mantenibilidad del código. Estos principios fueron propuestos por Robert C. Martin y se basan en la idea de que el código debe ser fácil de entender, extender y modificar.

A continuación, se describen brevemente cada uno de los principios SOLID:

* S - Principio de responsabilidad única (Single Responsibility Principle): Cada clase o módulo debe tener una sola responsabilidad, es decir, una única razón para cambiar. Esto ayuda a mantener el código claro y organizado, y a reducir la complejidad.

* O - Principio de abierto/cerrado (Open/Closed Principle): Las clases o módulos deben estar abiertos para la extensión, pero cerrados para la modificación. Esto significa que se deben poder agregar nuevas funcionalidades sin tener que modificar el código existente.

* L - Principio de sustitución de Liskov (Liskov Substitution Principle): Las clases hijas deben poder ser sustituidas por sus clases padres sin afectar el comportamiento del programa. Esto garantiza la interoperabilidad y la reutilización del código.

* I - Principio de segregación de interfaces (Interface Segregation Principle): Los clientes de una interfaz no deben estar obligados a implementar métodos que no utilizan. Esto promueve la modularidad y la flexibilidad del código.

* D - Principio de inversión de dependencias (Dependency Inversion Principle): Los módulos de alto nivel no deben depender de módulos de bajo nivel, sino de abstracciones. Esto permite una mayor independencia de los componentes del sistema y facilita la realización de cambios.

En resumen, la aplicación de los principios SOLID puede ayudar a los desarrolladores de software a crear código más limpio, mantenible y extensible, lo que a su vez puede mejorar la calidad y eficiencia del software.

## Single Responsibility Principle

El principio de responsabilidad única (Single Responsibility Principle)  se refiere a que cada clase debe tener una sola responsabilidad. Un ejemplo de aplicación de este principio podría ser el siguiente:

Supongamos que tenemos una entidad llamada Empleado que se encarga de almacenar los datos de un empleado, como su nombre, número de identificación, salario y cargo. Si aplicamos el principio de responsabilidad única, deberíamos dividir esta clase en dos clases diferentes, cada una con su propia responsabilidad. Una posible solución podría ser la siguiente:

``` java
public class Empleado {
    private String nombre;
    private int id;
    private double salario;
    private String cargo;

    public Empleado(String nombre, int id, double salario, String cargo) {
        this.nombre = nombre;
        this.id = id;
        this.salario = salario;
        this.cargo = cargo;
    }

    public String getNombre() {
        return nombre;
    }

    public int getId() {
        return id;
    }

    public double getSalario() {
        return salario;
    }

    public String getCargo() {
        return cargo;
    }
}
```
``` java
public class EmpleadoDAO {
    public void guardarEmpleado(Empleado empleado) {
        // Lógica para guardar el empleado en la base de datos
    }

    public void actualizarEmpleado(Empleado empleado) {
        // Lógica para actualizar los datos del empleado en la base de datos
    }

    public void eliminarEmpleado(Empleado empleado) {
        // Lógica para eliminar el empleado de la base de datos
    }
}
```

En este ejemplo, la clase Empleado se encarga únicamente de almacenar los datos de un empleado y proporciona métodos para acceder a ellos. La clase EmpleadoDAO, por otro lado, se encarga de interactuar con la base de datos para guardar, actualizar y eliminar los datos de un empleado. De esta manera, cada clase tiene su propia responsabilidad y se cumple el principio de responsabilidad única.

## Open/Closed Principle

El principio de abierto/cerrado (Open/Closed Principle)  se refiere a que las clases o módulos deben estar abiertos para la extensión, pero cerrados para la modificación. Un ejemplo de aplicación de este principio podría ser el siguiente:

Supongamos que tenemos una clase llamada Calculadora que se encarga de realizar operaciones matemáticas básicas, como sumar, restar, multiplicar y dividir. Si queremos agregar una nueva operación, por ejemplo, calcular la raíz cuadrada, no deberíamos modificar la clase Calculadora, sino extenderla mediante una nueva clase. Una posible solución podría ser la siguiente:

``` java
public class Calculadora {
    public double sumar(double a, double b) {
        return a + b;
    }

    public double restar(double a, double b) {
        return a - b;
    }

    public double multiplicar(double a, double b) {
        return a * b;
    }

    public double dividir(double a, double b) {
        return a / b;
    }
}

public class CalculadoraAvanzada extends Calculadora {
    public double raizCuadrada(double a) {
        return Math.sqrt(a);
    }
}
```
En este ejemplo, la clase Calculadora se encarga de realizar las operaciones matemáticas básicas. Si queremos agregar una nueva operación, en este caso la raíz cuadrada, en lugar de modificar la clase Calculadora, creamos una nueva clase llamada CalculadoraAvanzada que extiende de la clase Calculadora y agrega el método raizCuadrada(). De esta manera, se cumple el principio de abierto/cerrado, ya que la clase Calculadora está cerrada para la modificación y abierta para la extensión mediante la creación de nuevas clases.

## Liskov Substitution Principle

El principio de sustitución de Liskov (Liskov Substitution Principle)  se refiere a que los objetos de una clase derivada deben poder ser utilizados en lugar de los objetos de la clase base sin afectar la integridad del programa. Un ejemplo de aplicación de este principio podría ser el siguiente:

Supongamos que tenemos una clase llamada Figura que representa una figura geométrica y tiene un método para calcular su área:

``` java
public abstract class Figura {
    public abstract double area();
}
```

Ahora, creamos dos clases derivadas de Figura: Rectangulo y Triangulo:

``` java
public class Rectangulo extends Figura {
    private double base;
    private double altura;

    public Rectangulo(double base, double altura) {
        this.base = base;
        this.altura = altura;
    }

    @Override
    public double area() {
        return base * altura;
    }
}

public class Triangulo extends Figura {
    private double base;
    private double altura;

    public Triangulo(double base, double altura) {
        this.base = base;
        this.altura = altura;
    }

    @Override
    public double area() {
        return (base * altura) / 2;
    }
}

```

Ahora, si queremos calcular el área de una figura, podemos crear una función que reciba un objeto de tipo Figura y utilice su método area() para calcular su área:

``` java
public static void imprimirArea(Figura figura) {
    System.out.println("El área es: " + figura.area());
}
```

Esta función puede recibir como argumento un objeto de la clase Rectangulo o de la clase Triangulo, ya que ambas clases son subclases de Figura y cumplen el contrato definido por la clase base.

De esta manera, se cumple el principio de sustitución de Liskov, ya que los objetos de las clases derivadas (Rectangulo y Triangulo) pueden ser utilizados en lugar de los objetos de la clase base (Figura) sin afectar la integridad del programa.

## Interface Segregation Principle

El principio de segregación de interfaces (Interface Segregation Principle) se refiere a que una clase no debe implementar interfaces que no utiliza. Un ejemplo de aplicación de este principio  podría ser el siguiente:

Supongamos que tenemos una interfaz llamada Vehiculo que define los métodos básicos que debe tener cualquier vehículo:

``` java
public interface Vehiculo {
    public void acelerar();
    public void frenar();
    public void girar();
}
```
Ahora, creamos una clase llamada Coche que implementa la interfaz Vehiculo:
``` java
public class Coche implements Vehiculo {
    @Override
    public void acelerar() {
        System.out.println("El coche está acelerando.");
    }

    @Override
    public void frenar() {
        System.out.println("El coche está frenando.");
    }

    @Override
    public void girar() {
        System.out.println("El coche está girando.");
    }
}

```

Sin embargo, supongamos que ahora queremos agregar la funcionalidad de encender y apagar el coche. En lugar de agregar estos métodos a la interfaz Vehiculo, creamos una nueva interfaz llamada CocheElectrico que define los métodos adicionales:

``` java
public interface CocheElectrico {
    public void encender();
    public void apagar();
}
```
Ahora, podemos crear una nueva clase llamada CocheElectricoImpl que implementa ambas interfaces:

``` java
public class CocheElectricoImpl implements Vehiculo, CocheElectrico {
    @Override
    public void acelerar() {
        System.out.println("El coche eléctrico está acelerando.");
    }

    @Override
    public void frenar() {
        System.out.println("El coche eléctrico está frenando.");
    }

    @Override
    public void girar() {
        System.out.println("El coche eléctrico está girando.");
    }

    @Override
    public void encender() {
        System.out.println("El coche eléctrico está encendido.");
    }

    @Override
    public void apagar() {
        System.out.println("El coche eléctrico está apagado.");
    }
}

```

De esta manera, se cumple el principio de segregación de interfaces, ya que la clase CocheElectricoImpl implementa sólo los métodos que necesita y no implementa los métodos que no utiliza de la interfaz Vehiculo.

## Dependency Inversion Principle

El principio de inversión de dependencia (Dependency Inversion Principle)  se refiere a que los módulos de un programa deben depender de abstracciones en lugar de depender de implementaciones concretas. Un ejemplo de aplicación de este principio  podría ser el siguiente:

Supongamos que tenemos una clase llamada Impresora que tiene un método para imprimir un documento:

``` java
public class Impresora {
    public void imprimir(Documento documento) {
        System.out.println("Imprimiendo documento: " + documento.getContenido());
    }
}
```

Ahora, creamos una clase llamada Documento que representa un documento y tiene un método para obtener su contenido:

``` java
public class Documento {
    private String contenido;

    public Documento(String contenido) {
        this.contenido = contenido;
    }

    public String getContenido() {
        return contenido;
    }
}
```

Sin embargo, supongamos que ahora queremos agregar la funcionalidad de enviar el documento por correo electrónico. En lugar de modificar la clase Impresora, creamos una interfaz llamada DispositivoSalida que define un método para enviar el documento a un dispositivo de salida:

``` java
public interface DispositivoSalida {
    public void enviarDocumento(Documento documento);
}

```

Ahora, creamos dos nuevas clases que implementan esta interfaz: ImpresoraImpl y CorreoElectronicoImpl.

``` java
public class ImpresoraImpl implements DispositivoSalida {
    @Override
    public void enviarDocumento(Documento documento) {
        Impresora impresora = new Impresora();
        impresora.imprimir(documento);
    }
}

public class CorreoElectronicoImpl implements DispositivoSalida {
    @Override
    public void enviarDocumento(Documento documento) {
        System.out.println("Enviando correo electrónico con documento: " + documento.getContenido());
    }
}

```

Por último, modificamos la clase Documento para que reciba como argumento un objeto de tipo DispositivoSalida en lugar de un objeto de tipo Impresora:

``` java
public class Documento {
    private String contenido;

    public Documento(String contenido) {
        this.contenido = contenido;
    }

    public void enviar(DispositivoSalida dispositivoSalida) {
        dispositivoSalida.enviarDocumento(this);
    }

    public String getContenido() {
        return contenido;
    }
}

```

Ahora, podemos crear un objeto de tipo Documento y enviarlo a una impresora o por correo electrónico utilizando el método enviar():

``` java
Documento documento = new Documento("Este es el contenido del documento.");
DispositivoSalida dispositivoSalida = new CorreoElectronicoImpl();
documento.enviar(dispositivoSalida);

```

De esta manera, se cumple el principio de inversión de dependencia, ya que la clase Documento depende de la abstracción DispositivoSalida en lugar de depender de una implementación concreta como la clase Impresora.


## ¿Cómo se aplicaría este principio?

``` mermaid
classDiagram
    class Shape {
        +int x
        +int y
        +double area()
    }
    class Rectangle {
        +int width
        +int height
        +double area()
    }
    class Circle {
        +int radius
        +double area()
    }
    class ShapeAreaCalculator {
        +double calculateArea(Shape shape)
    }
    Shape <|-- Rectangle
    Shape <|-- Circle
    ShapeAreaCalculator ..> Shape
```

En este ejemplo se observa la aplicación de los principios de Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation y Dependency Inversion, que conforman el acrónimo SOLID.

- Single Responsibility: Cada clase (Shape, Rectangle y Circle) tiene una única responsabilidad, la de calcular su propia área.
- Open/Closed: Las clases Shape, Rectangle y Circle están abiertas para su extensión (por ejemplo, para agregar nuevas formas), pero cerradas para su modificación.
- Liskov Substitution: La clase Rectangle y Circle son subtipos de Shape y pueden ser utilizados en lugar de Shape sin alterar el comportamiento de la clase ShapeAreaCalculator.
- Interface Segregation: La clase ShapeAreaCalculator sólo depende de la interfaz Shape, que contiene los métodos necesarios para calcular el área de cualquier forma.
- Dependency Inversion: La clase ShapeAreaCalculator depende de la abstracción Shape en lugar de las clases concretas Rectangle y Circle.