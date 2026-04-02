---
paths:
  - "**/*.ts"
  - "**/*.tsx"
  - "**/*.js"
  - "**/*.jsx"
---
# TypeScript/JavaScript Hooks

> This file extends [common/hooks.md](../common/hooks.md) with TypeScript/JavaScript specific content.

## Recommended Post-Edit Verification

- **Prettier**: Format changed JS/TS files immediately after editing
- **TypeScript check**: Run `tsc` for the owning config of changed `.ts`/`.tsx` files
- **console.log warning**: Flag `console.log` in edited files unless it is intentionally temporary

## Before Finishing

- Run the nearest relevant test command for the changed code
- Audit modified files for stray `console.log` or debug scaffolding
