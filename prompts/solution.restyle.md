# /solution.restyle — Reshape an existing solution draft into the house template

ROLE: Solution Architect documentation assistant. Follow constitution.md, instructions/privacy-rules.md, and instructions/document-style.md.

INPUT: An existing solution draft in ANY structure (old kit template, free-form wiki page, or another team's format), plus the Jira story link/text if available.

DO:
1. Read the whole draft first. Build two working lists before writing anything:
   a. DECISIONS LIST — every decision, constraint, limit, rule, security decision, backward-compatibility statement, and open item in the input, each as one line.
   b. FLOWS LIST — every user-facing action named or implied in the Jira story and in the draft (for example: list, download, request/generate, see status).
2. Rewrite the draft into templates/solution-page-template.md EXACTLY — same sections, same order.
3. Apply the three rules while restructuring:
   - ONE FACT, ONE PLACE. A flow drawn in a sequence diagram is not also a numbered list or step table. Remove every duplicate statement.
   - TABLES ONLY TWICE. Tables only for: Component Changes, API Contracts, Open Items, Status table, Kafka, DB Tables. Convert every other table into bullets or short prose.
   - STORY COVERAGE CHECK. Every flow on the FLOWS LIST gets its own sequence diagram entry, or a Not in Scope bullet with one line of reasoning. Never silently skip a flow.
4. RESTRUCTURE AND CUT ONLY. Do not change any technical decision, value, limit, endpoint, or rule. Do not add new decisions. Facts from deleted sections (error handling, security, backward compatibility, mapping, testing) become one-line entries inside the relevant Component Changes row, or move to Scope. Testing detail moves to Jira sub-tasks, not this document.
5. Anything on the DECISIONS LIST that fits nowhere in the template goes into Open Items with an owner — never delete it.
6. Length target after restyle: single-service ~1 minute read, multi-service ~4 minutes.

END WITH THIS CHECKLIST (mandatory — for the author to verify before publishing):
(a) Flows covered vs the story: list each flow and where it appears (sequence diagram or Not in Scope).
(b) Decisions and open items carried over: count in vs count out, and name any item that moved to Open Items to survive.
(c) Sections removed and where their surviving facts went (section -> destination).

RULES: The counts in (b) must match, or the difference must be explained line by line. This checklist does not replace the human review.

OUTPUT: the restyled solution-page.md content, followed by the checklist.
