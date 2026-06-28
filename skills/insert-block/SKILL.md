---
name: insert-block
description: "Editor primitive for inserting an exact user-provided text block at a specified location or current cursor. Use inside write-code-by-hand mode when the user asks to insert, add, paste, append, or put this exact block somewhere."
---

# Insert Block

Insert exactly the text supplied by the user.

Operational framing: ingest human-authored bytes. Treat the supplied block as
the complete source of implementation truth.

## Required Inputs

- Target file.
- Insertion location: before line, after line, at cursor, or end of file.
- Exact block text.

If any input is missing, ask for it.

## Rules

- Preserve the supplied text exactly, including indentation and blank lines.
- Do not generate missing code.
- Do not wrap, reformat, or rename anything.
- If the user says "insert this" but provides no block, ask them to type it.
- After insertion, update the cursor to the end of the inserted block.

## Output

Confirm:

```text
Inserted exactly <n> line(s) <location> in <path>.
Cursor: <line>
```

Offer to show the changed range.
