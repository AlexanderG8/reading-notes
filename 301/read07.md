# Navegación y Routing

## Como se inicio la idea de React Router?

React Router surgió como una solución a la necesidad de manejar la navegación en aplicaciones de una sola página (SPA). Fue creado para permitir que las aplicaciones React puedan:

1. Cambiar el contenido mostrado sin recargar la página
2. Mantener URLs amigables y significativas 
3. Preservar el historial de navegación
4. Facilitar la navegación entre diferentes "páginas" o componentes

La primera versión fue lanzada en 2014 por Michael Jackson y Ryan Florence como una biblioteca independiente, y desde entonces se ha convertido en el estándar de facto para el enrutamiento en React.

## Qué es React Router?

React Router es una biblioteca de enrutamiento para React que permite:

- Crear rutas dinámicas en aplicaciones web
- Manejar la navegación entre diferentes componentes/páginas
- Mantener sincronizada la UI con la URL
- Implementar navegación anidada y protegida
- Gestionar parámetros de URL y query strings

Algunas características principales incluyen:

1. **Enrutamiento declarativo**: Define rutas usando componentes JSX
2. **Navegación programática**: Permite navegar mediante código
3. **Rutas anidadas**: Soporta jerarquías de rutas complejas
4. **Hooks especializados**: Como useParams, useNavigate, useLocation
5. **Manejo de historial**: Control sobre el historial del navegador

Se integra perfectamente con React y es esencial para crear SPAs modernas y navegables.

## Investigación

## React Router vs Navegación Tradicional

### 1. ¿Cuál es la diferencia entre Single Page Application (SPA) y Multi Page Application (MPA)?

Las principales diferencias son:

**SPA (Single Page Application)**:

- Carga una sola página HTML inicial
- Las actualizaciones de contenido son dinámicas mediante JavaScript
- No requiere recargas completas al navegar
- Mejor experiencia de usuario con transiciones más fluidas
- Menor consumo de datos después de la carga inicial

**MPA (Multi Page Application)**:

- Cada navegación carga una nueva página HTML completa
- Requiere recargas completas del navegador
- Mayor consumo de datos por cada navegación
- Arquitectura más tradicional y simple
- Mejor para SEO sin configuración adicional

### 2. ¿Por qué React Router no recarga la página completa al navegar entre vistas?

React Router no recarga la página completa porque:

1. Intercepta los cambios de URL
2. Actualiza solo los componentes necesarios usando el Virtual DOM
3. Mantiene el estado de la aplicación
4. Modifica el historial del navegador sin recargas
5. Renderiza el contenido de forma dinámica

### 3. ¿Qué ventajas tiene tener URLs específicas para cada vista de una aplicación React?

Tener URLs específicas para cada vista ofrece:

1. **Mejor experiencia de usuario**:

   - Permite marcar páginas como favoritos
   - Facilita compartir enlaces específicos
   - Navegación hacia atrás/adelante funcional

2. **Beneficios técnicos**:

   - SEO mejorado
   - Análisis de tráfico más preciso
   - Mantenimiento de estado entre recargas

3. **Organización del código**:

   - Estructura clara de la aplicación
   - Rutas predecibles y mantenibles
   - Separación lógica de componentes

## Hooks de React Router

### ¿Para qué sirve useParams() y en qué tipo de rutas se utiliza?

useParams() es un hook que:

- Permite acceder a los parámetros dinámicos de la URL
- Se utiliza en rutas con parámetros variables como `/user/:id`
- Retorna un objeto con los valores de los parámetros
- Es útil para rutas que necesitan identificadores o slugs

Ejemplo:

```jsx
import { useParams } from 'react-router-dom';

function UserProfile() {
  const params = useParams();
  return <h1>Perfil de usuario: {params.id}</h1>;
}
```

### ¿Cuál es la diferencia entre useNavigate() y el componente Link para navegación?

useNavigate() y Link tienen diferentes propósitos y casos de uso:

**useNavigate()**:

- Es un hook para navegación programática
- Permite navegar desde código JavaScript/eventos
- Puede incluir lógica adicional antes de navegar
- Útil para redirecciones condicionales
- Puede pasar estado entre rutas

Ejemplo:

```jsx
import { useNavigate } from 'react-router-dom';

function Login() {
  const navigate = useNavigate();

  function handleLogin() {
    // Lógica de inicio de sesión
    navigate('/dashboard'); // Redirecciona a /dashboard
  }

  return <button onClick={handleLogin}>Iniciar sesión</button>;
}
```

### ¿Cómo se puede pasar información entre vistas usando useLocation y state?

useLocation() y state permiten compartir datos entre rutas:

**Enviando state**:

- Se puede pasar state al navegar con useNavigate o Link
- El state persiste durante la navegación
- Útil para pasar datos que no deben estar en la URL

Ejemplo de envío:

```jsx
import { useNavigate } from 'react-router-dom';

function Login() {
  const navigate = useNavigate();

  function handleLogin() {
    // Lógica de inicio de sesión
    navigate('/dashboard', {
      state: {
        username: 'usuario123',
        role: 'admin',
      },
    }); // Redirecciona a /dashboard
  }

  return <button onClick={handleLogin}>Iniciar sesión</button>;
}
```

## Rutas Dinámicas y Parámetros

### ¿Qué significa una ruta como /contact/:id en React Router?

Una ruta con el patrón `/contact/:id` en React Router representa:

- Una ruta dinámica que puede aceptar diferentes valores para `:id`
- El segmento `:id` es un parámetro de ruta variable
- Puede coincidir con URLs como `/contact/1`, `/contact/abc`, etc.
- Permite crear rutas reutilizables para recursos similares

### ¿Cómo se accede al valor del parámetro id dentro del componente?

Para acceder al valor del parámetro `id` dentro del componente, se utiliza el hook `useParams()` de React Router:

```jsx
import { useParams } from 'react-router-dom';

function ContactDetail() {
  const { id } = useParams();
  
  return (
    <div>
      <h1>Contacto ID: {id}</h1>
      <p>Mostrando detalles del contacto con ID: {id}</p>
    </div>
  );
}
```

**Explicación:**

- `useParams()` retorna un objeto que contiene todos los parámetros de la URL actual
- Se puede usar destructuring para extraer el parámetro específico: `const { id } = useParams()`
- También se puede acceder como: `const params = useParams(); params.id`
- El valor siempre es un string, incluso si el parámetro parece ser un número

### ¿Qué pasa si el usuario navega directamente a una URL con parámetro inválido?

Cuando un usuario navega a una URL con un parámetro inválido, pueden ocurrir varias situaciones:

**1. El parámetro existe pero es inválido:**

```jsx
function ContactDetail() {
  const { id } = useParams();
  const [contact, setContact] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    // Intentar cargar el contacto
    fetchContact(id)
      .then(setContact)
      .catch(() => {
        setError('Contacto no encontrado');
      });
  }, [id]);

  if (error) {
    return <div>Error: {error}</div>;
  }

  if (!contact) {
    return <div>Cargando...</div>;
  }

  return <div>Contacto: {contact.name}</div>;
}
```

**2. Manejo de errores recomendado:**

- **Validación del parámetro**: Verificar si el ID tiene el formato esperado
- **Manejo de errores**: Mostrar mensajes de error apropiados
- **Redirección**: Redirigir a una página 404 o página principal
- **Valores por defecto**: Proporcionar comportamiento de respaldo

**3. Estrategias comunes:**

```jsx
function ContactDetail() {
  const { id } = useParams();
  const navigate = useNavigate();

  useEffect(() => {
    // Validar que el ID sea un número
    if (!/^\d+$/.test(id)) {
      navigate('/contacts'); // Redirigir si es inválido
      return;
    }

    // Continuar con la lógica normal
  }, [id, navigate]);
}
```

**Comportamientos típicos:**

- El componente se renderiza normalmente, pero `useParams()` retorna el valor tal como está en la URL
- Es responsabilidad del desarrollador validar y manejar parámetros inválidos
- React Router no valida automáticamente los parámetros
- Se recomienda implementar validación y manejo de errores apropiados

## Navegación Programática vs Declarativa

### ¿Cuándo usarías `navigate('/ruta')` vs `<Link to="/ruta">`?

La elección entre navegación programática (`navigate()`) y declarativa (`<Link>`) depende del contexto y la interacción del usuario:

**Usar `<Link to="/ruta">` (Navegación Declarativa) cuando:**

- **Enlaces tradicionales**: Elementos que el usuario puede hacer clic directamente
- **Navegación visible**: Menús, botones de navegación, enlaces en texto
- **Accesibilidad**: Los screen readers pueden identificar enlaces fácilmente
- **SEO**: Los crawlers pueden seguir los enlaces
- **Experiencia de usuario**: Permite click derecho, "abrir en nueva pestaña", etc.

```jsx
import { Link } from 'react-router-dom';

function Navigation() {
  return (
    <nav>
      <Link to="/home">Inicio</Link>
      <Link to="/products">Productos</Link>
      <Link to="/contact">Contacto</Link>
    </nav>
  );
}

function ProductCard({ product }) {
  return (
    <div className="card">
      <h3>{product.name}</h3>
      <Link to={`/products/${product.id}`}>Ver detalles</Link>
    </div>
  );
}
```

**Usar `navigate('/ruta')` (Navegación Programática) cuando:**

- **Lógica condicional**: Navegación basada en condiciones o validaciones
- **Eventos de formulario**: Redirección después de envío exitoso
- **Autenticación**: Redirección automática según estado de login
- **Efectos secundarios**: Navegación como resultado de una acción
- **Timeouts o eventos**: Navegación automática o programada

```jsx
import { useNavigate } from 'react-router-dom';

function LoginForm() {
  const navigate = useNavigate();
  const [credentials, setCredentials] = useState({ email: '', password: '' });

  const handleSubmit = async (e) => {
    e.preventDefault();
    
    try {
      const result = await login(credentials);
      if (result.success) {
        // Navegación programática después de login exitoso
        navigate('/dashboard');
      }
    } catch (error) {
      console.error('Error de login:', error);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      {/* campos del formulario */}
      <button type="submit">Iniciar Sesión</button>
    </form>
  );
}

function ProtectedRoute({ children }) {
  const navigate = useNavigate();
  const isAuthenticated = useAuth();

  useEffect(() => {
    if (!isAuthenticated) {
      // Redirección automática si no está autenticado
      navigate('/login');
    }
  }, [isAuthenticated, navigate]);

  return isAuthenticated ? children : null;
}
```

### ¿Cómo redirigir automáticamente después de crear un recurso exitosamente?

Para redirigir automáticamente después de crear un recurso, se utiliza `navigate()` en el callback de éxito:

**Patrón básico:**

```jsx
import { useNavigate } from 'react-router-dom';
import { useState } from 'react';

function CreateProduct() {
  const navigate = useNavigate();
  const [product, setProduct] = useState({ name: '', price: '' });
  const [loading, setLoading] = useState(false);

  const handleSubmit = async (e) => {
    e.preventDefault();
    setLoading(true);

    try {
      const newProduct = await createProduct(product);
      
      // Redirección automática después de creación exitosa
      navigate(`/products/${newProduct.id}`, {
        // Opcional: pasar estado para mostrar mensaje de éxito
        state: { message: 'Producto creado exitosamente' }
      });
    } catch (error) {
      console.error('Error al crear producto:', error);
      // Manejar error sin redirigir
    } finally {
      setLoading(false);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        value={product.name}
        onChange={(e) => setProduct({...product, name: e.target.value})}
        placeholder="Nombre del producto"
      />
      <input
        value={product.price}
        onChange={(e) => setProduct({...product, price: e.target.value})}
        placeholder="Precio"
      />
      <button type="submit" disabled={loading}>
        {loading ? 'Creando...' : 'Crear Producto'}
      </button>
    </form>
  );
}
```

**Opciones de redirección:**

**1. A la lista de recursos:**

```jsx
// Redirigir a la lista después de crear
navigate('/products');
```

**2. Al detalle del recurso creado:**

```jsx
// Redirigir al detalle del nuevo recurso
navigate(`/products/${newProduct.id}`);
```

**3. Con mensaje de éxito:**

```jsx
// Pasar estado para mostrar mensaje
navigate('/products', {
  state: { 
    message: 'Producto creado exitosamente',
    productId: newProduct.id 
  }
});
```

**4.Reemplazar en el historial:**

```jsx
// Reemplazar la entrada actual en el historial
navigate('/products', { replace: true });
```

### ¿Qué es el "historial del browser" y cómo interactúa con React Router?

El **historial del navegador** es una pila (stack) que mantiene un registro de todas las páginas visitadas durante una sesión de navegación. React Router interactúa con este historial para proporcionar navegación sin recargas de página.

**Conceptos clave:**

**1. Historia del Navegador:**

- **Stack de URLs**: Cada navegación agrega una entrada al historial
- **Botones Atrás/Adelante**: Permiten navegar por el historial
- **Entrada actual**: La URL actualmente visible
- **Persistencia**: Se mantiene durante la sesión del navegador

**2. Interacción con React Router:**

```jsx
import { useNavigate, useLocation } from 'react-router-dom';

function NavigationExample() {
  const navigate = useNavigate();
  const location = useLocation();

  const handleNavigation = () => {
    // Agregar nueva entrada al historial (comportamiento por defecto)
    navigate('/nueva-pagina');
  };

  const handleReplace = () => {
    // Reemplazar entrada actual sin agregar al historial
    navigate('/nueva-pagina', { replace: true });
  };

  const handleBack = () => {
    // Navegar hacia atrás en el historial
    navigate(-1);
  };

  const handleForward = () => {
    // Navegar hacia adelante en el historial
    navigate(1);
  };

  return (
    <div>
      <p>Ubicación actual: {location.pathname}</p>
      <button onClick={handleNavigation}>Ir a Nueva Página</button>
      <button onClick={handleReplace}>Reemplazar Página Actual</button>
      <button onClick={handleBack}>Atrás</button>
      <button onClick={handleForward}>Adelante</button>
    </div>
  );
}
```

**3. Tipos de navegación:**

- **Push (por defecto)**: Agrega nueva entrada al historial

```jsx
navigate('/nueva-ruta'); // Equivale a navigate('/nueva-ruta', { replace: false })
```

- **Replace**: Reemplaza la entrada actual

```jsx
navigate('/nueva-ruta', { replace: true });
```

- **Navegación numérica**: Moverse por el historial

```jsx
navigate(-1); // Atrás
navigate(-2); // Dos páginas atrás
navigate(1);  // Adelante
```

**4. Casos de uso para `replace: true`:**

- **Redirecciones de autenticación**: Evitar que el usuario regrese a páginas protegidas
- **Formularios enviados**: Prevenir reenvío accidental
- **Páginas de error**: Reemplazar rutas inválidas
- **Onboarding**: Evitar navegación hacia atrás en flujos lineales

```jsx
function LoginRedirect() {
  const navigate = useNavigate();
  const isAuthenticated = useAuth();

  useEffect(() => {
    if (isAuthenticated) {
      // Usar replace para evitar regresar a login
      navigate('/dashboard', { replace: true });
    }
  }, [isAuthenticated, navigate]);

  return <LoginForm />;
}
```

**Beneficios de la integración:**

- **Experiencia nativa**: Los botones del navegador funcionan correctamente
- **URLs compartibles**: Cada estado de la aplicación tiene una URL única
- **Navegación fluida**: Sin recargas de página
- **Estado preservado**: La aplicación mantiene su estado durante la navegación
- **Accesibilidad**: Compatible con tecnologías asistivas

## 📚 Recursos sugeridos

[React Router - Tutorial Oficial (EN)](https://reactrouter.com/en/main/start/tutorial)
Tutorial completo sobre conceptos fundamentales, rutas dinámicas y navegación programática.

[useParams Hook - Documentación (EN)](https://reactrouter.com/en/main/hooks/use-params)
Guía específica sobre cómo extraer parámetros de URLs dinámicas.

[useNavigate Hook - Documentación (EN)](https://reactrouter.com/en/main/hooks/use-navigate)
Ejemplos prácticos de redirección automática y navegación condicional.