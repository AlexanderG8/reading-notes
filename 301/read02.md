# React - State y Props

## 1\. `useState` Hook en React

### ¿Qué diferencia hay entre declarar una variable con `const` vs declararla con `useState`?

La principal diferencia radica en cómo React maneja los cambios y la **re-renderización de los componentes**.

  * **Declarar una variable con `const`**:
    Cuando declaras una variable con `const` dentro de un componente funcional de React, esa variable es **inmutable** y su valor se establece al momento del renderizado. Si su valor cambia en el futuro, **React no será notificado** de ese cambio y, por lo tanto, el componente **no se re-renderizará** automáticamente. El valor de esa variable se perdería en la próxima renderización del componente (por ejemplo, si el componente padre se re-renderiza). Es útil para valores que no van a cambiar o que no necesitan disparar una actualización de la UI.

  * **Declarar una variable con `useState` (el estado):**
    `useState` es un Hook de React que te permite agregar **estado** a tus componentes funcionales. Cuando declaras una variable de estado con `useState`, React la "rastrea". Esto significa que:

      * Proporciona una forma de almacenar un valor que **persiste entre renderizaciones** del componente.
      * Te da una función (`setConteo` en `const [conteo, setConteo] = useState(0)`) para **actualizar** ese valor.
      * Lo más importante: cuando usas la función de actualización (ej. `setConteo(conteo + 1)`), **React es notificado del cambio** y automáticamente programa una **re-renderización** de ese componente (y sus hijos si sus props cambian). Esto asegura que la interfaz de usuario se mantenga sincronizada con los datos.

En resumen, `const` define una variable con un valor fijo para una renderización, mientras que `useState` define un **valor con estado** que React puede observar, actualizar y que automáticamente dispara actualizaciones en la UI cuando cambia.

### Ejemplo de aplicación real que use *state* para gestionar datos

Un ejemplo muy claro es el **contador de "Me gusta" o "Likes" en Instagram o Twitter**.

Cuando un usuario hace clic en el botón de "Me gusta" en una publicación:

1.  El componente de la publicación (o el botón de "Me gusta" dentro de ella) tiene un **estado interno** para el número de "likes". Por ejemplo, `const [likes, setLikes] = useState(150);`.
2.  Al hacer clic, se ejecuta una función que llama a `setLikes(likes + 1)`.
3.  React detecta el cambio en el estado `likes`.
4.  React **re-renderiza** el componente del botón (o la publicación completa) para mostrar el nuevo número de "likes" (ej. 151), sin tener que recargar toda la página.
5.  Adicionalmente, esta acción podría disparar una llamada a una API para persistir el "like" en la base de datos del servidor.

### ¿Por qué React re-renderiza automáticamente cuando cambia el *state*?

React re-renderiza automáticamente cuando cambia el *state* debido a su **modelo de programación declarativo** y el uso del **Virtual DOM**.

Cuando llamas a la función actualizadora de estado (`setState` en componentes de clase o la función `set` en `useState` para componentes funcionales):

1.  **React detecta que el estado ha cambiado.**
2.  **Crea una nueva representación del componente en el Virtual DOM.** Piensa en el Virtual DOM como una copia ligera en memoria del DOM real.
3.  **Compara la nueva representación del Virtual DOM con la anterior.** Este proceso se llama **reconciliación** o "diffing". React es extremadamente eficiente en encontrar las diferencias mínimas.
4.  **Actualiza solo las partes necesarias del DOM real.** En lugar de reconstruir toda la interfaz, React solo aplica los cambios mínimos y necesarios al DOM real para que coincida con el nuevo Virtual DOM.

Este mecanismo garantiza que la UI siempre refleje el estado actual de los datos sin que el desarrollador tenga que manipular el DOM directamente, lo que lo hace más eficiente y menos propenso a errores.

-----

## 2\. *Props* y Comunicación entre Componentes

### ¿Cómo se comunican los componentes en React si los datos solo fluyen de padre a hijo?

La comunicación estándar y principal en React es **unidireccional: de padre a hijo**. Los datos se pasan de un componente padre a un componente hijo a través de ***props*** (propiedades).

  * Un componente padre puede pasar datos (variables, funciones, objetos, etc.) a sus componentes hijos como atributos en la declaración del componente.
  * El componente hijo recibe estas *props* como un objeto y puede acceder a los valores pasados.

<!-- end list -->

```jsx
// Componente Padre
function Padre() {
  const mensaje = "Hola desde el padre";
  return <Hijo texto={mensaje} />;
}

// Componente Hijo
function Hijo(props) {
  return <p>{props.texto}</p>; // El hijo recibe 'texto' como prop
}
```

### Un patrón común donde un componente hijo necesita “informar” al padre sobre cambios

Dado que los datos fluyen de padre a hijo, si un hijo necesita "informar" al padre sobre un evento o un cambio, el patrón común es que el **padre pase una función (un *callback*) como *prop* al hijo**.

El componente hijo entonces llama a esa función cuando ocurre el evento, pasándole los datos necesarios como argumentos. De esta forma, el control de la lógica y la manipulación del estado sigue residiendo en el padre, manteniendo el flujo de datos unidireccional y predecible.

**Ejemplo:** Un componente `BotonContador` (hijo) que incrementa un contador y notifica a un componente `App` (padre).

```jsx
// Componente Padre (App.js)
import React, { useState } from 'react';
import BotonContador from './BotonContador'; // Suponemos que BotonContador está en otro archivo

function App() {
  const [conteoTotal, setConteoTotal] = useState(0);

  // Función que el padre pasará al hijo
  const handleIncrementoHijo = () => {
    setConteoTotal(prevConteo => prevConteo + 1);
  };

  return (
    <div>
      <h1>Contador Total: {conteoTotal}</h1>
      {/* El padre pasa la función como una prop al hijo */}
      <BotonContador onIncremento={handleIncrementoHijo} />
      <BotonContador onIncremento={handleIncrementoHijo} />
    </div>
  );
}
export default App;

// Componente Hijo (BotonContador.js)
import React from 'react';

function BotonContador(props) {
  // Cuando el botón se hace clic, llama a la función que vino de las props
  // y que fue definida por el padre
  return (
    <button onClick={props.onIncremento}>
      Haz clic para incrementar el contador total
    </button>
  );
}
export default BotonContador;
```

En este ejemplo, `BotonContador` no tiene su propio estado para el contador, sino que ejecuta la función `onIncremento` que le pasó `App`. Es `App` quien mantiene el estado `conteoTotal` y lo actualiza.

### ¿Qué significa que las *props* son “inmutables” y por qué es importante?

Que las *props* son **"inmutables"** (o "solo de lectura") significa que un componente hijo **no debe ni puede modificar directamente las *props* que recibe de su componente padre**.

  * **No debes modificar las *props* directamente:** Intentar cambiar `props.algunaProp = "nuevo valor";` dentro del componente hijo resultará en un error en modo estricto o simplemente no funcionará como esperas, ya que React no espera ni detecta esos cambios.
  * **Las *props* son la fuente de la verdad para el hijo:** Para un componente hijo, las *props* que recibe son como las instrucciones de su padre en un momento dado. Si el padre quiere que el hijo muestre algo diferente, el padre debe actualizar su propio estado y, en consecuencia, pasar nuevas *props* al hijo.

**¿Por qué es importante?**

1.  **Flujo de datos predecible (*Unidirectional Data Flow*):** Refuerza el principio de que los datos fluyen en una sola dirección (de padre a hijo). Esto hace que el estado de la aplicación sea mucho más fácil de entender, depurar y predecir. Sabes que un componente solo puede recibir datos a través de *props* y que su propio estado es el único que puede controlar directamente.
2.  **Facilita el *debugging*:** Si un componente muestra datos incorrectos, sabes que la causa está en:
      * El propio estado del componente.
      * Las *props* que recibe del padre (y, por lo tanto, el estado del padre).
      * No hay una "cadena de dependencias" circular donde un hijo pueda afectar inesperadamente al padre o a otro hermano.
3.  **Componentes reusables y aislados:** Los componentes se vuelven más autónomos y confiables. Puedes usar el mismo componente en diferentes lugares con diferentes *props* sin preocuparte de que modifique los datos originales de donde vinieron.
4.  **Optimización:** React puede hacer ciertas optimizaciones asumiendo que las *props* no cambiarán inesperadamente por el hijo.

Si un hijo necesita cambiar algo que afecta al padre o a otros componentes, debe usar el patrón de "pasar una función *callback* como *prop*" que vimos antes.

-----

## 3\. *Array Methods* para Renderizado Dinámico

### ¿Cuál es la diferencia práctica entre `.map()`, `.find()` y `.filter()` en el contexto de React?

En el contexto de React, estos métodos de *array* son fundamentales para el renderizado dinámico de listas y la manipulación de datos, pero cada uno tiene un propósito distinto:

  * **`.map()`:**

      * **Propósito:** Transforma cada elemento de un *array* y devuelve un **nuevo *array*** con los resultados de la función aplicada a cada elemento. Es el método más común para **renderizar listas de componentes** en React.
      * **Contexto React:** Se utiliza para tomar una lista de datos (ej. un *array* de objetos de productos) y convertirla en una lista de elementos JSX (ej. un *array* de componentes `<Producto />`). Siempre devuelve un *array* del mismo tamaño que el original.
      * **Ejemplo:** `productos.map(producto => <Producto key={producto.id} data={producto} />)`

  * **`.filter()`:**

      * **Propósito:** Crea un **nuevo *array*** con todos los elementos que pasan una prueba (una función de *callback* que devuelve `true` o `false`). No modifica el *array* original.
      * **Contexto React:** Se usa para **seleccionar un subconjunto de datos** de un *array* basándose en ciertas condiciones, antes de renderizarlos. Es útil para funcionalidades de búsqueda, filtrado o mostrar solo elementos que cumplen ciertos criterios.
      * **Ejemplo:** `const productosFiltrados = productos.filter(producto => producto.precio < 100);` (luego, puedes mapear `productosFiltrados`).

  * **`.find()`:**

      * **Propósito:** Devuelve el **primer elemento** de un *array* que satisface una función de prueba. Si ningún elemento lo satisface, devuelve `undefined`.
      * **Contexto React:** Se usa para **encontrar un único elemento** específico dentro de una lista, por ejemplo, para mostrar los detalles de un elemento seleccionado, como un producto en una vista de detalle después de hacer clic en él en una lista.
      * **Ejemplo:** `const productoSeleccionado = productos.find(producto => producto.id === idDelProducto);` (luego, podrías renderizar un componente `<DetalleProducto data={productoSeleccionado} />`).

### Ejemplos de interfaces que muestren listas dinámicas

  * **Netflix / Spotify:**
      * Utilizan intensamente `.map()` para renderizar las **filas de películas/series o álbumes/canciones** en la página de inicio o en las categorías. Cada tarjeta de película/álbum es un componente renderizado dinámicamente a partir de un *array* de datos de medios.
      * Cuando buscas, usan `.filter()` para mostrar solo los resultados que coinciden con tu búsqueda.
  * **Amazon / Cualquier tienda *online*:**
      * La página de resultados de búsqueda o de categoría de productos usa `.map()` para mostrar cada **tarjeta de producto** individualmente.
      * Los filtros de precios, marcas, etc., detrás de escena usan `.filter()` para crear subconjuntos de productos a mostrar.

### ¿Por qué necesitamos la *prop* `key` cuando usamos `.map()` en React?

La *prop* `key` es un **atributo especial y obligatorio** que debes incluir en los elementos de una lista cuando los renderizas usando `.map()` en React. Es crucial para el **rendimiento y la estabilidad** de la interfaz de usuario.

  * **Identificación única de elementos:** `key` le da a React una forma de **identificar de manera única cada elemento** en una lista. Piensa en ella como una "huella digital" para cada componente hijo en esa lista.
  * **Optimización del *rendering*:** Cuando una lista cambia (se agregan, eliminan o reordenan elementos), React usa las `key`s para determinar qué elementos han cambiado, cuáles se han agregado y cuáles se han eliminado. Sin `key`s, React tendría que re-renderizar todos los elementos de la lista o intentar adivinar los cambios, lo que es ineficiente y puede llevar a problemas.
      * Si tienes `key`s, React puede mover elementos del DOM en lugar de reconstruirlos si su `key` permanece la misma pero su posición cambia.
      * Si un elemento se elimina, React puede encontrarlo por su `key` y removerlo eficientemente del DOM.
  * **Mantenimiento del estado interno:** Si los elementos de la lista tienen estado interno (por ejemplo, un campo de entrada con un valor, o un *checkbox* marcado), las `key`s aseguran que ese estado se mantenga correctamente asociado al elemento correcto, incluso si el orden de la lista cambia. Sin `key`s, React podría aplicar el estado de un elemento a otro incorrectamente.

**¿Qué usar como `key`?**

La `key` debe ser una **cadena o número único y estable** para cada elemento dentro de la misma lista.

  * **Idealmente, usa un ID único y persistente** de tus datos (ej. `producto.id` de una base de datos).
  * **Evita usar el índice del *array*** (`index`) como `key` si la lista puede cambiar de orden, agregar o eliminar elementos, ya que esto puede llevar a errores sutiles de rendimiento y estado. Solo úsalo si la lista es estática y no va a cambiar.

<!-- end list -->

```jsx
// CORRECTO: Usando un ID único de los datos
listaItems.map(item => (
  <ListItem key={item.id} data={item} />
));

// EVITAR (a menos que la lista sea estática y nunca cambie de orden/tamaño):
listaItems.map((item, index) => (
  <ListItem key={index} data={item} />
));
```

-----

## 4\. *Event Handlers* y Re-renderizado

### ¿Qué diferencia hay entre `onClick` en React vs `addEventListener` en JavaScript vanilla?

Ambos se usan para manejar eventos de usuario, pero difieren fundamentalmente en su enfoque y cómo se integran con sus respectivos entornos:

  * **`onClick` en React:**

      * **Sintaxis:** Es un ***prop*** de los elementos JSX (ej. `<button onClick={miFuncion}>`). Se escribe en *camelCase* (ej. `onClick`, `onChange`).
      * **Naturaleza:** Es un **evento sintético** de React. React envuelve los eventos nativos del navegador en su propio sistema de eventos para crear un entorno de manejo de eventos consistente y *cross-browser*.
      * **Delegación de eventos:** React maneja la delegación de eventos automáticamente. En lugar de adjuntar un *event listener* a cada elemento individual en el DOM real, React adjunta un solo *event listener* en el elemento raíz del DOM (o en un nivel superior) y luego usa un sistema de burbujeo para gestionar qué componente debe responder al evento. Esto mejora el rendimiento.
      * **Contexto:** Se utiliza para definir la función que se ejecutará cuando ocurra un evento en un elemento de un componente React. La función pasada se ejecuta en el contexto del componente, y los cambios de estado dentro de ella pueden disparar re-renderizados de React.

  * **`addEventListener` en JavaScript vanilla:**

      * **Sintaxis:** Es un método del objeto *Node* del DOM (ej. `elemento.addEventListener('click', miFuncion)`). El nombre del evento es una cadena en minúsculas (ej. `'click'`, `'change'`).
      * **Naturaleza:** Es un **método nativo del navegador** que permite adjuntar un *listener* de eventos directamente a un elemento específico en el DOM.
      * **Adjunto directo:** Adjunta un *listener* a cada elemento individual donde se llama, lo que puede ser menos eficiente si tienes muchos elementos con el mismo tipo de *listener*.
      * **Contexto:** Se ejecuta directamente en el contexto del DOM. Para interactuar con React, necesitarías acceder a los elementos del DOM usando *refs* de React, lo cual generalmente se evita para la manipulación directa a menos que sea absolutamente necesario.

En resumen, `onClick` de React es una abstracción de alto nivel que simplifica el manejo de eventos y lo integra con el ciclo de vida y el sistema de re-renderizado de React, mientras que `addEventListener` es una API de bajo nivel para interactuar directamente con el DOM del navegador.

### Una aplicación web que responde a *clicks* y cambia la interfaz inmediatamente

Casi cualquier aplicación web interactiva moderna que use React o un *framework* similar.

  * **Google Docs / Microsoft Word Online:** Cuando haces clic en un botón de formato (negrita, cursiva, subrayado), el texto seleccionado cambia inmediatamente. Cada clic en un icono de la barra de herramientas dispara un evento que actualiza el estado interno del documento, lo que lleva a un re-renderizado instantáneo del texto con el nuevo formato.
  * **Un juego web sencillo (ej. un *quiz*):** Al hacer clic en una opción de respuesta, la interfaz cambia instantáneamente para mostrar si la respuesta fue correcta o incorrecta, avanzar a la siguiente pregunta, o mostrar un puntaje. Cada clic del usuario es un evento que actualiza el estado del juego, y React re-renderiza la interfaz del *quiz* para reflejar esos cambios.

### ¿Cómo sabe React qué partes de la UI actualizar cuando cambia el *state*?

React sabe qué partes de la UI actualizar cuando cambia el *state* gracias al **Virtual DOM** y el proceso de **reconciliación** (o *diffing*) que mencionamos anteriormente.

Aquí están los pasos clave:

1.  **Cambio de Estado:** Un usuario interactúa con la UI (ej. un clic en un botón), lo que lleva a una llamada a la función de actualización del estado (`setEstado`).
2.  **Creación de un Nuevo Árbol del Virtual DOM:** React no modifica el DOM real de inmediato. En cambio, cuando el estado de un componente cambia, React ejecuta la función `render()` (o el cuerpo de la función para componentes funcionales) de ese componente y crea un **nuevo árbol del Virtual DOM**. Este nuevo árbol es una representación en memoria de cómo debería verse la UI después del cambio de estado.
3.  **Algoritmo de Reconciliación (*Diffing*):** React compara este **nuevo árbol del Virtual DOM** con el **árbol del Virtual DOM anterior**. Su algoritmo de *diffing* es muy eficiente y rápido.
      * Compara los tipos de elementos (si un `div` se convirtió en un `p`).
      * Si los tipos son iguales, compara sus *props* y su contenido.
      * Para listas de elementos, usa la *prop* `key` para identificar elementos que han sido agregados, eliminados o reordenados de manera eficiente.
4.  **Actualización Mínima del DOM Real:** Basándose en las diferencias que encuentra entre los dos árboles del Virtual DOM, React calcula la **cantidad mínima de cambios necesarios** para actualizar el DOM real.
5.  **Renderizado al DOM Real:** Finalmente, React aplica estos cambios directamente al DOM real del navegador. Esto es lo que ves como una actualización en la interfaz de usuario.

Este proceso de "diferenciar" el Virtual DOM y aplicar solo los cambios necesarios al DOM real es lo que hace a React tan eficiente y rápido, evitando la costosa manipulación directa de todo el DOM.

## Glosario de Nuevos Términos
- **State**: Datos que pueden cambiar durante la vida de un componente y causan re-renderizado automático cuando se modifican
- **Props**: Datos inmutables que se pasan de un componente padre a sus componentes hijos como parámetros
- **useState**: Hook de React que permite agregar estado local a componentes funcionales
- **Event Handler**: Función que responde a interacciones del usuario (clicks, inputs, etc.) y típicamente modifica el state
- **Re-renderizado**: Proceso automático por el cual React actualiza la UI cuando detecta cambios en el state o props
- **Flujo Unidireccional**: Patrón donde los datos siempre fluyen de componentes padre hacia hijos, nunca al revés
- **Array.map()**: Método que transforma cada elemento de un array, usado en React para renderizar listas de componentes
- **Array.find()**: Método que retorna el primer elemento que cumple una condición, usado para localizar elementos específicos
- **Array.filter()**: Método que retorna un nuevo array con elementos que cumplen una condición, usado para filtrar datos
- **Key prop**: Propiedad especial que React necesita para identificar elementos únicos en listas renderizadas dinámicamente
- **Immutability**: Principio de no modificar datos directamente, sino crear nuevas versiones cuando se necesitan cambios
- **Destructuring**: Sintaxis de JavaScript para extraer valores de objetos/arrays, comúnmente usada para props: `{ contact, onToggle }`