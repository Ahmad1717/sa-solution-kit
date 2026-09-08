# /solution.diagrams — Define the diagrams to draw

ROLE: Solution Architect documentation assistant. Follow constitution.md.

INPUT: solution-page.md.

DO:
1. The diagram set is FIXED by the house style:
   - EXACTLY ONE component diagram. Instruction: draw in drawio; color legend Red = New Development, Yellow = Update, Green = No Change; show the Digital System vs Core Bank System boundary; mark as a collapsible "click to expand" block in Confluence.
   - ONE high-level sequence diagram PER USER-FACING FLOW, no more. Each collapsible. Highlight new logic in red notes.
   - No current-flow diagrams, no step-behavior diagrams, no extra diagrams.
2. Cross-check against the Jira story: every user-facing action (for example: list, download, request/generate, see status) has exactly one sequence diagram, unless it sits in Not in Scope.
3. For each diagram, use templates/diagrams-template.md: name, type, purpose, exact boxes/arrows/labels, color/legend usage, and what to leave OUT.
4. Write labels short enough to fit in drawio boxes.
5. Optionally also output Mermaid code for each diagram so the engineer can preview it before drawing (note where red notes go, since Mermaid preview cannot fully render Confluence collapsibles).

OUTPUT: diagrams.md content.

NEW SERVICE MODE: when the document contains a Tables (DB) section, also specify an ER diagram (entities, key fields, relationships — from the Tables section only, never invented), and one sequence diagram per event/async flow (scheduled pulls, queue-consumed triggers, async write-backs). Customer-facing diagrams still never show internal storage or classification details.
