---
name: resume-to-website
description: Converts a resume (PDF, DOCX, or plain text) into a stunning, personalized, deployable single-page HTML portfolio website. Trigger this skill whenever the user mentions: uploading a resume, converting a CV to a website, building a personal portfolio from their resume, making a personal site to share with recruiters, or any phrasing like "turn my resume into a website", "make a portfolio site from my CV", "create a personal page from my resume". Also trigger when the user uploads a file that appears to be a resume/CV and asks to do something web-related with it. The output is a single self-contained HTML file that can be deployed for free on GitHub Pages, Netlify, or Vercel with zero additional setup.
---

# Resume → Aesthetic Website Skill (v2)

Turn any resume into a unique, deployable portfolio site. Every output must feel hand-crafted — never templated.

This skill runs in four phases:
1. **Extract** — structured data + rich personality signals
2. **Design** — full frontend-design methodology + contrast-pick heuristic
3. **Build** — polished, self-contained HTML
4. **Output** — file + deployment guide

---

## Phase 1 — Extract

### 1a. Read the file

- **PDF** → `pdftotext /mnt/user-data/uploads/<file> -` (fallback: python pdfplumber)
- **DOCX** → `python3 -c "import docx; d=docx.Document('/mnt/user-data/uploads/<file>'); [print(p.text) for p in d.paragraphs]"`
- **Plain text / already in context** → use directly

### 1b. Structured content

```
name, tagline/title, email, phone, location, linkedin, github, website
summary/about
experience: [{company, role, dates, bullets[]}]
education: [{institution, degree, dates, notes}]
skills: [categories with items]
projects: [{name, description, link}]
certifications / awards / publications / volunteer
languages spoken
```

### 1c. Personality signals — CRITICAL, drives uniqueness

Read the resume as a whole person. Extract ALL of these:

| Signal | What to look for |
|---|---|
| **Tone voice** | Clinical & precise? Warm & personable? Punchy & confident? Humble? Eccentric? |
| **Energy level** | Action verbs ("launched", "led", "drove") = high. Quieter verbs ("supported", "assisted") = low. |
| **Breadth vs depth** | Many domains (generalist) or one deep area (specialist)? |
| **Creative indicators** | Side projects, open-source, art, music, writing, unusual hobbies, community work |
| **Cultural texture** | International background? Multilingual? Non-linear career path? |
| **Company culture** | FAANG/enterprise → polished/structured. Startup → scrappy/fast. NGO/academia → values-driven. |
| **Writing style** | Long thoughtful bullets vs. punchy 1-liners. Jargon density. Passive vs. active voice. |
| **Hobbies & interests** | Sports → bold/kinetic. Music → rhythmic/editorial. Nature → organic/earthy. Gaming → dark/techy. Food → warm/sensory. |
| **Career arc** | Linear climb → classic. Pivot story → dynamic. Portfolio career → eclectic. |
| **Location / region** | Can inform spatial density, colour sensibility. |

Output a **Personality Profile** before doing anything else:
```
Tone: [clinical / warm / punchy / reflective / eccentric]
Energy: [high / medium / quiet]
Breadth: [generalist / balanced / specialist]
Creative pulse: [high / medium / low] — [specific indicators from resume]
Cultural texture: [notes]
Company culture: [enterprise / startup / academic / mixed]
Writing style: [dense technical / conversational / minimal / narrative]
Distinctive trait: [the single thing that makes this person memorable]
```

---

## Phase 2 — Design

Use the **full frontend-design methodology**. This is a design brief, not a template lookup.

### 2a. Aesthetic vocabulary — 24 directions

**Dark:**
| Name | Character |
|---|---|
| `terminal-noir` | Black bg, monospace accents, phosphor green or amber glow, scanline texture |
| `midnight-editorial` | Deep navy, serif headlines, subdued gold, ink-on-night |
| `brutalist-dark` | Near-black, stark white type, raw exposed grid, zero ornament |
| `cosmic` | Deep space bg, nebula gradient accents, floating elements, star particles |
| `neon-night` | Dark bg, electric neon (hot pink / lime / cyan), glitch micro-details |
| `obsidian-luxury` | Matte black, platinum/silver accents, ultra-thin hairlines, fashion-house feel |

**Light:**
| Name | Character |
|---|---|
| `swiss-editorial` | White + off-white, Neue Haas grid, tight typography, small red or black accents |
| `warm-paper` | Cream/parchment, warm serif, ink texture, nostalgic editorial |
| `luxury-serif` | Champagne/ivory bg, Didot-style display, gold or copper, refined spacing |
| `scandinavian-minimal` | Pure white, thin strokes, muted sage or dusty rose, airy negative space |
| `soft-pastel` | Gentle colour-field sections, rounded corners, friendly italic type |
| `code-minimal` | Off-white bg, monospace primary font, syntax-highlight accents, dev-doc feel |

**Bold / expressive:**
| Name | Character |
|---|---|
| `brutalist-light` | White bg, thick black borders, oversized type, intentionally broken grid |
| `maximalist-editorial` | Full-bleed colour sections, mixed font weights, collage-like composition |
| `art-deco` | Geometric ornament, symmetrical grandeur, muted gold + black, tall condensed type |
| `kinetic` | Bold primary colours, diagonal elements, strong motion, sports energy |
| `bauhaus` | Primary colours only, geometric sans, circles/squares as decorative elements |
| `retro-futurist` | 1970s sci-fi palette (burnt orange + cream), wide tracking, geometric display |

**Organic / character:**
| Name | Character |
|---|---|
| `hand-crafted` | Imperfect feel, mixed weights, warm neutrals, texture overlays, human touch |
| `academic-ink` | Oxford-college serif, justified text, ruled-line details, deep navy + red |
| `earthy-organic` | Terracotta, sage, warm linen, nature textures, rounded organic shapes |
| `blueprint` | Blueprint navy or white bg, thin technical strokes, engineering drawing feel |
| `dashboard` | Data-dense, card-based, professional charcoal + teal, clear KPI-like hierarchy |
| `risograph` | Bright overlapping colour layers, slight misregistration, grainy texture, zine energy |

### 2b. Contrast-pick rule — CRITICAL, prevents sameness

1. List **3–5 candidates** from the palette that could plausibly fit this person
2. Identify which one a naive field→style mapping would predict ("software engineer → terminal-noir")
3. **Strike that one out**
4. From the remaining candidates, pick the one best supported by *personality signals* — not job title

This is the core mechanism that prevents two software engineers from getting the same site. They might get `warm-paper` and `art-deco` instead of both getting `terminal-noir`.

**Exception rule:** If personality signals *strongly confirm* the obvious choice (e.g., person explicitly lists terminal customisation as a hobby, works in systems programming, writes in clipped technical style), you may select it — but the *execution* must be visually distinct: different colour temperature, different layout structure, different typographic personality.

### 2c. Write a design spec before touching HTML

```
AESTHETIC: [name]
RATIONALE: [2 sentences connecting personality signals → this choice]

TYPOGRAPHY:
  Display: [font name] — [why this font]
  Body: [font name]
  Accent: [font name or "none"]
  ⚠️ NEVER use Inter, Roboto, Arial, system-ui as primary fonts

COLOUR PALETTE:
  --bg:          #...
  --surface:     #...
  --accent:      #...
  --accent2:     #... (optional)
  --text:        #...
  --text-muted:  #...
  --border:      #...

LAYOUT:
  Hero shape: [full-bleed / split-grid / centered / asymmetric overlap / diagonal cut / etc.]
  Section rhythm: [editorial columns / timeline / cards / minimal list / stacked full-bleed / etc.]
  Nav style: [top sticky bar / floating pill / side rail / minimal corner mark]
  Spatial density: [airy / balanced / dense]

SIGNATURE DETAIL:
  [The one visual element that makes this site memorable and unrepeatable]

MOTION:
  Load: [staggered fade / blur-in / slide / typewriter / clip reveal]
  Scroll: [IntersectionObserver reveal / parallax / none]
  Hover: [describe the effect]
```

### 2d. Design principles (always apply)

- **Typography first** — The font pairing IS the personality. Choose characterful, unexpected fonts.
- **Atmosphere > decoration** — Depth through gradients, layered transparency, texture. Not clipart.
- **One unforgettable detail** — Animated gradient mesh, typographic oversizing, parallax layer, creative hover state, SVG texture — something that rewards attention.
- **Spatial intentionality** — Asymmetry, overlap, diagonal flow, and grid breaks used deliberately, not randomly.
- **Aesthetic coherence** — Every element speaks the same language. No warm-paper bg with neon accents.
- **Layout diversity** — If the last output used a 2-column split hero, use centered / asymmetric / diagonal cut next. Actively vary hero shape, experience display, skill visualisation, nav placement.

---

## Phase 3 — Build

Single self-contained HTML file. All CSS + JS inline. Google Fonts CDN is the only external call.

### Head block (always include)
```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[Name] — [Title]</title>
  <meta name="description" content="[One-line bio]">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=..." rel="stylesheet">
  <style>
    :root { --bg:#...; --surface:#...; --accent:#...; --text:#...; --text-muted:#...; --border:#...; }
  </style>
</head>
```

### Required sections (adapt labels to persona + aesthetic)
1. **Hero** — name, title/tagline, contact links, punchy intro
2. **About** — 2–4 sentences, human voice
3. **Experience** — company, role, dates, styled bullets
4. **Skills** — visual groupings (never a bare `<ul>`)
5. **Education** — concise
6. **Projects** *(if present)* — linked cards or list
7. **Contact / Footer** — CTA + social links

### Motion requirements
- Page load: staggered CSS `animation-delay` or IntersectionObserver reveal
- `html { scroll-behavior: smooth; }`
- Hover states on ALL interactive elements
- Sticky nav + active-section highlight (IntersectionObserver)
- Mobile responsive: Grid/Flexbox + `clamp()` type sizing, breakpoints 768px + 480px

### Hard anti-patterns
- ❌ `#3498db` blue or `#9b59b6` purple as accent colour
- ❌ Bare unstyled `<ul><li>` bullets
- ❌ `font-family: Arial, sans-serif` as primary
- ❌ Lorem ipsum — real resume content only, zero hallucination
- ❌ Identical layout structure to any "default" two-column split

---

## Phase 4 — Output

1. Write file → `/mnt/user-data/outputs/[firstname]-portfolio.html`
2. Call `present_files`
3. Tell the user:
   - Aesthetic chosen + one-line rationale
   - Deployment options:
     - **Netlify Drop** — drag & drop at netlify.com/drop, instant URL, no account
     - **GitHub Pages** — repo named `username.github.io`, upload as `index.html`
     - **Vercel** — import GitHub repo, one-click deploy

---

## Self-review checklist

- [ ] Personality Profile written (all 8 signals filled)
- [ ] Shortlist of 3–5 aesthetics generated
- [ ] Contrast-pick rule applied — obvious choice eliminated or explicitly justified
- [ ] Design spec written in full before HTML
- [ ] Fonts from Google Fonts — no Inter/Roboto/Arial as primary
- [ ] Resume content accurate — no hallucinated details
- [ ] Hero layout is NOT the default 2-column split (unless strongly justified by aesthetic)
- [ ] One memorable signature detail present
- [ ] Mobile responsive
- [ ] All links real (mailto:, actual URLs from resume)
- [ ] File fully self-contained
