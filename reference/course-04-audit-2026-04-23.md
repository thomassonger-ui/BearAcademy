# Course 4 Audit — "Operational Systems — How We Execute"

Read-only deep audit of course `id=21` on the live Moodle LMS, with a concrete plan to keep it as a single course. No changes made.

- **Site:** https://worldteachpathways.moodlecloud.com/course/view.php?id=21
- **Reviewer:** Tom Songer
- **Audit date:** 2026-04-23
- **Supersedes:** general note in `reference/moodle-audit-2026-04-23.md` flagging course 4 as an outlier

---

## Headline finding

**Course 4 isn't ~50 pages. It's ~32 unique activities with heavy duplication.**

The "weight" problem is phantom. Sections 4–8 are flat mirrors of the subsections already nested inside Section 3 (AI Playbook). The same AI content is displayed twice in two different navigation shapes. Fix the structure and the size problem disappears.

---

## Full content inventory (as of 2026-04-23)

### Sections 0–2 — Operational Base (8 activities)

| # | Section | Pages |
|---|---------|-------|
| 0 | CRM as Infrastructure | Start Here · Announcements Forum · CRM Is Operational Infrastructure · Visibility Creates Stability |
| 1 | Defined Transaction Workflow | Transaction Stage Discipline · Workflow Integrity |
| 2 | System Accountability | Performance Tracking · Reporting & Review |

### Section 3 — AI Playbook (26 items, but with 5 subsection wrappers)

Subsection groups nested inside:

1. **Introduction to the AI Playbook** — 9 pages (Intro, Lead Gen, Listing Marketing, Client Communication, Responsible AI Use, AI Workflow, AI Productivity Model, AI-Powered Daily Workflow, Next: Course 5 handoff)
2. **AI Knowledge Check** — 3 pages (Knowledge Check, Section Summary + Reflection, Your First AI Automation)
3. **AI-Enabled Agent vs Traditional Agent** — 4 pages (Comparison, Workflow Framework, Simulation Activity, 10-Minute Listing Challenge)
4. **AI Agents To Use In Your Real Estate Business** — 4 pages (Intro, Top 3 AI Agents, AI Stack, 5 Unexpected Trends)
5. **AI Checklist** — 1 checklist

Subsection wrappers count as "activities" in Moodle's counter, so the real unique content here is ~20 pages + 1 checklist, not 26.

### Sections 4–8 — AI content duplicated at the top level

| # | Section | Pages | Duplicates |
|---|---------|-------|------------|
| 4 | LEARNING TOPICS | 9 | Same pages as AI Playbook → Introduction subsection |
| 5 | KNOWLEDGE CHECK | 3 | Same pages as AI Playbook → AI Knowledge Check subsection |
| 6 | VISUAL FRAMEWORK & ACTIVITIES | 4 | Same pages as AI Playbook → AI-Enabled Agent subsection |
| 7 | RESOURCES | 4 | Same pages as AI Playbook → AI Agents To Use subsection |
| 8 | CHECKLIST | 1 | Same AI Checklist |

### Sections 9–10 — Closers

| # | Section | Pages |
|---|---------|-------|
| 9 | FINAL KNOWLEDGE CHECK | True or False Quiz |
| 10 | Payment Timeline | When You Get Paid — The Disbursement Process · What Delays Your Payment · Reading Your Commission Statement |

---

## Cohesion analysis

Three genuinely distinct modules hide inside one course:

| Module | Activities (unique) | Theme |
|--------|---------------------|-------|
| A — Operational Systems | 8 | CRM + workflow + accountability (the actual "how we execute" spine) |
| B — AI Playbook | ~20 | AI as an execution tool |
| C — Payment Timeline | 3 | Commission disbursement |

Module B dominates at ~75% of real content. The course title "How We Execute" covers all three, but the balance is lopsided.

**Payment Timeline placement is contested.** Course 2 (Brokerage Structure) already has a "How We Get Paid" section that could be a more natural home. Moodle's own section summary argues the opposite — keep it in Course 4 because payment *flow* is procedural, distinct from payment *economics*. Decision left to Tom.

---

## Plan to keep this as ONE course

### Priority 1 — Remove the duplication (highest leverage)

Decide one structure, not two. Right now AI content exists in both a subsectioned view (Section 3) and a flat view (Sections 4–8). Pick one.

- **Recommended:** keep Section 3 (AI Playbook with subsections), **delete Sections 4–8** as top-level sections. The subsection structure already does the organizing. This alone drops the course from 11 sections to 6 and eliminates ~20 "activities" from the count.
- **Alternative:** delete the subsections in Section 3 and keep the flat top-level grouping. Only do this if subsections aren't rendering well for agents on mobile.

### Priority 2 — Rebalance the spine

After dedup, the section list becomes:

```
0. Start Here + Announcements
1. CRM as Infrastructure
2. Transaction Workflow
3. System Accountability
4. AI Playbook (subsectioned)
5. Payment Timeline
6. Final Knowledge Check + Completion
```

Seven sections, ~32 unique activities. That's a normal Moodle course — Courses 2 and 5 in the Bear Academy catalog sit in the same size range.

### Priority 3 — Add a top-level "Course Map" panel

Because the course covers three distinct topics (CRM, AI, Payment), put a single "How This Course Is Organized" page as the first activity in Start Here. Three bullets:

- Part 1: Operational systems — CRM, workflow, accountability
- Part 2: AI Playbook — tools you use daily
- Part 3: Payment Timeline — how you get paid when the system works

This signals to the agent that the course covers three things on purpose, not by accident.

### Priority 4 — Decide on Payment Timeline (optional)

- **Keep here:** rename Section 5 to "Commission & Payment Execution" — frames it as *operational* payment discipline, distinct from the brokerage-structure "How We Get Paid" in Course 2 (which is the *economics* of payment).
- **Move to Course 2:** merges cleanly under the existing "How We Get Paid" section. Reduces Course 4 weight further.

### Priority 5 — Completion tracking

Because subsections nest activities, completion rules can get confused. After dedup, set each subsection to "completed when all children complete" and set the course completion to require: Final Knowledge Check passed + AI Checklist complete + Payment Timeline pages viewed. This gives a clean certificate trigger.

### Priority 6 — Name hygiene

- Drop the trailing "Page" from every module name (applies across all courses — fastest win is a site-wide find/replace).
- The duplicate page names are confusing when the subsection and its first nested page both read "Introduction to the AI Playbook Page" — rename each subsection to just the short label (e.g. "Introduction", "AI Knowledge Check", "Resources").

---

## Before / after

|  | Before | After cleanup |
|---|--------|---------------|
| Sections | 11 | 6 or 7 |
| Activities counted | ~50 | ~32 |
| Unique content items | ~32 | ~32 |
| Cognitive shape | "Which view is canonical?" | Three clear parts |

**Verdict:** keep as one course. The weight is phantom. Dedup the AI content, add a course map, make a call on Payment Timeline — and Course 4 sits comfortably in the existing 0–5 sequence.

---

## Refresh this audit

Re-run with Claude in Chrome on `course/view.php?id=21`. The DOM snippets at the bottom of `reference/moodle-audit-2026-04-23.md` work for this course too. Specifically useful for this audit:

```js
// Enumerate a single section including nested subsection activities
const section = document.querySelectorAll('.course-content li.section')[3]; // AI Playbook
Array.from(section.querySelectorAll('.activity')).map(a => ({
  name: a.querySelector('.instancename')?.textContent?.trim(),
  type: Array.from(a.classList).find(c => c.startsWith('modtype_'))?.replace('modtype_','')
}));
```
