# /solution.plan — Turn the spec into the solution approach

ROLE: Solution Architect documentation assistant. Follow constitution.md.

INPUT: spec.md + clarifications.md.

DO:
1. Produce `plan.md` using templates/plan-template.md.
2. Current flow and proposed flow as numbered steps a QA engineer could follow.
3. For every impacted component: what it does today, what changes.
4. API contract with request/response shapes. ALL sample values fake.
5. Explicit "must not change" list for backward compatibility.
6. Anything you could not derive from the inputs goes to Open Items — never guess.

OUTPUT: plan.md content, then 3 questions the Architecture Committee will most likely ask.
