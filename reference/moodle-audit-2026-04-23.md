# Moodle LMS Audit — 2026-04-23

Read-only audit of the live **World Teach Pathways** Moodle instance hosting Bear Academy. No changes made during this audit. This document is a snapshot of the current state as of April 23, 2026 and should be treated as reference context for future course-building work.

- **Site:** https://worldteachpathways.moodlecloud.com
- **Reviewer:** Tom Songer
- **Audit date:** 2026-04-23

---

## Courses in Production (7 total)

6 curriculum courses + 1 admin framework. All courses starred by Tom.

| # | ID | Title                                       | Sections | Activities (approx) |
|---|----|---------------------------------------------|----------|---------------------|
| 0 | 8  | Starting with Moodle                        | 5        | 10 pages + 1 forum  |
| 1 | 18 | Agent Onboarding — How We Think             | 5        | ~30 pages, 1 forum, 1 glossary, 1 quiz, 3 H5P, 1 cert |
| 2 | 19 | Brokerage Structure — How We Function       | 8        | ~22 pages, 1 forum, 1 cert |
| 3 | 22 | Sales Process — How We Produce              | 7        | ~12 pages, 1 forum, 1 H5P, 1 resource, 1 cert |
| 4 | 21 | Operational Systems — How We Execute        | 11       | ~50 pages, 2 checklists, 1 quiz, 5 subsections |
| 5 | 20 | Compliance & Risk — How We Protect          | 7        | ~18 pages, 1 forum, 1 quiz |
| — | 17 | Admin LMS Framework                         | (admin)  | —                   |

Course 0 shows 100% complete for Tom. Progress bars for other courses weren't rendered on the My Courses view at capture time.

---

## Naming & Taxonomy (established convention)

- **Numeric prefix `0–5`** creates a fixed learning sequence
- **Subtitle pattern** is *"How We [verb]"* — Think / Function / Produce / Execute / Protect. Each maps to a brokerage pillar.
- Every page module ends in the word `Page` (e.g. "Start Here Page", "Welcome Page"). Redundant in UI, but consistent and searchable.
- Every course starts with an orientation section (Start Here / Who We Are) plus an Announcements forum.
- Every course ends with a `Completion` or `FINAL KNOWLEDGE CHECK` section.

---

## Section Spine (repeats across all courses)

1. Orientation (Start Here / Announcements)
2. Foundation or Framework panels (Why / How / What)
3. Execution content (numbered modules or themed sections)
4. Resources / Checklists (dedicated section)
5. Knowledge Check (quiz or H5P)
6. Completion (custom certificate module)

Course 4 (Operational Systems) is the heaviest — 11 sections, ~50 pages, includes a 26-activity "AI Playbook" sub-area. Only course using the `subsection` module type.

---

## Activity Types in Use

| Type           | Count (approx) | Where it appears                                        |
|----------------|----------------|---------------------------------------------------------|
| `page`         | ~140+          | Primary delivery vehicle for every course               |
| `forum`        | 5              | One "Announcements" per course                          |
| `quiz`         | 3              | Governance acknowledgment + final knowledge checks      |
| `h5pactivity`  | 4              | Interactive exercises in courses 1 and 3                |
| `glossary`     | 1              | "Bear Team Operating Vocabulary" in course 1 only       |
| `checklist`    | 2              | Course 4 playbook + final checklist                     |
| `customcert`   | 3+             | Completion certificates                                 |
| `resource`     | 3              | File downloads (likely PDFs)                            |
| `subsection`   | 6              | Only course 4 uses these                                |

**Tendency:** heavily page-dominant. Quizzes and H5P are underused relative to page count.

---

## Page-Level Style (sampled 2 pages across 2 courses)

Both sampled lesson pages use the exact Bear Academy build standard wrapper:

```
max-width: 1000px; margin: auto;
font-family: Arial, Helvetica, sans-serif;
line-height: 1.6; color: #222;
```

Confirmed on both pages:

- Inline-styled wrapper div; no `<style>` tags inside content
- Navy `#1B365D` header bar
- Light gray `#f4f4f4` lesson strip
- `border-left: 4px solid #1B365D` content panels
- Tables present
- One page included an iframe (video block)
- ~9–11 inline-styled `<div>`s per page — matches the 9-section structural spec

**Pages sampled:**
- `mod/page/view.php?id=773` — "Risk in Real Estate Transactions" (course 5)
- `mod/page/view.php?id=749` — "Brokerage Vision & Structure" (course 1)

**Verdict:** the Bear Academy Moodle Build Standard is already in production. Every lesson sampled follows the same template pattern the `page-generator.md` prompt enforces. The repo templates and the live pages are aligned.

---

## Observations Worth Flagging

1. **Style system is already in production.** Sampled pages match the build standard in this repo. Templates are in sync with live pages.
2. **Course 4 is an outlier in weight.** 11 sections, ~50 pages, subsections. Worth deciding whether to keep as one course or split.
3. **Minimal interactive assessment.** Heavy page delivery, light quiz/H5P. If retention matters, more knowledge checks per section could help.
4. **Consistent completion mechanics.** Every course terminates in a certificate — good for agent accountability.
5. **"Page" suffix on every module name.** Consider dropping ("Start Here" vs "Start Here Page") — UI already labels the type.
6. **Announcements forum is duplicated per course.** Agents subscribed to all will get 6 separate notification streams. Site-level announcement channel may be cleaner.
7. **Glossary only lives in course 1.** Operating vocabulary is defined once but referenced across all courses. Could be elevated to a site-level glossary.

---

## How to Refresh This Audit

Next time you need a snapshot, pull from these endpoints (read-only, authenticated session in Claude in Chrome):

- My Courses: `https://worldteachpathways.moodlecloud.com/my/courses.php`
- Course view: `https://worldteachpathways.moodlecloud.com/course/view.php?id={courseId}`
- Page view:   `https://worldteachpathways.moodlecloud.com/mod/page/view.php?id={cmid}`

Section + activity structure is readable via DOM:

```js
Array.from(document.querySelectorAll('.course-content li.section'))
  .map(s => ({
    title: s.querySelector('.sectionname, h3')?.textContent?.trim(),
    activities: Array.from(s.querySelectorAll('.activity')).map(a => ({
      name: a.querySelector('.instancename')?.textContent?.trim(),
      type: Array.from(a.classList).find(c => c.startsWith('modtype_'))?.replace('modtype_','')
    }))
  }));
```

Page-level style markers to check:

- `#region-main div[style*="max-width"]` — the branded wrapper
- `[style*="1B365D"]` — navy hits (header bar, panel borders)
- `[style*="border-left"][style*="1B365D"]` — content panels
- `[style*="#f4f4f4"]` — lesson strip
