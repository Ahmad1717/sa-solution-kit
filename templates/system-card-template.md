# System Card: <component name>

A System Card is a one-page, pre-approved description of one component.
It contains ONLY safe facts: what the component does, its API shapes, its rules.
No code. No secrets. No customer data. Once approved, it becomes a reusable
input for every future solution document.

---
- Card owner: <team / person>
- Approved by: <lead / security>   Date: <date>
- Review the card again when: <e.g. every quarter, or when the component changes>
---

## 1. What it is
One or two sentences: the component's job in the system.

## 2. Who talks to it
- Called by: <components>
- It calls: <components / external systems>

## 3. Public interface (shapes only, fake values)
| Method + Path | Purpose | Key parameters | Key response fields |
|---|---|---|---|

## 4. Data it owns or reads (field NAMES only)
| Field / metadata name | Meaning |
|---|---|

## 5. Naming and format rules
File name formats, ID formats, enum values — with fake sample values.

## 6. Hard rules (things that must always stay true)
- e.g. "Existing callers without parameter X must see unchanged behavior."

## 7. Known limits and gotchas
- e.g. "Listing reads only the first page of results."

## 8. What is NOT in this card (and why)
- e.g. "Internal algorithms — not needed for solution documents."
