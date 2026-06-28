---
name: verify
description: "Editor primitive for running exact human-selected verification commands. Use inside write-code-by-hand mode when the user asks to run tests, lint, build, format, or execute a specific command."
---

# Verify

Run the exact command selected by the user.

## Rules

- Require the user's exact command.
- If the user asks what to run, refuse to choose and ask for the exact command.
- Do not change files in response to verification failures.
- Summarize command, exit status, and the key failing or passing lines.
- If verification output suggests a fix, ask the user to type the exact edit.

## Output

Use:

```text
Command:
<command>

Result:
<passed|failed|not run>

Notes:
<short summary>
```
