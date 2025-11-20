# **HardTonic — Plataforma Full-Stack de Comercio Electrónico para Videojuegos**

HardTonic es un sistema completo de comercio electrónico desarrollado para la venta de videojuegos digitales y físicos. El proyecto combina un frontend moderno construido en Angular con un backend estructurado en Node.js y Express, utilizando MongoDB como base de datos. La arquitectura ofrece una separación clara entre presentación, lógica de negocio y persistencia, permitiendo mantener el código ordenado, escalable y fácil de extender.

La aplicación permite a los usuarios navegar por un catálogo de productos segmentado por plataformas, visualizar detalles, gestionar un carrito de compras persistente y completar un flujo de compra simulado. Además, incluye un módulo de autenticación basado en JSON Web Tokens que controla las operaciones que requieren sesión iniciada.

---

## **Arquitectura General**

El proyecto está organizado en dos componentes principales:

### Frontend (carpeta `Web/`)

El cliente está implementado en Angular 18. La interfaz incluye pantallas para inicio, catálogo de productos, detalle de cada artículo, carrito, login y registro. Los servicios encapsulan la comunicación HTTP con el backend y la gestión del estado del carrito y la sesión. La estructura modular facilita la navegación y mantiene los componentes independientes entre sí.
El diseño se apoya en Tailwind CSS y Bootstrap para lograr una interfaz limpia, responsive y consistente.

### Backend (carpeta `backend/`)

El servidor está desarrollado con Node.js y Express. El archivo principal `app.js` configura las rutas, middlewares, conexión a la base de datos y manejo de errores.
Los modelos definen la estructura de usuarios, productos y carritos, mientras que los controladores gestionan las operaciones principales, como autenticación, consulta y gestión de productos, manipulación de carritos y procesamiento básico de pagos simulados.
La conexión a MongoDB se controla desde un módulo aislado, y las variables de entorno permiten adaptar el sistema a distintos ambientes.

---

## **Instalación y Puesta en Marcha**

Clonación del repositorio:

```
git clone https://github.com/Brayton16/hardtonic.git
cd hardtonic
```

### Ejecutar el frontend

```
cd Web
npm install
ng serve -o
```

La aplicación estará disponible en
`http://localhost:4200`

### Ejecutar el backend

```
cd backend
npm install
```

Antes de iniciarlo, es necesario crear un archivo `.env` dentro de la carpeta del backend con los valores:

```
PORT=3000
MONGO_URI=tu_cadena_de_conexion
JWT_SECRET=clave_segura
```

Luego:

```
node app.js
```

El servidor escuchará en
`http://localhost:3000`

---

## **Principales Funcionalidades**

El sistema permite registrar usuarios, iniciar sesión y navegar por un catálogo administrado desde la API. Cada producto incluye imagen, descripción y precio. Los usuarios pueden agregar artículos al carrito, actualizar cantidades o eliminarlos. El backend valida cada operación y mantiene coherencia entre los datos recibidos y los modelos de MongoDB.

El proceso de compra incluye un flujo de pago simulado que confirma la validez del carrito y devuelve una respuesta estructurada. Aunque actualmente no se integra una pasarela real, la arquitectura está diseñada para incorporar Stripe u otra solución con mínima modificación.

---

## **Autenticación**

La sesión del usuario se gestiona mediante JSON Web Tokens.
Al iniciar sesión, el backend genera un token firmado que el frontend almacena localmente. Las rutas protegidas exigen este token en el encabezado `Authorization`. Esto permite mantener una comunicación segura entre cliente y servidor y evitar accesos no autorizados.


