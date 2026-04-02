---
paths:
  - "**/*.go"
  - "**/go.mod"
  - "**/go.sum"
---
# Go Hooks

> This file extends [common/hooks.md](../common/hooks.md) with Go specific content.

## Recommended Post-Edit Verification

- **gofmt/goimports**: Format changed `.go` files immediately after editing
- **go vet**: Run static analysis on the touched package or module
- **staticcheck**: Run extended static analysis on modified packages when available

## Before Finishing

- Re-run the narrowest relevant `go test` command for the affected package
- If `go.mod` or `go.sum` changed, verify dependency and build health at the module level
