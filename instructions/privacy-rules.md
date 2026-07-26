# Privacy Rules — What Goes Into the AI and What Never Does

Read this before every session. When in doubt, leave it out.

## Allowed inputs
- Business requirement in your own words
- Component names and one-line responsibilities
- API endpoint paths and request/response field NAMES and shapes
- Metadata field names (for example: Document Type, Account Number as a field name)
- Filename FORMATS with fake values (for example: Statement_<accountNumber>_<MMYYYY>.pdf)
- Error scenarios and expected behavior
- Constraints ("existing monthly API must not change")
- Sanitized sample responses where every value is fake

## Never allowed
- Source code files, patches, diffs, or repository archives
- Secrets, tokens, API keys, certificates, connection strings
- Real customer data: names, account numbers, IBANs, phone numbers, national IDs
- Production logs or real request/response payloads
- Screenshots of internal tools, dashboards, or documents
- Anything marked confidential or restricted

## How to sanitize an example
Wrong:   "fileName": "Adhoc_Statement_013392048003_012026_042026.pdf"
Right:   "fileName": "Adhoc_Statement_000011112222_012026_042026.pdf"  (fake number, same format)

## If unsure
Ask your security team or your lead BEFORE pasting. A five-minute question is cheaper than an incident.
