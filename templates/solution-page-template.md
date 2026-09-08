# <Feature Name> — Solution Design

| Activity | Status |
|---|---|
| Solutioning | |
| Internal Review | |
| Arc Committee Approval | |

## Feature Summary
Maximum 3 sentences: what the feature does and why. No customer-journey narrative.

## Feature Flow
[Embed exported Figma screens here as images — do not paste a link only]

Figma (reference): <figma-url>

## User Stories / Tasks
- <Jira story link>
- <Jira solution task link>

> Template note: convert these to Jira smart links in Confluence so status badges render. No description table.

## Scope
- <short bullet, plain sentence>

## Not in Scope
Always include this section, even if it is one line.
- <short bullet + one line of reasoning>

## Dependencies
- <short bullet> (or "None.")

## Assumptions
- <short bullet>

## Solution Design

### Component Diagram
(placeholder — exactly one diagram)
- Draw in drawio.
- Color legend: Red = New Development, Yellow = Update, Green = No Change.
- Show the Digital System vs Core Bank System boundary.
- Mark as a collapsible "click to expand" block in Confluence.

### High-level Sequence Diagram
(placeholder — one collapsible diagram per user-facing flow, no more)
- Highlight new logic in red notes.

## Component Changes
The heart of the document. One row per service. Numbered, concrete actions inside each row, each with a placeholder for the BE Jira sub-task link.
Backward-compatibility, error-handling, and security notes are one-line entries inside the relevant component's row — never separate sections.

| Component | Required Changes |
|---|---|
| service-a | 1. <concrete action> (sub-task: <Jira link>). 2. <concrete action> (sub-task: <Jira link>). BC: <one line>. Errors: <one line>. Security: <one line>. |

## API Contracts
| Component | Request Endpoint | Existing or New |
|---|---|---|

Sample request/response JSON only for genuinely NEW endpoints. All values fake.

## Kafka
(Conditional section — include only when events are involved.)

| Topic | Publisher | Subscriber | Existing or New |
|---|---|---|---|

## Tables
(Conditional section — include only when DB changes exist.)

**<table_name>**
- <column_name> — <type> — NEW
- <column_name> — <type>

## Open Items
| Item | Owner | Status |
|---|---|---|

## Architecture / Design Recommendation
2 or 3 keyword bullets only (for example "Domain Driven", "Event Driven"). Never paragraphs.
