# ¿Cuál es el propósito de CSS?

**CSS** (Cascading Style Sheets) o en español **Hojas de Estilos en Cascada**, es un lenguaje diseñado para controlar los estilos y presentación de los elementos de HTML en una página web.

Su principal propósito es **distinguir la estructura del contenido HTML de su apariencia**, permitiendo personalizar:

- Tamaño
- Colores
- Espaciado
- Fuentes
- Disposición

Esto mejora la experiencia visual del usuario, además de facilitar el mantenimiento del diseño.

---

# ¿Qué analogía NO técnica usarías para explicar la responsabilidad de HTML vs. CSS?

Para poder explicar de una manera que todos entiendan la responsabilidad de **HTML** vs **CSS**, hagamos de idea que:

- **HTML** es como la **estructura de una casa**, donde se definen las paredes, puertas, ventanas, etc.
- **CSS** es la **decoración interior y exterior**, donde se decide el color de las paredes, el tipo de muebles y la distribución de los espacios.

# ¿Cuáles son las tres formas de insertar CSS en tu proyecto?
Según lo analizado en el artículo [Cómo agregar CSS](https://www.w3schools.com/css/css_howto.asp) a un sitio externo., existen 3 maneras de insertar CSS en nuestro proyecto.

1. **Externa**: Vinculando un archivo CSS separado con una etiqueta ``<link>`` en el ``<head>`` del documento HTML, como ``<link rel="stylesheet" href="styles.css">``. Es importante recalcar que una hoja de estilo externa se puede escribir en cualquier editor de texto y debe guardarse con una extensión **".css"**.
2. **Interna**: Escribiendo el CSS dentro de una etiqueta ``<style>`` en el ``<head>`` del documento HTML. Es importante indicar que se puede utilizar una hoja de estilo interna si una sola página HTML tiene un estilo único.
3. **En Línea**: Usando el atributo style directamente dentro de las etiquetas HTML, como ``<p style="color:red;">Texto</p>``. Esta manera se tiene que usar con moderación dado a que un estilo en línea se pierde de muchas de las ventajas de una hoja de estilo.

# Escribe un ejemplo de una regla CSS que daría texto rojo a todos los elementos ``<p>``.
Para aplicar el color rojo a todos los elementos ``<p>``, se puede aplicar la siguiente regla:
```
p {
	color : red;
}
```
Esta regla de CSS se puede usar en cualquier archivo CSS ya sea de manera externa, interna o en línea.