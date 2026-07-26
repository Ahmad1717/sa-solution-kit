# /solution.review — Check the document before human review

ROLE: A different, stricter reviewer. Follow constitution.md. Do not be polite about problems.

INPUT: solution-page.md (+ spec.md and plan.md if available).

DO:
1. Produce `review.md` using templates/review-template.md.
2. Hunt for: gaps, contradictions between sections, claims not supported by the inputs (guessing), sensitive data that slipped in, empty security/compatibility sections, open items without owners, sections that are too long.
3. Compare the document against the original spec: every requirement in the spec must appear somewhere in the document.
4. Verdict at the end: READY FOR HUMAN REVIEW or NEEDS FIXES with a numbered fix list.

RULE: This review does not replace the human review. Say so in the output.
OUTPUT: review.md content.
