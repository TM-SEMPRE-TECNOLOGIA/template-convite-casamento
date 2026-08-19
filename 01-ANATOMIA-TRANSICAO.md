# 01 — Anatomia da Transição: Capa → Vídeo → Tela Principal

Investigação do original: `https://webgencyinvitations.com/thesacredgarden`
(convite "The Sacred Garden" — Zohan & Rose, Tilda).
Fontes: `index-original-backup.html` (Tilda folder) e
`The Sacred Garden (13_08_2026 13：20：16) - singlefile-backup.html` (SingleFile).

## Mecânica EXATA (3 fases, 4 atores)

### Atores
| Elemento | Papel |
|---|---|
| `#weiOverlay` | Capa/envelope fullscreen (fixed, inset 0, z-index 99999). Clicável. |
| `#weiVideoWrap` | Tela do vídeo de abertura (fixed, inset 0, z-index 100000). Oculto por padrão. |
| `#weiVideo` | `<video muted playsinline preload="auto">` — max-width 440px, centralizado. |
| `#weiAudio` | `<audio loop>` — música de fundo (Einaudi — Divenire). |
| `#weiAudioBtn` | Botão flutuante play/pause (60px, bottom:20 right:20). Aparece SÓ após o vídeo. |

### Fase 1 — Toque na capa (startVideo)
```
overlay click/touchstart → startVideo():
  1. done = true (trava repetição)
  2. overlay.style.opacity = '0'          (transition 1.4s ease)
  3. overlay.style.pointerEvents = 'none'
  4. setTimeout(1400ms) → overlay.display = 'none'
  5. videoWrap.classList.add('wei-video-in')   → opacity 1 (transition 0.8s) + pointer-events all
  6. video.play()  ← SÍNCRONO
  7. audio.play()  ← SÍNCRONO (música começa junto com o vídeo)
```

### Fase 2 — Vídeo de abertura
- Fullscreen fixed, fundo = mesma cor da capa (creme `#F9F0E0`), vídeo centralizado.
- `timeupdate` monitora: `currentTime >= duration - 0.8` → dispara `endSequence()`.

### Fase 3 — Fim do vídeo (endSequence)
```
timeupdate → currentTime >= duration - 0.8:
  1. videoWrap.classList.remove('wei-video-in')
  2. videoWrap.classList.add('wei-video-out')   → opacity 0 (transition 1.4s)
  3. setTimeout(1400ms) → videoWrap.display = 'none'
  4. audioBtn.visibility = 'visible'; opacity = '1'   (transition 0.3s)
```
→ O vídeo começa a sumir 0.8s ANTES de terminar (fade de saída suave).
→ Só depois disso o botão flutuante de música aparece.

### Botão flutuante de áudio (pós-vídeo)
- `#weiAudioBtn`: 60x60, border-radius 50%, background `#5A0F1B` (vinho) — NOVO: verde oliva `#3E4A22`.
- Toggle: `audio.paused ? play() : pause()` + swap de ícones SVG (pause ▮▮ / play ▶).

## Tempos (replicados 1:1 no index.html)
| Transição | Duração |
|---|---|
| Fade out da capa | 1.4s |
| Fade in do vídeo | 0.8s |
| Antecipação do fim | 0.8s antes de terminar |
| Fade out do vídeo | 1.4s |
| Botão de áudio | 0.3s |

## O que foi ADAPTADO (não pode ser réplica cega)
1. **Capa**: original usava IMAGEM do envelope (ChatGPT Image). No reclone, o cliente
   ainda não tem a arte → implementado MONOGRAMA "A&R" + SELO DE CERA animado
   (borda iluminada pulsante + metades que partem ao abrir). Prompt p/ gerar a arte
   final em `02-PROMPT-CAPA.md` (salvar como `assets/capa.png`).
2. **Vídeo**: original usava `1782224012851.mp4` (casal Zohan & Rose). NO reclone foi
   gerado `assets/video-abertura.mp4` (4.8s, 720x1280) com a FOTO do casal (ken burns)
   — mesma duração/estrutura, mídia do cliente. Se o cliente enviar vídeo próprio,
   é só substituir o arquivo (manter ~4-6s e 720x1280).
3. **Áudio**: original Einaudi — Divenire (5min26s). Mantido como `assets/musica.mp3`
   (placeholder). Trocar quando o cliente escolher a música.
4. **Paleta**: creme + vinho → **verde oliva + branco** (cliente).
5. **Formulário RSVP**: original Tilda `t702` (Formspree NO services). NOVO: monta
   mensagem e abre `wa.me/558182165064` (WhatsApp +55 81 8216-5064).

## Como trocar a capa gerada (assets/capa.png)
No `index.html`, a capa usa monograma + selo em CSS. Para usar a IMAGEM gerada:
```html
<div id="weiOverlay">
  <img id="weiImg" src="assets/capa.png" alt="Toque para abrir" draggable="false" style="width:100%;max-width:440px">
  <!-- manter weiTapWrap -->
</div>
```
E remover/ocultar `#weiMonogram` e `#weiSeal` (ou sobrepor o selo animado por cima
da imagem — o selo continua dando o efeito de "abrir").
