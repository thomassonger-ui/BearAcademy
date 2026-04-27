# Lumi Build Guide

## Creating a New H5P Activity

1. Open Lumi.
2. Choose `Create New H5P`.
3. Select the activity type from your completed template.
4. Paste in the title, instructions, questions, answer choices, and feedback.
5. Preview the activity.
6. Fix wording, scoring, and feedback before exporting.

## Good Defaults by Activity Type

| Activity Type | Recommended Use | Settings |
|---|---|---|
| Question Set | Low-stakes checks | Unlimited retries, show feedback, show solution if practice |
| Course Presentation | Short guided lesson | Add checkpoints every 3-5 slides |
| Branching Scenario | Applied decision-making | Keep paths short, debrief each ending |
| Drag and Drop | Labeling or matching | Use clear drop zones and alt text |
| Interactive Video | Pause-and-practice | Add interactions at meaningful moments, not every few seconds |
| Summary | Wrap-up and retrieval | Use 3-5 statement groups |

## Naming Convention

Use lowercase names with module numbers:

- `module-01-topic-knowledge-check.h5p`
- `module-01-topic-interactive-video.h5p`
- `module-02-topic-branching-scenario.h5p`

## Moodle Gradebook Guidance

Use Moodle grades only when you need evidence of achievement. For ordinary practice, completion tracking is often enough.

Suggested settings:

| Purpose | Moodle Grade | Attempts | Completion |
|---|---|---|---|
| Practice | No grade or low points | Unlimited | View or receive score |
| Checkpoint | Points enabled | Multiple attempts | Passing grade |
| Required assessment | Points enabled | Limited attempts | Passing grade |

## Common Issues

- Missing H5P library: upload through Moodle's H5P activity or content bank so Moodle can install required libraries.
- Score not appearing: confirm grading is enabled in the H5P activity and Moodle grade settings.
- Activity too tall on mobile: reduce slide text, split long questions, and avoid wide tables inside H5P content.
- Students skip video interactions: set interactions to pause the video when the question appears.
