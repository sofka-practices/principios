El principio de "Persistence Ignorance" o "Ignorancia de Persistencia" es un principio de diseño de software que establece que los objetos del dominio no deben estar acoplados a los detalles de cómo se almacenan en una base de datos u otro tipo de almacenamiento persistente. En otras palabras, los objetos del dominio deben ser agnósticos en cuanto a la forma en que se guardan en la persistencia.

Este principio tiene como objetivo mantener una separación clara entre la lógica del negocio y la lógica de persistencia. Al separar estas dos preocupaciones, se pueden hacer cambios en la forma en que se almacena la información sin afectar la lógica del negocio, y viceversa.

Por ejemplo, supongamos que estamos construyendo una aplicación de venta de productos en línea. Los objetos del dominio podrían incluir clases como "Producto", "Carrito de compras", "Usuario", etc. Estos objetos se utilizan para representar las entidades del negocio, y deben ser independientes de cómo se almacenan en una base de datos o en otro tipo de almacenamiento persistente.

En lugar de hacer que los objetos del dominio tengan conocimiento directo de la lógica de persistencia, se pueden utilizar patrones de diseño como el patrón "Repository" para manejar la lógica de persistencia. Un objeto "Repository" es responsable de manejar la creación, lectura, actualización y eliminación de objetos del dominio en la base de datos o almacenamiento persistente. Al utilizar un objeto "Repository", se puede mantener una separación clara entre la lógica del negocio y la lógica de persistencia.

El principio de "Persistence Ignorance" también puede ayudar a simplificar el proceso de prueba. Al tener objetos del dominio independientes de la lógica de persistencia, se pueden crear objetos de prueba más fácilmente, sin tener que preocuparse por detalles de persistencia. Esto permite realizar pruebas más completas y precisas de la lógica del negocio.

En resumen, el principio de "Persistence Ignorance" es importante para mantener una separación clara entre la lógica del negocio y la lógica de persistencia en una aplicación de software. Esto puede hacer que el código sea más fácil de mantener, más fácil de probar y más fácil de modificar en el futuro.

## Ejemplo

En Java, se puede aplicar el principio de "Persistence Ignorance" utilizando el patrón "Repository". Por ejemplo, supongamos que tenemos una clase "Producto" que representa un producto en una aplicación de venta en línea. En lugar de tener métodos para guardar o cargar el producto directamente en la base de datos, se puede utilizar un objeto "Repository" para manejar la lógica de persistencia. Aquí hay un ejemplo de cómo se podría implementar esto en Java:

``` java
public class Producto {
   private int id;
   private String nombre;
   private double precio;
   //... otros atributos y métodos del producto

   //constructor, getters y setters

   //no hay métodos de persistencia aquí
}

public interface ProductoRepository {
   public void guardarProducto(Producto producto);
   public void actualizarProducto(Producto producto);
   public void borrarProducto(Producto producto);
   public Producto buscarProductoPorId(int id);
   //... otros métodos de repositorio
}

public class ProductoRepositoryImpl implements ProductoRepository {
   public void guardarProducto(Producto producto) {
      //Lógica para guardar el producto en la base de datos
   }

   public void actualizarProducto(Producto producto) {
      //Lógica para actualizar el producto en la base de datos
   }

   public void borrarProducto(Producto producto) {
      //Lógica para eliminar el producto de la base de datos
   }

   public Producto buscarProductoPorId(int id) {
      //Lógica para buscar el producto por su ID en la base de datos
      //y crear un objeto Producto a partir de los datos recuperados
      return new Producto(id, nombre, precio);
   }
   //... otros métodos de repositorio
}

``` 

En este ejemplo, la clase "Producto" representa un objeto del dominio, que es independiente de cómo se almacena en la base de datos. La interfaz "ProductoRepository" define los métodos para manejar la lógica de persistencia de los objetos del dominio. La implementación concreta "ProductoRepositoryImpl" maneja la lógica de persistencia, utilizando una base de datos o algún otro tipo de almacenamiento persistente.

Al separar la lógica de persistencia de los objetos del dominio, se puede mantener una separación clara entre la lógica del negocio y la lógica de persistencia. Esto puede hacer que el código sea más fácil de mantener y probar, y también puede permitir cambios en la forma en que se almacena la información sin afectar la lógica del negocio.

## ¿Cómo se aplicaría este principio?

``` mermaid
classDiagram
class Customer {
        -id: int
        -name: String
        -email: String
        +Customer(id: int, name: String, email: String)
        +getId(): int
        +getName(): String
        +getEmail(): String
        +updateName(name: String)
    }
    
class CustomerRepository {
        <<interface>>
        +save(customer: Customer)
        +findById(id: int): Customer
 }
    
class CustomerService {
        -customerRepository: CustomerRepository
        +CustomerService(customerRepository: CustomerRepository)
        +createCustomer(name: String, email: String): Customer
        +getCustomerById(id: int): Customer
}
    
Customer --> CustomerService
CustomerService ..> CustomerRepository
```
En este ejemplo, se pueden observar tres clases: Customer, CustomerRepository y CustomerService.

La clase Customer representa un objeto de tipo cliente, con tres atributos privados (id, name y email) y cuatro métodos públicos (Customer, getId, getName y updateName).

La interfaz CustomerRepository define los métodos que deben ser implementados por cualquier clase que se encargue de persistir los datos de un cliente. En este caso, se definen dos métodos: save y findById.

La clase CustomerService representa una clase que utiliza tanto la clase Customer como la interfaz CustomerRepository. Esta clase tiene un atributo privado (customerRepository) que se inicializa en el constructor, y dos métodos públicos (createCustomer y getCustomerById) que utilizan los métodos de la clase Customer y de la interfaz CustomerRepository para crear y obtener clientes.

Por último, se pueden observar las relaciones entre las clases, donde Customer se relaciona con CustomerService mediante una flecha y CustomerService se relaciona con CustomerRepository mediante una flecha punteada.

Este ejemplo muestra cómo se puede aplicar el principio de Persistence Ignorance, donde la clase Customer no sabe nada acerca de cómo se guardan sus datos, y la clase CustomerService se encarga de utilizar una implementación de la interfaz CustomerRepository para persistir y obtener datos de los clientes.