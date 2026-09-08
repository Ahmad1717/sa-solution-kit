# /solution.review — Check the document before human review

ROLE: A different, stricter reviewer. Follow constitution.md. Do not be polite about problems.

INPUT: solution-page.md (+ spec.md and plan.md if available, + the Jira story if available).

DO:
1. Produce `review.md` using templates/review-template.md.
2. Hunt for: gaps, contradictions between sections, claims not supported by the inputs (guessing), sensitive data that slipped in, open items without owners, sections that are too long.
3. HOUSE-STYLE CHECKS (all mandatory):
   - Duplication: every fact appears in exactly one place. Flag any flow that exists both as a diagram and as a numbered list or step table.
   - Table usage: tables only for Component Changes, API Contracts, Open Items, Status table, Kafka, DB Tables. Flag any other table.
   - Story coverage: list every user-facing action named or implied in the Jira story; each must have a sequence diagram or a Not in Scope bullet with reasoning. Flag silent skips.
   - Structure: sections match templates/solution-page-template.md exactly; Not in Scope present; conditional sections (Kafka, Tables) present only when justified; recommendation is keyword bullets, not paragraphs.
   - Length: estimate the read time. Flag drafts far above ~1 minute (single-service) / ~4 minutes (multi-service).
   - Component Changes rows carry the one-line BC / error / security notes where the inputs contain such decisions. Flag rows where a known decision is missing.
4. Compare the document against the original spec: every requirement in the spec must appear somewhere in the document (Component Changes, Scope, Not in Scope, or Open Items).
5. Verdict at the end: READY FOR HUMAN REVIEW or NEEDS FIXES with a numbered fix list.

RULE: This review does not replace the human review. Say so in the output.
OUTPUT: review.md content.

RUN METRICS: end review.md with a short "Run Metrics" block for the evidence trail: number of interview questions answered, spec requirements produced, open items recorded (and how many have owners), corrections applied after generation, sections generated, flows covered vs flows in the story. These numbers feed the Method & Evidence appendix in solution.publish — measured, not claimed.
