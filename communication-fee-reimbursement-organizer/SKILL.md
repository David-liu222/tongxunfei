---
name: communication-fee-reimbursement-organizer
description: Organize Chinese corporate phone or communication fee reimbursement packages for 力量煤业. Use when Codex needs to create a 通讯费/电话费报销明细表 from a policy, HR roster, invoice amounts, phone invoices, address book PDFs, and a Word/Excel reimbursement template while preserving template formatting, splitting amounts by person and month, matching phone numbers to personnel, and checking invoice buyer information.
---

# Communication Fee Reimbursement Organizer

## Overview

Use this skill to prepare 力量煤业-style communication fee reimbursement materials from policy, roster, address books, invoices, and an existing template. The output should be a filled reimbursement file that preserves the template plus a short exception list for anything that needs human confirmation.

Load `references/workflow.md` before doing the work. Load `references/policy-cheatsheet.md` when the user's sources are for 内蒙古准格尔旗力量煤业有限公司 or when the user provides the same buyer information. Load `references/address-books-2026-04.md` when the user asks to核对手机号/人员 or does not provide a newer company/mine address book.

## Operating Rules

- Treat the provided reimbursement template as authoritative for layout. Copy the template first, then fill cells; do not redesign tables, widths, fonts, merged cells, signature rows, or totals layout.
- Treat the newest user-provided policy source as authoritative. Use the cheat sheet only as a starting point and replace it when a newer制度汇编 or福利明细 says otherwise.
- Fill phone numbers from the newest available address books, not from invoices, when the address book and invoice disagree. If no newer address book is provided, use the bundled 2026年4月 company/mine address book reference. Record every discrepancy in the exception list.
- Never silently invent a missing person, phone number, month, grade, invoice amount, or buyer field. Leave it blank or mark it as pending confirmation in the exception list.
- Use exact money math with two decimal places for final display. Preserve formulas in the template when possible; if formulas must be replaced, explain why.
- Keep audit evidence: source filename, page/sheet if available, row or invoice number, normalized phone number, and the decision made.

## Workflow

1. Inventory the source files and identify their roles: policy, HR roster, company address book, mine address book, invoice PDFs/images/amount sheet, and reimbursement template.
2. Read the template structure first. Note table headers, repeated monthly rows, merged cells, total rows, and signature rows before filling anything.
3. Extract the reimbursement rules from the policy. Identify eligible grade/position, monthly cap, start-month rule, attendance limitations, and reimbursement principle.
4. Build a personnel lookup from the HR roster with name, department, position, grade, employment status, and any notes that affect eligibility.
5. Extract both address books into a contact lookup. Normalize names and phone numbers, then resolve duplicate names by department or exact phone match.
6. Extract each invoice or invoice amount record. Capture invoice number, date, service period, phone/account number, amount, buyer name, tax number, address/phone, bank, and bank account.
7. Validate invoice buyer information against the expected company information. Normalize spaces in tax numbers and bank accounts before comparing.
8. Match invoices to people by phone number first, then by person name only when the phone number is missing or unclear. Cross-check every match against HR roster and both address books.
9. Split amounts by person and month according to the invoice period and the template period. Apply the policy cap per person per month: reimbursed amount is the lesser of invoice amount and monthly standard unless the policy says otherwise.
10. Fill the copied template using the existing row pattern. If more people are needed than the template has, copy existing data rows and preserve styles, borders, formulas, row heights, and merged-cell behavior.
11. Create an exception list for phone mismatches, missing contacts, duplicate names, HR/address-book disagreements, invoice buyer mismatches, amount-over-cap cases, and missing invoice fields.
12. Render or otherwise visually inspect the final file. Check that totals, page layout, signatures, and table alignment still match the original template.

## Outputs

Produce these artifacts when enough source data is available:

- Filled reimbursement file in the same family as the template (`.docx` or `.xlsx`), with the original formatting preserved.
- Exception/check report (`.md`, `.xlsx`, or appended table as appropriate) listing every item requiring explanation or manual confirmation.
- Short final summary with output paths, total invoice amount, total reimbursed amount, and the count of exceptions.

If the user asks only to set up the reusable workflow, create or update this skill rather than processing a reimbursement package immediately.
