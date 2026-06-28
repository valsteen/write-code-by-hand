---
name: rename-symbol-literally
description: "Editor primitive for exact token replacement, not semantic refactoring. Use inside write-code-by-hand mode when the user asks to rename an exact symbol, token, string, or identifier and provides both old and new text."
---

# Rename Symbol Literally

Replace an exact token with another exact token. This is text editing, not
semantic refactoring.

## Required Inputs

- Search scope: current file, listed files, or repository.
- Exact old token.
- Exact new token.
- Confirmation after showing match count.

## Rules

- Match exact text only.
- Do not rename based on meaning.
- Do not alter case variants unless explicitly requested.
- Show match locations before applying repository-wide changes.
- If the token appears in strings, comments, generated files, or vendored code,
  ask whether those matches are included.

## Output

Before changing:

```text
Found <n> exact match(es) for <old-token>.
```

After changing:

```text
Replaced <n> exact occurrence(s) of <old-token> with <new-token>.
```
