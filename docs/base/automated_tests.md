# Automated Tests

El principio de automatización de pruebas (Automated Tests Principle) se refiere a la práctica de automatizar la ejecución de pruebas en el proceso de desarrollo de software. La automatización de pruebas permite a los equipos de desarrollo de software verificar el funcionamiento del software de manera rápida y eficiente, lo que a su vez ayuda a detectar y solucionar errores o defectos antes de que se libere el software al mercado.

Algunas de las ventajas de la automatización de pruebas son:

1. **Ahorro de tiempo:** la automatización de pruebas permite a los equipos de desarrollo de software ejecutar pruebas de manera más rápida y eficiente que las pruebas manuales, lo que a su vez ayuda a reducir el tiempo y los costos asociados con el proceso de desarrollo de software.

2. **Mejora de la calidad:** la automatización de pruebas ayuda a detectar y solucionar errores y defectos en el software de manera más temprana en el proceso de desarrollo, lo que a su vez contribuye a mejorar la calidad del software.

3. **Mayor cobertura de pruebas:** la automatización de pruebas permite ejecutar una gran cantidad de pruebas de manera rápida y eficiente, lo que a su vez ayuda a aumentar la cobertura de pruebas y detectar errores o defectos en áreas del software que de otra manera podrían ser pasadas por alto en el proceso de pruebas manuales.

Sin embargo, también es importante tener en cuenta que la automatización de pruebas no es adecuada para todos los tipos de pruebas y puede ser costosa y compleja de implementar. Por lo tanto, es importante evaluar cuidadosamente qué pruebas se pueden automatizar y cuáles no, y asegurarse de que los beneficios de la automatización de pruebas superen los costos y esfuerzos asociados.

## Los principios FIRST

Los principios "FIRST" de testing son un conjunto de principios que ayudan a los equipos de desarrollo a escribir pruebas de software efectivas. Cada letra en el acrónimo "FIRST" representa un principio específico, que se detallan a continuación:

1. **Fast (Rápido):** las pruebas deben ser rápidas y ejecutarse en un tiempo razonable. Las pruebas lentas pueden retrasar el proceso de desarrollo y hacer que los desarrolladores eviten ejecutar pruebas con frecuencia, lo que puede afectar la calidad del software.

2. **Independent (Independiente):** cada prueba debe ser independiente de las demás, y no debe depender del resultado de otras pruebas. Esto garantiza que cada prueba proporcione información valiosa y evita que los errores se propaguen a otras partes del sistema.

3. **Repeatable (Repetible):** las pruebas deben ser repetibles y producir los mismos resultados cada vez que se ejecutan. Esto permite a los desarrolladores identificar y solucionar problemas de manera confiable.

4. **Self-validating (Autovalidable):** las pruebas deben ser autovalidables, es decir, la prueba debe tener un resultado claro de "aprobado" o "fallido" sin necesidad de intervención humana adicional.

5. **Timely (Oportuno):** las pruebas deben escribirse y ejecutarse oportunamente en el proceso de desarrollo de software. Las pruebas deben ser parte integral del proceso de desarrollo de software y no deben agregarse al final del ciclo de desarrollo.

Los principios "FIRST" ayudan a los equipos de desarrollo a crear pruebas de software efectivas y confiables que ayudan a mejorar la calidad del software y garantizar su correcto funcionamiento.

### Ejemplo

A continuación, un ejemplo en Java de cómo aplicar los principios "FIRST" en una prueba unitaria:

Supongamos que tenemos una clase "Calculator" que tiene un método "sum" que toma dos números como parámetros y devuelve su suma. La siguiente sería una prueba unitaria que sigue los principios "FIRST":

``` java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    @Test
    public void testSum() {
        // Fast: la prueba debe ser rápida
        long startTime = System.currentTimeMillis();

        // Independent: la prueba debe ser independiente
        Calculator calculator = new Calculator();
        int result = calculator.sum(2, 3);

        // Repeatable: la prueba debe ser repetible
        assertEquals(5, result);

        // Self-validating: la prueba debe ser autovalidable
        assertTrue(result >= 0);

        // Timely: la prueba debe ser oportuna
        long endTime = System.currentTimeMillis();
        assertTrue(endTime - startTime < 100); // La prueba no debe tomar más de 100 milisegundos
    }
``` 

En esta prueba, se asegura que la suma de 2 y 3 sea igual a 5 y que el resultado sea un número positivo. Además, se mide el tiempo de ejecución de la prueba para garantizar que sea rápida.

### Ejemplo con Mocking

Aquí hay un ejemplo en Java de cómo crear una prueba unitaria con mocks:

Supongamos que tenemos una clase "UserService" que depende de una interfaz "UserRepository" para obtener información de usuario. La siguiente prueba unitaria utiliza un "mock" del repositorio para simular su comportamiento y probar el servicio:
``` java
import org.junit.jupiter.api.Test;
import static org.mockito.Mockito.*;

public class UserServiceTest {

    @Test
    public void testGetUserById() {
        // Configuramos el mock
        UserRepository mockRepository = mock(UserRepository.class);
        User user = new User("1", "John Doe");
        when(mockRepository.getUserById("1")).thenReturn(user);

        // Creamos el objeto a probar y lo hacemos dependiente del mock
        UserService userService = new UserService(mockRepository);

        // Ejecutamos el método y verificamos el resultado
        User result = userService.getUserById("1");
        assertEquals(user, result);

        // Verificamos que se haya llamado el método del mock
        verify(mockRepository).getUserById("1");
    }
}
```

En esta prueba, se crea un mock de la interfaz "UserRepository" y se configura para que devuelva un usuario específico cuando se llame al método "getUserById" con el ID correspondiente. Luego se crea un objeto "UserService" y se le hace depender del mock creado anteriormente. Se llama al método "getUserById" del servicio y se verifica que devuelva el mismo usuario que el mock. Finalmente, se verifica que el método "getUserById" del mock se haya llamado exactamente una vez. Esto nos permite probar el servicio sin tener que depender del comportamiento real del repositorio.

## En Resumen

En términos generales, se pueden hacer pruebas unitarias a cualquier componente o unidad de código que se pueda aislar y probar de manera independiente. A continuación, algunos ejemplos comunes de componentes que se suelen someter a pruebas unitarias:

* **Clases:** una clase que implementa una funcionalidad específica se puede probar con diferentes casos de prueba.

* **Métodos:** los métodos dentro de una clase se pueden probar individualmente, probando diferentes entradas y comparando los resultados con lo que se espera.

* **Funciones:** las funciones dentro de un módulo se pueden probar de manera similar a los métodos de una clase.

* **Componentes que dependen de servicios externos:** si una clase o función depende de servicios externos, se puede crear un mock o un stub para simular el comportamiento de esos servicios y probar la unidad de código de manera aislada.

* **Controladores:** los controladores de una aplicación web se pueden probar con diferentes entradas y verificar que la respuesta sea la esperada.

En resumen, cualquier unidad de código que se pueda aislar y probar de manera independiente se puede someter a pruebas unitarias.

### Consideraciones Finales

Aunque la mayoría del código puede ser sometido a pruebas automatizadas, hay algunas partes del código que son más difíciles o imposibles de probar automáticamente, como por ejemplo:

* Código que depende de recursos externos no controlables: si el código depende de recursos que están fuera del control del equipo de desarrollo, como una base de datos compartida o un servicio externo que no se puede emular, puede resultar difícil o imposible probar este código automáticamente.

* Código que depende de la interacción con el usuario: si el código está diseñado para interactuar directamente con el usuario, como una interfaz de usuario gráfica, puede resultar difícil o imposible probar este código automáticamente.

* Código que depende de factores externos no controlables: si el código depende de factores externos que no se pueden controlar o emular, como la fecha o la hora actual, puede resultar difícil o imposible probar este código automáticamente.

* Código que no es modular o que no está bien diseñado: si el código es difícil de aislar y probar de manera independiente, puede resultar difícil o imposible crear pruebas automatizadas efectivas para ese código.

Aunque estas partes del código pueden ser difíciles de probar automáticamente, todavía es importante asegurarse de que estén bien probadas de alguna manera. Por ejemplo, se pueden realizar pruebas manuales o pruebas exploratorias para verificar el comportamiento del código que no se puede probar automáticamente. Además, se pueden utilizar técnicas de refactorización de código para hacer que estas partes del código sean más modular y más fáciles de probar.


