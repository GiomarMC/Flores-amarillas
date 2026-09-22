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

El orden no se decide al cargar: el mp3 se intenta **siempre primero**, con un
`play()` síncrono dentro del clic en el regalo. Esa llamada dentro de un gesto
del usuario es lo único que todos los navegadores aceptan sin discutir, móviles
incluidos. Solo si falla se pasa a YouTube, que ya está creado en mudo desde la
carga de la página para no perder el gesto.

Un `pointerdown` sobre la caja, 100 ms antes del clic, despierta el
`AudioContext` (nace suspendido si no hay gesto) y empuja la descarga del mp3.

Lo único que la página no puede saltarse: si un iPhone tiene el interruptor
lateral en silencio, el audio HTML no suena. No hay web que lo evite.

El mp3 va en el repo a propósito: en iOS, quitarle el mudo a un iframe de
YouTube desde fuera del reproductor suele fallar, y con el archivo local eso
deja de depender de nadie.

## Editar los mensajes

Están en el array `MESSAGES`, al principio del `<script>`, en orden. Son 21
porque hoy es 21. Si cambias la cantidad, las órbitas y la numeración se
recalculan solas.

## Desplegar en GitHub Pages

Subir el repo y, en *Settings → Pages*, elegir la rama `main` y la carpeta
`/ (root)`. La página queda en `https://<usuario>.github.io/<repo>/`.
