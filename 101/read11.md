# 🌐 Read 11: Introducción al DOM y Proyectos

### 1. ¿Qué es el DOM?  
El DOM (Document Object Model) es una representación estructurada de un documento HTML o XML en forma de árbol. 🌳 Permite que los lenguajes de programación, como JavaScript, accedan y modifiquen la estructura, contenido y estilo de la página web de forma dinámica.  

---

### 2. Describe brevemente la relación entre el DOM y JavaScript.  
El DOM es la interfaz que JavaScript utiliza para interactuar con las páginas web. 🔗 A través del DOM, JavaScript puede seleccionar elementos, cambiar su contenido, modificar estilos y responder a eventos, como clics, para hacer las páginas más dinámicas e interactivas.  

---

### 3. ¿Qué método usarías para seleccionar un elemento del DOM por su ID y cómo se utiliza?  
El método `getElementById` se utiliza para seleccionar un elemento del DOM por su ID. 🆔 Por ejemplo:  
```javascript
const titulo = document.getElementById("miTitulo");
```
Esto selecciona el elemento con el ID miTitulo para que puedas modificarlo.

### 4 ¿Qué método utilizarías para cambiar el color de fondo de un elemento en el DOM y cómo se implementaría?
Usaría la propiedad style.backgroundColor para cambiar el color de fondo. 🎨 Ejemplo:
```javascript
const caja = document.getElementById("miCaja");
caja.style.backgroundColor = "lightblue";
```
Esto aplica un color de fondo azul claro al elemento con ID miCaja.

### Fuentes:
- [Introducción al DOM](https://developer.mozilla.org/es/docs/Web/API/Document_Object_Model/Introduction)
- [Manejo del DOM JS](https://www.freecodecamp.org/espanol/news/el-dom-de-javascript-un-tutorial-practico/)