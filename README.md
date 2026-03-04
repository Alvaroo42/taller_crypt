# API-CRUD

_Este proyecto consiste en el desarrollo de un Backend completo utilizando el stack tecnológico MEAN (MongoDB, Express, Angular, Node.js). El objetivo principal es crear una API RESTful que permita realizar operaciones CRUD (Crear, Leer, Actualizar, Borrar) sobre una base de datos MongoDB._

_En el caso de ser un API, se muestra a continuación un ejemplo de tabla con las posibles rutas (**endpoints**) del API (el tema de los colores es bastante novedoso y en mucho visores serán ignorados):_

Verbo HTTP | Ruta | Descripción
--------: | :------- | :--------
<span style="color:green">GET</span> | /api | Obtenemos todas las colecciones existentes en la DB.
<span style="color:green">GET</span> | /api/\{coleccion\} | Obtenemos todos los elementos de la tabla \{coleccion\}.
<span style="color:green">GET</span> | /api/\{coleccion\}/\{id\} | Obtenemos el elemento indicado en \{id\} de la tabla \{coleccion\}.
<span style="color:yellow">POST</span> | /api/\{coleccion\} | Creamos un nuevo elemento en la tabla \{coleccion\}.
<span style="color:blue">PUT</span> | /api/\{coleccion\}/\{id\} | Modificamos el elemento \{id\} de la tabla \{coleccion\}.
<span style="color:red">DELETE</span> | /api/\{coleccion\}/\{id\} | Eliminamos el elemento \{id\} de la tabla \{coleccion\}.

## Comenzando 🚀

_Estas instrucciones te permitirán obtener una copia del proyecto en funcionamiento en tu máquina local para propósitos de desarrollo y pruebas._

Ver **Deployment** para conocer cómo desplegar el proyecto.

### Pre-requisitos 📋

_Se debe tener instalado **Node JS** en el equipo de desarrollo. Las siguientes líneas muestran cómo hacerlo con líneas de comando (por eso escribiremos sh tras las tre comiilas invertidas) para **Ubuntu 22.04**:_

```sh
sudo apt update
sudo apt install npm
sudo npm clean -f
sudo npm i -g n
sudo n stable
```

_Igualmente se debe tener instalada la DB **MongoDB** y asegurarnos que está lanzada..._

```sh
sudo apt update
sudo apt install -y mongodb
sudo systemctl start mongodb
```
# Fase 2: Seguridad y Autenticación (Guía 06)

En esta segunda fase estamos implementando la capa de seguridad de la API, centrada en la autenticación mediante Tokens (WS Auth).  

Antes de integrar la seguridad en el servidor principal, hemos desarrollado una serie de scripts de prueba para comprender las tecnologías implicadas.

---

## 🧪 Prueba 1: Criptografía de contraseñas (bcrypt)

**Descripción:**  
Implementación de la librería `bcrypt` para proteger las contraseñas de los usuarios antes de guardarlas en la base de datos.

**Conceptos clave:**
- Generación de **Salts** (datos aleatorios).
- Creación de **Hashes irreversibles** (con un coste de procesamiento de 10 iteraciones).
- Comparación de contraseñas en texto plano contra hashes.
- Uso de **Callbacks** y **Promesas** para pruebas de validación.

---

## 🧪 Prueba 2: Gestión de Fechas y Tiempos (moment)

**Descripción:**  
Uso de la librería `moment.js` para estandarizar el manejo del tiempo en el servidor.

**Conceptos clave:**
- Obtención de fechas actuales.
- Manipulación del tiempo (añadir días/horas).
- Conversión a formato **Unix Timestamp**.
- Gestión de la caducidad lógica de los tokens de sesión.

---

## 🧪 Prueba 3: Estructura de un JSON Web Token (JWT)

**Descripción:**  
Estudio de la anatomía de un token JWT:

- **Cabecera (Header)**
- **Payload**
- **Firma (Signature)**

**Conceptos clave:**
- Codificación en formato **Base64Url**.
- Uso de firma digital para garantizar que los datos no han sido manipulados por el cliente.

---

## 🧪 Prueba 4: Módulo Helper para Tokens (jwt-simple)

**Descripción:**  
Creación de un módulo reutilizable para abstraer la lógica de generación y validación de tokens.

**Conceptos clave:**
- Uso de una clave secreta (`SECRET`) y tiempo de expiración centralizados en `config.js`.

### 🔹 Método `creaToken(user)`
Genera un token firmado inyectando:
- ID del usuario
- Fecha de creación (`iat`)
- Fecha de caducidad (`exp`)

### 🔹 Método `decodificaToken(token)`
- Uso de **Promesas** para verificar la validez del token.
- Captura y gestión de errores comunes:
  - Token caducado
  - Token mal formado
  - Firma inválida

---

# 📦 Despliegue

Agrega aquí notas adicionales sobre cómo realizar el deployment del proyecto:

- Configuración de variables de entorno.
- Uso de HTTPS.
- Configuración de servidor
- Configuración de producción (`NODE_ENV=production`).

---

# 🛠️ Construido con

- **Express** – Infraestructura de aplicaciones web Node.js mínima y flexible que proporciona un conjunto sólido de características para aplicaciones web y móviles.
- **MongoDB Node.js Driver** – Driver oficial para trabajar con MongoDB en aplicaciones JavaScript.
- **CORS** – Middleware para habilitar CORS en aplicaciones Node.js/Express.
- **Helmet** – Ayuda a proteger aplicaciones Express configurando distintos headers HTTP.
- **Morgan** – Middleware para logging de peticiones HTTP en Node.js.
- **Nodemon** – Herramienta que reinicia automáticamente la aplicación al detectar cambios en los archivos.
- **jwt-simple** – Módulo para codificar y decodificar JWT en Node.js.
- **Moment.js** – Librería para manipulación y formateo de fechas.
- **bcrypt** – Librería para el hash seguro de contraseñas.

---

# 📌 Versionado

Usamos **Git** para el versionado.  
Para todas las versiones disponibles, consulta los **tags del repositorio**.

En este repositorio se puede encontrar la evolución del proyecto desde la estructura básica de un servicio, hasta un servicio CRUD completo con:

- Comunicación HTTPS
- Soporte para CORS
- Seguridad con Helmet
- Autorización tipo Bearer basada en tokens JWT

---

## 📜 Historial de versiones

| Tag     | Descripción |
|---------|-------------|
| v1.0.25 | API Rest Hola Mundo. |
| v2.0.0  | API Rest CRUD (sin DB). |
| v3.0.0  | API Rest CRUD (con DB MongoDB). |
| v3.1.0  | API Rest CRUD con seguridad. |
| v3.2.0  | API Rest CRUD con seguridad y auth basado en Bearer JWT. |

## Autores ✒️

_Todos aquellos que ayudaron a levantar el proyecto desde sus inicios:_

* **Paco Maciá** - _Trabajo Inicial_ - [pmacia]
* **Álvaro Márquez Sirvent** - _Documentación y desarrollo_ - [ams]


## Expresiones de Gratitud 🎁

* Comenta a otros sobre este proyecto 📢
* Invita una cerveza 🍺 o un café ☕ a alguien del equipo.
* Da las gracias públicamente 🤓.
* etc.
