# recursos.nilmarrugat.com: landings e imanes de TMV

Repositorio de las webs de captación de Nil Marrugat (TMV | Tu Mejor Versión). Se publica solo con GitHub Pages (rama `main`, raíz) en https://recursos.nilmarrugat.com. Todo en castellano.

## Estructura

```
<palabra>/index.html        landing del imán (formulario de Kit con doble opt-in)
<palabra>/<ruta-oculta>/    la web del imán, a la que solo se llega al confirmar el correo
<palabra>/img/              imágenes de ese imán
_base/                      plantilla maestra de landing y gracias (copia de /80/ con lo que cambia marcado CAMBIA; guía en _base/LEEME.md)
_plantillas/correo-confirmacion.md   correo de confirmación de Kit (genérico, dos huecos por imán)
```

- La **landing** es casi siempre la misma: cambian el titular, la promesa, el visual y la palabra clave. Se parte de `_base/` (`cp -r _base <palabra>`). Proceso completo de un imán nuevo: skill `web-imanes`.
- La **web del imán** es lo que cambia de verdad en cada uno.
- Imán activo: `80` (Mapa 80/20, vídeo CAPT-01).
  - Landing: `/80/` (formulario propio → Kit, formulario `10219237`, `action=https://app.kit.com/forms/10219237/subscriptions`, campo `email_address`).
  - Tras suscribirse: `/80/gracias/`. Tras confirmar el correo (doble opt-in): `/80/mapa-k7q2/` (la web del imán).
  - ReplyRush: disparador global "80" → botón a `/80/`. La landing antigua de Kit (`f42a00a7d1`) queda como reserva y también redirige a `/80/mapa-k7q2/`.
  - Limitación conocida: Kit solo envía el correo de confirmación a suscriptores nuevos; quien ya estaba en la lista no lo recibe.

## Equipo de skills (en `.claude/skills/`): orden de uso

1. **landing-page-design** (elayadesign, MIT): solo la **Parte A** (preguntas previas, estructura, conversión y copy). Su Parte B (visual) **no** se aplica: manda la marca de abajo.
2. **taste-skill** (Leonxlnx, MIT): dirección visual y composición. Flujo de imágenes: Claude escribe el prompt, Nil lo genera en su ChatGPT Plus (en primera persona, "hazme una foto de mí") y deja el archivo en la carpeta del imán.
3. **emil-design-eng**, **animate**, **choreograph**, **improve-animations**, **review-animations** (Emil Kowalski, MIT): todo el movimiento (hero con scroll, transiciones, microinteracciones). Un solo momento animado protagonista por página. Respetar `prefers-reduced-motion`.
4. **impeccable** (Paul Bakaus, Apache 2.0): `critique` y `polish` antes de publicar.

Si dos skills chocan, manda este archivo; si este archivo choca con lo que diga Nil, manda Nil.

## Marca (por encima de cualquier skill)

- **Estética:** minimalismo cálido lo-fi: papel cálido, luz de lámpara, grano de película suave. Nada genérico ni "de plantilla".
- **Color:** papel `#F7EFE3` · tinta café `#2B1D14` · texto `#4A3829` · gris `#7C6857` · línea `#E9DBC7` · tarjeta `#FFFAF2` · brasa `#3A2416` · naranja `#EB7018` (cifras, acentos, script) · fluorescente `#F8C043` (subrayados) · verde `#2CA74B` (solo checks).
- **Tipografía:** Archivo Black (titulares, interletraje −0,07 em) · Cal Sans (subtítulos) · Mr Dafoe (script naranja, en minúsculas) · texto corrido: Inter de momento (pendiente de sustituir por una alternativa con más carácter, a decidir con Nil).
- **Copy:** tono de Nil (18 años, directo, sin relleno). Nunca prometer atención personal ("te leo a todos"). Nunca inventar datos, testimonios ni cifras: solo los reales (p. ej. sus boletines: 1.º bach 8,8 de media final).
- **Privacidad de imágenes reales:** tapar logos del colegio, números de identificación, firmas y nombres de terceros.
- **Técnica:** HTML/CSS/JS sin dependencias de compilación; `noindex` en las webs de imanes; móvil primero (casi todo el tráfico llega desde Instagram).

## Publicar

`git add -A && git commit && git push` a `main`; GitHub Pages tarda ~1 min. Comprobar en el navegador antes de dar algo por hecho.
