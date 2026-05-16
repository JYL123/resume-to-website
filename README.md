

# resume-to-website

**A Claude skill that turns your resume into a unique, deployable portfolio website — in one conversation.**

Upload your resume. Get back a beautiful, self-contained HTML file you can deploy for free in under two minutes. No templates. No two sites look alike.

---

## 🌐 Live Demo

https://sample-resume-website.vercel.app/

https://github.com/user-attachments/assets/21a6beaf-bbba-4bfe-bfa5-253ac01feac2

---


## Who is this for

**Job seekers** who want a personal site but don't have time to build one from scratch.

**Students** applying for internships or their first role who need a professional online presence.

**Freelancers** who want a portfolio they can share with clients instead of attaching a PDF.

**Career changers** whose resume tells a pivot story that a conventional CV format doesn't do justice.

**Anyone** who has a resume and wants a link they're proud to put in their email signature.

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

## Supported resume formats

| Format | Support |
|---|---|
| PDF | ✅ Full support |
| Word (.docx) | ✅ Full support |
| Plain text | ✅ Paste directly into chat |
| Google Docs | ✅ Export as PDF or paste text |
| LinkedIn PDF export | ✅ Works well |

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
