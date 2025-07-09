# Formularios y Eventos

## Formularios Controlados vs No Controlados

**¿Cuál es la diferencia fundamental entre un formulario controlado y uno no controlado en React?**

La diferencia fundamental es que en un formulario controlado, React controla completamente el valor de los inputs a través del estado del componente (usando ``value`` y ``onChange``), mientras que en un formulario no controlado, el DOM mantiene el estado interno de los inputs y React solo accede a los valores cuando los necesita (típicamente usando ``useRef`` o accediendo al evento del formulario).

**¿Por qué React recomienda usar formularios controlados como práctica estándar?**

React recomienda formularios controlados porque proporcionan un control total sobre el flujo de datos, permitiendo validación en tiempo real, formateo automático de entrada, manejo consistente del estado, mejor debugging y testing, además de mantener el principio de "single source of truth" donde React es la única fuente de verdad para el estado del formulario, lo que hace el código más predecible y mantenible.

## Event Handling en React

**¿Qué diferencias hay entre ``onChange`` y ``onSubmit`` en términos de cuándo se ejecutan?**

``onChange`` se ejecuta inmediatamente cada vez que el usuario modifica el valor de un input (cada tecla presionada, cada carácter escrito), mientras que ``onSubmit`` se ejecuta solo cuando el usuario envía el formulario completo (presionando Enter o haciendo click en un botón de tipo submit), lo que significa que ``onChange`` es continuo y ``onSubmit`` es un evento único al finalizar.

**¿Por qué es necesario usar ``event.preventDefault()`` en formularios de React?**

Es necesario usar ``event.preventDefault()`` porque por defecto los formularios HTML tienen un comportamiento nativo que recarga la página completa al ser enviados, y en React queremos mantener el control del estado y la navegación sin que la página se recargue, permitiendo manejar el envío del formulario con JavaScript y mantener la experiencia de Single Page Application (SPA).

## Spread Operator e Inmutabilidad

**¿Qué significa inmutabilidad en el contexto de React state?**

La inmutabilidad en React state significa que nunca debes modificar directamente el estado existente, sino crear una nueva copia del estado con los cambios aplicados, porque React usa comparación de referencias para detectar cambios y decidir cuándo re-renderizar componentes, por lo que si modificas el estado directamente, React no detectará el cambio y no actualizará la interfaz.

**¿Por qué ``[...array, newItem]`` es preferible a ``array.push(newItem)`` cuando actualizas estado?**

``[...array, newItem]`` es preferible porque crea un nuevo array con el elemento añadido (manteniendo inmutabilidad), mientras que ``array.push(newItem)`` modifica el array original y devuelve solo la nueva longitud, lo que hace que React no detecte el cambio de estado porque la referencia del array sigue siendo la misma, impidiendo que se dispare un re-render y actualice la interfaz.

## Validación de Formularios

**¿Cuáles son las ventajas y desventajas de validar ``onChange`` vs ``onSubmit``?**

Validar ``onChange`` tiene la ventaja de proporcionar feedback inmediato al usuario y corregir errores mientras escribe, pero puede ser intrusivo y mostrar errores prematuros antes de que termine de escribir; mientras que validar ``onSubmit`` es menos intrusivo y permite al usuario completar todo el formulario sin interrupciones, pero puede ser frustrante descubrir múltiples errores solo al final, especialmente en formularios largos.

**¿Cómo mejora la experiencia de usuario mostrar errores de validación en tiempo real?**

La validación en tiempo real mejora la experiencia de usuario porque reduce la fricción al permitir corrección inmediata de errores, evita la frustración de descubrir problemas después de completar todo el formulario, proporciona guidance contextual mientras el usuario está enfocado en cada campo, y acelera el proceso de completar el formulario correctamente, creando una experiencia más fluida e intuitiva.

## Pequeña reflexión
Piensa en formularios que uses diariamente (redes sociales, email, compras online). ¿Qué características tienen los mejores formularios en términos de facilidad de uso y feedback al usuario?
### Mi opinión

Los mejores formularios comparten características clave: validación en tiempo real que no es intrusiva, mensajes de error claros y específicos, indicadores visuales de progreso, autocompletado inteligente, diseño limpio con campos bien etiquetados, y feedback inmediato sobre acciones exitosas. También tienen características como guardar automáticamente borradores, permitir corrección fácil de errores, y mantener el contexto del usuario sin perder información ingresada.

```jsx
function FormularioEmail() {
  const [email, setEmail] = useState('');
  const [error, setError] = useState('');
  const [isValid, setIsValid] = useState(false);

  const validarEmail = (value) => {
    if (!value) {
      setError('');
      setIsValid(false);
    } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value)) {
      setError('Email inválido');
      setIsValid(false);
    } else {
      setError('');
      setIsValid(true);
    }
  };

  const handleChange = (e) => {
    const value = e.target.value;
    setEmail(value);
    validarEmail(value);
  };

  return (
    <div>
      <input
        type="email"
        value={email}
        onChange={handleChange}
        placeholder="tu@email.com"
        className={`input ${error ? 'error' : ''} ${isValid ? 'valid' : ''}`}
      />
      {error && <span className="error-message">{error}</span>}
      {isValid && <span className="success-icon">✓</span>}
    </div>
  );
}
```
