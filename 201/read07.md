# 📚 Resumen sobre Objetos y Funciones Constructoras en JavaScript

## 🏗️ Conceptos Básicos de Objetos en JavaScript  
Los **objetos** en JavaScript son estructuras clave que permiten almacenar datos en pares **clave-valor**.  
Ejemplo de un objeto simple:  

```js
const persona = {
  nombre: "Juan",
  edad: 30,
  saludar: function () {
    console.log(`Hola, soy ${this.nombre}`);
  },
};
```
### 🔹 Características principales:
- ✅ Los objetos agrupan datos y métodos relacionados.
- ✅ Se pueden modificar dinámicamente agregando o eliminando propiedades.
- ✅ JavaScript usa prototipos en lugar de clases tradicionales.

## 🏗️ Funciones Constructoras en JavaScript
Antes de ES6, la manera más común de crear múltiples objetos con la misma estructura era usando funciones constructoras.
```js
function Persona(nombre, edad) {
  this.nombre = nombre;
  this.edad = edad;
}

const juan = new Persona("Juan", 30);
console.log(juan.nombre); // "Juan"
```
### 🔹 Características:
- ✅ Se usa la palabra clave this para asignar propiedades al objeto creado.
- ✅ Se debe invocar con new para que this apunte al nuevo objeto.
- ✅ Permiten la reutilización de código y la creación de múltiples instancias.

## 🧬 Prototipos y Métodos Compartidos
JavaScript usa prototipos en lugar de herencia clásica. Esto permite compartir métodos sin duplicarlos en cada instancia.
```js
Persona.prototype.saludar = function () {
  console.log(`Hola, soy ${this.nombre}`);
};

juan.saludar(); // "Hola, soy Juan"
```
✅ Ventaja: Ahorra memoria al compartir métodos entre instancias.

## 🆕 Clases en ES6: Una Alternativa a las Funciones Constructoras
Desde ES6, las clases ofrecen una sintaxis más clara y organizada.
```js
class Persona {
  constructor(nombre, edad) {
    this.nombre = nombre;
    this.edad = edad;
  }
  saludar() {
    console.log(`Hola, soy ${this.nombre}`);
  }
}
const maria = new Persona("María", 25);
maria.saludar(); // "Hola, soy María"
```
✅ Ventajas de las clases:

- Mejor legibilidad y organización.
- Soporte para herencia con extends.
- Facilitan el mantenimiento del código.

## 🔀 Ramas en Git: Organización del Código
En desarrollo colaborativo, Git permite gestionar cambios sin afectar la rama principal mediante ramas (branches).

### 🔹 Beneficios de usar ramas:
- ✅ Se pueden desarrollar nuevas funcionalidades sin alterar el código estable.
- ✅ Facilitan la colaboración entre varios desarrolladores.
- ✅ Se pueden probar cambios antes de fusionarlos (merge).

Ejemplo de cómo crear y cambiar de rama en Git:
```sh
git branch nueva-funcionalidad
git checkout nueva-funcionalidad
```
🔹 Fusionar cambios a la rama principal:
```sh
git checkout main
git merge nueva-funcionalidad
```
✅ Ayuda a mantener la estabilidad del código y a resolver conflictos antes de integrarlos.


## 🧐 Análisis sobre Programación Orientada a Objetos en JavaScript

## 1️⃣ “Todos los lenguajes orientados a objetos soportan herencia múltiple por defecto.”  
**❌ Mito**  
No todos los lenguajes soportan **herencia múltiple** de forma nativa. Por ejemplo, **Java y JavaScript no permiten herencia múltiple directa** en clases, aunque en JavaScript se puede simular usando **mixins o composición**.

---

## 2️⃣ “La Programación Orientada a Objetos permite organizar el código en entidades con responsabilidad clara.”  
**✅ Verdad**  
La **POO** permite estructurar el código en **clases y objetos**, asignando responsabilidades a cada entidad, lo que mejora la **modularidad, reutilización y mantenimiento**.

---

## 3️⃣ “En JavaScript, usar funciones constructoras es obsoleto porque existen las clases desde ES6.”  
**❌ Mito**  
Aunque ES6 introdujo la **sintaxis de clases**, las **funciones constructoras** siguen siendo válidas y ampliamente usadas, especialmente en código heredado. Internamente, las clases en JavaScript siguen funcionando con **prototipos**, por lo que no son "obsoletas", solo menos comunes.

---

## 4️⃣ “La abstracción implica eliminar cualquier detalle que no sea importante para la funcionalidad principal.”  
**✅ Verdad**  
La **abstracción** en POO consiste en **ocultar los detalles internos** de una implementación y exponer solo las funcionalidades esenciales. Esto mejora la **seguridad y simplicidad** del código.

---

## 5️⃣ “Para crear objetos usando funciones constructoras, es obligatorio usar el prototipo explícitamente.”  
**❌ Mito**  
Las **funciones constructoras** en JavaScript crean automáticamente un **prototipo vinculado** al objeto, por lo que **no es obligatorio** modificarlo manualmente. Sin embargo, se puede extender el prototipo para compartir métodos entre instancias.

---

## 6️⃣ “La POO promueve la escalabilidad al agrupar datos y comportamiento en entidades lógicas.”  
**✅ Verdad**  
La POO organiza el código en **clases y objetos**, facilitando la **extensibilidad y reutilización**. Esto permite manejar proyectos grandes de manera más eficiente.

---

## 7️⃣ “La palabra clave this en las funciones constructoras apunta a un objeto global, sin importar si se usa new.”  
**❌ Mito**  
Cuando una función constructora se llama con `new`, `this` apunta al **nuevo objeto creado**. Si se llama sin `new`, `this` puede apuntar al **objeto global** (`window` en navegadores) o ser `undefined` en `strict mode`.
