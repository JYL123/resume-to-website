# resume-to-website

**A Claude skill that turns your resume into a unique, deployable portfolio website — in one conversation.**

Upload your resume. Get back a beautiful, self-contained HTML file you can deploy for free in under two minutes. No templates. No two sites look alike.

---

## What it does

Most "resume to website" tools apply the same template to everyone. This skill reads your resume differently — it extracts not just your job history, but your **personality**: your writing tone, hobbies, career arc, cultural background, and the specific energy you bring to your work. Then it picks a visual aesthetic that fits *you*, not your job title.

Two software engineers will get two completely different sites.

### Sample outputs

| Person | Field | Aesthetic chosen | Why |
|---|---|---|---|
| Kai Nakamura | Systems / compiler engineer | `warm-paper` editorial | Philosophy reader, quiet precise writing, academic-to-industry arc — not the expected terminal-noir |
| Priya Mehta | Full-stack startup engineer | `risograph` zine | Music producer, high-energy verbs, startup scrappy — bold and expressive |
| Sofia Reyes | Brand strategist | `art-deco` | Ceramics hobby, luxury client work, Barcelona roots — geometric grandeur |
| Jamie Park | UX researcher | `soft-pastel` editorial | Film photography, journaling, warm empathetic tone — light and human |

---

## Install on Claude

### Requirements
- A Claude account (Free, Pro, or higher)
- **Code Execution** enabled in settings

### Enable Code Execution
1. Go to **claude.ai** → profile icon → **Settings**
2. Open **Features** (or **Capabilities**)
3. Toggle **Code execution and file creation** → ON

### Install the skill
1. Download **`resume-to-website-v2.skill`** from this repository
2. In Claude, go to **Settings → Features → Skills**
3. Click the **+** button and upload the `.skill` file
4. Toggle the skill **ON**

That's it. The skill activates automatically whenever you mention converting a resume.

> **Note:** The `.skill` file is a zip archive. Do not unzip it before uploading — Claude reads it as-is.

---

## How to use it

Start a new chat and do one of the following:

### Option A — Upload your resume file
Attach your resume (PDF or DOCX) and say:

```
Turn my resume into a website.
```

### Option B — Paste plain text
Paste your resume text directly into the chat and say:

```
Make a portfolio site from this.
```

### Option C — Natural phrasing
The skill recognises many phrasings. Any of these will trigger it:

```
Convert my CV into a website
Build a personal portfolio from my resume
Make a site I can share with recruiters
Create a personal page from my resume
```

### What you get back
- A **single `.html` file** — fully self-contained, no dependencies
- Claude tells you which **aesthetic was chosen** and why
- **Three free deployment options** with step-by-step instructions

---

## How it works

The skill runs in four phases:

### Phase 1 — Extract

Claude reads your resume and pulls two layers of information:

**Structured content**
Your name, contact info, work history, education, skills, projects, and awards — everything that goes into a traditional CV.

**Personality signals** — this is what drives uniqueness

Claude reads your resume as a whole person, extracting:

| Signal | Examples |
|---|---|
| Tone & voice | Clinical and precise vs. warm and conversational vs. punchy and confident |
| Energy level | High-action verbs ("launched", "led", "drove") vs. quieter verbs ("supported", "contributed") |
| Creative indicators | Side projects, open-source work, art, music, writing, unusual hobbies |
| Cultural texture | International background, multilingual, non-linear career path |
| Company culture | FAANG/enterprise (polished) vs. startup (scrappy) vs. academia (methodical) |
| Hobbies & interests | Sports → bold/kinetic. Music → rhythmic/editorial. Nature → organic/earthy |
| Career arc shape | Linear climb vs. pivot story vs. portfolio career |
| Writing style | Jargon density, bullet length, passive vs. active voice |

These signals are combined into a **Personality Profile** before any design decisions are made.

---

### Phase 2 — Design

Claude selects an aesthetic from a palette of **24 directions**:

**Dark themes** — `terminal-noir`, `midnight-editorial`, `brutalist-dark`, `cosmic`, `neon-night`, `obsidian-luxury`

**Light themes** — `swiss-editorial`, `warm-paper`, `luxury-serif`, `scandinavian-minimal`, `soft-pastel`, `code-minimal`

**Bold / expressive** — `brutalist-light`, `maximalist-editorial`, `art-deco`, `kinetic`, `bauhaus`, `retro-futurist`

**Organic / character** — `hand-crafted`, `academic-ink`, `earthy-organic`, `blueprint`, `dashboard`, `risograph`

**The contrast-pick rule** prevents sameness: Claude first identifies the *obvious* aesthetic for your field (e.g. "software engineer → terminal-noir"), then eliminates it from contention. The final choice is made from the remaining candidates based on personality signals — not your job title.

Before writing any HTML, Claude writes a full **design spec**:
- Display font + body font (always from Google Fonts — never Arial, Inter, or Roboto)
- Full colour palette as CSS variables
- Hero layout shape, section rhythm, nav style
- One **signature detail** — a visual element specific to this site

---

### Phase 3 — Build

Claude generates a **single self-contained HTML file** with all CSS and JS inline. The only external call is Google Fonts.

Every site includes:
- **Sticky navigation** with active-section highlighting
- **Staggered load animations** (CSS keyframes or IntersectionObserver)
- **Hover states** on all interactive elements
- **Smooth scroll** between sections
- **Mobile responsive** layout (tested at 375px, 768px, 1100px)
- **Semantic HTML** with proper meta tags and description

Sections generated: Hero · About · Experience · Skills · Education · Projects *(if present)* · Contact

---

### Phase 4 — Output

Claude saves the file and presents it for download, then explains how to deploy it:

| Platform | Cost | Time | Notes |
|---|---|---|---|
| **Netlify Drop** | Free | 30 seconds | Drag-and-drop, no account needed |
| **GitHub Pages** | Free | 5 minutes | Free `username.github.io` subdomain |
| **Vercel** | Free | 2 minutes | Import GitHub repo, auto-deploys on update |

---

## Who is this for

**Job seekers** who want a personal site but don't have time to build one from scratch.

**Students** applying for internships or their first role who need a professional online presence.

**Freelancers** who want a portfolio they can share with clients instead of attaching a PDF.

**Career changers** whose resume tells a pivot story that a conventional CV format doesn't do justice.

**Anyone** who has a resume and wants a link they're proud to put in their email signature.

---

## Supported resume formats

| Format | Support |
|---|---|
| PDF | ✅ Full support |
| Word (.docx) | ✅ Full support |
| Plain text | ✅ Paste directly into chat |
| Google Docs | ✅ Export as PDF or paste text |
| LinkedIn PDF export | ✅ Works well |

---

## Frequently asked questions

**Will my site look the same as someone else's?**
No. The contrast-pick rule actively prevents field-based sameness. Two people in the same job will almost always get different aesthetics because the decision is driven by personality signals, not job title.

**Can I ask for a specific style?**
Yes. You can say things like "make it dark and minimal" or "I want something warm and editorial" and Claude will factor that into the aesthetic decision.

**What if I don't have projects or awards?**
Those sections are only generated if your resume contains them. The skill adapts to whatever content you have.

**Can I edit the output?**
Absolutely. The HTML file is clean and readable. All colours are defined as CSS variables at the top — change `--accent` and the whole site updates. Fonts are a single Google Fonts import line.

**Is the deployment really free?**
Yes. Netlify Drop requires no account and no payment. GitHub Pages and Vercel both have permanent free tiers. You only pay if you want a custom domain (~$12/year from any registrar).

**Does it work on the Claude free plan?**
Yes — as long as Code Execution is enabled in settings.

---

## Files in this repository

```
resume-to-website-v2.skill   ← Install this in Claude
SKILL.md                     ← The skill instructions (readable reference)
samples/
  kai-portfolio.html         ← warm-paper · Systems engineer
  priya-portfolio.html       ← risograph · Full-stack engineer
  sofia-portfolio.html       ← art-deco · Brand strategist
  jamie-portfolio.html       ← soft-pastel · UX researcher
README.md                    ← This file
```

---

## Deploying to Vercel (quick reference)

1. Rename your file to `index.html`
2. Create a GitHub repo and upload it
3. Go to [vercel.com](https://vercel.com) → **Add New → Project**
4. Import the repo → **Deploy**
5. Live at `your-repo-name.vercel.app`

Every future edit to `index.html` on GitHub triggers an automatic redeploy.

---

## Contributing

Found an aesthetic direction that's missing? A resume format that doesn't parse well? Open an issue or submit a pull request to `SKILL.md`. The skill is plain Markdown — readable and editable by anyone.

---

*Built with Claude · Deployable anywhere · Free forever*
