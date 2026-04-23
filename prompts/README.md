# Prompts

AI prompts used to generate Bear Academy Moodle pages. Paste one of these into Claude or ChatGPT and fill in the variables at the bottom.

| File                 | Use when                                                  |
|----------------------|-----------------------------------------------------------|
| `page-generator.md`  | Generate a new lesson page from a topic description       |

---

## How to Use

1. Open the prompt file
2. Copy the full contents
3. Fill in the four variables at the bottom:
   - Course Name
   - Lesson Title
   - Page Number
   - Topic / Content Description
4. Paste into your LLM of choice
5. Copy the output HTML directly into Moodle TinyMCE (source view)
6. Validate against the checklist in `/reference/build-standard.md`

---

## Keeping Prompts in Sync

The prompt encodes the Bear Academy Moodle Build Standard. If you update `/reference/build-standard.md`, update `page-generator.md` in the same commit so output stays consistent.
