# 🚀 Proyecto Final - BackNodeJS

## 💡 Descripción

Este proyecto corresponde al **Trabajo Final Integrador del curso de
Node.js de Talento Tech**.\
Su objetivo es desarrollar un **backend completo** utilizando:

-   Node.js
-   Express
-   Firebase Firestore
-   Autenticación JWT
-   Arquitectura por capas (rutas, controladores, servicios y modelos)

El sistema expone una **API REST** que permite:

-   Gestionar productos: crear, obtener y eliminar
-   Autenticar usuarios mediante credenciales
-   Proteger rutas privadas con un middleware de autenticación

## 🔧 Tecnologías Utilizadas

-   **Node.js**
-   **Express**
-   **Firebase Firestore**
-   **jsonwebtoken (JWT)**
-   **CORS**
-   **body-parser**
-   **dotenv**

## 📌 Requerimientos Cubiertos

### **1. Configuración Inicial**

-   Proyecto inicializado con `npm init -y`
-   ESModules habilitado con `"type": "module"`
-   Script `npm start` configurado
-   Archivo principal `index.js`

### **2. Dependencias Instaladas**

Incluye:\
`express`, `cors`, `body-parser`, `dotenv`, `firebase`, `jsonwebtoken`

### **3. Configuración del Servidor**

-   Servidor Express configurado
-   CORS habilitado
-   `body-parser` para interpretar JSON
-   Manejo de rutas no encontradas (404)
-   Variables en archivo `.env`

### **4. Rutas**

`src/routes/`

-   **products.routes.js**
    -   GET `/api/products`
    -   GET `/api/products/:id`
    -   POST `/api/products/create`
    -   DELETE `/api/products/:id`
-   **auth.routes.js**
    -   POST `/auth/login`

### **5. Controladores y Servicios**

Ubicados en `src/controllers/` y `src/services/`.

### **6. Acceso a los Datos (Firebase)**

-   Conexión en `src/data/data.js`
-   Modelo de productos en `src/models/products.models.js`
-   Servicios conectados al modelo

### **7. Protección de Rutas (JWT)**

-   Middleware en `src/middleware/authentication.js`
-   Generación de tokens en `src/data/token.js`
-   Ruta de login devuelve un **Bearer Token** válido

## 🧩 Estructura del Proyecto

    PFI-BACKNODE/
    │── node_modules/
    │── src/
    │   ├── controllers/
    │   │   ├── auth.controllers.js
    │   │   └── products.controllers.js
    │   ├── data/
    │   │   ├── data.js
    │   │   └── token.js
    │   ├── middleware/
    │   │   └── authentication.js
    │   ├── models/
    │   │   └── products.models.js
    │   ├── routes/
    │   │   ├── auth.routes.js
    │   │   └── products.routes.js
    │   └── services/
    │       └── products.services.js
    │── .env
    │── .gitignore
    │── index.js
    │── package.json
    │── package-lock.json
    │── vercel.json

## 🔐 Variables de Entorno (.env)

Ejemplo recomendado:

    FIREBASE_API_KEY=xxxx
    FIREBASE_AUTH_DOMAIN=xxxx
    FIREBASE_PROYECT_ID=xxxx
    FIREBASE_STORAGE_BUCKET=xxxx
    FIREBASE_MESSAGING_SENDER_ID=xxxx
    FIREBASE_APP_ID=xxxx
    JWT_SECRET_KEY=xxxx

## 📜 Scripts Disponibles

### Iniciar el servidor:

    npm start

## 🛣️ Endpoints de la API

### 🔑 **Autenticación**

#### **POST /auth/login**

**Body:**

``` json
{
  "email": "usuario@example.com",
  "password": "841574"
}
```

**Respuesta (200):**

``` json
{
  "token": "Bearer eyJhbGciOiJIUzI1..."
}
```

### 📦 **Productos**

#### **GET /api/products**

Devuelve todos los productos.

#### **GET /api/products/:id**

Devuelve un producto por ID.

#### **POST /api/products/create**

**(Requiere Token JWT)**

**Header:**

    Authorization: Bearer <token>

**Body:**

``` json
{
  "categoria": "Electrónica",
  "nombre": "Auriculares Sony",
  "precio": 350
}
```

#### **DELETE /api/products/:id**

**(Requiere Token JWT)**

## 🔒 Autenticación y Seguridad

Este proyecto utiliza **JWT** para proteger rutas privadas.

El middleware `authentication.js` valida:

-   Que el header Authorization exista
-   Que el token sea un Bearer válido
-   Que la firma coincida con el secreto JWT

Si la validación falla → responde con **401 Unauthorized**

## 🌐 Deploy (Opcional)

Incluye archivo `vercel.json` para despliegue en Vercel.

## ⚙️ Cómo Ejecutar el Proyecto

### 1. Clonar el repositorio

    git clone <url-del-repositorio>

### 2. Instalar dependencias

    npm install

### 3. Configurar variables de entorno

Crear un archivo `.env` en la raíz del proyecto.

### 4. Iniciar el servidor

    npm start

Servidor corriendo en:\
http://localhost:3000