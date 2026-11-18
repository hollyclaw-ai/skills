---
name: csv-report
description: Build short Markdown reports from CSV files (summaries, group-bys, simple charts). Use when the user asks to analyze a CSV/TSV spreadsheet export or turn tabular data into a concise report — not for PDF forms, databases, or travel booking.
---

# CSV Report

Turn a CSV/TSV into a concise Markdown report with explicit assumptions.

## When to Use

- User provides a CSV/TSV (or path) and wants summary stats, group-bys, or a short written report
- Don't use for: PDF/form filling, SQL/database migrations, travel/booking, or generic "help with files"

## Procedure

1. Confirm the file path and schema (column names, delimiter, encoding). Done when columns are listed back to the user.
2. Ask or infer the report goal (overview, top-N, anomaly scan). Done when the goal is one sentence.
3. Compute only the metrics needed for that goal; show units and row counts. Done when numbers are reproducible from the file.
4. Write a short Markdown report: goal, key figures, caveats. Done when caveats include missing values and filter choices.

## Pitfalls

- Wide over-trigger descriptions pull in unrelated file tasks — keep description scoped to CSV/TSV reporting.
- Do not invent rows; if the file is missing, stop and ask.
