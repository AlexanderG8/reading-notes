# DOM como API de Objetos

## 📚 Introducción

1. [Introducción al Document Object Model (DOM)](#introducción-al-document-object-model-dom)
2. [querySelectorAll](#queryselectorall)
3. [Expresiones Regulares en JavaScript](#expresiones-regulares-en-javascript)
4. [Mito o Verdad?](#mito-o-verdad)

--

## Introducción al Document Object Model (DOM)

🔗 [Artículo Original](https://developer.mozilla.org/es/docs/Web/API/Document_Object_Model/Introduction)

### 1️⃣ ¿Qué es el DOM?
El DOM (Document Object Model) es una interfaz que representa documentos HTML/XML como una estructura de árbol donde cada elemento (etiquetas, atributos, texto) es un nodo. Permite a programas (como JavaScript) modificar dinámicamente el contenido, estructura y estilo de una página web.

### Características clave:
No es parte de JavaScript: Es una API web accesible desde JS (y otros lenguajes).

Estándar universal: Definido por el W3C.

Modelo orientado a objetos: Los elementos son objetos con propiedades y métodos.

### 2️⃣ Estructura del DOM: El Árbol de Nodos
El DOM organiza los elementos como un árbol jerárquico:
```mermaid
graph TD
  A[document] --> B(html)
  B --> C(head)
  B --> D(body)
  C --> E(title)
  D --> F(h1)
  D --> G(p)
  F --> H(Texto "Hola")
  G --> I(Texto "Mundo")
```

### Tipos de nodos principales:
| Tipo de Nodo | Ejemplo |
|--------------|----------|
| Document     | ``document`` (raíz del árbol)   |
| Element      | ``<div>``, ``<p>``, ``<body>``   |
| Attr         | ``class="ejemplo"``   |
| Text         | Texto dentro de una etiqueta (``<p>Hola</p>`` → "Hola")  |
| Comment      | ``<!-- Esto es un comentario --> ``  |

### 3️⃣ ¿Para qué sirve el DOM?
Principalmente para:

- **Leer/modificar contenido:**

```javascript
document.getElementById("titulo").textContent = "Nuevo título";
```

- **Cambiar estilos:**

```javascript
document.querySelector("p").style.color = "red";
```

- **Añadir/eliminar elementos:**

```javascript
const nuevoElemento = document.createElement("div");
document.body.appendChild(nuevoElemento);
```

- **Gestionar eventos:**

```javascript
boton.addEventListener("click", () => alert("¡Hola!"));
```

### 4️⃣ Ejemplo Práctico

```html
<!DOCTYPE html>
<html>
<head>
  <title>Ejemplo DOM</title>
</head>
<body>
  <h1 id="saludo">Hola</h1>
  <script>
    // Acceder al elemento <h1> y modificarlo
    const titulo = document.getElementById("saludo");
    titulo.textContent = "¡Bienvenido al DOM!";
    titulo.style.color = "blue";
  </script>
</body>
</html>
```

**Resultado:** El texto "Hola" cambia a "¡Bienvenido al DOM!" en color azul.

### 5️⃣ Diferencias clave

- **DOM vs HTML:**
  - **HTML:** Código estático (lo que escribes).
  - **DOM:** Representación viva del HTML que puede modificarse en tiempo real.

- **DOM vs JavaScript:**
  - El DOM es una API independiente, pero JS es el lenguaje más usado para interactuar con él.

### 🚀Conclusión
El DOM es el puente entre el documento HTML y los lenguajes de programación, permitiendo crear páginas web dinámicas e interactivas.

## querySelectorAll
🔗 [Artículo Original](https://developer.mozilla.org/es/docs/Web/API/Document/querySelectorAll)

### 1️⃣ ¿Qué es querySelectorAll?

``querySelectorAll()`` es un método del DOM que devuelve una lista estática de nodos (NodeList) con todos los elementos que coincidan con uno o más selectores CSS especificados.

### Características clave:

- ✨ Versátil: Acepta cualquier selector CSS válido (etiquetas, clases, IDs, atributos, pseudoclases).

- 🛑 Estático: La NodeList devuelta no se actualiza automáticamente si el DOM cambia.

- 📜 Soporte universal: Funciona en todos los navegadores modernos.

### 2️⃣ Sintaxis y Parámetros

```javascript
const elementos = document.querySelectorAll(selectores);
```

### Parámetros:

- selectores:
  - Tipo: String.
  - Contiene uno o más selectores CSS separados por comas (ej: "p, .clase, #id").

### Valor devuelto:

  - Una NodeList (similar a un array, pero con métodos limitados).

### 3️⃣ Diferencia entre NodeList y Array

| Característica | NodeList | Array |
|--------------|----------|-------|
| Mutabilidad | Estática (generalmente) | Dinámica |
| Métodos disponibles | ``forEach()``, ``item()`` | ``map()``, ``filter()``, etc. |
| Conversión | ``Array.from(NodeList)`` | No requiere conversión |

### Ejemplo de conversión a Array:

```javascript
const lista = document.querySelectorAll(".clase");
const array = Array.from(lista); // Ahora es un Array completo
```

### 4️⃣ Uso práctico

#### Ejemplo 1: Seleccionar elementos por clase

```javascript
// Selecciona todos los elementos con clase "destacado"
const destacados = document.querySelectorAll('.destacado');

// Cambiar su color de texto
destacados.forEach(elemento => {
  elemento.style.color = 'red';
});
```

#### Ejemplo 2: Ejemplo 2: Seleccionar múltiples tipos de elementos

```javascript
// Selecciona todos los <p>, <div> y elementos con clase "importante"
const varios = document.querySelectorAll('p, div, .importante');
```

#### Ejemplo 3: Anidamiento de selectores

```javascript
// Selecciona todos los <li> dentro de <ul class="lista">
const itemsLista = document.querySelectorAll('ul.lista li');
```

### 5️⃣ querySelectorAll vs querySelector vs getElementBy*

| Método | Devuelve | ¿Dinámico? | Sintaxis |
|--------------|----------|-------|-------|
| querySelectorAll | NodeList (Todos) | No | ``document.querySelectorAll(selectores)`` |
| querySelector | Primer element o null | Sí | ``document.querySelector(selector)`` |
| getElementBy* | Un elemento o null | Sí | ``document.getElementById(id)`` |
| getElementsByClassName | HTMLCollection (vivos) | Sí | ``document.getElementsByClassName(className)`` |

### ¿Cuándo usar cada uno?

- Usa ``querySelectorAll()`` cuando necesites múltiples elementos con selectores CSS complejos.
- Usa ``getElementBy*`` cuando necesites colecciones actualizables en tiempo real.

### 6️⃣ Consideraciones de Rendimiento

⚠️ Ojo con los selectores muy amplios:

```javascript
// Ineficiente: busca en TODO el documento
const todosLosDivs = document.querySelectorAll('div');

// Mejor: acota la búsqueda a un contenedor
const contenedor = document.getElementById('app');
const divsLocales = contenedor.querySelectorAll('div');
```

### 7️⃣ Ejemplo Avanzado: Eventos en múltiples elementos

```javascript
// Añadir evento click a todos los botones con clase "accion"
const botones = document.querySelectorAll('.accion');

botones.forEach(boton => {
  boton.addEventListener('click', () => {
    console.log('Botón presionado:', boton.textContent);
  });
});
```

### ✅ Conclusión

- ``querySelectorAll()`` es potente para selecciones complejas estáticas.
- Combínalo con ``Array.from()`` o ``forEach()`` para manipulación eficiente.
- Alternativas: Usa ``getElementsByClassName`` o ``getElementsByTagName`` para colecciones dinámicas.

## Expresiones Regulares en JavaScript

🔗 [Artículo Original](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Regular_Expressions)

### 🔍 **¿Qué son las Expresiones Regulares?**

Herramientas para:

- **Buscar** patrones en texto
- **Validar** formatos (emails, teléfonos)
- **Extraer/modificar** partes de cadenas

```javascript
// Sintaxis básica
const regex = /patrón/[banderas];
const regexObj = new RegExp('patrón', 'banderas');
```
### 🌟 Componentes principales

1. **Patrones básicos**

|Patrón | Significado | Ejemplo|
|-------|-------------|--------|
| `\d` | Dígito (0-9) | `/\d/` → "5" en "a5" |
| `\w` | Carácter alfanumérico | `/\w/` → "a" en "!a" |
| `\s` | Espacio en blanco | `/\s/` → " " en "a b" |
| `.` | Cualquier carácter | `/./` → "a" en "a!" |

2. **Cuantificadores**

|Símbolo | Función | Ejemplo|
|-------|-------------|--------|
| `*` | Cero o más veces | `/a*/` → "" o "aaa" |
| `+` | Una o más veces | `/a+/` → "a" o "aa" |
| `?` | Cero o una vez | `/a?/` → "" o "a" |
| `{n}` | Exactamente n veces | `/\d{3}/` → "123" |

3. **Banderas (flags)**

|Banderas | Efecto |
|-------|-------------|
| `i` | Ignorar mayúsculas/minúsculas|
| `g` | Buscar todas las coincidencias |
| `m` | Multilínea |

### 💡 Métodos clave

1. **test() → Verifica coincidencia**

```javascript
/^[a-z]+$/.test("hola"); // true
/\d/.test("abc"); // false
```

2. **exec() → Devuelve array con detalles**

```javascript
const resultado = /(\d{2})-(\d{2})/.exec("15-04");
// ["15-04", "15", "04", index: 0, ...]
```

3. **String.match() → Similar a exec**

```javascript
"2023-05-20".match(/\d{4}/); // ["2023"]
```

4. **String.replace() → Reemplaza coincidencias**

```javascript
"foo bar".replace(/\w+/, "hola"); // "hola bar"
```

### 🛠 Ejemplos prácticos

1. **Validación de email**

```javascript
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
emailRegex.test("user@example.com"); // true
```

2. **Extraer números de teléfono**

```javascript
const text = "Llame al 555-1234 o 800-5678";
const phones = text.match(/\d{3}-\d{4}/g); // ["555-1234", "800-5678"]
```

3. **Formatear fechas**

```javascript
"15-04-2023".replace(/(\d{2})-(\d{2})-(\d{4})/, "$3/$2/$1");
// Resultado: "2023/04/15"
```

### ⚠️ Errores comunes

1. **Escapar caracteres especiales:**

```javascript
// Incorrecto (busca "a" seguido de cualquier carácter)
/a./.test("a*"); // true

// Correcto (busca "a*" literal)
/a\*/.test("a*"); // true
```

2. **Greedy vs lazy:**

```javascript
/<.+>/.exec("<div>hola</div>")[0]; // "<div>hola</div>" (greedy)
/<.+?>/.exec("<div>hola</div>")[0]; // "<div>" (lazy)
```

### 📊 Comparación: Literal vs Constructor

|Aspecto | Literal | Constructor |
|-------|-------------|-------------|
| Uso | Patrones fijos| Patrones dinámicos |
| Ejemplo | ``/\d+/`` | `new RegExp('\\d+')` |
| Ventaja | Mejor rendimiento | Permite concatenación |

### 🚀 Ejemplo avanzado: Tokenizador

```javascript

const text = "3 manzanas y 5 naranjas";
const regex = /(\d+)\s(\w+)/g;
let tokens = [], match;

while ((match = regex.exec(text)) !== null) {
  tokens.push({ cantidad: match[1], item: match[2] });
}
/*
[
  { cantidad: "3", item: "manzanas" },
  { cantidad: "5", item: "naranjas" }
]
*/
```

### 🔍 Herramientas recomendadas

1. [RegExr - Probador interactivo](https://regexr.com/)
2. [Regex101 - Debugger con explicaciones](https://regex101.com/)
3. [Cheatsheet - Hoja de referencia rápida](https://cheatsheet.io/regex/)

### ✅ Conclusión

- Regex son poderosas para manejo de texto
- Combina patrones con banderas para mayor flexibilidad
- Prueba siempre tus expresiones con casos extremos

## Mito o Verdad ?

1. Usar querySelector() siempre devuelve una colección de nodos, incluso si selecciona uno solo.

    - **Mito**: ``querySelector()`` devuelve solo el primer nodo que coincide (o null), no una colección.

2. El DOM permite manipular estilos CSS directamente desde JavaScript usando propiedades específicas como ``.style`` y ``.classList``.

    - **Verdad**: El DOM permite manipular estilos directamente con ``.style`` (para estilos en línea) y ``.classList`` (para clases CSS).

3. Una expresión regular (Regex) siempre devolverá el mismo resultado sin importar el contexto o idioma del texto que analice.

    - **Mito**: Las Regex pueden comportarse diferente según el idioma (ej: \w incluye letras acentuadas solo con la bandera ``u``: ``/\w/u``).

4. Utilizar ``querySelectorAll()`` es menos eficiente que ``getElementById()`` cuando se busca un único elemento por su ID.

    - **Verdad**: ``getElementById()`` es más rápido para buscar un único ID, ya que está optimizado para ese caso.

5. Todos los métodos del DOM devuelven elementos del mismo tipo, no existen diferencias entre ellos.

    - **Mito**: Los métodos del DOM devuelven distintos tipos (``HTMLCollection`` vs ``NodeList``, dinámicos vs estáticos).

6. ``querySelectorAll()`` permite seleccionar múltiples elementos y devuelve una lista estática (no viva) de nodos.

    - **Verdad**: ``querySelectorAll()`` devuelve una ``NodeList`` estática (no se actualiza si el DOM cambia).

7. Las expresiones regulares (Regex) se pueden utilizar para transformar contenido de texto (Markdown a HTML, por ejemplo) sin necesidad de librerías externas.

    - **Verdad**: Regex puede transformar texto (ej: reemplazar ``texto`` por ``<strong>texto</strong>``), pero para conversiones complejas (Markdown → HTML) se recomiendan librerías.

8. Los cambios realizados en los nodos del DOM usando JavaScript son permanentes incluso después de refrescar la página.

    - **Mito**: Los cambios en el DOM se pierden al refrescar, a menos que se guarden en almacenamiento (localStorage, base de datos, etc.).

