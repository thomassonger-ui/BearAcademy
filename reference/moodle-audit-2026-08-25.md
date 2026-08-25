# Bear Academy — Mobile Fit Audit, Courses 0–5
**Read-only audit. Nothing was changed.** · 2026-08-25 · worldteachpathways.moodlecloud.com

Method: every Page activity, course home, quiz, H5P, checklist, glossary and certificate rendered inside Tom's logged-in Chrome at **360 px** (small Android) and **390 px** (iPhone 14–16) — 326 renders. A page fails if any content element extends past the right edge of the screen.

## Scorecard

| Course | Moodle id | Pages | Fail @360 | Fail @390 | Worst spill | Verdict |
|---|---|---|---|---|---|---|
| 0 – Starting with Moodle | 8 | 11 | 0 | 0 | — | **PASS** |
| 1 – Agent Onboarding | 18 | 29 | 6 | 4 | 90 px | FAIL |
| 2 – Brokerage Structure | 19 | 25 | 13 | 7 | 176 px | FAIL |
| 3 – Sales Process | 22 | 15 | 0 | 0 | — | **PASS** |
| 4 – Operational Systems | 21 | 29 | 19 | 18 | 230 px | FAIL |
| 5 – Compliance & Risk | 20 | 20 | 15 | 13 | 167 px | FAIL |
| 6 – BrokerMint (fixed earlier today) | 24 | 23 | 0 | 0 | — | **PASS** |

**53 of 129 pages (41%) fail on a phone.** Quizzes, H5P activities, checklists, the glossary and all course home pages pass. (Certificate activity pages show a wide admin table to teachers only — students see a download button; confirmed on Course 24.)

## Root cause — one problem, everywhere
Every single failure is a **3-, 4- or 5-column HTML table** inside a page that has 16–40 px of side padding. At 360 px there is ~280–310 px left for content; a 3-column table needs more than that, so it pushes the whole page sideways. Same defect as Course 24. Nothing else is at fault: videos, images and buttons are already responsive.

| Course | Tables total | 3+ column tables | Widest |
|---|---|---|---|
| 1 | 29 | 7 | 5 columns |
| 2 | 30 | 21 | 5 columns |
| 4 | 37 | 20 | 4 columns |
| 5 | 32 | 19 | 4 columns |

Complication: courses were built on **three different page templates** (900 px wrapper with `padding: 0 16px`; 960 px; 1000 px) with four different table style strings — so the fix must target tables by structure, not by copying Course 24's exact find-and-replace.

## Failing pages
**Course 1 (18):** Who to Contact (976) · Your Economics at Bear Team (1057) · Why Systems Win (753) · Organizing Your Business Files (928) · Decisions Are Documented (802) · Escalate Early (803)

**Course 2 (19):** How Decisions Flow (981) · Who to Contact (997) · Communication Channels (982) · Client Communication Standards (983) · Internal Reporting in BearTeamOS (984) · Brand Identity (985) · Compliance & Representation (987) · What We Track (988) · Your Growth Path (990) · Money Quick Reference (1004) · Commission Split Structure (991) · What the Brokerage Covers (995) · The Real Cost Comparison (996)

**Course 4 (21):** Transaction Stage Discipline (785) · Workflow Integrity (786) · Reporting & Review (788) · Performance Tracking (787) · AI for Listing Marketing (907) · AI for Client Communication (908) · AI Productivity Model (913) · AI-Powered Daily Workflow (914) · AI-Enabled vs Traditional Agent (916) · AI-Supported Workflow (917) · AI Workflow Simulation (918) · 10-Minute Listing Challenge (919) · AI Agents To Use (921) · Top 3 AI Agents (922) · AI Stack (923) · 5 Unexpected AI Trends (932) · When You Get Paid (963) · What Delays Your Payment (964) · Reading Your Commission Statement (965)

**Course 5 (20):** Risk in RE Transactions (773) · Early Risk Identification (774) · Disclosure Standards (775) · Documentation Integrity (776) · Florida Required Disclosure Forms (971) · RESPA (972) · Dual Agency & Conflicts (974) · Fair Housing (973) · Escalation Triggers (777) · Escalation Process (778) · Audit Authority (779) · Compliance Alignment (780) · Escrow Deductions (966) · Escrow Disputes (967) · E&O Insurance (968)

(Numbers are Moodle cm ids: `mod/page/view.php?id=NNN`.)

## Side notes (not mobile failures)
- Course-home "Not available unless…" notices show as truncated with "…" on phones — that is Moodle core behaviour, not our content.
- Course 1 "CRM Discipline" (757) loads three ~150–270 KB PNG screenshots from GitHub Pages. They work, but ~585 KB on cellular is slow; worth compressing when convenient.

## Proposed fix (awaiting your go-ahead — no edits made)
Apply the same treatment that passed 92/92 on Course 24, adapted to each template, to the **53 failing pages only** (or to all 129 for consistency — your call):
1. Side padding scales down on phones with `clamp()`; desktop unchanged.
2. Tables: phone font 12 px, tighter cells, `overflow-wrap: anywhere`, wrapped in a `max-width:100%` container.
3. 4- and 5-column tables (6 of them) restructured to 3 columns or stacked — needs a quick content decision per table; I'll list them before touching.
4. Re-run the same 360/375/390/412 verification and deliver the pass/fail proof.
5. Update the BearAcademy repo build standard + templates + page-generator prompt so nothing ships non-mobile again.

Estimated time: ~30 minutes for the four courses once approved.
