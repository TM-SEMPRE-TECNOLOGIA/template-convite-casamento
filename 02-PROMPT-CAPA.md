# PROMPT — Capa do Convite (Alex & Rúbia)

> Uso: gerar a imagem do ENVELOPE/CAPA (o que aparece antes de "Toque para abrir").
> Depois de gerada, salvar como `assets/capa.png` — o `index.html` já referencia esse caminho.

## Prompt principal (simples e direcionado)

"Invitation cover art, elegant minimal wedding invitation envelope, vertical
portrait format. Centered monogram with the initials A & R in an ornate serif
script, deep olive green color. A single round wax seal button below the
monogram, olive green wax with a soft warm cream rim light glowing around its
edge, like an illuminated border. Clean cream-white background, subtle fine
botanical olive branch line art on the corners, soft natural paper texture.
Luxurious, timeless, refined. No text besides the initials A & R. No people,
no photos."

## Variação curta (se quiser mais direto)

"Elegant wedding invitation cover, cream background, olive green wax seal with
glowing illuminated border, ornate initials A & R in serif script, subtle olive
branch corner decorations, minimal, luxurious, vertical."

## O que o site faz com ela

- A imagem gerada vira a capa (`#weiOverlay img`).
- O botão de cera (wax seal) com borda iluminada é animado em CSS no HTML:
  - Borda creme/dourada pulsando (glow) enquanto espera o toque;
  - Ao tocar, o selo "abre" (gira + expande + fade) e dispara o vídeo de abertura.
- Se preferir a imagem SEM o selo (só iniciais), o HTML desenha o selo animado
  por cima — basta indicar.

## Se quiser a capa com o selo já "aberto" (metade da cena)

"Same invitation cover, but the wax seal is partially cracked open, warm light
escaping from the crack, olive green and cream palette."
