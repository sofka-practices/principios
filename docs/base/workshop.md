# Taller de principios de programación
## Ejercicio 1 - Aplicar el principio de Single Responsibility
Refactoriza el siguiente código para aplicar el principio de Single Responsibility:

``` java
public class Invoice {
  private double subtotal;
  private double tax;
  private double total;
  
  public Invoice(double subtotal, double tax) {
    this.subtotal = subtotal;
    this.tax = tax;
    this.total = subtotal + tax;
  }
  
  public void print() {
    System.out.println("Subtotal: " + subtotal);
    System.out.println("Tax: " + tax);
    System.out.println("Total: " + total);
  }
}
```

## Ejercicio 2 - Aplicar el principio de Open/Closed
Refactoriza el siguiente código para aplicar el principio de Open/Closed:

``` java
public class Vehicle {
  private String type;
  
  public void start() {
    if (type.equals("car")) {
      System.out.println("Starting car...");
    } else if (type.equals("motorcycle")) {
      System.out.println("Starting motorcycle...");
    }
  }
}

```

## Ejercicio 3 - Aplicar el principio de Liskov Substitution
Refactoriza el siguiente código para aplicar el principio de Liskov Substitution:

``` java
public interface Shape {
  public double calculateArea();
}

public class Rectangle implements Shape {
  private double width;
  private double height;
  
  public Rectangle(double width, double height) {
    this.width = width;
    this.height = height;
  }
  
  public double calculateArea() {
    return width * height;
  }
}

public class Square implements Shape {
  private double side;
  
  public Square(double side) {
    this.side = side;
  }
  
  public double calculateArea() {
    return side * side;
  }
}

```

## Ejercicio 4 - Aplicar el principio de Interface Segregation
Refactoriza el siguiente código para aplicar el principio de Interface Segregation:

``` java
public interface IShape {
  public void draw();
  public void resize();
}

public class Circle implements IShape {
  public void draw() {
    System.out.println("Drawing circle...");
  }
  
  public void resize() {
    System.out.println("Resizing circle...");
  }
}

public class Square implements IShape {
  public void draw() {
    System.out.println("Drawing square...");
  }
  
  public void resize() {
    System.out.println("Resizing square...");
  }
}
```

## Ejercicio 5 - Aplicar el principio de Dependency Inversion
Refactoriza el siguiente código para aplicar el principio de Dependency Inversion:

``` java
public class UserService {
  private UserDao userDao;
  
  public UserService() {
    userDao = new UserDao();
  }
  
  public void saveUser(User user) {
    userDao.save(user);
  }
}

public class UserDao {
  public void save(User user) {
    // code to save user to database
  }
}

```
## Taller: Programación orientada a principios con conceptos bancarios
### Objetivo
Aplicar los principios de programación para desarrollar un sistema bancario que permita realizar transacciones y consultas de cuentas bancarias.

### Requisitos
* Conocimiento básico de programación orientada a objetos en Java.
* Un IDE de Java instalado (Eclipse, IntelliJ, NetBeans, entre otros).
* Conexión a internet.
### Pasos
1. **Definición de clases:** En primer lugar, se deben definir las clases necesarias para el sistema bancario. Se sugiere una clase CuentaBancaria que contenga los atributos numeroCuenta, saldo y titular, y los métodos depositar(), retirar() y consultarSaldo(). También se pueden crear clases adicionales como Banco y Transaccion para facilitar el manejo del sistema.

2. **Aplicación del principio de responsabilidad única:** Revisar la implementación de las clases y asegurarse de que cada una tenga una única responsabilidad. Por ejemplo, la clase CuentaBancaria debe ser responsable únicamente de la gestión de la cuenta bancaria.

3. **Aplicación del principio de abierto/cerrado:** Implementar un nuevo tipo de cuenta bancaria que permita acumular intereses sin tener que modificar la clase CuentaBancaria existente. Para ello, se puede crear una nueva clase CuentaAhorro que extienda de CuentaBancaria y agregue el atributo tasaInteres.

4. **Aplicación del principio de sustitución de Liskov:** Revisar la implementación de las clases y asegurarse de que las clases derivadas (CuentaAhorro) se puedan utilizar como las clases base (CuentaBancaria) sin afectar el comportamiento del sistema.

5. **Aplicación del principio de segregación de interfaz:** Revisar las interfaces de las clases y asegurarse de que sean cohesivas y sólo contengan los métodos necesarios para su responsabilidad. Por ejemplo, la interfaz de la clase CuentaAhorro sólo debería contener los métodos necesarios para la gestión de una cuenta de ahorro.

6. **Aplicación del principio de inversión de dependencia:** Utilizar interfaces para reducir la dependencia entre las clases. Por ejemplo, en lugar de depender directamente de la clase CuentaBancaria, la clase Banco puede depender de una interfaz Cuenta para la gestión de cuentas bancarias.

### Conclusiones
Este taller permitió aplicar los principios de programación orientada a objetos en un caso de uso real como es un sistema bancario. Es importante recordar que la aplicación correcta de estos principios permite obtener un código más limpio, mantenible y escalable.

## Preguntas de Repaso

1. ¿Cuáles son los principios SOLID? ¿Puedes describir brevemente cada uno?
2. ¿Qué es el principio de Responsabilidad Única (SRP)? ¿Por qué es importante?
3. ¿Qué es el principio de Abierto/Cerrado (OCP)? ¿Puedes dar un ejemplo?
4. ¿Qué es el principio de Sustitución de Liskov (LSP)? ¿Por qué es importante?
5. ¿Qué es el principio de Segregación de Interfaces (ISP)? ¿Puedes dar un ejemplo?
6. ¿Qué es el principio de Inversión de Dependencia (DIP)? ¿Por qué es importante?
7. ¿Qué es el principio de Encapsulamiento? ¿Puedes dar un ejemplo en Java?
8. ¿Qué es el principio de Separación de Preocupaciones (SoC)? ¿Por qué es importante?
9. ¿Qué es el principio de KISS? ¿Puedes dar un ejemplo en Java?
10. ¿Qué es el principio YAGNI? ¿Puedes dar un ejemplo en Java?
11. ¿Qué es el principio de DRY? ¿Por qué es importante?
12. ¿Qué es el principio de Bounded Contexts? ¿Puedes dar un ejemplo?
13. ¿Qué es el principio de Persistence Ignorance? ¿Puedes dar un ejemplo en Java?
14. ¿Cuál es la relación entre los principios de programación y la calidad del software?
15. ¿Por qué es importante seguir los principios de programación en el desarrollo de software?

