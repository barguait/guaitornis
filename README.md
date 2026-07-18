# Guaitornis

Sitio de fotografía de aves de Federico Barreiro. No usa ningún framework ni paso de compilación: es HTML/CSS/JS simple que lee las tarjetas desde `content/aves.json`. Eso permite editar todo desde un panel visual en `/admin` sin tocar código.

## Estructura

```
index.html            → la página pública
content/aves.json      → los datos de cada ave (esto edita el panel /admin)
images/uploads/         → las fotos (el panel /admin sube acá)
admin/index.html        → el editor (Decap CMS)
admin/config.yml         → qué campos tiene cada ave en el editor
netlify.toml              → configuración de despliegue
```

## 1. Subir el proyecto a GitHub

**Sin usar la terminal (más simple):**
1. Entrá a github.com y creá una cuenta si no tenés.
2. Click en "New repository". Nombre: `guaitornis`. No marques "Add a README" (ya tenés uno). Creá el repositorio.
3. En la página del repo vacío, click en "uploading an existing file" y arrastrá **todo el contenido de esta carpeta** (todos los archivos y subcarpetas, manteniendo la estructura). Confirmá el commit.

**Con git, si lo preferís:**
```bash
cd guaitornis
git init
git add .
git commit -m "Primera versión de Guaitornis"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/guaitornis.git
git push -u origin main
```

## 2. Conectar con Netlify

1. Entrá a netlify.com (podés loguearte con tu cuenta de GitHub).
2. "Add new site" → "Import an existing project" → elegí GitHub → autorizá acceso → seleccioná el repo `guaitornis`.
3. En la configuración de build: dejá el comando de build **vacío** y el directorio de publicación como `.` (ya viene así en `netlify.toml`).
4. Deploy site. En un minuto vas a tener una URL tipo `algo-random.netlify.app` (después la podés personalizar o conectarle un dominio propio).

## 3. Activar el editor en /admin

El panel usa **Netlify Identity** (para que solo vos puedas entrar a editar) y **Git Gateway** (para que los cambios se guarden como commits en tu repo de GitHub).

1. En el dashboard de tu sitio en Netlify, andá a la pestaña **Identity** → **Enable Identity**.
2. Dentro de Identity, andá a **Settings and usage** y en "Registration" elegí **Invite only** (así nadie más se puede registrar solo).
3. Más abajo, en **Services**, activá **Git Gateway**.
4. Volvé a la pestaña Identity → **Invite users** → escribí tu email → Send.
5. Te va a llegar un mail de invitación de Netlify. Abrilo y hacé click en el link: te va a llevar al sitio y te va a pedir que configures una contraseña.

## 4. Usar el editor

1. Andá a `tu-sitio.netlify.app/admin`.
2. Iniciá sesión con el mail y la contraseña que configuraste.
3. Vas a ver el "Catálogo de aves" con la lista de especies cargadas. Click en una tarjeta para editarla, o en el botón para agregar una especie nueva.
4. Completá foto, nombre local, nombre científico, fecha y descripción, y apretá **Publish**.
5. En 1 o 2 minutos el sitio en vivo se actualiza solo, sin que tengas que hacer nada más.

Las 5 especies de ejemplo (Hornero, Benteveo, Tero, Zorzal, Cotorra) no tienen foto real todavía — quedaron como referencia de diseño. Podés editarlas con tus propias fotos, o borrarlas desde el mismo panel.
