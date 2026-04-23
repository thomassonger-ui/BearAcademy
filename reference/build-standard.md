# Bear Academy Moodle Build Standard

This is the canonical build standard for every page published to Bear Team Academy in Moodle 5.1. All templates in `/templates` and the AI prompt in `/prompts/page-generator.md` derive from this document. If something here changes, those files change too.

---

## Platform Rules (Non-Negotiable)

- **Inline CSS only.** No `<style>` tags.
- **No external CSS or JavaScript.**
- Must render correctly inside the **Moodle TinyMCE editor**.
- Must be **mobile-responsive** using simple HTML structure only.

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
   - Padding: `24px`

4. **Content Panels** (use multiple)
   - Background: `#f7f9fc`
   - Left border: `4px solid #1B365D`
   - Padding: `16px`

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

9. **Navigation Row**
   - Flex container
   - LEFT: Back button — outlined, white background, `#1B365D` border
   - RIGHT: Next button — black background

---

## Table Standard

If a table is used:

- Header background: `#1B365D`
- Header text: white
- Alternating row colors: `#f7f9fc` / `#ffffff`
- Border color: `#d9d9d9`

---

## Validation Checklist (Before Publishing)

- [ ] Page opens with the global wrapper `<div>`
- [ ] All nine structural sections present and in correct order
- [ ] Only inline CSS — no `<style>` tags, no external links
- [ ] Header bar uses `#1B365D` + white text
- [ ] Content panels use `#f7f9fc` background + `4px solid #1B365D` left border
- [ ] Footer contains all four required lines
- [ ] Navigation row has Back (outlined) and Next (black)
- [ ] Page renders correctly in TinyMCE preview
- [ ] Page renders correctly on mobile width (< 480px)

If anything is missing → fix it before publishing.
