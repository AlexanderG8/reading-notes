### ¿Cómo funcionan internamente las clases en JavaScript y en qué se diferencian de las funciones constructoras tradicionales?
**Respuesta**:  
Las clases en JavaScript son una forma sintáctica más moderna y clara para definir objetos y trabajar con herencia. Internamente, las clases son funciones constructoras bajo el capó, pero su sintaxis es más intuitiva y tiene características adicionales, como métodos estáticos y la herencia directa mediante `extends`.

---

### ¿Cuál es la diferencia entre un estado global y un estado local?
**Respuesta**:  
El estado **local** es específico de un componente o función y no es accesible desde otras partes de la aplicación. El estado **global**, en cambio, es accesible desde cualquier parte de la aplicación y suele ser compartido entre varios componentes o funciones.

---

### ¿Qué es un estado estático y cómo se diferencia del estado local y global?
**Respuesta**:  
Un **estado estático** es un valor que no cambia a lo largo de la ejecución del programa o que cambia solo en ciertas condiciones, pero de manera muy controlada. A diferencia del estado **local**, que cambia dentro de un contexto específico, y el estado **global**, que puede ser accedido y modificado desde cualquier parte, el estado estático suele ser constante o cambia de forma más limitada.

---

### ¿Cómo se gestiona el estado global de manera segura?
**Respuesta**:  
El estado global se debe gestionar cuidadosamente, utilizando técnicas como un gestor de estado centralizado o una solución que controle los cambios en el estado. Esto asegura que los datos no se modifiquen de manera inesperada desde diferentes partes de la aplicación, lo que podría generar inconsistencias.

---

### ¿Cuáles son las ventajas y desventajas de usar estado local vs estado global?
**Respuesta**:  
- **Estado local**:  
  - **Ventajas**: Aislado, fácil de gestionar y modificar dentro de un componente o función.  
  - **Desventajas**: Si varios componentes necesitan compartir el mismo estado, se necesita propagar los datos, lo que puede complicar el diseño.
  
- **Estado global**:  
  - **Ventajas**: Ideal para compartir datos entre diferentes partes de la aplicación sin necesidad de pasarlos explícitamente entre componentes.  
  - **Desventajas**: Puede volverse difícil de gestionar y propenso a errores si no se controla adecuadamente.

---

### ¿Cómo saber si usar estado local o global en mi aplicación?
**Respuesta**:  
Usa **estado local** cuando los datos solo se necesitan en un contexto específico o componente. Usa **estado global** cuando los datos necesitan ser accesibles y modificados por varias partes de la aplicación.
