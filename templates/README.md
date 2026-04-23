# Templates

Production-ready HTML templates for Moodle TinyMCE. Copy the file contents directly into a Moodle page — no conversion needed.

| File                            | Use when                                           |
|---------------------------------|----------------------------------------------------|
| `moodle-page-base.html`         | Standard lesson page — text + panels only          |
| `moodle-page-with-video.html`   | Lesson page that embeds a 16:9 responsive video    |
| `moodle-page-with-table.html`   | Lesson page that includes a structured data table  |

---

## Rules

- **Inline CSS only.** Do not add `<style>` blocks.
- **No external JS.** Do not add `<script>` tags.
- Keep the wrapper `<div style="max-width: 1000px; ...">` as the first element.
- Keep the nine-section structure in the same order — see `/reference/build-standard.md`.

---

## Editing Workflow

1. Open the template file
2. Replace placeholder text (Course Name, Lesson Title, Page Number, content copy)
3. Update the "Last updated" date in the footer
4. Set the Back and Next button `href` to the correct Moodle page URLs
5. Paste the final HTML into Moodle TinyMCE (source view)
6. Preview on desktop + mobile widths before publishing

---

## Adding a New Template

- Start from `moodle-page-base.html`
- Keep all build-standard sections
- Add your variant section in the correct position (e.g., video below content panels, before closing panel)
- Add a row to the table above with the filename and "use when" description
