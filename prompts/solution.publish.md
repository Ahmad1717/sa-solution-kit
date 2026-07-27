# /solution.publish — Prepare the document for publishing into the company wiki

ROLE: Solution Architect documentation assistant. Follow constitution.md.

INPUT: the final solution-page.md (after solution.review passed), plus diagrams.md.

DO:
1. Produce a ready-to-paste instruction for the company's publishing assistant
   (for example Atlassian Rovo, or a person doing it manually). The instruction
   must say: reformat this document into the official wiki template,
   RESTRUCTURED, NOT REDESIGNED.
2. Produce a section mapping table: each section of solution-page.md -> the
   matching section of the official template, so nothing is lost or reordered
   by accident.
3. Produce the hard rule list for the publisher. The publisher must NOT change:
   the architecture, the API contracts, any sample value, the Open Items, the
   security decisions, or any number (limits, counts, formats). Wording and
   layout may change; facts may not.
4. Produce the "Method & Evidence" appendix (see below) and instruct the
   publisher to attach it at the end of the published page.
5. End with a short checklist for the human: verify diagrams are attached,
   verify the ticket link works, verify Open Items table survived unchanged.

METHOD & EVIDENCE APPENDIX (generate it, one page maximum):
- Inputs used: plain-English interview answers, business requirements,
  approved System Cards (list which). State clearly: no source code, no
  secrets, no customer data were used.
- Numbers from this run: interview questions answered, open items recorded
  (with owners), corrections applied after generation, spec requirements count.
- The line: "This document is AI-assisted and human-reviewed. Final technical
  accuracy is owned by <name>, Solution Architect."
This appendix is what makes the method auditable. Never skip it.

OUTPUT: publish.md containing: the publisher instruction, the mapping table,
the hard rules, the appendix, and the human checklist.
