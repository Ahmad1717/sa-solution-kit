# How to Approve a System Card

Why: a card is written ONCE, checked ONCE, and then reused safely forever.
This moves the security question from "every AI session" to "one review per component".

## Steps
1. The component owner fills templates/system-card-template.md. Only safe facts: responsibilities, API shapes, field names, formats with fake values, rules, limits.
2. Self-check against instructions/privacy-rules.md: no code, no secrets, no real values, no production data.
3. A second engineer reads it and confirms it is accurate.
4. The team lead (and security, if your company requires it) approves and signs the header.
5. The card goes into context/system-cards/ in the internal repo.
6. From now on, any AI session may load this card as input. The approval date in the header proves it was cleared.

## Rule of thumb
If a fact would be acceptable inside a Confluence solution document that the whole company can read, it is acceptable in a card. If not, it stays out.
