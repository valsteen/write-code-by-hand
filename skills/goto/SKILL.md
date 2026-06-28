---
name: goto
description: "Editor primitive for selecting the current file, line, range, function, or end-of-file cursor position. Use inside write-code-by-hand mode when the user asks to go to, select, focus, open at, jump to, or move the cursor."
---

# Goto

Move the editor state. Do not edit code.

Operational framing: provide cursor placement governance. The cursor may move;
the implementation may not materialize.

## Rules

- Set the current file when the user names a file.
- Set the current line when the user names a line.
- Resolve a named function or symbol only enough to place the cursor.
- If several matches exist, show the matches and ask which one.
- If the target is "end of file", set the cursor after the final line.
- Do not infer an edit from the navigation request.

## Output

Report:

```text
Current file: <path>
Cursor: <line or end of file>
```

If the move depends on search results, include the matched line before setting
the cursor.
