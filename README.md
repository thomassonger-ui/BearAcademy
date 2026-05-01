# BearAcademy

Moodle 5.1 course standards, templates, prompts, and H5P assets for **Bear Team Academy** — the training system used by agents at Bear Team Real Estate, Orlando, FL.

---

## What this repo is

This is a **standards and tooling repo** — not a content archive.

It holds the rules, templates, prompts, and H5P source files used to build and maintain Bear Academy. The live content (133+ Moodle pages across Courses 1–5) lives in the LMS at `worldteachpathways.moodlecloud.com`. A full HTML backup of those pages is planned as a future backfill.

---

## Repo Structure

```
BearAcademy/
├── README.md                    ← You are here
├── reference/                   ← Build standards, style guide, instructional design rules, audits
│   ├── page-format-standard.md  ← CANONICAL page spec (use this one)
│   ├── build-standard.md        ← Navigation standard + validation checklist
│   ├── style-guide.md           ← Color tokens and typography
│   ├── instructional-design.md  ← Tone and content rules
│   └── moodle-audit-2026-04-23.md
├── templates/                   ← Production-ready HTML templates for Moodle TinyMCE
│   ├── moodle-page-base.html
│   ├── moodle-page-with-video.html
│   └── moodle-page-with-table.html
├── prompts/                     ← AI prompts used to generate new course pages
│   └── page-generator.md
├── H5P/                         ← H5P activity specs, source files, and authoring kit
│   ├── authoring-kit/           ← Templates, examples, and upload checklist
│   ├── build-the-transaction-file/  ← Drag and Drop activity (Course 1)
│   └── who-to-contact/          ← Image Hotspots activity (Course 1)
└── courses/                     ← Reserved for future HTML page backups
```

---

## How to build a new Moodle page

1. Open `prompts/page-generator.md`
2. Fill in the four variables at the bottom (course name, lesson title, page number, topic)
3. Paste the full prompt into Claude
4. Copy the output HTML directly into the Moodle TinyMCE editor (source view)
5. Validate against the checklist in `reference/build-standard.md`

---

## Which reference document to use

| Task | Use |
|---|---|
| Building or editing a page | `reference/page-format-standard.md` — canonical spec |
| Checking nav rules and validation checklist | `reference/build-standard.md` |
| Color tokens and font rules | `reference/style-guide.md` |
| Tone and content rules | `reference/instructional-design.md` |
| Building an H5P activity | `H5P/authoring-kit/` |

> **`page-format-standard.md` is the single source of truth for page layout. If it conflicts with any other doc, it wins.**

---

## Non-Negotiables

- **Inline CSS only.** Moodle TinyMCE strips `<style>` blocks.
- **No external JS.** Pages must render in a sandboxed Moodle iframe.
- **Execution over theory.** Every page answers "what does the agent DO after this?"
- **Mobile responsive** — max-width `900px` wrapper with `padding: 0 16px`.
- **Navigation:** PREVIOUS = solid navy `#1B365D`. NEXT = solid black `#000000`. No outlined buttons.

---

## Brand

- **Brokerage:** Bear Team Real Estate, Orlando FL
- **Broker/Owner:** Bethanne Baer
- **LMS:** Moodle 5.1 on MoodleCloud
- **Primary color:** `#1B365D`
- **Copyright:** WorldTeachPathways 2026

---

## Maintainer

Tom Songer — Team Lead, Bear Team Real Estate
