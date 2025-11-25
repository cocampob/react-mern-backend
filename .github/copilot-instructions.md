# Copilot Instructions for 09-calendar-backend

## Visión General
Este proyecto es un backend básico para una aplicación de calendario, construido con Node.js y Express. La estructura está orientada a separar rutas, controladores y recursos públicos. Actualmente, solo se implementa la autenticación básica; el CRUD de eventos está pendiente.

## Estructura Principal
- `index.js`: Punto de entrada. Configura Express, carga variables de entorno, define middlewares y monta rutas.
- `routes/`: Define rutas agrupadas por dominio. Ejemplo: `auth.js` para autenticación.
- `controllers/`: Lógica de negocio para cada ruta. Ejemplo: `auth.js` maneja registro, login y renovación de token.
- `public/`: Archivos estáticos servidos en la raíz (`index.html`, `styles.css`).

## Flujos y Patrones Clave
- **Rutas**: Todas las rutas de autenticación están bajo `/api/auth`. Ejemplo: `POST /api/auth/new` para registro.
- **Controladores**: Cada ruta delega en funciones del controlador correspondiente. Ejemplo: `crearUsuario`, `loginUsuario`, `revalidarToken`.
- **Validaciones**: Se usa `express-validator` (aunque aún no está implementado en los controladores actuales).
- **Variables de entorno**: Se cargan desde `.env` usando `dotenv`. El puerto se define en `PORT`.
- **Middlewares**: Se usa `express.json()` para parsear el body y `express.static('public')` para servir archivos estáticos.

## Comandos de Desarrollo
- Iniciar en modo desarrollo (con recarga):
  ```sh
  npm run dev
  ```
- Iniciar en modo producción:
  ```sh
  npm start
  ```

## Convenciones Específicas
- Los controladores reciben siempre `(req, res = response)` y responden con objetos JSON.
- Los mensajes de error y éxito siguen el formato `{ ok: boolean, msg: string, ... }`.
- El nombre de usuario debe tener más de 5 caracteres (ver lógica en `crearUsuario`).
- El proyecto usa CommonJS (`require/module.exports`).

## Extensiones y Mejoras Futuras
- CRUD de eventos pendiente bajo `/api/events`.
- Integrar validaciones con `express-validator` en los controladores.
- Añadir tests y documentación de endpoints.

## Ejemplo de Ruta y Controlador
- **Ruta:** `POST /api/auth/new`
- **Controlador:** `crearUsuario` en `controllers/auth.js`

---

**Referencia rápida de archivos clave:**
- Entrada: `index.js`
- Rutas: `routes/auth.js`
- Controladores: `controllers/auth.js`
- Estáticos: `public/`

> Actualiza este archivo si cambian los flujos principales, convenciones o estructura del proyecto.