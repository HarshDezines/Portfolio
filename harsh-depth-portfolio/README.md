# Harsh Depth — portfolio

Open `index.html` through any static server (e.g. `npx serve .` or `python3 -m http.server`).
GSAP 3.12.5 + ScrollTrigger load from cdnjs. Fonts: Manrope and IBM Plex Mono from Google Fonts
(the sticker artwork uses Bagel Fat One).

## Editing
Everything editable is at the top of the script in `index.html`:
- `SITE` – top-left brand label, hero heading, eyebrow and description, the name on the HELLO sticker,
  the badge sticker text, email, and the Instagram and LinkedIn URLs.
- `STICKERS` – where each sticker sits on the character (image px); `onFace` makes it move with the head,
  and `tilt` angles it to follow the curve of the cheek.
- `CHAPTERS` – per chapter: id, its sticker, which side of the sticker its card prefers on desktop
  (`card.side` + `card.align`; it moves to the next clear side if needed), the desktop zoom (`push`),
  the phone zoom and framing (`mobile`), scroll lengths, and the copy. Work rows are inactive until you add a
  `url` as the third item of a row, e.g. `["Project One", "CGI & Product Visuals", "https://…"]`.
  Camera target and focus radius come from the sticker automatically.
- `FACE` – facial gesture amounts: head lean (px / degrees), brow lift, blink timing, lid drop.
  Set any amount to 0 to switch that gesture off.
- `FLAMES` – fire colours, how high it climbs on each side, flame size, droplet count, hover radius,
  how much it sinks while the camera is in a chapter, and the resolution cap. The fire is a WebGL
  shader; it lowers its own resolution (down to half) if a device can't keep up.

## Assets
- `character.webp` – your render, edge-faded, with the shirt extended 460px downward for deep zooms.
- `character-blur.webp` – pre-blurred copy used as the out-of-focus layer.
- `character-matte.png` – cutout of the character, used to tuck the flames behind it.
- `stk-*-shade.png` – the cheek's light and colour under each face sticker, printed onto it so it looks stuck to the skin.
  If you move a face sticker, these need regenerating for its new spot.
- `eye-*-plate.webp` – eye whites with the original iris painted out.
- `eye-*-iris.png` – the original irises cut out as separate layers.
- `eye-*-mask.png` – eyeball shapes that clip the moving irises.
- `eye-*-lid.png` – upper eyelids built from the render's own lid skin, for blinks.

## Fallbacks
- Missing eye files: the original, static eyes show.
- No WebGL: head lean, brow lift and the flames switch off; everything else works.
- Missing matte: the flames stay hidden rather than drawing over the character.
- Reduced motion: flames freeze and droplets stop, head lean and brow lift switch off;
  hover heat, blinks and eye tracking remain.
