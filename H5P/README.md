# H5P Builds for Bear Academy

This folder contains all H5P interactive activities built for Bear Academy courses, organized one folder per H5P. Each folder contains:

- **`*.h5p`** — the packaged file ready to upload to Moodle (Add activity → H5P → Package file)
- **`spec.md`** — the content spec (what each interaction says, where it lives in the course, validation checklist)
- **`content.json`** — the H5P content data (text, hotspot positions, branching logic, etc.)
- **`h5p.json`** — the H5P manifest (library dependencies)
- **Source media** (PNG, MP4, etc.) used as inputs

## How to upload to Moodle

The Content Bank "Upload" button does **not** accept `.h5p` packages. Use this path instead:

1. Open the target course in Moodle with **Edit mode** ON
2. In the section where the H5P should live, click **Add an activity or resource**
3. Pick **H5P**
4. In the activity settings, the **Package file** field accepts `.h5p` uploads
5. Drag the `.h5p` file from this folder into the picker
6. Save and display

## How to regenerate a `.h5p` from source

If you edit `content.json` or replace the source image:

```bash
cd <activity-folder>
zip -r ../<activity-name>.h5p .
```

The zip must contain `h5p.json` and `content/content.json` at the root, with referenced media under `content/`.

---

## Activities in this folder

| Folder | Activity | Course | Section | Replaces / augments |
|---|---|---|---|---|
| `who-to-contact/` | Image Hotspots — Your Two-Person Command Structure | 1 — Agent Onboarding | Who We Are | cm 976 (Page: Who to Contact) |

---

*Bear Academy build system · See `reference/build-standard.md` for the page/nav standard.*
