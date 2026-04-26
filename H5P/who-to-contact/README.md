# Who to Contact — Image Hotspots

**Course:** 1 — Agent Onboarding: How We Think
**Section:** 1 — Who We Are
**Replaces:** cm 976 (Page: Who to Contact)
**H5P type:** H5P.ImageHotspots 1.10
**Estimated learner time:** 3–4 minutes

## Files

| File | Purpose |
|---|---|
| `who-to-contact.h5p` | Packaged H5P, ready to upload to Moodle as a Course Activity |
| `spec.md` | Full content spec: every hotspot's title, body copy, urgency, and rationale |
| `content.json` | The H5P content data (hotspot positions, popover HTML, image reference) |
| `h5p.json` | H5P manifest with library dependencies |
| `orgchart-source.png` | Source background image (1600×1100) — Bear Team navy + photos of Beth and Tom |

## Hotspots (4)

1. **Bethanne "Beth" Baer — Broker / Owner** (left photo)
   - Compliance, deal risk, legal threats, agent conflicts
2. **Tom Songer — Team Lead** (right photo)
   - BearTeamOS™, training, marketing/branding
3. **⚠ Emergency Escalation** (bottom-left red badge)
   - Outside-business-hours rules
4. **🚪 Open Door Policy** (bottom-right navy badge)
   - Cultural reinforcement: reaching out is the standard

## Before going live

- [ ] Replace `[TOM PHONE]` and `[TOM EMAIL]` placeholders in Tom's hotspot popover
- [ ] Upload as a new H5P activity in Course 1 Section 1, between cm 808 and cm 749
- [ ] Configure completion: `Done: View`
- [ ] Add navigation buttons in the activity description per `reference/build-standard.md`:
  - PREV: `← PREVIOUS` (navy, links to cm 808)
  - NEXT: `NEXT →` (black, links to cm 749) — OR keep existing cm 976 page as a deeper reference and link there as `READ MORE →`
- [ ] Decide: replace cm 976 entirely, or keep it as a deeper-reference page chained after this H5P

## How to update

If you change the content:

1. Edit `content.json` directly (hotspot text, positions, etc.) OR re-author in Moodle's Content Bank
2. Re-zip: `cd who-to-contact && zip -r ../who-to-contact.h5p .`
3. Re-upload to the H5P activity in Moodle (the Package file field)
