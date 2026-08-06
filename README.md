# your-astrophysicist

Portfolio site for **Jessica Syafaq Muthmaina** — M.Sc. Astrophysics & Cosmology
candidate at Università degli Studi di Padova.

Static HTML + CSS, no build step and no framework. Open `index.html` directly, or:

```sh
python3 -m http.server
# → localhost:8000
```

```
index.html    every section, content inline
styles.css    design system
img/          4 photos carried over from the source portfolio
```

## Sections

ticker → nav → hero → about → focus → featured research → outreach → cv → contact → footer

## Content

Sourced from the existing `jessica_portfolio` build (a Windows 98 desktop concept)
and re-laid out in the design language below. Every fact — degrees, the IRAM
Grenoble traineeship, the 28/30 lab grade, the 4C31.61 paper, the YouTube and
Substack channels, the Garut advocacy work — is carried across verbatim.

Two deliberate changes:

- **The Allan variance formula is hand-set in HTML/CSS** (`.math`, `.frac`, `.sum`)
  rather than pulled from MathJax, dropping two CDN scripts. It is one static
  formula, so a 1 MB typesetting engine wasn't worth it.
- **No testimonial section.** The reference design has one; the source portfolio
  had no quote to put in it, and inventing praise wasn't an option. The slot became
  the outreach section instead.

The source's interactive Allan deviation simulator was left out — it was a feature
of the Win98 concept rather than portfolio content. Happy to port it if wanted.

There is no email address anywhere in the source data, so the contact CTA points at
Substack. Swap it in `#contact` and the footer if a real address should go there.

## Design system

Adapted from [digitalsbyjannah.com](https://digitalsbyjannah.com/), extracted from
that site's Readymag project payload and per-page rendered snippets.

### Colour

| Token | Value | Use |
| --- | --- | --- |
| `--cream` | `#f0f0ea` | page canvas |
| `--cream-deep` | `#e7e7df` | alternate band |
| `--ink` | `#1e1e20` | text, dark sections, footer |
| `--pink-soft` | `#fccae9` | outreach + CTA bands, hover fills |
| `--pink-hot` | `#ff5fc6` | accents, ticker marks |
| `--rose` | `#ea587d` | italic emphasis, labels |
| `--grey` | `#a2a2a2` | indices, muted meta |

### Type

The reference pairs a custom display face with Typekit body fonts (`rkwd`, `xgnl`,
`wtqc`) that are licence-locked, so this build substitutes close free equivalents:

- **Display** — Fraunces (was `custom_155407`, used at 55–80px)
- **Body** — Poppins (also used on the reference, 19px / 1.65)
- **Labels & UI** — Courier New, bold, lowercase — the reference's signature move;
  it sets nav, eyebrows, buttons, tags and footer headings in mono.

### Structural motifs carried over

- Scrolling marquee ticker pinned above the nav
- Lowercase mono navigation
- Oversized editorial statements with italic emphasis words
- Floating sticker glyphs (the reference uses emoji; this uses `✦ ★ 🌌`)
- Sharp corners throughout (`border-radius: 0`)
- Full-bleed dark band for focus, pink bands for outreach and the closing CTA
- Hairline-ruled rows and cards that lift or fill pink on hover

Respects `prefers-reduced-motion`; breakpoints at 900px and 560px.
