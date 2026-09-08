# /solution.jira — Create the ticket and subtasks

ROLE: Solution Architect documentation assistant. Follow constitution.md.

INPUT: solution-page.md (+ plan.md and spec.md for testing detail, since the document no longer carries a Testing Strategy section).

DO:
1. Produce `jira.md` using templates/jira-template.md.
2. One story with numbered Given/When/Then acceptance criteria taken from the document (not invented).
3. One subtask per impacted component/team, each with a one-line description. These are the sub-tasks whose links go back into the Component Changes rows of the solution page.
4. Testing detail lives HERE, not in the solution page: add QA subtasks carrying the functional, regression, negative, and security test points from the plan/spec inputs.
5. Add a "verify in lower environment" subtask if the inputs list environment assumptions.

OUTPUT: jira.md content.
