# Feature Input — EXAMPLE (fictional bank, all values fake)

## 1. Basic Information
- Feature name: Show already-generated custom statements in the mobile app
- Ticket number/link: BANK-12345
- Business owner / PO: Jane (Product)
- Technical owner: Ali (Mobile Solution Architect)
- Teams involved: iOS, Android, Backend, QA
- Target phase: Phase 1
- Target environment: TEST then PROD

## 2. Business Requirement
- What does the business want: Customers should see custom statements they already generated, instead of generating the same statement again.
- Why is it needed: Reduces duplicate generation load and support calls.
- Current customer/user problem: Custom statements disappear after generation; customers cannot find them again.
- Success criteria: Customer sees a "Recent statements" list and downloads an old custom statement without regenerating.

## 3. Current Behavior
- How it works today: Monthly statements are listed and downloadable. Custom statements can be requested but are not listed afterwards.
- The gap: No listing of already-generated custom statements.
- Current flow:
  1. Customer opens Statements.
  2. Customer picks Monthly or Custom.
  3. Monthly shows a list; Custom only offers a new request.
- Current APIs: GET /accounts/{accountId}/statements?duration=RECENT (listing), GET /statement/{statementId} (download)
- Current services/components: mobile-app, api-gateway, customer-api, document-adapter, document-store, pdf-generator

## 4. Proposed Solution
- New behavior: Add a "Recent statements" section in the Custom statement screen showing already-generated custom statements for the selected account.
- New flow:
  1. Customer opens Custom statement and selects an account.
  2. App calls the listing API with statementType=CUSTOM.
  3. customer-api asks document-adapter for custom documents of that account.
  4. document-adapter filters by Account Number metadata.
  5. App shows periods like "JANUARY 2026 - APRIL 2026"; download uses the existing API.
- What changes for the customer: They can see and re-download old custom statements.
- What changes internally: New optional query parameter, account-based filtering, filenames will include the account number.
- What must NOT change: Monthly listing API behavior and the download API.

## 5. Impacted Components
- customer-api — owns the mobile listing API — add optional statementType parameter (default MONTHLY), custom listing path, sorting and limit.
- document-adapter — reads the document store — filter custom documents by Account Number metadata; support parent and child account flows.
- pdf-generator — creates statement PDFs — include the account number in new custom statement filenames.

## 6. API Contracts
- Existing API: GET /accounts/{accountId}/statements?duration=RECENT — monthly listing, unchanged.
- Updated API: same endpoint + optional statementType=CUSTOM and optional limit.
- Request parameters: statementType (MONTHLY default | CUSTOM), limit (max items).
- Response fields: month, year, statementId, and for CUSTOM also fromMonth, fromYear, toMonth, toYear, fileName.
- Sample response (fake values):
  {"data":{"statements":[{"month":"APRIL","year":"2026","statementId":"FAKE123","statementType":"CUSTOM","fromMonth":"JANUARY","fromYear":"2026","toMonth":"APRIL","toYear":"2026","fileName":"Custom_Statement_000011112222_012026_042026.pdf"}]}}
- Backward compatibility: missing statementType behaves exactly as today.

## 7. Data Mapping
- Source fields: document store metadata — Document Type, Account Number, Start Date, End Date; filename.
- Target fields: month/year range shown to the customer.
- Mapping rules: filename date range -> fromMonth/fromYear/toMonth/toYear; display uses month level only.
- Sorting / filtering / limits: newest first by end month; default limit 6, max 12.

## 8. Error Handling
- No custom statements found -> 200 with empty list; app hides the section.
- Invalid statementType -> 400 validation error.
- Document store unavailable -> standard service error.
- Document missing Account Number metadata -> do not return it (fail closed).
- Filename does not match the expected pattern -> skip that item, never fail the whole list.

## 9. Security / Privacy / Compliance
- Data allowed in responses: statement periods, statement IDs.
- Data NOT allowed: internal storage classification, tokens, headers.
- Access rules: a customer sees only documents of the selected account they own; child accounts checked through the relationship.
- Compliance notes: full account number appears in the filename — confirm with security whether that is acceptable in downloads and emails.

## 10. Testing Strategy
- Functional: listing with and without statementType; parent and child accounts.
- Regression: monthly listing unchanged; download unchanged.
- Integration: end-to-end from app to document store in TEST.
- Negative: wrong account, missing metadata, malformed filename, limit above max.
- Security/privacy: cross-account access attempt returns nothing.
- Environment validation: seed TEST with old-format and new-format filenames.

## 11. Assumptions
- Existing documents already carry Account Number metadata. (Verify in TEST.)
- The existing download API works for the returned statement IDs.

## 12. Open Items
- Final empty-state design — Owner: Design
- Maximum number of items in the app — Owner: PO + Backend
- Where legacy-generated documents are stored (same folder or not) — Owner: Backend
