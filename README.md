# BearAcademy

Moodle 5.1 course content for **Bear Team Academy** — the training system used by agents at Bear Team Real Estate, Orlando, FL.

This repo is the source of truth for every Moodle page, template, build standard, and AI prompt we use to produce course content. Every page in Moodle is generated from these templates so the look, structure, and instructional tone stay consistent.

---

## Repo Structure

```
BearAcademy/
├── README.md                    ← You are here
├── reference/                   ← Build standards, style guide, instructional design rules
│   ├── build-standard.md
│   ├── style-guide.md
│   └── instructional-design.md
├── templates/                   ← Production-ready HTML templates for Moodle TinyMCE
│   ├── README.md
│   ├── moodle-page-base.html
│   ├── moodle-page-with-video.html
│   └── moodle-page-with-table.html
├── prompts/                     ← AI prompts used to generate new course pages
│   ├── README.md
│   └── page-generator.md
└── courses/                     ← Finished course pages, organized by course
    └── README.md
```

---

## How to Use This Repo

**Generating a new Moodle page**
1. Open `prompts/page-generator.md`
2. Fill in the four variables at the bottom (course name, lesson title, page number, topic)
3. Paste the full prompt into Claude or ChatGPT
4. Copy the output HTML directly into the Moodle TinyMCE editor

**Editing the build standard**
- All structural and styling rules live in `reference/build-standard.md`
- Update the standard there first, then update `prompts/page-generator.md` so the AI output stays in sync

**Adding a new template**
- Start from `templates/moodle-page-base.html`
- Keep inline CSS only — no `<style>` tags, no external stylesheets
- Add a short README entry in `templates/README.md`

---

## Non-Negotiables

- **Inline CSS only.** Moodle TinyMCE strips `<style>` blocks.
- **No external JS.** Pages must render in a sandboxed Moodle iframe.
- **Execution over theory.** Every page answers "what does the agent DO after this?"
- **Mobile responsive** via simple HTML — no frameworks.

---

## Brand + Platform

- **Brokerage:** Bear Team Real Estate (Orlando, FL)
- **Broker/Owner:** Bethanne Baer
- **LMS:** Moodle 5.1
- **Primary color:** `#1B365D` (deep navy)
- **Copyright:** WorldTeachPathways 2026

---

## Maintainer

Tom Songer — Team Lead, Bear Team Real Estate
