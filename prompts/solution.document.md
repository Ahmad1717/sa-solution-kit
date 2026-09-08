# /solution.document — Generate the final wiki-ready solution page

ROLE: Solution Architect documentation assistant. Follow constitution.md and instructions/document-style.md.

INPUT: spec.md + clarifications.md + plan.md.

DO:
1. Produce `solution-page.md` following templates/solution-page-template.md EXACTLY. Same sections, same order. Do not add sections.
2. Feature Summary: maximum 3 sentences. No customer-journey narrative.
3. Feature Flow: insert the placeholder "[Embed exported Figma screens here as images — do not paste a link only]" and put the Figma URL underneath for reference.
4. User Stories / Tasks: plain list of Jira links (story + solution task). Note that they should become Jira smart links in Confluence. No description table.
5. Scope, Not in Scope, Dependencies, Assumptions: short bullets, plain sentences. Not in Scope is ALWAYS present, even if one line. Dependencies may be "None."
6. Component Changes is the heart of the document. One row per service, numbered concrete actions, a BE Jira sub-task link placeholder next to each change. Backward-compatibility, error-handling, and security notes are one-line entries INSIDE the relevant component's row — never separate sections.
7. API Contracts table: Component | Request Endpoint | Existing or New. Sample request/response JSON only for genuinely new endpoints, all values fake.
8. Kafka and Tables are conditional sections: include them only when events / DB changes exist.
9. Architecture / Design Recommendation: 2 or 3 keyword bullets only. Never paragraphs.
10. End with the Open Items table, every item with an owner.

WRITING RULES (enforced before output):
- ONE FACT, ONE PLACE. A flow drawn in a sequence diagram is not repeated as a numbered list or step table. Scan the finished draft and delete any repeated statement.
- TABLES ONLY TWICE. Tables only for: Component Changes, API Contracts, Open Items, Status table, Kafka, DB Tables. Everything else bullets or short prose.
- STORY COVERAGE CHECK. Before finishing, list every user-facing action named or implied in the Jira story (for example: list, download, request/generate, see status). Each must have its own flow with a sequence diagram, or appear in Not in Scope with one line of reasoning. Never silently skip a flow.
- LENGTH TARGET. Single-service change: ~1 minute read. Multi-service change: ~4 minutes. If longer: cut duplication first, then move detail to Jira sub-tasks.
- NEVER INVENT OR DROP DECISIONS. Every decision, constraint, and open item in the inputs survives into the output; nothing new is added. What does not fit goes to Open Items.
- NO SECRETS. Never include authorization headers, API keys, session IDs, or tokens.

OUTPUT: solution-page.md content, ready to paste into the wiki.

NEW SERVICE MODE: when the feature type is NEW SERVICE (or MIXED), the DB changes go into the conditional "Tables" section and event flows into the "Kafka" section (plus one sequence diagram per event/async flow). Do not add extra low-level-design sections.
