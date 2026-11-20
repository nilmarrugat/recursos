# _base: plantilla de landing de imán

Copia de `/80/` (aprobada por Nil el 20-nov-2026), con cada parte que cambia marcada con un comentario `CAMBIA`. Las carpetas que empiezan por `_` no se publican en GitHub Pages: esto es solo plantilla.

## Cómo se usa

1. `cp -r _base <palabra>` (la palabra es la de "comenta X", p. ej. `80`).
2. Cambia todo lo marcado con `CAMBIA` en `<palabra>/index.html` y `<palabra>/gracias/index.html`. Lo demás (estructura, estilos, formulario, validación, FAQ de spam y precio, pie) **no se toca**.
3. Imágenes en `<palabra>/img/`: `portada.jpg` (1400×1050, ~160 KB), las de la prueba y, si hay escena con vídeo, `img/escena/001.jpg…`.
4. La web del imán va en `<palabra>/<ruta-oculta>/` (4 caracteres aleatorios, p. ej. `mapa-k7q2`), con `noindex`.

## Qué se cambia (y qué no)

| Parte | Se cambia | Reglas |
|---|---|---|
| Titular + firma | Sí | Promesa concreta. Firma en Mr Dafoe, minúsculas, girada −4°, `margin:-10px 0 0 4px` |
| Entradilla | Sí | Qué es, para qué y cuánto tarda. Mismo nombre del recurso que en el correo |
| Formulario | Solo `KIT_FORM_ID` y el nombre del recurso en el texto pequeño | Pregunta "¿A qué correo te lo mando?", placeholder "El que miras cada día", botón "Envíamelo" |
| Dato de portada | Sí | Real y verificable (en estudios: 8,8 en 1.º de bach) |
| Foto de portada | Sí | Propia, generada en el ChatGPT de Nil con prompt en primera persona; distinta de la escena |
| Escena | Sí o se quita | Un solo momento animado por página |
| Cómo funciona | Sí | 3 pasos reales |
| Prueba | Sí | La del pilar del imán; datos de terceros tapados |
| FAQ | Parcial | Se mantienen spam y precio; el resto, dudas reales |
| Cierre | Titular y texto pequeño | Lo que dejan de hacer ("Deja de estudiarlo todo por si acaso") |

Marca, colores, tipografías y calidez (focos de luz por sección, grano, sombras cálidas): ver `CLAUDE.md`. No se cambian por imán.

## Escena con vídeo que avanza con el scroll (técnica del 80)

1. Fotograma inicial: recorte 9:16 de una foto propia. Fotograma final: otra imagen propia, con la composición donde aterriza la ficha (en el 80, la hoja vista desde arriba).
2. Kling (`kling.ai`, cuenta de Nil): Video Generation → **Kling 4.0** → **Keyframes** (es el único modelo que acepta fotograma final), 720p, 5 s, Adaptive. Cuesta 50 créditos (la cuenta gratis da ~66). Prompt: movimiento de cámara continuo, sin cortes ni deformaciones, cara consistente, luz cálida, grano.
3. Nil lo descarga (Descargas). Fotogramas: `ffmpeg -i video.mp4 -vf "crop=W:H_sin_marca_de_agua:0:0,scale=600:-2" -q:v 6 img/escena/%03d.jpg` (recorta por abajo la marca de agua de Kling).
4. En el JS: `N` = número de fotogramas; `x=295.5 de 600` = centro horizontal del papel en el último fotograma (para centrar la ficha). En portátil el vídeo va con fondo ambiente desenfocado del propio fotograma.

## Página de gracias

Dice el asunto exacto del correo de Kit y el texto exacto del botón, avisa de que suele caer en Promociones y lleva el botón "Buscarlo en Gmail" (búsqueda `from:(hola@nilmarrugat.com) in:anywhere newer_than:1d`).

## Correo de confirmación

`_plantillas/correo-confirmacion.md`.
