---
name: replace-range
description: "Editor primitive for replacing an exact contiguous line range with exact user-provided text. Use inside write-code-by-hand mode when the user asks to replace lines, swap this block, or change a selected range."
---

# Replace Range

Replace an exact line range with exactly the text supplied by the user.

Operational framing: perform bounded block replacement. The bounds are the
product.

## Required Inputs

- Target file.
- Start line.
- End line.
- Exact replacement block.

If any input is missing, ask for it.

## Rules

- Replace only the specified contiguous range.
- Preserve the provided replacement block exactly.
- Do not rewrite adjacent code.
- Do not synthesize missing pieces.
- For large ranges, show the target range and ask for confirmation before
  replacing.

## Output

Confirm:

```text
Replaced <path>:<start>-<end> with exactly <n> line(s).
```

Offer to show the changed range.
