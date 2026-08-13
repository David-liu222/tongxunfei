# Communication Fee Regression Tests

Use these cases after material rule changes. They are acceptance scenarios, not source data.

## Floating Table Person-Block Pagination

- Input: a Word template uses a page-anchored floating table (`w:tblpPr`) with vertically merged person cells, and at least two people have enough month rows to approach a page boundary.
- Expected layout: each person's complete month block stays on one rendered page; no name/position cell is separated from its month rows.
- Expected structure: page-sized table blocks preserve the original table grid, borders, merges, fonts, row heights, and column widths; the original header appears at the top of each block and the total row appears once at the end.
- Forbidden fixes: do not rely only on `keepNext`, `cantSplit`, `pageBreakBefore` on a table row, or a page break inserted inside a cell; do not leave cloned floating tables sharing the same page anchor.
- Expected validation: render every page and inspect visually; structural validation alone is insufficient. There must be no blank page, overlapping table, orphan continuation row, or duplicated total.
