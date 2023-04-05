"Don't Repeat Yourself" (DRY) es un principio de programación que promueve la idea de que cada pieza de información en un sistema debe tener una única representación, una única fuente de verdad, para evitar la repetición innecesaria de código.

Este principio se aplica a diferentes niveles en el desarrollo de software, desde la arquitectura de la aplicación hasta el nivel del código fuente. En general, se busca evitar la duplicación de código o la repetición de lógica en diferentes partes del sistema, ya que esto puede llevar a problemas de mantenimiento, inconsistencias y errores.

En lugar de repetir el mismo código, se busca definir una única fuente de información que se pueda reutilizar en diferentes partes del sistema. Esto puede lograrse a través de la creación de funciones, clases, bibliotecas o módulos reutilizables, que encapsulan la lógica y se pueden utilizar en diferentes partes del sistema.

Por ejemplo, en lugar de repetir la misma validación de entrada de usuario en diferentes partes de una aplicación web, se podría definir una función de validación de entrada de usuario que se pueda reutilizar en diferentes formularios de la aplicación.

El principio DRY se relaciona estrechamente con otros principios de programación, como el principio de responsabilidad única (SRP) y el principio de interfaz de usuario única (SUI), ya que todos promueven la idea de tener una única fuente de verdad y evitar la duplicación de información. Al seguir estos principios, se puede lograr un código más limpio, eficiente, mantenible y escalable.

## Ejemplo
Un ejemplo concreto en Java que sigue el principio DRY podría ser la creación de una función que calcule el promedio de una lista de números enteros. En lugar de repetir la misma lógica de cálculo del promedio en diferentes partes del código, se podría definir una función que se pueda reutilizar en diferentes partes del sistema.

Por ejemplo:
``` java
public class AverageCalculator {
   public static double calculateAverage(List<Integer> numbers) {
      int sum = 0;
      for (int number : numbers) {
         sum += number;
      }
      return (double) sum / numbers.size();
   }
}
```
En este ejemplo, la función calculateAverage recibe una lista de números enteros y calcula el promedio utilizando un bucle for. Al definir esta función en una clase separada, se puede reutilizar en diferentes partes del sistema sin tener que repetir la misma lógica de cálculo del promedio.

Por ejemplo, en diferentes partes del sistema se podría utilizar la función calculateAverage para calcular el promedio de calificaciones de estudiantes, el promedio de ventas diarias de una tienda o el promedio de edades de un grupo de personas, entre otros usos. En todos los casos, se estaría reutilizando la misma función en lugar de duplicar la misma lógica en diferentes partes del código.

## Programación funcional

Este principio se ajusta muy bien a la programación funcional dado los principios de la programación funcional obliga a tener elementos aislados y que sea reutilizables, por ejemplo  la creación de una función que calcule la suma de los números impares en una lista de números enteros. En lugar de repetir la misma lógica de filtrado y sumatoria en diferentes partes del código, se podría definir una función que se pueda reutilizar en diferentes partes del sistema.

Por ejemplo, utilizando la librería de funciones lambda de Java, se podría escribir el siguiente código:

``` java
import java.util.Arrays;
import java.util.List;

public class SumOddNumbers {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        int sum = sumOddNumbers(numbers);
        System.out.println("Sum of odd numbers: " + sum);
    }
    
    public static int sumOddNumbers(List<Integer> numbers) {
        return numbers.stream()
                      .filter(n -> n % 2 != 0)  // filtrar números impares
                      .reduce(0, Integer::sum); // sumar los números impares filtrados
    }
}
``` 

En este ejemplo, la función sumOddNumbers recibe una lista de números enteros y utiliza la librería de funciones lambda de Java  para filtrar los números impares y sumarlos. Al definir esta función como una función separada, se puede reutilizar en diferentes partes del sistema sin tener que repetir la misma lógica de filtrado y sumatoria en diferentes partes del código.

Por ejemplo, se podría utilizar la función sumOddNumbers en diferentes partes del sistema para calcular la suma de los números impares de diferentes listas de números enteros. En todos los casos, se estaría reutilizando la misma función en lugar de duplicar la misma lógica en diferentes partes del código.

## ¿Cómo se aplicaría este principio?

``` mermaid
classDiagram
class Animal {
  -name: String
  -age: int
  +Animal(name: String, age: int)
  +setName(name: String)
  +setAge(age: int)
  +getName(): String
  +getAge(): int
}

class Dog {
  -breed: String
  -sound: String
  +Dog(name: String, age: int, breed: String, sound: String)
  +setBreed(breed: String)
  +setSound(sound: String)
  +getBreed(): String
  +getSound(): String
  +makeSound()
}

class Cat {
  -type: String
  -sound: String
  +Cat(name: String, age: int, type: String, sound: String)
  +setType(type: String)
  +setSound(sound: String)
  +getType(): String
  +getSound(): String
  +makeSound()
}

class Main {
  +main(args: String[])
}

Animal <|-- Dog
Animal <|-- Cat

```

En este ejemplo, se puede observar que la clase Animal contiene propiedades comunes como name y age, que son utilizadas tanto en la clase Dog como en la clase Cat. En lugar de repetir estas propiedades en ambas clases, se utiliza la herencia para hacer que Dog y Cat hereden de la clase Animal. De esta manera, se evita repetir código y se sigue el principio de DRY.