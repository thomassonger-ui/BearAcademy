# Bear Academy — Page Format Standard

**Version:** 1.0 · **Last updated:** April 2026 · **Applies to:** All Moodle pages across Courses 1–5 + Admin LMS Framework

This is the canonical visual and structural specification for every `mod_page` activity in Bear Academy. Every page in the curriculum must match this format exactly.

---

## 1. Outer wrapper (required on every page)

```html
<div style="max-width: 900px; margin: auto; padding: 0 16px; font-family: Arial, Helvetica, sans-serif; line-height: 1.6; color: #222;">
  <!-- page content here -->
</div>
```

- `max-width: 900px` — readable line length; mobile breakpoint handled by `padding: 0 16px`
- `font-family: Arial` — reliable cross-device render
- `color: #222` — softer than pure black, reduces eye fatigue
- Do **not** use `flex-wrap: wrap` on nav rows — it causes buttons to clump on narrow viewports

---

## 2. Navy header panel (required at top)

```html
<div style="background:#1B365D; color:#fff; padding:20px 24px; border-radius:6px; margin-bottom:20px;">
  <div style="font-size:clamp(13px,2.2vw,14px); opacity:.85; letter-spacing:1px; font-weight:600; text-transform:uppercase;">
    {SECTION LABEL}
  </div>
  <h1 style="font-size:clamp(22px,4vw,28px); margin:6px 0 0; color:#fff;">
    {PAGE TITLE}
  </h1>
</div>
```

- `#1B365D` — Bear Team navy, the brand primary
- `clamp()` sizing — scales from mobile to desktop without breakpoint rules
- Section label uppercase + letter-spacing — feels like a category tag
- **Never duplicate the title as an h2 right after the banner** — that was the Admin LMS Framework bug we had to fix

---

## 3. Body content patterns

### Section headings
```html
<h3 style="color:#1B365D; font-size:clamp(16px,2.6vw,18px); margin-top:20px;">Lead Intake — One Pipeline, One Source of Truth</h3>
```

### Definition lists (term — description pattern)
```html
<ul>
  <li><strong>Conversations</strong> — raw activity. Every dial, every text, every door.</li>
  <li><strong>Appointments</strong> — qualified intent. A date and time on the calendar.</li>
  <li><strong>Contracts</strong> — executed deals. The only output that pays.</li>
</ul>
```

### Data tables
```html
<table style="width:100%; border-collapse:collapse;">
  <thead>
    <tr style="background:#f1f1f1;">
      <th style="padding:10px; text-align:left; border:1px solid #ddd;">Field</th>
      <th style="padding:10px; text-align:left; border:1px solid #ddd;">Why It Matters</th>
    </tr>
  </thead>
  <tbody>
    <tr><td style="padding:10px; border:1px solid #ddd;">Full name + phone</td><td style="padding:10px; border:1px solid #ddd;">Required for contact and routing.</td></tr>
    <tr><td style="padding:10px; border:1px solid #ddd;">Source</td><td style="padding:10px; border:1px solid #ddd;">Drives ROI tracking and lead-cost reporting.</td></tr>
  </tbody>
</table>
```

### Styled panels (navy left border — reference/supporting info)
```html
<div style="background:#f8fafc; border-left:4px solid #1B365D; padding:14px 18px; border-radius:4px; margin-bottom:12px;">
  <div style="font-weight:700; color:#1B365D; font-size:15px; margin-bottom:4px;">{HEADING}</div>
  <div style="font-size:14px; color:#333;">{BODY}</div>
</div>
```

### Action Required callout (amber — do-this-now instruction)
```html
<div style="background:#fff8e1; border-left:4px solid #c27a00; padding:16px 20px; border-radius:4px; margin-bottom:20px;">
  <div style="font-weight:700; color:#c27a00; font-size:15px; margin-bottom:4px;">Action Required:</div>
  <div style="font-size:14px; color:#333;">{what the agent must do now}</div>
</div>
```

### Success / completion callout (green)
```html
<div style="background:#f8fafc; border-left:4px solid #2D7A4F; padding:14px 18px; border-radius:4px;">
  <div style="font-weight:700; color:#2D7A4F; font-size:15px; margin-bottom:4px;">{GREEN HEADER}</div>
  <div style="font-size:14px; color:#333;">{BODY}</div>
</div>
```

---

## 4. Navigation row (required at bottom)

```html
<div style="display:flex; justify-content:space-between; align-items:center; gap:12px; margin:28px 0 8px;">
  <a style="background:#1B365D; color:#ffffff; padding:12px 22px; text-decoration:none; font-weight:bold; border-radius:4px;" href="{PREV_URL}">← PREVIOUS</a>
  <a style="background:#000000; color:#ffffff; padding:12px 22px; text-decoration:none; font-weight:bold; border-radius:4px; margin-left:auto;" href="{NEXT_URL}">NEXT →</a>
</div>
```

**Critical rules:**
- Use `justify-content: space-between` + `margin-left: auto` on NEXT — NOT `flex-wrap: wrap`
- First page → replace PREVIOUS with a gray `<span>` reading "← First Page"
- Last page → replace NEXT with gray `<span>` reading "End of Course" or similar
- NEVER mix old-style buttons (BACK / TAKE QUIZ) with the new PREVIOUS / NEXT — remove the old ones first

---

## 5. Footer (required at bottom of every page)

```html
<div style="text-align: center; font-size: 11px; color: #666; margin-top: 12px;">
  <hr>
  Bear Academy Training System<br>
  Powered by Moodle LMS<br>
  Last updated: April 2026 | Copyright WorldTeachPathways 2026
</div>
```

Update the year/month when the course year rolls over.

---

## 6. Section description format (goes on the section, not on a page)

Same wrapper + header pattern as pages, plus a panel list describing what's inside the section.

Section descriptions should be 2,500–5,000 characters. A section that's empty or under 400 characters is a red flag that needs styling.

---

## 7. What to strip when importing pasted content

ChatGPT exports leave these artifacts — always strip them:

| Pattern | Example | Action |
|---|---|---|
| `data-start="..."` attributes | `<p data-start="1084" data-end="1184">` | Regex: `/\s*data-(start\|end)="\d+"/g` → remove |
| Duplicate h2 title | `<h2>Governance Statement</h2>` right below navy banner | Remove |
| "Course Code: X" boilerplate | `<p><strong>Course Code:</strong> BA-ADMIN-001</p>` | Remove (redundant with banner) |
| Legacy BACK / TAKE QUIZ buttons | `<a>← BACK</a> <a>TAKE QUIZ →</a>` | Remove before adding new nav |
| Old `max-width: 1000px` wrapper | Fixed-width non-mobile | Replace with 900px responsive |
| `flex-wrap: wrap` on nav row | Causes mobile button clumping | Remove; add `margin-left: auto` on NEXT |

---

## 8. Rollout checklist (when creating / fixing a page)

1. Wrap content in 900px responsive wrapper
2. Add navy header panel (section label + h1 title)
3. Verify body content uses the approved patterns (headings, tables, panels, callouts)
4. Strip any ChatGPT `data-start`/`data-end` attributes
5. Strip duplicate title / boilerplate metadata
6. Add Prev/Next flex nav row (no flex-wrap)
7. Add Bear Academy footer
8. Check the activity name matches the h1 title
9. Set Activity completion if the page is required for course completion
10. Verify on mobile width (sidebar or dev tools) that nav buttons stay at opposite ends

---

## 9. Color tokens

| Token | Hex | Use |
|---|---|---|
| Navy | `#1B365D` | Header panel bg, h2/h3 text, PREVIOUS btn, left border on info panels |
| Black | `#000000` | NEXT button bg |
| White | `#ffffff` | Text on navy + black backgrounds |
| Body text | `#222222` | Page body paragraphs |
| Secondary text | `#333333` | Panel body text |
| Footer gray | `#666666` | Footer text |
| Panel bg | `#f8fafc` | Info panel background |
| Table header | `#f1f1f1` | Data table header row |
| Table border | `#dddddd` | Data table cell borders |
| Amber action | `#c27a00` | Action Required header + left border |
| Amber bg | `#fff8e1` | Action Required background |
| Green complete | `#2D7A4F` | Completion / certification callouts |
| Gray disabled | `#e5e7eb` / `#6b7280` | First Page / End of Course indicator |
