<<<<<<< HEAD
# Convite de Casamento — TEMPLATE TM Sempre Tecnologia

**Base reutilizável** clonada do projeto "Alex e Rúbia — Convite Casamento" (13/08/2026).
Nomes, local, data, WhatsApp e mídias foram GENERALIZADOS — pronto para personalizar por cliente.

## Dados atuais (placeholder)
| Item | Valor |
|---|---|
| Noivos | Carolina & Matheus |
| Data/Horário | 14/02/2027 · 17h (countdown ajustado) |
| Local | Praia do Paraíso — Orla Sul · Búzios · RJ |
| Paleta | Verde oliva #555B3E + creme #F9F0E0 |
| RSVP | WhatsApp TM Sempre Tecnologia (62) 99604-6458 |

## Como personalizar por cliente

### 1. Nomes, data e local (no `index.html`)
```
Alex & Rúbia        → [Noivo] & [Noiva]
Carolina & Matheus  → nomes reais
14.02.27            → data do casal
Praia do Paraíso    → local real
Orla Sul · Búzios · RJ → endereço real
new Date(2027,1,14,17,0,0) → countdown (mês 0-based: janeiro=0, fevereiro=1...)
```

### 2. WhatsApp do RSVP
No `index.html`, substituir **TODOS** os `5562996046458` pelo número do cliente:
```
wa.me/55<DDD><numero>  (só dígitos, sem + ou espaços)
```

### 3. Mapa (iframe do Google Maps)
Trocar o `src` do iframe pelo embed do local real:
```
https://maps.google.com/maps?q=<Endereço URL-encoded>&z=14&output=embed
```

### 4. Imagens (pasta `assets/img/`)
| Arquivo | O que é | Onde trocar |
|---|---|---|
| `capa.webp` | Envelope + monograma | Capa "Toque para abrir" |
| `selo-cera-template.webp` | Selo de cera (botão RSVP) | Seção Confirme sua presença |
| `sob-a-graca-template.png` | "Sob a graça de Deus" | Hero |
| `rosa-template.png` | Rosa decorativa | Programação |
| `casal-vertical.jpg` | Foto do casal (9:16) | Seções do casal |
| `mapa-template.webp` | Mapa do Brasil estilizado | Seção Localização |
| `favicon.*` | Ícone do site | Aba do navegador |

**Dica:** manter 9:16 para `casal-vertical.jpg` e 900x1200 para `capa.webp`.
Fotos do cliente: gerar a partir de banco grátis (Pexels/Unsplash) ou material do casal.

### 5. Vídeo de abertura (`assets/video/video-abertura-template.mp4`)
720x1280, 4.8s, ken-burns (gerado com a foto genérica). Substituir pelo vídeo do casal
(Google Flow ou produção própria). Manter ~4-6s e 720x1280.

### 6. Música (`assets/audio/musica.mp3`)
Einaudi — Divenire (genérica). Trocar pela música do casal se quiser.

## Deploy por cliente
```bash
# repo dedicado por cliente (NUNCA reusar o mesmo repo)
gh repo create <nome> --public --source . --push
gh api -X POST "repos/TM-SEMPRE-TECNOLOGIA/<nome>/pages" -f "source[branch]=main" -f "source[path]=/" --jq '.html_url'
```
URL: `https://tm-sempre-tecnologia.github.io/<nome>/`

## Estrutura
```
Convite Casamento - Template/
├── index.html                    ← SITE (personalizar aqui)
├── backups/index-original-backup.html
├── assets/
│   ├── img/     ← capa, selo, rosas, fotos, mapa, favicons
│   ├── video/   ← vídeo de abertura
│   ├── audio/   ← música
│   └── fonts/   ← Cinzel, Ovo, Imperial Script, BeauRivage
└── README.md
```

---
Desenvolvido por TM Sempre Tecnologia · (62) 99604-6458
=======
# Convite de Casamento — Alex & Rúbia

**Estado atual: copy-only.** `index.html` = template ORIGINAL (The Sacred Garden /
Tilda) com **somente os textos** trocados para pt-BR (dados do casal). Toda a
mídia, paleta e layout originais foram mantidos intencionalmente.

## Dados do cliente
| Item | Valor |
|---|---|
| Noivos | Alex e Rúbia |
| Data/Horário | 27/09/2026 · 14h (countdown ajustado) |
| Local | Praia de Maracaípe — em frente à Pousada Maraoka (Ipojuca, PE) |
| Paleta | (mantida a original — aguardando edição pontual p/ verde oliva) |
| RSVP | (formulário original — aguardando edição pontual p/ WhatsApp) |

## O que mudou (SÓ TEXTO)
- Nomes: Zohan & Rose → Alex & Rúbia
- "Wedding Day" → "Vamos nos casar"; "Two Souls / One destiny / A Lifetime
  written by Allah" → "Duas almas / Um destino / Uma história escrita com amor"
- Mensagens, seções, programação, local, traje, presentes → pt-BR
- Formulário RSVP → pt-BR
- Countdown → 27/09/2026 14h
- `<title>` / og:title → Alex & Rúbia · Casamento

## O que NÃO mudou (intencional — aguardando instrução)
- Vídeo de abertura (original Zohan & Rose do CDN R2) — **será substituído pelo
  vídeo do Google Flow que o Thiago vai fazer**
- Música (Einaudi — Divenire, CDN R2)
- Imagem da capa (envelope original)
- Paleta (creme + vinho originais)
- Layout/estrutura Tilda inteira
- Horários da programação (5 PM etc.) — edição pontual pendente

## Arquivos
```
Alex e Rúbia - Convite Casamento/
├── index.html                        ← SITE (original + copy pt-BR)
├── index-original-backup.html        ← Original intacto (fonte da copy)
├── index-v1-custom-backup.html       ← Minha 1ª versão (descartada)
├── The Sacred Garden (...) - singlefile-backup.html  ← SingleFile original
├── 01-ANATOMIA-TRANSICAO.md          ← Investigação da transição capa→vídeo→tela
├── 02-PROMPT-CAPA.md                 ← Prompt p/ arte da capa (uso futuro)
├── README.md
└── assets/                           ← mídias da v1 (não usadas pelo index atual;
                                         mantidas até o vídeo do Google Flow chegar)
```

## Link público
https://tm-sempre-tecnologia.github.io/convite-alex-rubia/

## Próximas edições (pontuais, aguardando o Thiago)
1. Vídeo da entrada (Google Flow) → substituir a mídia original
2. Paleta verde oliva + branco
3. Horários da programação
4. RSVP → WhatsApp +55 81 8216-5064
>>>>>>> e30759a (backup: sincronizacao completa e inventario 2026-08-18 21:48)
