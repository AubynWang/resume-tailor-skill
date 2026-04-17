# Resume Tailor Skill — Agent Instructions

## Purpose
This project is a resume tailoring skill pack.
It customizes resumes to match specific job descriptions
using only truthful, user-provided materials.
It does NOT invent or exaggerate content.

## Folder Structure

| Folder | Purpose | Examples |
|---|---|---|
| `source/` | User's real resume materials | Old resumes, project notes, internship notes, education details |
| `templates/` | Resume layout templates | Chinese template, English template, HTML template |
| `assets/` | Photos and visual assets | Profile photo, icons, logos |

## File Role Identification

Do not rely solely on folder names. Identify file roles by content:
- Files primarily containing real personal information → treat as source
- Files primarily defining layout, structure, or style → treat as template
- Files containing both → extract facts as source, reuse layout as template reference
- If a file appears misplaced, still use it correctly based on content and user intent

## Rules

1. Use ONLY facts from files in `source/`. Never fabricate content.
2. If critical information is missing, ask the user before proceeding.
3. Never add skills, experiences, or achievements not in user materials.
4. Default output: HTML review-ready draft (single-column, one-page A4).
5. Alternative output: text-only draft when user explicitly requests it.
6. Support bilingual output (Chinese / English).
7. If user does not specify language, infer from template, source materials, and JD.
8. Always flag gaps between JD requirements and user materials.
9. Separate confirmed facts from suggested phrasing.
10. Never copy template placeholder text as if it were real user content.
11. Do not silently remove user experiences — ask first.
12. If no JD is provided, optimize for general professional clarity and avoid over-specialized tailoring.

## Template Selection

If multiple templates exist, prefer the one that best matches:
1. Explicit user preference
2. Target language
3. One-page A4 suitability
4. Visual stability for review and print

## Workflow

1. Read the target JD from user input (if provided)
2. Read all files in `source/` and `templates/`, identify file roles by content
3. Build a fact inventory — every claim must trace to a source file
4. Match user facts to JD requirements
5. Generate tailored resume draft
6. Self-check: no fabrication, no inflation, gaps flagged, layout correct
7. Present draft with notes on what was changed, kept, and what gaps remain

## Response Style

- Prioritize execution over discussion
- Avoid unnecessary meta-commentary
- Provide clear deliverables first
- Keep reasoning compact when explanation is needed
- Maintain professional tone

## Constraints

- Do not invent work experience, projects, or certifications
- Do not inflate metrics or impact numbers
- Do not silently remove user experiences — ask first
- Do not preserve bad formatting at the cost of readability
- Respect all user-specified layout and language requirements