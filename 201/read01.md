# **🌐Fundamentos de la Web Moderna**
### 1. **Artículo: [HTML Semántico](https://es.semrush.com/blog/html-semantico/)** 🌐

#### Resumen:
El artículo explica la importancia del **HTML semántico** en el desarrollo web. El HTML semántico se refiere al uso de etiquetas que describen el significado del contenido, no solo su apariencia. Esto mejora la accesibilidad, el SEO y la mantenibilidad del código. 🛠️

#### Conceptos clave:
- **Etiquetas semánticas**: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`, etc. 🏷️
- **Beneficios**:
  - **Accesibilidad**: Ayuda a los lectores de pantalla a interpretar mejor la estructura del contenido. 🦯
  - **SEO**: Los motores de búsqueda comprenden mejor la jerarquía y relevancia del contenido. 🔍
  - **Mantenibilidad**: El código es más legible y fácil de actualizar. 📂
- **Ejemplos prácticos**: Cómo estructurar una página web usando etiquetas semánticas. 🖥️

#### Dato importante:
El uso de HTML semántico no solo es una buena práctica, sino que también es un requisito para cumplir con los estándares de accesibilidad **WCAG (Web Content Accessibility Guidelines)**. Esto es especialmente relevante si desarrollas sitios web para instituciones públicas o empresas que deben cumplir con normativas de accesibilidad. ⚖️

### 2. **Artículo: [Introducción a la Accesibilidad Web](https://www.w3.org/WAI/fundamentals/accessibility-intro/es)** ♿

#### Resumen:
Este artículo, publicado por la **W3C (World Wide Web Consortium)**, introduce los conceptos fundamentales de la accesibilidad web. Explica por qué la accesibilidad es crucial y cómo beneficia a todos los usuarios, incluyendo personas con discapacidades. 🌍

#### Conceptos clave:
- **¿Qué es la accesibilidad web?**: Hacer que los sitios web sean utilizables por todas las personas, independientemente de sus capacidades. 🤝
- **Beneficios**:
  - Inclusión de personas con discapacidades (visuales, auditivas, motoras, cognitivas). 👁️‍🗨️👂🦽🧠
  - Mejora la experiencia de usuario para todos (por ejemplo, subtítulos en videos benefician a personas en entornos ruidosos). 🎧
  - Cumplimiento de normativas legales. ⚖️
- **Pautas de accesibilidad**: Introducción a las **WCAG (Web Content Accessibility Guidelines)**, que se basan en cuatro principios: perceptible, operable, comprensible y robusto. 📜
- **Herramientas**: Uso de validadores de accesibilidad y pruebas con lectores de pantalla. 🛠️

#### Dato importante:
La accesibilidad no es solo un tema ético, sino también legal. En muchos países, como España (Ley General de Derechos de las Personas con Discapacidad) o Estados Unidos (Americans with Disabilities Act), es obligatorio que los sitios web sean accesibles. Ignorar la accesibilidad puede resultar en demandas y multas. ⚠️


### 3. **Artículo: [Guía de Prompting](https://www.promptingguide.ai/es)** 🤖

#### Resumen:
Este artículo es una guía introductoria sobre el concepto de **prompting** en el contexto de la inteligencia artificial (IA). Explica cómo interactuar con modelos de lenguaje como GPT para obtener respuestas precisas y útiles. 🧠

#### Conceptos clave:
- **¿Qué es un prompt?**: Es la instrucción o pregunta que se le da a un modelo de IA para generar una respuesta. 💬
- **Técnicas de prompting**:
  - **Prompting directo**: Preguntas simples y directas. 🎯
  - **Prompting contextual**: Proporcionar contexto adicional para obtener respuestas más precisas. 📚
  - **Few-shot prompting**: Dar ejemplos previos para guiar al modelo. 📋
- **Aplicaciones**: Uso de prompting en tareas como redacción, traducción, generación de código, etc. ✍️🌐💻
- **Buenas prácticas**:
  - Ser claro y específico en las preguntas. ✅
  - Probar diferentes enfoques si la respuesta no es satisfactoria. 🔄
  - Ajustar el nivel de detalle según la necesidad. 🎚️

#### Dato importante:
El prompting no es solo útil para desarrolladores o expertos en IA. Cualquier persona puede aprovechar esta técnica para mejorar su productividad, desde estudiantes que necesitan ayuda con tareas hasta profesionales que buscan automatizar partes de su trabajo. 🚀

## **✅Lista de Mitos y Verdades para Analizar**

### 1. Usar `<div>` para cada sección del sitio es la mejor forma de estructurar una página. 
**Respuesta:** **Mito** ❌  
**Justificación:**  
- Usar `<div>` para todo no es la mejor práctica. Las etiquetas semánticas como `<header>`, `<main>`, `<section>`, `<article>`, y `<footer>` describen mejor el contenido y mejoran la accesibilidad y el SEO.  
- **Evidencia:** Según el artículo de [HTML Semántico](https://es.semrush.com/blog/html-semantico/), el uso de etiquetas semánticas ayuda a los motores de búsqueda y a los lectores de pantalla a entender la estructura del contenido.  


### 2. Aplicar roles y atributos ARIA es imprescindible para mejorar la accesibilidad de un sitio.  
**Respuesta:** **Verdad** ✅ (pero con matices)  
**Justificación:**  
- Los roles y atributos ARIA son útiles para mejorar la accesibilidad, especialmente en aplicaciones dinámicas o complejas. Sin embargo, no siempre son necesarios si el HTML semántico ya describe correctamente el contenido.  
- **Evidencia:** La [W3C](https://www.w3.org/WAI/fundamentals/accessibility-intro/es) recomienda usar ARIA solo cuando el HTML semántico no es suficiente.  


### 3. La semántica HTML no influye en absoluto en el posicionamiento SEO de una página. 
**Respuesta:** **Mito** ❌  
**Justificación:**  
- La semántica HTML sí influye en el SEO. Los motores de búsqueda utilizan las etiquetas semánticas para entender la estructura y relevancia del contenido.  
- **Evidencia:** Según [Semrush](https://es.semrush.com/blog/html-semantico/), el uso correcto de etiquetas como `<h1>`, `<h2>`, y `<article>` mejora el posicionamiento.  


### 4. La IA puede generar código HTML y sugerir etiquetas semánticas, pero el desarrollador debe revisarlas antes de usarlas. 
**Respuesta:** **Verdad** ✅  
**Justificación:**  
- Las herramientas de IA, como ChatGPT o GitHub Copilot, pueden generar código HTML, pero no siempre son perfectas. El desarrollador debe revisar y ajustar el código para asegurarse de que cumpla con los estándares de accesibilidad y semántica.  
- **Evidencia:** La [Guía de Prompting](https://www.promptingguide.ai/es) menciona que la IA es una herramienta útil, pero no reemplaza el juicio humano.  


### 5. Colocar texto alternativo (alt) en imágenes solo sirve para mejorar el resultado en la búsqueda de Google.  
**Respuesta:** **Mito** ❌  
**Justificación:**  
- El atributo `alt` no solo ayuda al SEO, sino que también es esencial para la accesibilidad. Permite que los lectores de pantalla describan las imágenes a usuarios con discapacidad visual.  
- **Evidencia:** La [W3C](https://www.w3.org/WAI/fundamentals/accessibility-intro/es) destaca que el texto alternativo es crucial para la accesibilidad.  


### 6. Solo las personas con discapacidad visual se benefician de los sitios accesibles.  
**Respuesta:** **Mito** ❌  
**Justificación:**  
- La accesibilidad beneficia a todos, no solo a personas con discapacidad visual. Por ejemplo, los subtítulos ayudan a personas en entornos ruidosos, y una navegación clara facilita la experiencia para todos los usuarios.  
- **Evidencia:** La [W3C](https://www.w3.org/WAI/fundamentals/accessibility-intro/es) explica que la accesibilidad mejora la experiencia para todos.  


### 7. Las etiquetas `<header>`, `<main>` y `<footer>` ordenan el contenido y facilitan su lectura.  
**Respuesta:** **Verdad** ✅  
**Justificación:**  
- Estas etiquetas semánticas ayudan a organizar el contenido de manera lógica, lo que facilita la lectura tanto para los usuarios como para los motores de búsqueda.  
- **Evidencia:** El artículo de [HTML Semántico](https://es.semrush.com/blog/html-semantico/) destaca su importancia para la estructura y accesibilidad.  


### 8. Incluso en proyectos pequeños, la accesibilidad y la semántica siguen siendo factores esenciales.  
**Respuesta:** **Verdad** ✅  
**Justificación:**  
- La accesibilidad y la semántica son importantes en cualquier proyecto, sin importar su tamaño. Ignorarlas puede limitar el alcance del sitio y generar problemas legales.  
- **Evidencia:** La [W3C](https://www.w3.org/WAI/fundamentals/accessibility-intro/es) enfatiza que la accesibilidad debe ser una prioridad desde el inicio.  


### 9. Un orden lógico de encabezados (h1, h2, h3…) facilita la navegación con lectores de pantalla.  
**Respuesta:** **Verdad** ✅  
**Justificación:**  
- Los encabezados bien estructurados permiten a los lectores de pantalla navegar el contenido de manera eficiente.  
- **Evidencia:** La [W3C](https://www.w3.org/WAI/fundamentals/accessibility-intro/es) recomienda un uso correcto de los encabezados para mejorar la accesibilidad.  


### 10. Los motores de búsqueda suelen priorizar sitios con estructura semántica y contenido ordenado.  
**Respuesta:** **Verdad** ✅  
**Justificación:**  
- Los motores de búsqueda valoran la estructura semántica porque les ayuda a entender el contenido y su relevancia.  
- **Evidencia:** [Semrush](https://es.semrush.com/blog/html-semantico/) confirma que el HTML semántico mejora el SEO.  


### 11. No se pueden combinar elementos semánticos con otros más genéricos como `<div>` o `<span>` en el mismo documento HTML.
**Respuesta:** **Mito** ❌  
**Justificación:**  
- Sí se pueden combinar. Los elementos semánticos dan significado al contenido, mientras que `<div>` y `<span>` se usan para agrupar o estilizar elementos sin significado específico.  
- **Evidencia:** La documentación de [MDN Web Docs](https://developer.mozilla.org/es/) muestra ejemplos de uso combinado.  


### 12. Implementar accesibilidad puede requerir ajustes de código, pero beneficia a todo tipo de usuarios a largo plazo.
**Respuesta:** **Verdad** ✅  
**Justificación:**  
- La accesibilidad mejora la experiencia para todos los usuarios, no solo para aquellos con discapacidades. Además, puede aumentar el alcance y la usabilidad del sitio.  
- **Evidencia:** La [W3C](https://www.w3.org/WAI/fundamentals/accessibility-intro/es) destaca sus beneficios universales.  


### 13. La IA, al ser imparcial, siempre provee sugerencias de accesibilidad 100% correctas.
**Respuesta:** **Mito** ❌  
**Justificación:**  
- La IA no es perfecta y puede cometer errores. Además, no siempre entiende el contexto completo de un proyecto.  
- **Evidencia:** La [Guía de Prompting](https://www.promptingguide.ai/es) menciona que las sugerencias de IA deben ser revisadas por humanos.  


### 14. Un buen uso de HTML5 semántico hace el proyecto más mantenible y promueve la colaboración entre desarrolladores.
**Respuesta:** **Verdad** ✅  
**Justificación:**  
- El HTML semántico facilita la lectura y comprensión del código, lo que mejora la mantenibilidad y la colaboración en equipos.  
- **Evidencia:** El artículo de [HTML Semántico](https://es.semrush.com/blog/html-semantico/) destaca su impacto en la mantenibilidad.  


### 15. La accesibilidad es un requerimiento opcional y solo aplica en organizaciones públicas o gubernamentales.
**Respuesta:** **Mito** ❌  
**Justificación:**  
- La accesibilidad es un requisito legal en muchos países y aplica a todo tipo de organizaciones. Además, es una buena práctica que beneficia a todos los usuarios.  
- **Evidencia:** La [W3C](https://www.w3.org/WAI/fundamentals/accessibility-intro/es) explica que la accesibilidad es un derecho universal.  


## 📍Conclusión:
- **HTML semántico**: Esencial para mejorar la estructura, accesibilidad y SEO de tu sitio web. 🌐
- **Accesibilidad web**: No solo es una buena práctica, sino también un requisito legal en muchos casos. ⚖️
- **Prompting**: Una habilidad poderosa para interactuar con modelos de IA y optimizar tareas. 🤖

