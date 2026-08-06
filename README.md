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

Every section is a Windows 98 application window, reusing the file metaphor from
the original desktop build. The page still scrolls normally — the windows are
static, not draggable.

| Section | Window |
| --- | --- |
| hero | bare desktop, dotted wallpaper, no window |
| about | `AboutMe.txt — Notepad`, with File/Edit/Search/Help menu |
| focus | `System Properties — Jessica Info`, tech stack in a fieldset |
| research | `Quasar_Research.doc — WordPad`, with B/I/U toolbar |
| outreach | `Outreach.url — Internet Explorer`, with address bar |
| cv | `Resume.txt — Notepad` |
| contact | modal dialog with icon and OK-style buttons |
| footer | taskbar — Start button, section tabs, live clock |

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

Windows 98 chrome wearing the palette of
[digitalsbyjannah.com](https://digitalsbyjannah.com/), which was extracted from that
site's Readymag project payload and per-page rendered snippets.

### Colour

| Token | Value | Use |
| --- | --- | --- |
| `--cream` | `#f0f0ea` | page canvas |
| `--cream-deep` | `#e7e7df` | window face, alternate band |
| `--ink` | `#1e1e20` | text, dark bands, deepest bevel edge |
| `--pink-soft` | `#fccae9` | outreach band, button hover |
| `--pink-hot` | `#ff5fc6` | title bar gradient, accents |
| `--rose` | `#ea587d` | title bar gradient, labels, italic emphasis |
| `--grey` | `#a2a2a2` | mid bevel shadow |

Win98's grey-and-navy chrome is retinted: window faces are cream rather than
`#c0c0c0`, and title bars run a rose → hot-pink gradient in place of the classic
navy → blue.

### Bevels

The whole look rests on four-layer inset shadows. Raised surfaces go light on the
top-left, dark on the bottom-right; sunken panels invert it:

```css
box-shadow:
  inset -1px -1px 0 0 var(--w-dark),    /* outer bottom-right */
  inset  1px  1px 0 0 var(--w-light),   /* outer top-left     */
  inset -2px -2px 0 0 var(--w-shadow),  /* inner bottom-right */
  inset  2px  2px 0 0 var(--w-hilite);  /* inner top-left     */
```

Windows add a hard `5px 5px` offset shadow — no blur, so it reads as period-correct
depth rather than a modern drop shadow.

### Type

Four families, each with one job:

- **Fraunces** — editorial display headings, the one thing kept fully from the
  reference site (whose own display face is a licence-locked custom upload)
- **Poppins** — body copy, also used on the reference
- **Courier New** — labels, menus, buttons, status bars, taskbar tabs
- **Silkscreen** — pixel type, restricted to window title bars, the brand mark and
  the Start button

### Details

- Marquee ticker pinned above the menu-bar nav
- Dotted wallpaper behind the hero, the only section without a window
- Sunken document areas for Notepad/WordPad text, sunken photo frames
- Allan variance formula hand-set in HTML/CSS (`.math`, `.frac`, `.sum`)
- Win98 scrollbars via `::-webkit-scrollbar`, checkerboard track included
- Sticky taskbar with a live clock; `_ □ ×` controls are decorative
  (`aria-hidden`), so nothing on screen promises an interaction it can't deliver

Respects `prefers-reduced-motion`; breakpoints at 900px and 560px.
