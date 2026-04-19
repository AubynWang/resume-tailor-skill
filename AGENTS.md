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
9. Separate confirmed facts from suggested phrasing. Tag inferred facts with `*` and do not include them in the final resume unless the user explicitly accepts them.
10. Never copy template placeholder text as if it were real user content.
11. Do not silently remove user experiences — ask first.
12. If no JD is provided, optimize for general professional clarity and avoid over-specialized tailoring.
13. For projects: directly relevant → keep; indirectly relevant (any transferable skill, shared context, or loosely similar task pattern with JD) → aggressively rephrase bullets to highlight transferable elements; completely unrelated (zero connection, rephrasing would be fabrication) → ask user whether to remove. Stop only for "Remove" decisions — rephrase proceeds automatically. If user does not respond, keep the project. Never silently delete projects.

## Template Selection

If multiple templates exist, prefer the one that best matches:
1. Explicit user preference
2. Target language
3. One-page A4 suitability
4. Visual stability for review and print

## Workflow

1. Read the target JD from user input (if provided)
2. Read EVERY file in `source/` without exception. Do not skip any file because another file "already has the main resume." Every file may contain unique facts. Skipping a file leads to incomplete fact inventory and undetected conflicts. Also read templates/ for layout reference.
3. Build a fact inventory — every claim must trace to a source file
   - If Conflicting or Inferred facts exist: present to user and wait for confirmation
   - Otherwise: proceed automatically
4. Classify each project: Directly relevant / Indirectly relevant / Completely unrelated
   - Directly relevant → automatically keep
   - Indirectly relevant → automatically rephrase bullets to highlight transferable skills (do not invent — only reframe)
   - Completely unrelated → ask user whether to remove before generating draft
   - If no removal needed: proceed automatically
5. Generate tailored resume draft
6. Self-check: no fabrication, no inflation, gaps flagged, layout correct, overflow handled
7. Present draft with notes on what was changed, kept, and what gaps remain

## Response Style

- Prioritize execution over discussion
- Avoid unnecessary meta-commentary
- Provide clear deliverables first
- Keep reasoning compact when explanation is needed
- Maintain professional tone

## Constraints

- Do not invent work experience, projects, or certifications
- Do not fabricate source file citations — every claim must trace to a real file in `source/`; if a file cannot be read, report failure and ask the user
- Do not inflate metrics or impact numbers
- Do not silently remove user experiences — ask first
- Do not preserve bad formatting at the cost of readability
- Respect all user-specified layout and language requirements
- **Photo path**: always relative to the output file's location. For `output/xxx.html` use `../assets/证件照原片.JPG`; for root-level `output_xxx.html` use `assets/证件照原片.JPG`
- **One-page density control**: before writing bullets, estimate total content volume. Dense content → write lean bullets (short sentences, drop修饰词, merge similar points). Sparse content → write fuller bullets (add secondary detail). Target ~90–95% page fill. Small bottom margin (5–10%) is normal. No separate expand/compress cycle — density is controlled during writing.
- **Conditional stop**: Conflicting or Inferred facts → stop and wait for user; all facts Confirmed/Merged → auto proceed. Remove decisions → always stop for confirmation, no matter what the user says.
- **Lazy-load photos**: never load image data until final output step.
- **Source citation integrity**: every Fact Inventory entry must trace to a real readable file in `source/`. If a file cannot be read, report failure and ask user to provide content directly.
- **Preserve context on regeneration**: if user requests a new version after confirmation, reuse the same fact inventory rather than re-parsing source files.