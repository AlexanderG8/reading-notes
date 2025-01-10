# 🚀 **Guía Básica de JavaScript**  

## 🧮 **¿Cuáles son los diferentes tipos de datos que se pueden utilizar en JavaScript y cómo se diferencian entre sí?**  
JavaScript ofrece varios tipos de datos para manejar información:  
- 🔢 **Números**: Enteros y decimales (ejemplo: `42`, `3.14`).  
- 📝 **Cadenas de texto (Strings)**: Secuencias de caracteres (ejemplo: `"Hola mundo"`).  
- ✅ **Booleanos**: Valores lógicos (`true` o `false`).  
- ❌ **Null**: Representa la ausencia intencional de un valor.  
- 🤷‍♂️ **Undefined**: Variable declarada pero no inicializada.  
- 🪙 **Símbolos (Symbols)**: Identificadores únicos e inmutables.  
- 📦 **Objetos**: Estructuras complejas como arreglos y funciones.  

Cada tipo tiene propiedades únicas y se usa según el contexto.  

---

## 🔄 **¿Cómo se utilizan las estructuras condicionales if y else en JavaScript, y qué propósito cumplen dentro de un programa?**  
Las estructuras condicionales permiten tomar decisiones en el programa:  
- 🌟 **`if`**: Evalúa una condición; si es verdadera (`true`), ejecuta el código asociado.  
- 🚦 **`else`**: Proporciona una alternativa cuando la condición es falsa.  

📌 **Ejemplo**:  
```javascript
if (hora < 12) {
  console.log("¡Buenos días!");
} else {
  console.log("¡Buenas tardes!");
}
```
Son esenciales para manejar el flujo del programa de forma dinámica.

## ➕ ¿Cuáles son los diferentes tipos de operadores en JavaScript y cómo se utilizan los operadores aritméticos para realizar cálculos?
JavaScript incluye diversos operadores para manipular datos:

- ➗ Aritméticos: Suma (+), resta (-), multiplicación (*), división (/), resto (%), exponenciación (**).
- ✍️ Asignación: Asigna valores (=).
- ⚖️ Comparación: Compara valores (==, ===, >, <).
- 🔗 Lógicos: Operan con booleanos (&&, ||, !).

📌 Ejemplo de operador aritmético:
```
let suma = 5 + 3; // Resultado: 8
```

## 🖋️ ¿Cómo se declara una variable en JavaScript y cuáles son las diferencias entre var, let y const en cuanto a su alcance y mutabilidad?
En JavaScript, puedes declarar variables usando:

- 🌍 var: Alcance global o de función, permite redeclaración y reasignación.
- 🛑 let: Alcance de bloque, permite reasignación pero no redeclaración.
- 🔒 const: Alcance de bloque, no permite reasignación ni redeclaración.

📌 Ejemplo:
```
let edad = 25; // Mutable y con alcance de bloque
const nombre = "Juan"; // Inmutable
```
Usa let y const para un código más seguro y moderno.

## 🔗 Recursos extras
- [Variables y tipos de datos de JS](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Grammar_and_types)
- [Operadores en JS](https://es.javascript.info/operators)
- [Operadores condicionales](https://es.javascript.info/ifelse)