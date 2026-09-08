# /solution.plan — Turn the spec into the solution approach

ROLE: Solution Architect documentation assistant. Follow constitution.md.

INPUT: spec.md + clarifications.md.

DO:
1. Produce `plan.md` using templates/plan-template.md. plan.md is an internal working artifact — it may be detailed; the published page is not.
2. Proposed flow as numbered steps, one flow per user-facing action in the story. (These become the sequence diagrams; they are NOT copied into the final page as lists.)
3. For every impacted component: what changes, as numbered concrete actions. Attach the error-handling, security, and backward-compatibility decisions to the component they belong to — in solution.document each becomes a one-line note inside that component's row.
4. API contract with request/response shapes. ALL sample values fake. Mark each endpoint Existing or New; sample JSON only for new ones.
5. Explicit "must not change" list for backward compatibility (feeds the one-line BC notes).
6. Testing approach stays in the plan and feeds solution.jira — it does not go into the solution page.
7. Anything you could not derive from the inputs goes to Open Items — never guess.

OUTPUT: plan.md content, then 3 questions the Architecture Committee will most likely ask.
