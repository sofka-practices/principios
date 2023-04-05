El principio "Writing automated tests" (Escribir pruebas automatizadas) es una práctica fundamental en el desarrollo de software, incluyendo el desarrollo frontend. Consiste en escribir y ejecutar pruebas automatizadas para asegurar que el código de la aplicación se comporte como se espera y detectar errores antes de que se presenten en producción.

En frontend, las pruebas automatizadas se enfocan en verificar el comportamiento de los componentes de la interfaz de usuario, incluyendo su apariencia, interacción y funcionalidad. Algunas herramientas populares para escribir pruebas automatizadas en frontend incluyen Jest, Cypress y Selenium.

Escribir pruebas automatizadas en frontend puede ofrecer varios beneficios. Por ejemplo:

* Ayuda a detectar errores y problemas de rendimiento en una etapa temprana del desarrollo, lo que puede ahorrar tiempo y costos a largo plazo.

* Mejora la calidad del código al requerir que el desarrollador tenga una mejor comprensión del comportamiento esperado de los componentes de la interfaz de usuario.

* Facilita la colaboración en el equipo, ya que las pruebas automatizadas pueden ser compartidas y ejecutadas por cualquier miembro del equipo.

* Permite realizar cambios en el código de manera más segura, ya que se pueden ejecutar pruebas automatizadas para asegurar que el cambio no rompa ninguna funcionalidad existente.

En resumen, el principio "Writing automated tests" es importante en frontend para garantizar la calidad del código, detectar errores tempranamente y mejorar la colaboración en el equipo.

## ¿Cómo aplicar el principio?

Supongamos que tenemos un componente React llamado Counter que muestra un número y tiene dos botones para aumentar o disminuir ese número en uno. Aquí está el código del componente:

``` javascript
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  const handleIncrement = () => {
    setCount(count + 1);
  };

  const handleDecrement = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
    </div>
  );
}

export default Counter;
```

Para escribir pruebas automatizadas para este componente con Jest, podemos crear un archivo Counter.test.js en el mismo directorio que el componente con el siguiente código:

``` javascript
import React from "react";
import { render, fireEvent } from "@testing-library/react";
import Counter from "./Counter";

test("Counter increments and decrements correctly", () => {
  const { getByText } = render(<Counter />);

  const countElement = getByText(/count/i);
  const incrementButton = getByText(/increment/i);
  const decrementButton = getByText(/decrement/i);

  expect(countElement).toHaveTextContent("0");

  fireEvent.click(incrementButton);
  expect(countElement).toHaveTextContent("1");

  fireEvent.click(decrementButton);
  expect(countElement).toHaveTextContent("0");
});

```

En este ejemplo, estamos importando las funciones render y fireEvent de @testing-library/react para renderizar el componente y simular eventos de clic en los botones. Luego, utilizamos la función getByText para obtener los elementos de la interfaz de usuario que necesitamos (el elemento de texto que muestra el conteo y los botones de incremento y decremento). Finalmente, estamos utilizando las funciones expect y toHaveTextContent para asegurarnos de que el conteo se esté incrementando y disminuyendo correctamente después de hacer clic en los botones.

Ejecutando esta prueba con Jest, debería producir una salida similar a esta:
``` bash
 PASS  ./Counter.test.js
  ✓ Counter increments and decrements correctly (20 ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
```
