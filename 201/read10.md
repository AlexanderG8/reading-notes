# Funciones y Callbacks en JavaScript

## Funciones -> [Articulo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions)

Las funciones en JavaScript son bloques de código reutilizables que permiten encapsular lógica, mejorar la legibilidad y facilitar el mantenimiento del código. Este informe analiza el artículo de MDN sobre Funciones en JavaScript, destacando:

- Sintaxis básica y declaración de funciones

- Tipos de funciones (declaradas, expresadas, arrow, generadoras, asíncronas)

- Manejo de parámetros y argumentos

- Ámbito (scope) y closures

- Recursión y casos de uso avanzados

A continuación, se detallan los conceptos clave con explicaciones, ejemplos y retos prácticos.

### 1. Declaración de Función

#### ¿Qué es?

- Una función declarada con la palabra clave `function` y un nombre identificador. Se carga antes de la ejecución del código (hoisting).

#### ¿Cómo funciona?

```javascript
function sumar(a, b) {
  return a + b;
}
console.log(sumar(2, 3)); // 5
```

#### Casos de uso:

- Cuando necesitas reutilizar lógica en múltiples lugares.

- Para organizar el código en bloques lógicos.

#### Retos prácticos:

- Crea una función que calcule el área de un círculo (área = π * r²).

- Escribe una función que convierta grados Celsius a Fahrenheit.

- Implementa una función que determine si un número es primo.

- Crea una función que devuelva el factorial de un número.

- Escribe una función que invierta una cadena de texto.

### 2. Expresión de Función

#### ¿Qué es?

- Una función asignada a una variable o constante. No tiene hoisting y puede ser anónima.

#### ¿Cómo funciona?

```javascript
const restar = function(a, b) {
  return a - b;
};
console.log(restar(5, 3)); // 2
```

#### Casos de uso:

- Cuando necesitas una función como valor (ej. callbacks).

- Para evitar contaminación del ámbito global.

#### Retos prácticos:

- Crea una expresión de función que multiplique dos números.

- Escribe una función que cuente las vocales en una cadena.

- Implementa una función que verifique si una palabra es palíndromo.

- Crea una función que genere un número aleatorio entre 1 y 100.

- Escribe una función que sume todos los números de un array.

### 3. Arrow Functions (ES6+)

#### ¿Qué es?

- Sintaxis compacta para funciones anónimas, con this léxico (no redefine su propio this).

#### ¿Cómo funciona?

```javascript
const duplicar = (num) => num * 2;
console.log(duplicar(4)); // 8
```

#### Casos de uso:

- Callbacks concisos (ej. .map(), .filter()).

- Funciones de una sola línea.

#### Retos prácticos:

- Convierte una función declarada en arrow function.

- Usa arrow functions para filtrar números pares de un array.

- Crea una arrow function que devuelva el mayor de dos números.

- Escribe una arrow function que capitalice la primera letra de una cadena.

- Implementa una arrow function que sume todos los argumentos pasados.

### 4. Parámetros y Argumentos

#### ¿Qué es?

- Parámetros: Variables definidas en la función.

- Argumentos: Valores pasados al llamar la función.

#### ¿Cómo funciona?

```javascript
function saludar(nombre = "Invitado") {
  return `Hola, ${nombre}!`;
}
console.log(saludar("Ana")); // "Hola, Ana!"
console.log(saludar()); // "Hola, Invitado!"
```

#### Casos de uso:

- Funciones con valores predeterminados.

- Manejo flexible de entradas.

#### Retos prácticos:

- Crea una función con parámetros predeterminados.

- Implementa una función que acepte argumentos variables (arguments).

- Escribe una función que concatene dos strings con un separador personalizable.

- Crea una función que calcule el promedio de números variables.

- Implementa una función que valide si un número está en un rango dado.

### 5. Closures

#### ¿Qué es?

- Una función que recuerda su ámbito léxico, incluso cuando se ejecuta fuera de él.

#### ¿Cómo funciona?

```javascript
function contador() {
  let count = 0;
  return () => ++count;
}
const incrementar = contador();
console.log(incrementar()); // 1
console.log(incrementar()); // 2
```

#### Casos de uso:

- Variables privadas en funciones.

- Memorización (cachear resultados).

#### Retos prácticos:

- Crea un closure que genere IDs autoincrementales.

- Implementa un closure para una calculadora con memoria.

- Escribe un closure que registre cuántas veces se ha llamado.

- Crea un closure que devuelva una función con un saludo personalizado.

- Implementa un closure para simular un contador de vida en un juego.

> En mi opinión, las funciones son esenciales en JavaScript y dominarlas mejora la estructura, legibilidad y mantenibilidad del código.

## Callbacks en JavaScript -> [Articulo](https://javascript.info/callbacks)

Los callbacks son funciones pasadas como argumentos a otras funciones para ser ejecutadas posteriormente, generalmente después de una operación asíncrona o condicional. Este informe analiza el artículo de JavaScript.info sobre Callbacks, cubriendo:

- Definición y propósito de los callbacks

- Uso en operaciones síncronas y asíncronas

- Problemas comunes (callback hell, manejo de errores)

- Alternativas modernas (Promesas, async/await)

A continuación, se detallan los conceptos clave con explicaciones, ejemplos y retos prácticos.

### Conceptos Clave

#### 1. ¿Qué es un Callback?

Definición:
Una función que se pasa como argumento a otra función y se ejecuta después de que esta última complete una tarea.

#### ¿Cómo funciona?

```javascript
function saludar(nombre, callback) {
  console.log(`Hola, ${nombre}!`);
  callback(); // Ejecuta el callback
}

function despedir() {
  console.log("Adiós!");
}

saludar("Ana", despedir); 
// Salida: 
// "Hola, Ana!"  
// "Adiós!"
```

#### Casos de uso:

- Operaciones asíncronas (ej. peticiones HTTP, temporizadores).

- Eventos (ej. addEventListener).

- Personalización de comportamientos (ej. funciones de orden superior como map o filter).

#### Retos prácticos:

- Crea una función que acepte un array y un callback, y aplique el callback a cada elemento.

- Implementa un callback que se ejecute después de un retraso de 2 segundos (setTimeout).

- Escribe una función que procese un número y llame a un callback con el resultado al cuadrado.

- Crea un callback que valide si un número es par y devuelva true o false.

- Simula una petición HTTP con setTimeout y usa un callback para manejar la "respuesta".

### 2. Callbacks Síncronos vs. Asíncronos

#### Definición:

- Síncrono: El callback se ejecuta inmediatamente (ej. Array.map()).

- Asíncrono: El callback se ejecuta después de una operación no bloqueante (ej. setTimeout).

#### Ejemplo síncrono:

```javascript
function procesarArray(arr, callback) {
  return arr.map(callback);
}
const resultado = procesarArray([1, 2, 3], (num) => num * 2);
console.log(resultado); // [2, 4, 6]
```

#### Ejemplo asíncrono:

```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback("Datos recibidos");
  }, 1000);
}
fetchData((data) => console.log(data)); // "Datos recibidos" (tras 1 segundo)
```

#### Retos prácticos:

- Crea una función que use un callback síncrono para filtrar números mayores que 5.

- Implementa un callback asíncrono que simule una carga de datos con setTimeout.

- Combina ambos: una función que procese datos síncronamente y luego llame a un callback asíncrono.

- Escribe un callback que se ejecute después de dos operaciones asíncronas secuenciales.

- Crea una función que acepte un callback y lo ejecute solo si una condición es verdadera.

### 3. Callback Hell (Infierno de Callbacks)

#### Definición:

- Anidación excesiva de callbacks que dificulta la legibilidad y el mantenimiento.

#### Ejemplo:

```javascript
setTimeout(() => {
  console.log("Paso 1");
  setTimeout(() => {
    console.log("Paso 2");
    setTimeout(() => {
      console.log("Paso 3");
    }, 1000);
  }, 1000);
}, 1000);
```

#### Solución:

- Usar Promesas o async/await.

- Modularizar el código en funciones separadas.

#### Retos prácticos:

- Refactoriza el ejemplo anterior usando funciones nombradas para cada setTimeout.

- Simula una secuencia de 3 operaciones asíncronas sin anidación excesiva.

- Escribe un flujo de autenticación (login → obtener perfil → mostrar datos) con callbacks planos.

- Implementa un manejador de errores para cada callback en una cadena.

- Convierte un callback hell en una solución con Promesas.

### 4. Manejo de Errores con Callbacks

#### Patrón estándar:

- El primer argumento del callback suele ser un error (error-first callbacks).

#### Ejemplo:

```javascript
function dividir(a, b, callback) {
  if (b === 0) {
    callback(new Error("División por cero"), null);
  } else {
    callback(null, a / b);
  }
}

dividir(10, 2, (err, resultado) => {
  if (err) {
    console.error(err.message);
  } else {
    console.log(resultado); // 5
  }
});
```

#### Retos prácticos:

- Crea una función que lea un archivo simulado (con setTimeout) y maneje errores.

- Implementa una calculadora con callbacks que valide operandos no numéricos.

- Escribe un callback que maneje errores en una petición HTTP simulada.

- Refactoriza el ejemplo de división para usar un objeto de error personalizado.

- Diseña un sistema de reintentos para una operación fallida usando callbacks.

### 5. Alternativas a Callbacks (Promesas, Async/Await)

#### Motivación:

- Los callbacks pueden volverse complejos en flujos asíncronos avanzados.

#### Ejemplo con Promesa:

```javascript
function fetchData() {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Datos resueltos"), 1000);
  });
}

fetchData().then((data) => console.log(data));
```

#### Retos prácticos:

- Convierte un callback hell en una cadena de Promesas.

- Implementa el ejemplo de división con manejo de errores usando Promesas.

- Escribe una función async/await que espere dos operaciones asíncronas.

- Crea una utilidad para promisificar funciones con callbacks.

- Combina callbacks y Promesas en un mismo flujo de trabajo.

> En mi opinión, los callbacks son fundamentales en JavaScript para manejar operaciones asíncronas y personalizar comportamientos, pero su uso inadecuado puede llevar a código difícil de mantener.
> 
> Recomendaciones:
>
>- Usar Promesas o async/await para flujos complejos.
>
>- Modularizar callbacks anidados en funciones independientes.
>
>- Siempre implementar manejo de errores (error-first).

## Funciones de Orden Superior en JavaScript ->  [Articulo](https://www.eloquentjavascript.es/05_higher_order.html)

Las funciones de orden superior son un pilar fundamental en JavaScript, permitiendo operar sobre otras funciones (como argumentos o valores de retorno). Este informe analiza el capítulo 5 de Eloquent JavaScript: Funciones de Orden Superior, cubriendo:

- Definición y características de las funciones de orden superior

- Funciones que aceptan otras funciones como argumentos (ej. map, filter, reduce)

- Funciones que retornan nuevas funciones (closures, factories)

- Composición funcional y abstracción

A continuación, se detallan los conceptos clave con explicaciones, ejemplos y retos prácticos.

### Conceptos Clave

#### 1. ¿Qué es una Función de Orden Superior?

#### Definición:

Una función que cumple al menos una de estas condiciones:

1. Acepta una o más funciones como argumentos.

2. Retorna una función como resultado.

#### Ejemplo básico:

```javascript
// Función que acepta un callback (orden superior)
function ejecutarOperacion(a, b, operacion) {
  return operacion(a, b);
}

// Callback (función normal)
function sumar(x, y) {
  return x + y;
}

console.log(ejecutarOperacion(2, 3, sumar)); // 5
```

#### Casos de uso:

1. Abstracción de patrones repetitivos (ej. iteraciones).

2. Personalización de comportamientos (ej. estrategias de procesamiento).

3. Creación de utilidades reutilizables (ej. decoradores, factories).

#### Retos Prácticos

1. Crea una función de orden superior que aplique una operación matemática (suma, resta, etc.) a dos números.

2. Implementa una función repetir(n, accion) que ejecute accion n veces.

3. Escribe una función que tome un array y un callback, y retorne un nuevo array con el callback aplicado a cada elemento.

4. Diseña una función mayorQue(n) que retorne otra función para validar si un número es mayor que n.

5. Crea una función logger(fn) que ejecute fn y registre en consola su nombre y argumentos.


#### 2. Funciones que Aceptan Callbacks

#### Definición:
Funciones de orden superior que reciben funciones para personalizar su lógica (ej. métodos de arrays).

#### Ejemplo con Array.map:

```javascript
const numeros = [1, 2, 3];
const duplicados = numeros.map((num) => num * 2);
console.log(duplicados); // [2, 4, 6]
```

#### Ejemplo personalizado:

```javascript
function filtrar(array, prueba) {
  const resultado = [];
  for (let item of array) {
    if (prueba(item)) {
      resultado.push(item);
    }
  }
  return resultado;
}

const pares = filtrar([1, 2, 3, 4], (num) => num % 2 === 0);
console.log(pares); // [2, 4]
```

#### Retos prácticos:

1. Implementa tu propia versión de Array.filter sin usar el método nativo.

2. Crea una función transformar(array, fn) que aplique fn a cada elemento y retorne un nuevo array.

3. Escribe una función contarSi(array, condicion) que cuente elementos que cumplan condicion.

4. Diseña una función procesarTexto(texto, fn) que aplique fn a cada palabra del texto.

5. Simula el método Array.reduce con una función personalizada.

#### 3. Funciones que Retornan Funciones

#### Definición:
Funciones que generan y retornan nuevas funciones (útil para crear comportamientos personalizados).

#### Ejemplo con factory function:

```javascript
function crearSaludador(saludo) {
  return function(nombre) {
    return `${saludo}, ${nombre}!`;
  };
}

const saludarEnEspañol = crearSaludador("Hola");
console.log(saludarEnEspañol("Ana")); // "Hola, Ana!"
```

#### Ejemplo con closures:

```javascript
function contador() {
  let cuenta = 0;
  return function() {
    cuenta += 1;
    return cuenta;
  };
}

const incrementar = contador();
console.log(incrementar()); // 1
console.log(incrementar()); // 2
```

#### Retos prácticos:

1. Crea una función multiplicador(n) que retorne una función para multiplicar por n.

2. Implementa una función prefijador(prefijo) que añada un prefijo a strings.

3. Diseña una función cache(fn) que cachee resultados para evitar cálculos repetidos.

4. Escribe una función crearValidador(regla) que retorne un validador basado en regla.

5. Crea una función generadorDeIds() que retorne una función para generar IDs únicos.

#### 4. Abstracción y Composición Funcional

#### Definición:
Usar funciones de orden superior para ocultar detalles complejos y combinar operaciones simples.

#### Ejemplo de abstracción:

```javascript
// Sin abstracción
for (let i = 0; i < 10; i++) {
  console.log(i);
}

// Con abstracción
function repetir(n, accion) {
  for (let i = 0; i < n; i++) {
    accion(i);
  }
}

repetir(10, console.log);
```

#### Ejemplo de composición:

```javascript
function componer(f, g) {
  return function(x) {
    return f(g(x));
  };
}

const duplicar = (x) => x * 2;
const sumarUno = (x) => x + 1;

const duplicarYSumar = componer(sumarUno, duplicar);
console.log(duplicarYSumar(3)); // 7 (3*2=6 → 6+1=7)
```

#### 5. Retos prácticos:

1. Crea una función pipe(fn1, fn2) que ejecute fn1 y luego fn2 sobre el resultado.

2. Implementa una función andThen(fn1, fn2) similar a componer, pero en orden inverso.

3. Diseña una utilidad ejecutarEnSecuencia(...funcs) que aplique todas las funciones en orden.

4. Escribe una función condicional(predicado, fn) que ejecute fn solo si predicado es verdadero.

5. Crea una función medirTiempo(fn) que ejecute fn y retorne el tiempo que tardó.

#### 5. Métodos de Arrays como Funciones de Orden Superior

#### Definición:
JavaScript incluye funciones de orden superior nativas para manipular arrays:

| Método|Descripción|Ejemplo
|---|---|---
| map|Transforma cada elemento|array.map(x => x * 2)
| filter|Filtra elementos según condición|array.filter(x => x > 5)
| reduce|Reduce el array a un único valor|array.reduce((acc, x) => acc + x, 0)
| some|Verifica si algún elemento cumple condición|array.some(x => x < 0)
| every|Verifica si todos cumplen condición|array.every(x => x !== null)

#### Ejemplo integrado:

```javascript
const datos = [1, 2, 3, 4, 5];

// Pipeline funcional
const resultado = datos
  .filter((x) => x % 2 === 0) // [2, 4]
  .map((x) => x * 10) // [20, 40]
  .reduce((acc, x) => acc + x, 0); // 60

console.log(resultado); // 60
```

#### 6. Retos prácticos

1. Dado un array de strings, crea un nuevo array con las longitudes de cada string.

2. Filtra un array de números para obtener solo los positivos y luego súmalos.

3. Usa reduce para contar cuántas veces aparece cada letra en un string.

4. Implementa una función aplanar(array) que convierta un array de arrays en uno plano.

5. Combina map, filter y reduce para calcular el promedio de números pares.


---

## Conceptos Clave en total 

- **Funciones de Primera Clase**:
JavaScript permite tratar las funciones como valores, lo que significa que pueden ser asignadas a variables, almacenadas en estructuras de datos, pasadas como argumentos y devueltas como resultado de otras funciones.

- **Callbacks**:
Funciones que se pasan como argumentos a otras funciones y se ejecutan en un momento específico. Se usan comúnmente en el manejo de eventos y en la programación asincrónica.

- **Funciones de Orden Superior**:
Funciones que reciben otras funciones como parámetros o retornan funciones. Son esenciales para la programación funcional y facilitan la reutilización del código.

---

## Reflexiones para Analizar Críticamente

### 1. Funciones como valores en JavaScript

**¿Qué ventajas tiene el tratar a las funciones como valores en JavaScript? ¿En qué situaciones esta característica puede generar código difícil de depurar?**

Tratar funciones como valores permite mayor flexibilidad y reutilización de código. Puedes pasar funciones como argumentos, retornarlas desde otras funciones o asignarlas a variables, lo que facilita patrones como callbacks y factories. Sin embargo, cuando las funciones son anónimas o se pasan en cascada, puede ser difícil rastrear errores debido a la falta de nombres descriptivos en la pila de llamadas.

**Ejemplo**:

```javascript
// Ventaja: Flexibilidad
const operaciones = {
  suma: (a, b) => a + b,
  resta: (a, b) => a - b
};

function calcular(a, b, operacion) {
  return operacion(a, b);
}

console.log(calcular(5, 3, operaciones.suma)); // 8

// Problema: Depuración complicada
setTimeout(() => {
  obtenerDatos(() => {
    procesar(() => console.log("Listo")); // ¿Dónde falló?
  });
}, 1000);
```

**Conclusión:**

Las funciones como valores son poderosas para crear código modular, pero es importante nombrarlas adecuadamente y evitar anidaciones excesivas para facilitar la depuración.

### 2. Uso de Callbacks

**¿Cuándo es recomendable usar callbacks en vez de ejecutar directamente una función? ¿Cómo afectan los callbacks a la legibilidad del código?**

Los callbacks son ideales para operaciones asíncronas (como peticiones HTTP o temporizadores) o para personalizar comportamientos (como en Array.map). Sin embargo, su uso excesivo puede reducir la legibilidad, especialmente cuando se anidan ("callback hell").

**Ejemplo**:

```javascript
// Caso ideal: Asincronía
function cargarImagen(url, callback) {
  const img = new Image();
  img.onload = () => callback(null, img);
  img.onerror = (err) => callback(err);
  img.src = url;
}

// Callback hell (mala legibilidad)
login(() => {
  getUser(() => {
    getPosts(() => { ... });
  });
});
```

**Conclusión:**

Usa callbacks para asincronía o personalización, pero considera Promesas o async/await para mejorar la legibilidad en flujos complejos.

### 3. Callback Hell

**¿Por qué el uso excesivo de callbacks puede llevar a código difícil de entender? ¿Qué alternativas existen para evitar este problema?**

El callback hell ocurre al anidar múltiples callbacks, creando una estructura piramidal difícil de seguir. Esto complica el mantenimiento y la depuración. Las alternativas modernas son Promesas y async/await, que permiten un flujo lineal.

**Ejemplo:**

```javascript
// Callback hell
fs.readFile("archivo1.txt", (err, data1) => {
  fs.readFile("archivo2.txt", (err, data2) => {
    fs.writeFile("resultado.txt", data1 + data2, (err) => {
      if (err) throw err;
    });
  });
});

// Solución con Promesas
Promise.all([
  fs.promises.readFile("archivo1.txt"),
  fs.promises.readFile("archivo2.txt")
]).then(([data1, data2]) => {
  return fs.promises.writeFile("resultado.txt", data1 + data2);
});
```

**Conclusión:**

Evita el callback hell usando Promesas o async/await para código más limpio y mantenible.

### 4. Funciones de Orden Superior en la Práctica

**¿Cómo el uso de funciones de orden superior puede hacer que el código sea más modular y reutilizable? ¿Puedes mencionar un ejemplo donde una función de orden superior simplifique una tarea común?**

Las funciones de orden superior (FOS) permiten abstraer patrones repetitivos, haciendo el código más modular. Por ejemplo, los métodos de arrays (map, filter) son FOS que evitan escribir loops manuales.

**Ejemplo:**

```javascript
// Sin FOS (menos reutilizable)
const numeros = [1, 2, 3];
const duplicados = [];
for (let i = 0; i < numeros.length; i++) {
  duplicados.push(numeros[i] * 2);
}

// Con FOS (más claro)
const duplicados = numeros.map((num) => num * 2);

// FOS personalizada
function crearMultiplicador(factor) {
  return (num) => num * factor;
}
const duplicar = crearMultiplicador(2);
console.log(duplicar(5)); // 10
```

**Conclusión:**

Las FOS promueven la reutilización y claridad, especialmente en manipulación de datos.

### 5. Eficiencia y Performance

**¿Las funciones de orden superior y los callbacks afectan el rendimiento de una aplicación? ¿Cuándo es mejor evitar su uso?**

**Respuesta:**
En general, el impacto en rendimiento es mínimo, pero en bucles críticos (ej. procesamiento de millones de datos), las FOS como map pueden ser más lentas que un for clásico debido a sobrecarga de llamadas a funciones.

**Ejemplo:**

```javascript
// Benchmark: for vs map
const arrayGrande = Array(1e6).fill(1);

// for (más rápido en bucles grandes)
let suma = 0;
for (let i = 0; i < arrayGrande.length; i++) {
  suma += arrayGrande[i];
}

// reduce (más lento)
const suma = arrayGrande.reduce((acc, num) => acc + num, 0);
```

**Conclusión:**

Usa FOS/callbacks para claridad en la mayoría de casos, pero opta por loops tradicionales en código crítico para performance.

### 6. Aplicación en el Editor de Markdown

**¿Cómo podríamos aprovechar funciones de orden superior en la implementación del editor? ¿En qué parte del código sería más útil su uso?**

Las FOS son ideales para procesar texto (ej. aplicar formatos, filtrar líneas) o manejar eventos (ej: botones de acción). Por ejemplo, un sistema de plugins podría usar FOS para permitir extensiones personalizadas.

**Ejemplo:**

```javascript
// Procesamiento de markdown con FOS
const formatos = {
  negrita: (texto) => `**${texto}**`,
  cursiva: (texto) => `_${texto}_`,
};

function aplicarFormato(texto, formato) {
  return formato(texto);
}

console.log(aplicarFormato("Hola", formatos.negrita)); // **Hola**

// Sistema de plugins
const plugins = [sanitizarTexto, resaltarSintaxis];
const contenidoProcesado = plugins.reduce(
  (texto, plugin) => plugin(texto), 
  "# Título"
);
```

**Conclusión:**

Usa FOS en el editor para manejar formatos, eventos o plugins, haciendo el código extensible y mantenible.


