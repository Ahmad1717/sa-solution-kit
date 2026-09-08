# Document Style Rules (BE house style)

- Plain English. Short sentences. No buzzwords.
- **One fact, one place.** Every fact appears in exactly one section. If a flow is drawn in a sequence diagram, it is NOT also written as a numbered list or a step table. Before finishing, scan the document and remove any repeated statement.
- **Tables only twice (plus fixed exceptions).** Tables are allowed ONLY for: Component Changes, API Contracts, Open Items, the Status table, Kafka, and DB Tables. Everything else is bullets or short prose.
- No standalone sections for Error Handling, Security, Backward Compatibility, Testing Strategy, Data/Metadata Mapping, Design Principles, Component Description, Existing/Proposed Experience, or step-behavior tables. If a fact from these areas is a real decision, it becomes one line inside the relevant Component Changes row (or Scope). Testing detail belongs in Jira, not in the document.
- Design screens: embed exported Figma screens as images. A link alone is not enough; keep the URL underneath for reference.
- **Length target.** A single-service change reads in about 1 minute; a multi-service change in about 4 minutes. If the draft is longer, cut duplication first, then move detail to Jira sub-tasks.
- **Story coverage.** Every user-facing action named or implied in the Jira story gets its own flow with a sequence diagram, or an entry in Not in Scope with one line of reasoning. Never silently skip a flow.
- **Never invent or drop decisions.** When restructuring, every decision, constraint, and open item in the input survives into the output, and nothing new is added. What does not fit the template goes to Open Items.
- **No secrets.** Never include authorization headers, API keys, session IDs, or tokens in any document. All sample values fake.
- Every open item lives in the Open Items table with an owner. No open questions hidden inside paragraphs.
