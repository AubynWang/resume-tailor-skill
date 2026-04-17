# Resume Tailor Skill

## What This Project Is
A resume tailoring skill pack. It customizes resumes to match specific job descriptions
using only truthful, user-provided materials. It does NOT invent or exaggerate content.

## Project Structure

```
resume-tailor-skill/
├── CLAUDE.md                    ← You are reading this (auto-loaded by Claude Code)
├── AGENTS.md                    ← Cross-tool compatible version
├── .claude/skills/resume-tailor/
│   └── SKILL.md                 ← Main skill execution rules (invoke via /resume-tailor)
├── source/                      ← User's real resume materials
├── templates/                   ← Resume templates
├── assets/                      ← Photos and visual assets
├── README.md                    ← Human-readable guide
├── 00_OPEN THIS FIRST.txt       ← Quick start for first-time users
└── Resume Tailor Skill PRD v1.0 (CN-EN).md  ← Design document
```

## Folder Conventions

| Folder | What Goes In | Examples |
|---|---|---|
| `source/` | Real resume materials | Old resumes, master resume, project notes, internship notes, education details, skills notes |
| `templates/` | Resume layout templates | Chinese template, English template, HTML template |
| `assets/` | Visual resources | Profile photo, icons, logos |

## Core Rules (MUST follow)

1. Use ONLY verified facts from files in `source/`. Never fabricate.
2. If critical information is missing, ASK the user before proceeding.
3. Never add skills, experiences, or achievements not present in user materials.
4. Separate "confirmed facts" from "suggested phrasing" when presenting drafts.
5. Do not remove or downplay user experiences without explicit confirmation.
6. Respect all layout constraints the user specifies.

## Default Behavior

- **Default output**: HTML review-ready draft
- **Alternative output**: Text-only draft (when user explicitly requests wording only)
- **Default layout**: Single-column, standard format, one-page A4
- **Photo placement**: Left side of header (if photo exists in `assets/`)
- **Bilingual support**: Chinese and English
- **Language inference**: If user does not specify language, infer from template, source materials, and JD

## Workflow Summary

1. Read the target JD from user input
2. Read all files in `source/` and `templates/`
3. Build a fact inventory — every claim must trace to a source file
4. Match user facts to JD requirements, rank by relevance
5. Identify gaps (JD requirements not covered by materials)
6. Generate tailored draft
7. Flag gaps and present for user review

## Response Style

- Prioritize execution over discussion
- Avoid unnecessary meta-commentary or over-explaining obvious steps
- Provide clear deliverables first, reasoning second
- Keep explanation compact when needed
- Maintain professional tone at all times
- If the user asks for analysis, comparison, or rationale, explain decisions in a structured way

## How to Invoke the Skill

Option A: Use the slash command
```
/resume-tailor
```

Option B: Directly describe the task in chat. This file ensures Claude
already understands the project context.

## What NOT to Do

- Do not invent work experience, project details, or certifications
- Do not inflate metrics or impact numbers
- Do not guess technical skills not mentioned in source materials
- Do not silently drop user experiences to fit page limits — ask first
- Do not copy template placeholder text as if it were user truth
- Do not preserve bad formatting at the cost of readability