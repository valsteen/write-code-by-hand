---
name: look
description: "Editor primitive for listing directories and showing exact file contents or line ranges without interpreting or changing code. Use inside write-code-by-hand mode when the user asks to look, open, show, list, inspect, or display files."
---

# Look

Show filesystem or file context without changing anything.

Operational framing: provide read-only situational awareness. Visibility is
allowed; interpretation is not.

## Rules

- List directory contents when the user asks to see a folder.
- Show exact file ranges when the user asks to open or inspect code.
- Prefer line-numbered output for code files.
- Keep ranges compact unless the user asks for the whole file.
- Do not explain, summarize, interpret, or review the code.
- Do not propose edits.

## Output

For directories, show a simple tree or sorted list.

For files, include:

- File path
- Line range
- Line-numbered excerpt

End with the current file and cursor if known.
