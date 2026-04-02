---
paths:
  - "**/*.py"
  - "**/*.pyi"
---
# Python Hooks

> This file extends [common/hooks.md](../common/hooks.md) with Python specific content.

## Recommended Post-Edit Verification

- **black/ruff**: Format changed `.py` files immediately after editing
- **mypy/pyright**: Run type checking for the touched module or package when the project uses it

## Warnings

- Warn about `print()` statements in edited files (prefer the `logging` module instead)

## Before Finishing

- Run the nearest relevant test target for the changed Python code
- Prefer targeted pytest commands before broad suite runs
