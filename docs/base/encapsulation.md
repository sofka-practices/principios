El principio de encapsulamiento es uno de los conceptos fundamentales de la programación orientada a objetos. Se refiere a la técnica de ocultar los detalles internos de una clase y exponer solo una interfaz pública bien definida para interactuar con ella.

La encapsulación permite que el código sea más modular y más fácil de mantener, ya que los cambios en la implementación interna de una clase no afectarán a otros componentes del sistema que dependen de ella. Además, la encapsulación promueve la seguridad y la integridad de los datos, ya que solo los métodos de la clase que exponen la interfaz pública pueden modificar los datos internos de la clase.

Para implementar la encapsulación, se definen los atributos y métodos de una clase como públicos, privados o protegidos. Los atributos privados solo son accesibles dentro de la propia clase, mientras que los atributos públicos pueden ser accedidos desde cualquier parte del sistema. Los métodos públicos son aquellos que se exponen a través de la interfaz pública de la clase, mientras que los métodos privados solo son accesibles dentro de la propia clase.

Por ejemplo, considera una clase "CuentaBancaria" que tiene los atributos privados "saldo" y "titular" y los métodos públicos "depositar" y "retirar". La encapsulación permite que los métodos "depositar" y "retirar" actualicen el saldo de la cuenta, mientras que el atributo "saldo" está protegido de modificaciones directas desde fuera de la clase.

En resumen, el principio de encapsulación es un concepto clave de la programación orientada a objetos que se refiere a la técnica de ocultar los detalles internos de una clase y exponer solo una interfaz pública bien definida para interactuar con ella. La encapsulación permite que el código sea más modular, más fácil de mantener y promueve la seguridad y la integridad de los datos.

## Ejemplo

Aquí tienes un ejemplo en Java que muestra cómo se puede implementar la encapsulación en una clase Persona:

``` java
public class Persona {
    private String nombre;
    private int edad;

    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public int getEdad() {
        return edad;
    }

    public void setEdad(int edad) {
        this.edad = edad;
    }
}
```

En este ejemplo, los atributos nombre y edad están definidos como privados, lo que significa que solo pueden ser accedidos desde dentro de la propia clase. En su lugar, se proporcionan métodos públicos getNombre, setNombre, getEdad y setEdad para acceder a los atributos.

Estos métodos permiten leer y escribir los valores de los atributos de la clase, pero el código externo no tiene acceso directo a ellos. De esta manera, la clase Persona encapsula la información sobre el nombre y la edad de una persona, lo que significa que otros componentes del sistema solo pueden interactuar con ella a través de la interfaz pública proporcionada por los métodos get y set.

## Encapsulación de comportamiento

La encapsulación de comportamiento se refiere a la técnica de ocultar los detalles de implementación de un comportamiento complejo detrás de una interfaz simple y fácil de usar. En lugar de exponer todos los detalles de implementación, la encapsulación de comportamiento proporciona una interfaz clara y bien definida para interactuar con el comportamiento.

La encapsulación de comportamiento se utiliza a menudo en el diseño de patrones de software, como el patrón de diseño State o el patrón de diseño Strategy. En estos patrones, la encapsulación de comportamiento se logra mediante la definición de una interfaz común para diferentes implementaciones de comportamiento.

Por ejemplo, considera un sistema de procesamiento de pagos que necesita soportar diferentes métodos de pago, como tarjetas de crédito, transferencias bancarias y PayPal. En lugar de exponer todos los detalles de implementación de cada método de pago, se puede definir una interfaz común MetodoPago que define los métodos necesarios para procesar un pago:

``` java
public interface MetodoPago {
    public void procesarPago(double cantidad);
    public String getNombreMetodoPago();
}
```

Luego, se pueden implementar diferentes clases que implementen la interfaz MetodoPago, cada una con su propia implementación de los métodos procesarPago y getNombreMetodoPago para soportar diferentes métodos de pago. Estas clases pueden encapsular todos los detalles de implementación de su método de pago correspondiente detrás de la interfaz común MetodoPago.

``` java
public class TarjetaCredito implements MetodoPago {
    public void procesarPago(double cantidad) {
        // implementación de procesamiento de pago con tarjeta de crédito
    }
    public String getNombreMetodoPago() {
        return "Tarjeta de crédito";
    }
}

public class TransferenciaBancaria implements MetodoPago {
    public void procesarPago(double cantidad) {
        // implementación de procesamiento de pago con transferencia bancaria
    }
    public String getNombreMetodoPago() {
        return "Transferencia bancaria";
    }
}

public class PayPal implements MetodoPago {
    public void procesarPago(double cantidad) {
        // implementación de procesamiento de pago con PayPal
    }
    public String getNombreMetodoPago() {
        return "PayPal";
    }
}
```

Con la encapsulación de comportamiento, el resto del sistema solo necesita interactuar con la interfaz común MetodoPago para procesar un pago, sin preocuparse por los detalles de implementación de cada método de pago individual. Esto hace que el sistema sea más modular, más fácil de mantener y más escalable en caso de que se agreguen nuevos métodos de pago en el futuro.

## ¿Cómo se aplicaría este principio?

``` mermaid
classDiagram

class Animal {
  - String name
  - int age
  - boolean isAlive
  + Animal(name: String, age: int)
  + getName(): String
  + getAge(): int
  + isAlive(): boolean
  + setName(name: String): void
  + setAge(age: int): void
  + setAlive(alive: boolean): void
}

class Zoo {
  - List<Animal> animals
  + Zoo()
  + addAnimal(animal: Animal): void
  + removeAnimal(animal: Animal): void
  + getAnimals(): List<Animal>
}

```

En este ejemplo, tenemos dos clases: Animal y Zoo. La clase Animal tiene tres atributos privados: name, age e isAlive, y tres métodos públicos que permiten acceder a estos atributos (getName(), getAge() e isAlive()) y tres métodos públicos que permiten modificar estos atributos (setName(), setAge() y setAlive()). De esta manera, se cumple el principio de Encapsulamiento ya que los atributos privados solo son accesibles a través de métodos públicos, lo que protege los datos y evita que se puedan modificar desde fuera de la clase.

Por otro lado, la clase Zoo tiene una lista de animales (atributo privado) y tres métodos públicos que permiten agregar y remover animales de la lista (addAnimal() y removeAnimal()) y obtener la lista de animales (getAnimals()). En este caso, la clase Zoo utiliza la clase Animal para representar los animales que tiene en su lista, pero no tiene conocimiento de cómo se implementa la clase Animal, lo que cumple con el principio de Persistence Ignorance.