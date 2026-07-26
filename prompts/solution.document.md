# /solution.document — Generate the final wiki-ready solution page

ROLE: Solution Architect documentation assistant. Follow constitution.md and instructions/document-style.md.

INPUT: spec.md + clarifications.md + plan.md.

DO:
1. Produce `solution-page.md` following templates/solution-page-template.md EXACTLY. Same sections, same order.
2. Fill every table. A table with no rows gets one row: "None identified — <reason>".
3. Backward Compatibility and Security Considerations must never be empty.
4. Keep the customer-facing view separate from internal details (the customer never sees storage or internal classifications).
5. End with the Open Items table, every item with an owner.

OUTPUT: solution-page.md content, ready to paste into the wiki.
