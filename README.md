# Brand Books — Euller Lolato

Portal público com os Brand Books dos clientes da consultoria.

🔗 **[brandbooks.eullerlolato.com](https://brandbooks.eullerlolato.com)**

---

## Estrutura

```
brandbooks/
├── index.html          ← Portal de entrada (CSS e JS inline)
├── vendor/             ← Lenis vendorizado (sem CDN externo)
│   ├── lenis.min.js
│   └── lenis.css
└── kody/
    ├── index.html      ← Brand Book da Kody
    └── logos/           ← Assets visuais
```

## Clientes

| Cliente | Status | Link |
|:--------|:-------|:-----|
| Kody | ✅ Ativo | [/kody](https://brandbooks.eullerlolato.com/kody/) |
| Consciência Aplicada | 🔜 Em breve | — |

---

## Motion

O site é HTML puro — não há build. O CSS e o JS vivem inline no `index.html`, e
a única dependência externa é o [Lenis](https://github.com/darkroomengineering/lenis),
vendorizado em `vendor/` para não depender de CDN.

**Scroll suave.** Lenis com `lerp: 0.1`, âncoras e scroll aninhado resolvidos
pela própria lib. Mesma config dos outros sites do `eullerlolato.com`.

**Deriva da fumaça.** O `.hero-bg` é `position: fixed`, então não tem posição
própria na página para medir — o parallax comum (por `getBoundingClientRect`)
não funcionaria nele. A deriva vem do **progresso total do scroll** (0 a 1),
escrita em `--parallax-y` e aplicada por `transform` no CSS. O `inset: -8% 0` dá
a folga para a borda da imagem não entrar em cena nos 6% de deslocamento.

**`html:not(.lenis)`.** O Lenis marca `<html class="lenis">` quando assume o
scroll; o `scroll-behavior: smooth` nativo precisa sair do caminho nesse
momento, senão os dois disputam a mesma rolagem. Sem Lenis (reduced-motion, JS
off) o nativo segue valendo.

Tudo checa `prefers-reduced-motion` — sob essa flag nada disso inicializa.

Origem dos efeitos: acervo `kodyos/referencias/fourdesignestudio` (ver
`EFFECTS.md` lá).

---

> Hospedado na Vercel · Deploy automático via GitHub (branch `main`)
