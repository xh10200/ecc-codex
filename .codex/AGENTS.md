# ECC for Codex CLI

This supplements the root `AGENTS.md` with Codex-specific guidance.

The repository is intentionally local-only: no project workflow should depend
on remote documentation lookup, remote connectors, hosted research tools, or
subprocess patterns that require additional online model calls.

## Model Recommendations

| Task Type | Recommended Model |
|-----------|------------------|
| Routine coding, tests, formatting | GPT 5.4 |
| Complex features, architecture | GPT 5.4 |
| Debugging, refactoring | GPT 5.4 |
| Security review | GPT 5.4 |

## Skills Discovery

Skills are auto-loaded from `.agents/skills/`. Each skill contains:
- `SKILL.md` — Detailed instructions and workflow

Available skills:
- api-design — REST API design patterns
- bun-runtime — Bun runtime and package-manager workflow
- coding-standards — Universal coding standards
- e2e-testing — Playwright E2E tests
- eval-harness — Eval-driven development
- frontend-patterns — React/Next.js frontend patterns
- golang-patterns — Idiomatic Go development patterns
- golang-testing — Go testing and TDD patterns
- nextjs-turbopack — Next.js and Turbopack workflow
- python-patterns — Idiomatic Python development patterns
- python-testing — Python testing and pytest patterns
- security-review — Comprehensive security checklist
- tdd-workflow — Test-driven development with 80%+ coverage
- verification-loop — Build, test, lint, typecheck, security

## Local-Only Runtime

Treat the project-local `.codex/config.toml` as a local execution baseline:

- no project-managed remote connectors
- no remote documentation lookup
- no repo-managed web search or discovery tooling
- no subprocess workflows that require additional online model sessions

## Multi-Agent Support

Codex now supports multi-agent workflows behind the experimental `features.multi_agent` flag.

- Enable it in `.codex/config.toml` with `[features] multi_agent = true`
- Define project-local roles under `[agents.<name>]`
- Point each role at a TOML layer under `.codex/agents/`
- Use `/agent` inside Codex CLI to inspect and steer child agents

Core role configs in this repo include:
- `.codex/agents/planner.toml` — implementation planning
- `.codex/agents/architect.toml` — architecture analysis
- `.codex/agents/code-reviewer.toml` — correctness and maintainability review
- `.codex/agents/security-reviewer.toml` — security review
- `.codex/agents/go-reviewer.toml` — Go review
- `.codex/agents/python-reviewer.toml` — Python review
- `.codex/agents/typescript-reviewer.toml` — TypeScript review
- `.codex/agents/database-reviewer.toml` — database review
- `.codex/agents/gan-planner.toml`, `.codex/agents/gan-generator.toml`, `.codex/agents/gan-evaluator.toml` — rapid frontend prototype loop

## Codex Runtime Notes

- `AGENTS.md` is the repository entry point.
- Skills are surfaced from `.agents/skills/`.
- Multi-agent roles are defined in `.codex/config.toml` and `.codex/agents/*.toml`.
- The stable sub-agent entry point is `/agent <name> <task>`.
- External integrations are intentionally excluded from the project baseline.
- Safety is enforced through instructions, sandboxing, approval policy, and explicit verification steps.

## Security Without Hooks

Since Codex lacks hooks, security enforcement is instruction-based:
1. Always validate inputs at system boundaries
2. Never hardcode secrets — use environment variables
3. Run `npm audit` / `pip audit` before committing
4. Review `git diff` before every push
5. Use `sandbox_mode = "workspace-write"` in config
