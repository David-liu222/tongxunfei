---
name: communication-fee-reimbursement-organizer
description: Organize Chinese corporate phone or communication fee reimbursement packages for 力量煤业. Use when Codex needs to create a 通讯费/电话费报销明细表 from a policy, HR roster, invoice amounts, phone invoices, address book PDFs, and a Word/Excel reimbursement template while strictly preserving the template's fonts, formatting, table structure, merged cells, widths, row heights, signature blocks, and formulas; filling 人员级别 from an explicit person-level grade, award title, or the `岗位` column in the phone/fuel reimbursement personnel ledger instead of approval wording; sorting reimbursement-detail people by personnel level from high to low before assigning serial numbers; splitting amounts by person and month; recalculating 发票金额 and 实报金额 with over-cap amounts excluded from reimbursement; matching phone numbers to personnel; arranging invoice PDFs by department in the reimbursement-detail order; and checking invoice buyer information.
---

# Communication Fee Reimbursement Organizer

## Overview

Use this skill to prepare 力量煤业-style communication fee reimbursement materials from policy, roster, address books, invoices, and a reimbursement template. The output should be a filled reimbursement file that preserves the template plus a short exception list for anything that needs human confirmation.

Load `references/workflow.md` before doing the work. Load `references/policy-cheatsheet.md` when the user's sources are for 内蒙古准格尔旗力量煤业有限公司 or when the user provides the same buyer information. Load `references/address-books-2026-04.md` when the user asks to核对手机号/人员 or does not provide a newer company/mine address book. Load `references/bundled-workbooks.md` when the task needs HR roster data, phone/fuel reimbursement eligibility records, or bundled workbook paths.

## Operating Rules

- Treat the provided reimbursement template as authoritative for layout and formatting. If the user does not provide a newer template, use the bundled `assets/templates/通讯费第1季度.docx`. Copy the template first, then fill only the required data cells. Do not redesign tables, widths, row heights, fonts, font sizes, bold/italic settings, alignment, borders, cell shading, merged cells, signature rows, formulas, page margins, headers, footers, or totals layout.
- Preserve every visual and structural setting from the template unless the user explicitly asks for a formatting change. When adding rows, duplicate the nearest matching template row style and merged-cell behavior; never create fresh formatting from defaults.
- Treat user-provided current HR rosters and reimbursement eligibility ledgers as authoritative. If the user does not provide newer files, use the bundled workbooks under `assets/data/` and consult `references/bundled-workbooks.md` for their sheet structure.
- Treat the newest user-provided policy source as authoritative. Use the cheat sheet only as a starting point and replace it when a newer制度汇编 or福利明细 says otherwise.
- Fill phone numbers from the newest available address books, not from invoices, when the address book and invoice disagree. If no newer address book is provided, use the bundled 2026年4月 company/mine address book reference. Record every discrepancy in the exception list.
- Fill the template `级别` column by display priority: (1) if the person record has an explicit level/grade after the person's name or in a dedicated grade field, use that level; (2) if the reimbursement eligibility comes from a named honor or special qualification such as 年度劳模 or 优秀班组长, display the exact year/title from the source, such as `2025年优秀班组长`; (3) if no explicit level exists, use the person's岗位名称 from `2026年：电话费、燃油费报销人员统计.xlsx` or the newest phone/fuel reimbursement personnel ledger. For 专员类人员, write the岗位名称 rather than a generic approval category. Do not fill this column from `报销依据` or approval-source wording such as `请示审批报销`; keep those only in audit evidence or the exception/check report.
- Sort reimbursement-detail people by resolved personnel level from high to low before assigning `序号` or filling final rows. The sort key is for ordering only; it must not override the separate template `级别` display-priority rule. Use the hierarchy in `references/policy-cheatsheet.md`; preserve source order for people at the same level, and place unresolved levels last with an exception/check note.
- Never silently invent a missing person, phone number, month, grade, invoice amount, or buyer field. Leave it blank or mark it as pending confirmation in the exception list.
- Treat `发票金额` as the original invoice or billing amount for that person-month, and independently calculate `实报金额` from the monthly reimbursement standard. Do not copy invoice amount into reimbursed amount when the invoice amount exceeds the standard.
- Exclude over-cap amounts from reimbursement: for each person and month, `实报金额 = min(发票金额, 报销标准)`, and `超额不予报销金额 = max(发票金额 - 报销标准, 0)`. Record over-cap cases in the exception/check report or a calculation audit table.
- After the reimbursement detail table is filled, use it as the ordering authority for invoice assembly. Group invoice files by department and merge each department's invoices in the same person/month order shown in the reimbursement detail table. Do not sort invoices by filename, file creation time, or invoice number when that conflicts with the detail-table order.
- Use exact money math with two decimal places for final display. Preserve formulas in the template when possible; if formulas must be replaced, explain why.
- Keep audit evidence: source filename, page/sheet if available, row or invoice number, normalized phone number, and the decision made.

## Workflow

1. Inventory the source files and identify their roles: policy, HR roster, company address book, mine address book, invoice PDFs/images/amount sheet, and reimbursement template.
2. Read the template structure first. Note table headers, repeated monthly rows, merged cells, total rows, signature rows, fonts, alignment, borders, column widths, row heights, page margins, headers, footers, and formulas before filling anything.
3. Extract the reimbursement rules from the policy. Identify eligible grade/position, monthly cap, start-month rule, attendance limitations, and reimbursement principle.
4. Build a personnel lookup from the HR roster with name, department, position, grade, employment status, and any notes that affect eligibility, but resolve the template `级别` display value by the priority rule: explicit person-level grade first, named honor/special qualification with year/title second, ledger岗位名称 third. Use HR fields only as a fallback for missing ledger evidence, and record that fallback in the exception/check report.
5. Extract both address books into a contact lookup. Normalize names and phone numbers, then resolve duplicate names by department or exact phone match.
6. Extract each invoice or invoice amount record. Capture invoice number, date, service period, phone/account number, amount, buyer name, tax number, address/phone, bank, and bank account.
7. Validate invoice buyer information against the expected company information. Normalize spaces in tax numbers and bank accounts before comparing.
8. Match invoices to people by phone number first, then by person name only when the phone number is missing or unclear. Cross-check every match against HR roster and both address books.
9. Resolve each person's ordering level from the newest available grade/position evidence, then sort people from high to low before assigning serial numbers. Keep same-level people in the source/detail order unless the user gives another tie-breaker.
10. Split amounts by person and month according to the invoice period and the template period. Recalculate both `发票金额` and `实报金额` at the person-month level. Apply the policy cap per person per month: reimbursed amount is the lesser of invoice amount and monthly standard unless the policy says otherwise, and the excess is not reimbursed.
11. Fill the copied template using the existing row pattern and template formatting exactly. If more people are needed than the template has, copy existing data rows and preserve styles, fonts, borders, formulas, row heights, column widths, and merged-cell behavior.
12. If invoice PDF/image files are provided, assemble department-level invoice PDFs after the reimbursement detail table is complete. Build the merge order from the filled detail table, group by department, and preserve each original invoice page without resizing or editing its content unless conversion is required for image invoices.
13. Create an exception list for phone mismatches, missing contacts, duplicate names, HR/address-book disagreements, unresolved ordering levels, invoice buyer mismatches, amount-over-cap cases, missing invoice fields, and any invoice file that cannot be matched or ordered.
14. Render or otherwise visually inspect the final reimbursement file and merged invoice PDFs. Check that totals, page layout, signatures, table alignment, invoice page count, and department invoice order are correct.

## Outputs

Produce these artifacts when enough source data is available:

- Filled reimbursement file in the same family as the template (`.docx` or `.xlsx`), with the original formatting preserved. When using the bundled template, output a copied and filled `.docx`, never modify the bundled asset in place.
- Department-level merged invoice PDFs when invoice files are available. Name them clearly by department, and order invoices exactly as the department's people/months appear in the reimbursement detail table.
- Exception/check report (`.md`, `.xlsx`, or appended table as appropriate) listing every item requiring explanation or manual confirmation.
- Short final summary with output paths, total invoice amount, total reimbursed amount, and the count of exceptions.

If the user asks only to set up the reusable workflow, create or update this skill rather than processing a reimbursement package immediately.
