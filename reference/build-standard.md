# Bear Academy Moodle Build Standard

This is the canonical build standard for every page published to Bear Team Academy in Moodle 5.1. All templates in `/templates` and the AI prompt in `/prompts/page-generator.md` derive from this document. If something here changes, those files change too.

---

## Platform Rules (Non-Negotiable)

- **Inline CSS only.** No `<style>` tags.
- **No external CSS or JavaScript.**
- Must render correctly inside the **Moodle TinyMCE editor**.
- Must be **mobile-responsive** using simple HTML structure only — see **Mobile Standard** below. Every page must fit a 360 px phone screen with zero horizontal scrolling. No exceptions.

---

## Global Layout Wrapper

Every page MUST begin with this container:

```html
<div style="max-width: 1000px; margin: auto; font-family: Arial, Helvetica, sans-serif; line-height: 1.6; color: #222;">
```

And close with `</div>` at the very end of the page.

---

## Required Page Structure (Order is Fixed)

1. **Header Bar**
   - Background: `#1B365D`
   - White text
   - Title: `Bear Team Academy`
   - Subtitle: Course + Section

2. **Lesson Strip**
   - Light gray background: `#f4f4f4`
   - Displays lesson title + page number

3. **Main Content Container**
   - White background
   - Border: `#d9d9d9`
   - Padding: `clamp(12px, 4vw, 24px)` (24 px on desktop, 12 px on phones)
   - `overflow-wrap: anywhere` so filenames and URLs can never push the page wide

4. **Content Panels** (use multiple)
   - Background: `#f7f9fc`
   - Left border: `4px solid #1B365D`
   - Padding: `clamp(10px, 3vw, 16px)` (16 px on desktop, 10 px on phones)

5. **Structured Panel** *(optional — for tables or structured breakdowns)*
   - Background: `#f4f7fb`
   - Full border
   - Used for tables or structured breakdowns

6. **Video Block** *(optional)*
   - Responsive iframe wrapper (16:9 ratio)

7. **Closing Panel**
   - Reinforces execution, system, or outcome

8. **Footer**
   - Center aligned, small text
   - Required lines:
     - Bear Academy Training System
     - Powered by Moodle LMS
     - Last updated date
     - Copyright WorldTeachPathways 2026

9. **Navigation Row** *(see Navigation Standard below)*

---

## Navigation Standard (NEW — enforced April 2026)

Every activity in every course MUST end with a single navigation row matching this rule.

### The Two-Button Rule

**One row. Two buttons. No exceptions.**

| Position | Button | Background | Text color | Default label |
|---|---|---|---|---|
| LEFT | PREVIOUS | `#1B365D` (navy, solid) | `#FFFFFF` | `← PREVIOUS` |
| RIGHT | NEXT (or custom) | `#000000` (black, solid) | `#FFFFFF` | `NEXT →` |

Both buttons use **identical sizing, padding, and typography** — only the background color differs. The PREVIOUS button is always navy. The NEXT button (or its custom-labeled replacement) is always black.

### Required Button Styling

Both buttons MUST use this inline style template:

```
color: #FFFFFF;
padding: 12px 24px;
text-decoration: none;
border-radius: 4px;
font-size: 16px;
font-weight: bold;
display: inline-block;
```

PREVIOUS adds `background: #1B365D;`
NEXT adds `background: #000000;`

### Required Row Container

The navigation row MUST use this flex container:

```
display: flex;
justify-content: space-between;
align-items: center;
gap: 16px;
flex-wrap: wrap;
margin-top: 24px;
```

### Custom Labeled Buttons

When the next activity is a quiz, lab, simulation, certificate, or course transition, the NEXT button SHOULD be replaced with a labeled custom button — not added in addition.

| Destination | Custom NEXT label |
|---|---|
| Quiz | `TAKE QUIZ →` |
| Lab / Simulation | `START LAB →` or `START SIMULATION →` |
| Certificate | `GET CERTIFICATE →` |
| Next course | `GO TO COURSE 2 →` |
| Topic-specific page | e.g. `WHY STRUCTURE MATTERS →` |

The custom button **replaces** the generic `NEXT →` — never sit next to it. Two right-side buttons is a bug.

### First-Page Rule

On the **first page of a course or section**, omit the PREVIOUS button entirely. Do not show a grayed-out or disabled pill. The NEXT (or custom) button alone, right-aligned, is correct. To right-align a single button, change the row's `justify-content` to `flex-end`.

### Last-Page Rule

The last activity in a course (typically the Acknowledgment / Next Steps page) uses a custom NEXT button labeled with the destination, e.g. `GO TO COURSE 2 →`. PREVIOUS may be a labeled pointer back, e.g. `← PREVIOUS: Certificate`.

### Activity-Type Coverage

The two-button rule applies to **every activity type that an agent navigates through**, including:

- Page (`mod/page`)
- Forum (`mod/forum`) — buttons live in the forum description
- Glossary (`mod/glossary`) — buttons live in the glossary description
- Quiz (`mod/quiz`) — buttons live in the quiz description (the activity intro)
- H5P (`mod/h5pactivity`) — buttons live in the H5P activity description
- Custom Certificate (`mod/customcert`) — buttons live in the certificate description

Activities without a description editor (rare) are exempt only if the user cannot land on them as an activity page.

### Anti-Patterns (forbidden)

- ❌ Three or more navigation buttons in one row
- ❌ A standalone custom labeled button **above or below** the generic PREV/NEXT pair
- ❌ Two NEXT-style buttons in the same row (e.g. `NEXT →` plus `NEXT PAGE →`)
- ❌ Disabled gray "← First Page" pill on the first page (use the First-Page Rule instead)
- ❌ Outlined / ghost-style PREVIOUS buttons (PREVIOUS is solid navy)
- ❌ `«` / `»` arrows (use Unicode `←` / `→` for consistency with the live system)

### Audit Reference

A full pre-fix audit of Course 1 navigation issues (including the duplicate-button bug on cm 793 Structured Library, cm 755 Compliance & Risk, and cm 978 Acknowledgment & Next Steps) is documented in `reference/course-1-nav-audit-2026-04.md` (if archived) and corresponds to the navigation standard codified above.

---

## Table Standard

If a table is used:

- Header background: `#1B365D`
- Header text: white
- Alternating row colors: `#f7f9fc` / `#ffffff`
- Border color: `#d9d9d9`
- **Maximum 3 columns.** A 4th column must be merged into another (e.g. a step number becomes "1. " at the start of the next cell; a short reference becomes a second line in the first cell).
- Every table is wrapped and styled exactly like this:

```html
<div style="max-width: 100%; overflow-x: auto;">
  <table style="width: 100%; border-collapse: collapse; font-size: clamp(12px, 3.6vw, 14px); overflow-wrap: anywhere;">
    <tr style="background: #1B365D; color: #ffffff;">
      <th style="padding: clamp(5px, 1.6vw, 8px); text-align: left; border: 1px solid #d9d9d9;">Column</th>
    </tr>
    <tr style="background: #f7f9fc;">
      <td style="padding: clamp(5px, 1.6vw, 8px); border: 1px solid #d9d9d9; vertical-align: top;">Cell</td>
    </tr>
  </table>
</div>
```

- Never set a pixel `width` on a cell, never use `white-space: nowrap`, never set `min-width`.

---

## Mobile Standard (enforced August 2026)

**Every page must fit inside a phone screen — 360 px Android and 375/390 px iPhone — with no horizontal scrolling. No exceptions.**

Why this exists: an August 2026 audit found 53 of 129 pages in Courses 1–5 (and every table page in Course 6) spilling off the right edge of a phone. Every failure was a 3–5 column table inside 24 px + 16 px of side padding, which leaves only ~280 px of content width on a 360 px screen.

Rules (all inline CSS — no `<style>`, no media queries needed):

1. **Side padding scales with the screen** using `clamp(min, vw, max)`. Desktop keeps the max value; phones get the min. Header `padding: clamp(14px, 4vw, 20px) clamp(12px, 4vw, 24px)`; lesson strip and footer `padding: 12px clamp(12px, 4vw, 24px)` / `16px clamp(12px, 4vw, 24px)`; main container `clamp(12px, 4vw, 24px)`; panels `clamp(10px, 3vw, 16px)`.
2. **Tables** follow the Table Standard above: max 3 columns, `clamp()` font and cell padding, `overflow-wrap: anywhere`, wrapped in a `max-width: 100%; overflow-x: auto` div.
3. **Main content container** carries `overflow-wrap: anywhere` so long filenames, URLs and email addresses break instead of forcing width.
4. **Images**: `max-width: 100%; height: auto; display: block;` — never a pixel width.
5. **Videos**: the 16:9 responsive wrapper (`position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;` with an absolutely positioned 100%×100% iframe).
6. **Navigation row** keeps `flex-wrap: wrap` so PREVIOUS / NEXT stack on narrow screens.
7. **Never** use fixed pixel widths ≥ 300 px, `white-space: nowrap`, `min-width`, floats wider than 50%, or multi-column CSS grids without `auto-fit`/`minmax`.

Verification (required before publishing): open the page in a 360 px wide frame or Chrome DevTools device mode. No element may extend past the right edge, and no table may need its own horizontal scroll. Claude can run this check across a whole course in about 10 minutes — see `reference/moodle-audit-2026-08-25.md` for the method.

---

## Validation Checklist (Before Publishing)

- [ ] Page opens with the global wrapper `<div>`
- [ ] All nine structural sections present and in correct order
- [ ] Only inline CSS — no `<style>` tags, no external links
- [ ] Header bar uses `#1B365D` + white text
- [ ] Content panels use `#f7f9fc` background + `4px solid #1B365D` left border
- [ ] Footer contains all four required lines
- [ ] **Navigation row has exactly two buttons** — PREVIOUS (navy `#1B365D`) on left, NEXT or custom labeled button (black `#000000`) on right
- [ ] No standalone "WHY X →" / "GO TO Y →" / labeled button outside the nav row
- [ ] Custom labeled NEXT replaces (does not duplicate) the generic NEXT
- [ ] First page of a course/section omits PREVIOUS (does not show a grayed pill)
- [ ] Arrow characters are `←` and `→` (not `«` / `»`)
- [ ] Page renders correctly in TinyMCE preview
- [ ] Page fits a 360 px phone with zero horizontal scrolling (Mobile Standard) — tables ≤ 3 columns, `clamp()` padding, `overflow-wrap: anywhere`

If anything is missing → fix it before publishing.
