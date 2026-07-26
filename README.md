# SA Solution Kit

A spec-driven workflow for writing **solution design documents** with AI — without ever sharing source code, secrets, or customer data.

[Spec Kit](https://github.com/github/spec-kit) applies spec-driven thinking to writing code. This kit applies the same idea to **solution architecture documentation**:

```
Requirement → Specify → Clarify → Plan → Document → Diagrams → Ticket → Review
```

Each step is a fixed command with a fixed job. The engineer supplies knowledge; the AI supplies structure and writing. The result looks the same no matter who runs it — it does not depend on being "good at prompting".

## Why no source code?

Because it is not needed. A solution document describes intent: flows, components, contracts, rules. All of that fits in the structured **feature input form** (`templates/feature-input-template.md`), written in plain English with fake sample values. The `constitution.md` forbids the AI from asking for code, secrets, or customer data — so the process is safe by design, which matters in regulated environments like banking.

## The workflow

| Step | Command | Output |
|---|---|---|
| 1 | `solution.specify` | `spec.md` — clean, testable specification |
| 2 | `solution.clarify` | `clarifications.md` — the AI finds gaps and asks you, one question at a time |
| 3 | `solution.plan` | `plan.md` — flows, components, contracts, compatibility |
| 4 | `solution.document` | `solution-page.md` — wiki-ready final document |
| 5 | `solution.diagrams` | `diagrams.md` — exact draw.io diagram instructions (+ Mermaid previews) |
| 6 | `solution.jira` | `jira.md` — story, subtasks, acceptance criteria |
| 7 | `solution.review` | `review.md` — gap/conflict/privacy check before human review |

## How to use

**Claude Code:** the commands are in `.claude/commands/` — type `/solution.specify` etc.
**GitHub Copilot:** prompt files are in `.github/prompts/` — run `/solution.specify` in chat.
**Cursor:** commands are in `.cursor/commands/`.
**Any other AI chat:** open the file in `prompts/` for the step you want, paste it, then paste your input. Works everywhere.

Start by copying `templates/feature-input-template.md`, filling it, and running step 1. A full filled example is in `examples/statement-listing-input.md` (fictional bank, fake values).

## The rules

- `constitution.md` — the 10 rules the AI must always follow (specification first, no guessing, no code, no sensitive data, human review is mandatory).
- `instructions/privacy-rules.md` — exactly what may and may not be pasted into an AI tool.
- `instructions/document-style.md` — plain-English writing rules.

## The most important rule

AI output is a draft. **The engineer or Solution Architect reviews and owns the final document.** The kit makes you faster; it does not replace your judgement.

## System Cards — the reusable knowledge layer

Instead of describing your system from zero every time (or worse, uploading code), each component gets a **System Card**: a one-page, pre-approved sheet of safe facts — its job, API shapes, field names, formats, and hard rules (`templates/system-card-template.md`). A card is written once, approved once by your lead (`instructions/how-to-approve-a-card.md`), stored in `context/system-cards/`, and reused in every future document. The AI loads the cards for the impacted components and already knows your world — safely, because every card was cleared before it was ever used.
