El principio Using a standardized way of fetching the data hace referencia a la importancia de tener un enfoque consistente y estandarizado para la recuperación de datos en una aplicación web.

En general, existen varias formas de obtener datos en una aplicación web, como por ejemplo: haciendo peticiones HTTP a un servidor, usando APIs, o a través de bases de datos. Es importante tener un enfoque estandarizado para la recuperación de datos, ya que esto ayuda a mejorar la eficiencia y la confiabilidad de la aplicación.

Un enfoque estandarizado para la recuperación de datos puede incluir la implementación de patrones de diseño como el patrón de arquitectura MVC (Modelo-Vista-Controlador), que separa la lógica de la aplicación en capas diferentes y asigna responsabilidades específicas a cada una de ellas. En este patrón, la capa del modelo se encarga de manejar la recuperación de datos, mientras que la capa del controlador se encarga de procesar y manipular esos datos.

Además, es común utilizar frameworks o librerías que implementan este enfoque estandarizado de recuperación de datos, como por ejemplo React, Vue o Angular, que utilizan la librería Axios para manejar las peticiones HTTP y la recuperación de datos.

Al utilizar un enfoque estandarizado para la recuperación de datos, se puede reducir la cantidad de código redundante en la aplicación, hacerla más fácil de mantener y mejorar su escalabilidad. También se puede mejorar la calidad del código, ya que se sigue un patrón común y probado para manejar los datos en la aplicación.



## Ejemplo

Supongamos que estamos construyendo una aplicación web de comercio electrónico que necesita mostrar una lista de productos a los usuarios. Para hacer esto, necesitamos recuperar los datos de los productos desde el servidor.

En lugar de escribir código para hacer peticiones HTTP a un servidor para recuperar los datos de los productos en cada componente de nuestra aplicación, podríamos crear un módulo o una clase en JavaScript que se encargue de recuperar los datos de los productos de manera estandarizada.

Por ejemplo, podríamos crear un archivo llamado "productService.js" que exporte una clase "ProductService" que se encargue de recuperar los datos de los productos desde el servidor utilizando una API RESTful. La clase podría tener métodos como "getAllProducts" para recuperar todos los productos, "getProductById" para recuperar un producto por su identificador y "addProduct" para agregar un nuevo producto al servidor.

Aquí hay un ejemplo de cómo se podría implementar la clase ProductService utilizando la librería Axios para realizar peticiones HTTP:

``` javascript
import axios from 'axios';

class ProductService {
  async getAllProducts() {
    const response = await axios.get('/api/products');
    return response.data;
  }

  async getProductById(productId) {
    const response = await axios.get(`/api/products/${productId}`);
    return response.data;
  }

  async addProduct(product) {
    const response = await axios.post('/api/products', product);
    return response.data;
  }
}

export default new ProductService();
```

Luego, en cualquier componente de nuestra aplicación que necesite mostrar una lista de productos, simplemente tendríamos que importar el módulo ProductService y llamar al método getAllProducts. Por ejemplo:

``` javascript
import React, { useState, useEffect } from 'react';
import ProductService from './productService';

function ProductList() {
  const [products, setProducts] = useState([]);

  useEffect(() => {
    async function fetchProducts() {
      const products = await ProductService.getAllProducts();
      setProducts(products);
    }

    fetchProducts();
  }, []);

  return (
    <ul>
      {products.map((product) => (
        <li key={product.id}>{product.name}</li>
      ))}
    </ul>
  );
}

export default ProductList;
```

En este ejemplo, estamos utilizando el método getAllProducts de ProductService para recuperar los datos de los productos en el componente ProductList. Al hacerlo de esta manera, estamos utilizando un enfoque estandarizado y coherente para la recuperación de datos en toda nuestra aplicación, lo que ayuda a mejorar la eficiencia y la confiabilidad de la misma.

## ¿Cómo aplicar el principio?
``` mermaid
graph TD;
  A[Componente1] <--> |Petición|B[Servicio];
  F[Componente2] <--> |Petición|B[Servicio];
  B --> |Request|C[API];
  C --> |Response|B;

```
El componente hace uso del servicio para realizar una petición HTTP al servidor y recibir una respuesta HTTP que contiene los datos solicitados. Luego, el componente procesa los datos recibidos y actualiza la vista en la que se encuentra. Este es el enfoque estándar y recomendado para el uso de servicios en componentes de una aplicaciones web.





