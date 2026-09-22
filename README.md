# Galaxia de Flores Amarillas

Regalo para el 21 de septiembre. Se abre una caja, el universo se expande y
quedan 21 flores en órbita alrededor de una galaxia; cada flor guarda un mensaje.

Todo vive en `index.html`: una sola página, sin build, sin dependencias salvo
Three.js desde CDN.

## Verlo en local

```sh
python3 -m http.server 8777
```

Y abrir <http://127.0.0.1:8777>. Conviene servirlo así y no abrir el archivo con
doble clic: con `file://` el navegador trata la página como origen nulo y YouTube
se niega a cargar, así que la canción no suena.

## La música

La página intenta, en este orden:

1. `the-night-we-met.mp3` junto al `index.html`
2. YouTube (`KtlgYxa6BMU`), que solo funciona servido por http/https
3. un pad sintetizado, para que nunca quede en silencio

El reproductor de YouTube se crea al cargar la página, en mudo y ya sonando —
que es lo único que los navegadores permiten sin un gesto del usuario. El clic
en el regalo solo le quita el mudo, y por eso la canción entra en el acto.

El `.gitignore` deja fuera los archivos de audio. Si quieres desplegar el mp3
con la página (más fiable que YouTube en móviles), borra esa línea del
`.gitignore` y haz `git add -f the-night-we-met.mp3`.

## Editar los mensajes

Están en el array `MESSAGES`, al principio del `<script>`, en orden. Son 21
porque hoy es 21. Si cambias la cantidad, las órbitas y la numeración se
recalculan solas.

## Desplegar en GitHub Pages

Subir el repo y, en *Settings → Pages*, elegir la rama `main` y la carpeta
`/ (root)`. La página queda en `https://<usuario>.github.io/<repo>/`.
