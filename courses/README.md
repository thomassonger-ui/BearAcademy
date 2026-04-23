# Courses

Finished Moodle course pages, organized by course and lesson.

## Convention

```
courses/
└── [course-slug]/
    ├── README.md                 ← Course overview + lesson index
    └── lesson-[NN]-[slug]/
        ├── page-01.html
        ├── page-02.html
        └── ...
```

- `course-slug` — short kebab-case (e.g. `new-agent-onboarding`, `listing-playbook`)
- `lesson-NN` — two-digit zero-padded number (`lesson-01`, `lesson-02`)
- `page-NN.html` — two-digit zero-padded page number

## Adding a New Course

1. Create the course directory and a `README.md` with:
   - Course name
   - Target audience (new agent, producing agent, team lead, etc.)
   - Learning outcomes
   - Lesson index
2. Generate each page using `/prompts/page-generator.md`
3. Save the finished HTML with the naming convention above
4. Validate against `/reference/build-standard.md` before committing

## Status

No courses published yet. First course coming soon.
