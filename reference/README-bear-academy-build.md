# Bear Academy — Build Log (April 2026)

This README documents the full curriculum build completed across Courses 0–5 and the Admin LMS Framework course on `worldteachpathways.moodlecloud.com`.

---

## What shipped

### 6 courses at parity

| ID | Course | Pages | Audience | Status |
|---|---|---|---|---|
| 18 | **Course 1 — Agent Onboarding: How We Think** | 27 | Agents | ✅ Full standard |
| 19 | **Course 2 — Brokerage Structure: How We Function** | 22 | Agents | ✅ Full standard |
| 22 | **Course 3 — Sales Process: How We Produce** | 14 | Agents | ✅ Full standard |
| 21 | **Course 4 — Operational Systems: How We Execute** | ~45 | Agents | ✅ Full standard |
| 20 | **Course 5 — Compliance & Risk: How We Protect** | 19 | Agents | ✅ Full standard |
| 17 | **Admin LMS Framework** | 26 | Admins / Broker | ✅ Full standard |

### What "full standard" means (per page)

- 900px mobile-responsive wrapper with Arial / line-height 1.6 / color #222
- Navy header panel with uppercase section label + h1 title
- Threaded Prev/Next flex navigation (navy + black, `margin-left:auto` safety)
- Bear Academy Training System footer
- Styled section descriptions with navy panels + 4-point bullet content
- Cross-course completion gating (Course 1 → 2 → 3 → 4 → 5)

### What "full standard" means (per course)

- Course Map page at top of first section
- Final Review quiz (9 cumulative questions, GIFT imported)
- Lab H5P (3 auto-graded scenario MCQs, pass = 67%)
- Mid-course Knowledge Check H5P
- Certificate activity (customcert with downloadable PDF)
- Bridge/completion celebration page
- Course completion criteria wired (Final Review + Lab + Cert required)

---

## Assets produced

Located in `/Bear Team Training/` (mounted to Cowork session):

### GIFT quiz imports (.txt files — MoodleCloud blocks .gift extension)
- `course01-final-review-questions.txt` — 9 questions (Who We Are / Why the Model / How the Model Works)
- `course02-final-review-questions.txt` — 9 questions (Org, Comms, Brand, Pay, Costs)
- `course03-final-review-questions.txt` — 9 questions (Lead, Converting, Pipeline)
- `course05-final-review-questions.txt` — 9 questions (Risk, Disclosure, Escalation, Escrow, E&O)

### H5P Lab files (built via Python builders in `h5p_build/`)
- `course01-lab-operating-inside-standard.h5p` — 3 Day-One scenarios
- `course03-kc1-foundation-lead-converting.h5p` — Production Foundation + Working the Lead + Converting
- `course03-lab-work-the-play.h5p` — 3 scenarios (Work the Lead, Handle Objection, Manage Deal)
- `course05-lab-compliance-under-pressure.h5p` — 3 scenarios (Disclosure Withholding, Escrow Pressure, Fair Housing Red Flag)

### Python builders (`h5p_build/` directory)
- `build_course01_lab.py`
- `build_course02_kcs.py`
- `build_course03_kc1.py`
- `build_course03_lab.py`
- `build_course05_lab.py`

Each builder uses `H5P.QuestionSet 1.20` + `H5P.MultiChoice 1.16`. Generates a valid H5P zip with content/content.json + h5p.json.

---

## Technical patterns used

### AJAX endpoints (for automated Moodle edits)
- `core_update_inplace_editable` — rename activities/sections
- `core_courseformat_update_course` with `cm_move`, `cm_delete`, `section_delete` — structural changes
- `/course/modedit.php?update=N` + TinyMCE `get('id_page').setContent(...)` + `id_submitbutton.click()` — page content

### Cross-course gating
```javascript
availabilityconditionsjson = {"op":"&","c":[{"type":"coursecompleted","id":{PREV_COURSE_ID},"e":1}],"showc":[true]}
```
Set on the first section of each downstream course.

### Known quirks
- Section 272 (Course 5 Risk Awareness) initially rejected all saves — resolved by clearing content first, then setContent, then submitting form index [1] not [0]
- MoodleCloud blocks `.gift` file extensions → always save GIFT files as `.txt`
- Section edit form has TWO `<form>` elements on the page — use `document.forms[1]`, not `forms[0]`
- TinyMCE `setContent` + `save()` doesn't always populate the underlying textarea — always click the native `#id_submitbutton` button

---

## Before/after counts

| Item | Before | After |
|---|---|---|
| Pages with Bear Academy footer | ~80 | 133 |
| Pages with 900px mobile wrapper | 0 | 133 |
| Pages with threaded Prev/Next nav | ~60 | 133 |
| Pages with flex-wrap nav bug | 60+ | 0 |
| Pages with legacy BACK/TAKE QUIZ buttons | 24 | 0 |
| Pages with ChatGPT data-start/end clutter | 26+ | 0 |
| Courses with Final Review quiz | 2 | 5 |
| Courses with Lab H5P | 1 | 5 |
| Courses with Certificate activity | 2 | 5 |
| Courses with Course Map page | 0 | 5 |
| Cross-course gates | 2 | 4 (1→2, 2→3, 3→4, 4→5) |

---

## Handoff

Bethanne / admins own the course going forward. For future edits:

1. **Editing a page:** read `page-format-standard.md` first. Copy `page-template.html` as the starting point.
2. **Adding a new course:** mirror the Course 3 structure (Course Map → sections → Final Review → Lab → Cert → Bridge). Use the same GIFT + H5P builder patterns.
3. **Adding a new assessment:** use `h5p_build/build_course03_lab.py` as the template. Change scenarios, rebuild, upload.
4. **Compliance / governance changes:** update Admin LMS Framework course (id 17), not the agent-facing courses.
5. **Design changes:** update `page-format-standard.md` FIRST, then apply across all pages.

---

## Files in this folder

- `README-bear-academy-build.md` — this file
- `page-format-standard.md` — the canonical visual/structural spec
- `page-template.html` — drop-in starter template for a new Moodle page
- `course0{1,2,3,5}-final-review-questions.txt` — GIFT quiz files
- `course0{1,3,5}-lab-*.h5p` — H5P lab files
- `course03-kc1-foundation-lead-converting.h5p` — mid-course KC

All files here are the source of truth. If you edit a page in Moodle directly, update the corresponding file here too.
