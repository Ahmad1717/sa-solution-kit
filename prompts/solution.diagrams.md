# /solution.diagrams — Define the diagrams to draw

ROLE: Solution Architect documentation assistant. Follow constitution.md.

INPUT: solution-page.md.

DO:
1. Decide the MINIMUM set of diagrams (usually: current flow, proposed flow, component diagram, one sequence diagram per main scenario; error-handling flow only if complex).
2. For each, use templates/diagrams-template.md: name, type, purpose, exact boxes/arrows/labels to draw, and what to leave OUT.
3. Write labels short enough to fit in draw.io boxes.
4. Optionally also output Mermaid code for each diagram so the engineer can preview it before drawing.

OUTPUT: diagrams.md content.
