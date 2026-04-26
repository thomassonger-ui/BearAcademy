# H5P Drag and Drop — "Build the Transaction File"

**Course:** 1 — Agent Onboarding: How We Think
**Section:** 3 — How the Model Works
**Replaces / consolidates:** cm 799 (File Integrity), cm 802 (Decisions Are Documented), cm 928 (Organizing Your Business Files)
**H5P type:** H5P.DragQuestion (Drag and Drop) — built in **Lumi**, exported as `.h5p`, hosted on GitHub Pages, embedded via iframe in Moodle
**Estimated learner time:** 12–15 minutes
**Build effort (in Lumi):** ~45 minutes

---

## What this activity teaches

The #1 reason new agents lose commission is misfiled paperwork. This activity has the agent *physically* place 18 documents into the four stages of a transaction file. They get muscle memory for what belongs where, when. Reading about it doesn't stick. Doing it does.

---

## Background image

**File:** `background.png` (1600 × 1000 px)

The image has 4 quadrant drop zones drawn into it:

| Position | Zone | x | y | width | height |
|---|---|---|---|---|---|
| Top-left | Pre-Listing | 30 | 130 | 758 | 408 |
| Top-right | Active Listing | 812 | 130 | 758 | 408 |
| Bottom-left | Under Contract | 30 | 562 | 758 | 408 |
| Bottom-right | Closed | 812 | 562 | 758 | 408 |

Use these coordinates exactly when defining drop zones in Lumi.

---

## Task description (paste into Lumi)

```
Build the Bear Team transaction file.

Drag each document below into the correct stage. Aim for 100% — misfiled paperwork is the #1 reason new agents lose commission. You can retry as many times as needed. Click "Check" when you're done.
```

---

## The 18 documents (with correct drop zones)

Use **text labels** for each draggable element (Lumi → Add element → Text).

### Stage 1 — Pre-Listing (4 documents)

| # | Document text | Why here |
|---|---|---|
| 1 | Listing Agreement | Hired representation has to be signed before marketing |
| 2 | Seller's Property Disclosure | Required at listing under FL law; protects against future claims |
| 3 | Comparative Market Analysis (CMA) | Pricing rationale; handed to seller at listing presentation |
| 4 | Listing Photos & Media Authorization | Seller's written permission to use images and video |

### Stage 2 — Active Listing (4 documents)

| # | Document text | Why here |
|---|---|---|
| 5 | MLS Listing Sheet | Generated when the property goes active |
| 6 | Showing Feedback Log | Captured during the active listing window |
| 7 | Open House Sign-In Sheet | Only relevant while listing is on the market |
| 8 | Price Reduction Documentation | Mid-listing pricing change |

### Stage 3 — Under Contract (6 documents)

| # | Document text | Why here |
|---|---|---|
| 9 | Signed Purchase Agreement | The offer has been accepted; contract executed |
| 10 | Earnest Money Receipt | Confirms deposit per contract terms |
| 11 | Inspection Report | Buyer's due diligence in escrow |
| 12 | Inspection Response / Repair Addendum | Negotiated repairs after inspection |
| 13 | Appraisal Report | Lender-required during contract period |
| 14 | Final Walkthrough Sign-Off | Buyer's last check before closing |

### Stage 4 — Closed (4 documents)

| # | Document text | Why here |
|---|---|---|
| 15 | Closing Disclosure (CD) | Final settlement statement; buyer must receive 3 days before close |
| 16 | Recorded Deed | Title transfer is recorded post-close |
| 17 | Commission Disbursement Authorization (CDA) | Sent to title to release commission |
| 18 | Closed-File Archive Note | Internal note confirming file is complete and archived |

---

## Drop zone definitions (paste coordinates into Lumi)

In Lumi → Drag and Drop → Step 2 → Drop Zones:

| Drop zone label | x | y | width | height | Background opacity |
|---|---|---|---|---|---|
| Pre-Listing | 30 | 130 | 758 | 408 | 0% (invisible — image already shows the zone) |
| Active Listing | 812 | 130 | 758 | 408 | 0% |
| Under Contract | 30 | 562 | 758 | 408 | 0% |
| Closed | 812 | 562 | 758 | 408 | 0% |

> Lumi expresses zones as **percentages** by default. If your version uses %, the conversions are: `Pre-Listing = 1.875%, 13%, 47.375%, 40.8%` etc. (divide x and width by 1600, y and height by 1000, multiply by 100). Use whichever input mode Lumi gives you.

For each drop zone, in **"Correct elements"**, select only the documents listed under its stage above.

---

## Settings (Behavioural settings tab in Lumi)

| Setting | Value | Why |
|---|---|---|
| Enable "Retry" button | ✅ ON | Adults learn from retry — let them iterate |
| Enable "Check" button | ✅ ON | Required for scoring |
| Enable "Show Solution" button | ✅ ON | After max attempts, reveal placement |
| Single point | ❌ OFF | Score per item (18 points total, not all-or-nothing) |
| Apply penalties | ❌ OFF | Don't double-penalize misplaced items |
| Background opacity (drop zone) | 0% | Image already visualizes zones |
| Show feedback | "On Check" | Don't reveal correctness mid-drag |
| Pass percentage | 80% | Tight but reachable; ~3-4 misplacements allowed before failing |

---

## Feedback ranges (Behavioural settings → Overall Feedback)

| Score range | Feedback |
|---|---|
| 0–49% | "Not yet. Misfiled paperwork is how new agents lose deals. Review the four stages and try again." |
| 50–79% | "Closer. You have the structure right but a few documents are in the wrong stage. Click each red item and re-place it." |
| 80–99% | "Strong. You'd file most things in the right place on Day 1. Aim for 100% — every document matters." |
| 100% | "✅ You can build a Bear Team transaction file. Misfiled paperwork won't be how you lose deals. Move on." |

---

## Localization / text overrides (optional, only if you want Bear Team voice)

| H5P default | Bear Team override |
|---|---|
| "Check" | "Check My File" |
| "Retry" | "Try Again" |
| "Show Solution" | "Show Me the Right Placement" |
| "You got @score of @total points" | "You filed @score of @total documents correctly." |

---

## Lumi step-by-step

1. Open **Lumi Education** desktop app
2. Click **New Content** → choose **Drag and Drop** (NOT "Drag the Words" — different content type)
3. **Title:** `Build the Transaction File`
4. **Task description:** paste from the section above
5. **Step 1 — Settings:**
   - Background image: upload `background.png`
   - Background opacity: 100% (we want the image visible)
6. **Step 2 — Define task:**
   - **Add 4 Drop Zones** using the coordinates table above. For each:
     - Label: stage name (e.g., "Pre-Listing")
     - Background opacity: 0%
     - Show label: ❌ OFF (image already labels them)
   - **Add 18 Text Elements** using the document list above. For each:
     - Element type: Text
     - Text: the document name
     - Width: ~22%, Height: ~6%
     - Set "**Drop zones (correct)**" — assign the element to its correct stage's drop zone(s)
     - Single drop zone per element (no multi-zone)
7. **Behavioural settings tab:** apply the settings table above
8. **Overall Feedback:** add the four ranges
9. **Save** the H5P, then **Export → .h5p file** with name `build-the-transaction-file.h5p`
10. **Lumi → Export → HTML** with name `build-the-transaction-file.html` (this is the version we iframe into Moodle)

---

## Where this activity sits in Course 1

**Replaces:** cm 799 (File Integrity), cm 802 (Decisions Are Documented), cm 928 (Organizing Your Business Files)

After deploying:
- Hide / unlist these three Pages in Moodle (don't delete — keep as deeper reference if needed)
- Insert one new Page in Section 3 named **"Build the Transaction File"**
- Embed the H5P via iframe at the top, with a short framing paragraph
- Adjacent navigation:
  - PREV: cm 798 (Broker Visibility) — `← PREVIOUS`
  - NEXT: cm 801 (Brand Discipline) — `NEXT →`

---

## Validation checklist before publishing

- [ ] All 4 drop zones placed at correct coordinates (no overlap, no off-image)
- [ ] All 18 documents have a single correct drop zone assigned
- [ ] Text on each draggable is legible at full mobile width
- [ ] Retry + Show Solution + Check buttons all enabled
- [ ] Pass threshold set to 80%
- [ ] Overall feedback ranges populated for 0–49%, 50–79%, 80–99%, 100%
- [ ] Tested in Lumi preview by misfiling 3–4 items and confirming feedback shows red marks
- [ ] Tested at 100% score → confirms passing message
- [ ] Exported as `.h5p` AND `.html` (HTML is what gets iframed into Moodle)
- [ ] HTML pushed to `BearAcademy/H5P/build-the-transaction-file/` and verified at the GitHub Pages URL
- [ ] Iframe inserted in the new Moodle Page with `height: 1000px` (taller than Hotspots — drag activity needs more room)
- [ ] PREV/NEXT navigation row in Moodle Page matches `reference/build-standard.md`

---

## Files in this folder

| File | Purpose |
|---|---|
| `background.png` | The 4-quadrant workspace image (Lumi background) |
| `zone-coordinates.json` | Drop zone coordinates in pixels (1600×1000 base) |
| `spec.md` | This document |
| `build-the-transaction-file.h5p` | (You produce in Lumi) — packaged H5P for re-use |
| `build-the-transaction-file.html` | (You produce in Lumi) — self-contained HTML for Moodle iframe |

---

*Bear Academy H5P build · Drag-and-Drop #1 · Spec finalized April 2026*
