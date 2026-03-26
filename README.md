# Welcome to your Expo app 👋

This is an [Expo](https://expo.dev) project created with [`create-expo-app`](https://www.npmjs.com/package/create-expo-app).

## Get started

1. Install dependencies

   ```bash
   npm install
   ```

2. Start the app

   ```bash
   npx expo start
   ```

In the output, you'll find options to open the app in a

- [development build](https://docs.expo.dev/develop/development-builds/introduction/)
- [Android emulator](https://docs.expo.dev/workflow/android-studio-emulator/)
- [iOS simulator](https://docs.expo.dev/workflow/ios-simulator/)
- [Expo Go](https://expo.dev/go), a limited sandbox for trying out app development with Expo

You can start developing by editing the files inside the **app** directory. This project uses [file-based routing](https://docs.expo.dev/router/introduction).

## Get a fresh project

When you're ready, run:

```bash
npm run reset-project
```

This command will move the starter code to the **app-example** directory and create a blank **app** directory where you can start developing.

## Learn more

To learn more about developing your project with Expo, look at the following resources:

- [Expo documentation](https://docs.expo.dev/): Learn fundamentals, or go into advanced topics with our [guides](https://docs.expo.dev/guides).
- [Learn Expo tutorial](https://docs.expo.dev/tutorial/introduction/): Follow a step-by-step tutorial where you'll create a project that runs on Android, iOS, and the web.

## Join the community

Join our community of developers creating universal apps.

- [Expo on GitHub](https://github.com/expo/expo): View our open source platform and contribute.
- [Discord community](https://chat.expo.dev): Chat with Expo users and ask questions.

## Despliegue en GitHub Pages

Esta app está configurada para generar una versión estática para web y publicarla en GitHub Pages usando la carpeta `docs` del repositorio.

### 1. Configuración de Expo para web estática

En `app.json` ya están definidos los ajustes clave:

- Salida estática para web:

  ```json
  "web": {
    "output": "static",
    "favicon": "./assets/images/favicon.png"
  }
  ```

- Base URL para GitHub Pages (debe coincidir con el nombre del repositorio):

  ```json
  "experiments": {
    "typedRoutes": true,
    "reactCompiler": true,
    "baseUrl": "/bancaza"
  }
  ```

Si cambias el nombre del repositorio o del proyecto en GitHub, actualiza también `baseUrl` (por ejemplo, `/mi-repo`) para que las rutas funcionen correctamente en producción.

### 2. Generar la versión estática en `docs`

Desde la raíz del proyecto:

1. Instala dependencias (solo la primera vez o cuando cambien):

   ```bash
   npm install
   ```

2. Genera la exportación estática para web dentro de la carpeta `docs`:

   ```bash
   npx expo export --platform web --output-dir docs
   ```

Esto creará/actualizará la carpeta `docs` con los archivos HTML, JS, assets y el archivo `.nojekyll` necesario para GitHub Pages.

### 3. Subir cambios a GitHub

1. Añade y haz commit de los cambios (incluyendo la carpeta `docs`):

   ```bash
   git add .
   git commit -m "build web para GitHub Pages"
   git push origin main
   ```

### 4. Configurar GitHub Pages

En el repositorio de GitHub:

1. Ve a **Settings → Pages**.
2. En **Source**, selecciona **Deploy from a branch**.
3. En **Branch**, elige `main` y la carpeta `/docs` como ruta.
4. Guarda los cambios.

GitHub Pages generará y publicará el sitio usando el contenido de `docs`.

### 5. URL de producción

Con la configuración actual, la aplicación se sirve en:

- `https://pacopul.github.io/bancaza`

Si el repositorio o el usuario cambian, la URL seguirá el formato:

- `https://<usuario>.github.io/<nombre-del-repo>`

### 6. Flujo para futuras actualizaciones

Cada vez que modifiques la app y quieras actualizar la versión pública:

1. Ejecuta de nuevo la exportación estática:

   ```bash
   npx expo export --platform web --output-dir docs
   ```

2. Haz commit y push de los cambios:

   ```bash
   git add .
   git commit -m "actualiza build web"
   git push origin main
   ```

3. Espera unos segundos/minutos a que GitHub Pages reprocese el contenido y actualice la web.
