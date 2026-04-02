# Everything Claude Code (ECC) — Agent Instructions

This repository is a lightweight **personal Codex guidance base** for agent instructions, reusable skills, rules, and domain docs.

## Repository Entry Point

Treat this file as the default repository-wide instruction entry point for Codex and similar coding agents.

At the start of every task:
- Automatically apply this file as the primary working policy.
- Read `RULES.md` for hard constraints and non-negotiable guardrails.
- Read `SOUL.md` for identity, tone, and operating philosophy.
- For Codex-specific behavior, check `.codex/` and `.agents/` first when relevant material exists there.
- Then load only the relevant supporting material from `skills/`, `rules/`, `docs/`, and `agents/` based on the task domain, language, risk, and workflow stage.
- Do not wait for the user to explicitly remind you to use those files.

Priority and interpretation:
- Direct user instructions override repository preferences unless they conflict with higher-level harness or system instructions.
- `AGENTS.md` is the main execution guide.
- Codex-specific local configuration in `.codex/` and `.agents/` should be preferred over generic repository guidance when both are applicable and do not conflict with higher-level instructions.
- `RULES.md` defines concise hard rules and should be treated as stricter than advisory guidance elsewhere in the repo.
- `SOUL.md` defines persona and operating philosophy, not low-level task procedure.
- `CLAUDE.md` is a secondary compatibility/reference document and should only be consulted when it is specifically useful.

Task routing defaults:
- For implementation work, first check whether `.codex/` or `.agents/` already define Codex-specific guidance for the task.
- Otherwise identify the relevant language or domain rules under `rules/` and the matching workflow/domain skill under `skills/`.
- For risky or high-impact changes, prefer the stricter interpretation of security, testing, and review guidance.
- For ambiguous tasks, inspect the smallest relevant set of supporting files first instead of loading large portions of the repo by default.

Response defaults:
- Reply to the user in Chinese unless the user asks for another language.
- Keep answers concise by default, but expand when the task is complex or the user asks for depth.
- Optimize for practical progress over process ceremony.

## Core Principles

1. **Agent-First** — Delegate to specialized agents for domain tasks
2. **Test-Driven** — Write tests before implementation, 80%+ coverage required
3. **Security-First** — Never compromise on security; validate all inputs
4. **Immutability** — Always create new objects, never mutate existing ones
5. **Plan Before Execute** — Plan complex features before writing code

## Available Agents

| Agent | Purpose | When to Use |
|-------|---------|-------------|
| planner | Implementation planning | Complex features, refactoring |
| architect | System design and scalability | Architectural decisions |
| tdd-guide | Test-driven development | New features, bug fixes |
| code-reviewer | Code quality and maintainability | After writing/modifying code |
| security-reviewer | Vulnerability detection | Before commits, sensitive code |
| build-error-resolver | Fix build/type errors | When build fails |
| e2e-runner | End-to-end Playwright testing | Critical user flows |
| refactor-cleaner | Dead code cleanup | Code maintenance |
| docs-lookup | Documentation lookup via Context7 | API/docs questions |
| go-reviewer | Go code review | Go projects |
| go-build-resolver | Go build errors | Go build failures |
| database-reviewer | PostgreSQL/Supabase specialist | Schema design, query optimization |
| python-reviewer | Python code review | Python projects |
| loop-operator | Autonomous loop execution | Run loops safely, monitor stalls, intervene |
| harness-optimizer | Harness config tuning | Reliability, cost, throughput |
| typescript-reviewer | TypeScript/JavaScript code review | TypeScript/JavaScript projects |
| gan-planner | Frontend prototype planning | Rapid GAN-style prototype specs |
| gan-generator | Frontend prototype generation | Rapid GAN-style prototype implementation |
| gan-evaluator | Frontend prototype evaluation | GAN-style prototype testing and scoring |

## Agent Orchestration

Use agents proactively without user prompt:
- Complex feature requests → **planner**
- Code just written/modified → **code-reviewer**
- Bug fix or new feature → **tdd-guide**
- Architectural decision → **architect**
- Security-sensitive code → **security-reviewer**
- Autonomous loops / loop monitoring → **loop-operator**
- Harness config reliability and cost → **harness-optimizer**

Use parallel execution for independent operations — launch multiple agents simultaneously.

## Security Guidelines

**Before finishing any non-trivial change:**
- No hardcoded secrets (API keys, passwords, tokens)
- All user inputs validated
- SQL injection prevention (parameterized queries)
- XSS prevention (sanitized HTML)
- CSRF protection enabled
- Authentication/authorization verified
- Rate limiting on all endpoints
- Error messages don't leak sensitive data

**Secret management:** NEVER hardcode secrets. Use environment variables or a secret manager. Validate required secrets at startup. Rotate any exposed secrets immediately.

**If security issue found:** STOP → use security-reviewer agent → fix CRITICAL issues → rotate exposed secrets → review codebase for similar issues.

## Coding Style

**Immutability (CRITICAL):** Always create new objects, never mutate. Return new copies with changes applied.

**File organization:** Many small files over few large ones. 200-400 lines typical, 800 max. Organize by feature/domain, not by type. High cohesion, low coupling.

**Error handling:** Handle errors at every level. Provide user-friendly messages in UI code. Log detailed context server-side. Never silently swallow errors.

**Input validation:** Validate all user input at system boundaries. Use schema-based validation. Fail fast with clear messages. Never trust external data.

**Code quality checklist:**
- Functions small (<50 lines), files focused (<800 lines)
- No deep nesting (>4 levels)
- Proper error handling, no hardcoded values
- Readable, well-named identifiers

## Testing Requirements

**Minimum coverage: 80%**

Test types (all required):
1. **Unit tests** — Individual functions, utilities, components
2. **Integration tests** — API endpoints, database operations
3. **E2E tests** — Critical user flows

**TDD workflow (mandatory):**
1. Write test first (RED) — test should FAIL
2. Write minimal implementation (GREEN) — test should PASS
3. Refactor (IMPROVE) — verify coverage 80%+

Troubleshoot failures: check test isolation → verify mocks → fix implementation (not tests, unless tests are wrong).

## Development Workflow

1. **Clarify** — Restate the goal, constraints, and likely risk level
2. **Load Minimal Context** — Read only the relevant `rules/`, `skills/`, `docs/`, and `agents/` files
3. **Implement Incrementally** — Prefer small, reviewable changes over broad rewrites
4. **Verify** — Run the smallest meaningful checks first, then broaden if risk is high
5. **Summarize Clearly** — Report what changed, what was verified, and any remaining risk in Chinese

## Personal Workflow Defaults

- Prefer direct execution over long planning unless the task is genuinely complex.
- Prefer the minimum number of files and the minimum scope of change needed to solve the problem.
- Avoid creating new top-level files unless they clearly improve the long-term usability of this repo.
- Favor reusable skills and rules over repeating the same instructions in every conversation.
- Treat this repo as a long-lived personal operating manual for Codex, not as a product to package for others.

## Workflow Surface Policy

- `skills/` is the canonical workflow surface.
- New workflow contributions should land in `skills/`, `rules/`, `docs/`, or `agents/` based on whether they represent workflow logic, hard constraints, reference knowledge, or role definitions.
- Keep the root concise: only entrypoint and high-signal policy files should live there.

## Git Workflow

- Only think about commits when the user explicitly asks for commit help.
- If a commit is requested, use a conventional format such as `<type>: <description>`.

## Architecture Patterns

**API response format:** Consistent envelope with success indicator, data payload, error message, and pagination metadata.

**Repository pattern:** Encapsulate data access behind standard interface (findAll, findById, create, update, delete). Business logic depends on abstract interface, not storage mechanism.

**Skeleton projects:** Search for battle-tested templates, evaluate with parallel agents (security, extensibility, relevance), clone best match, iterate within proven structure.

## Performance

**Context management:** Avoid last 20% of context window for large refactoring and multi-file features. Lower-sensitivity tasks (single edits, docs, simple fixes) tolerate higher utilization.

**Build troubleshooting:** Use build-error-resolver agent → analyze errors → fix incrementally → verify after each fix.

## Project Structure

```
AGENTS.md        — repository entry point and execution guide
RULES.md         — hard constraints and guardrails
SOUL.md          — identity, tone, and operating philosophy
CLAUDE.md        — secondary Claude-specific compatibility note
agents/          — specialized subagent definitions
skills/          — workflow skills and domain knowledge
rules/           — always-follow guidelines and language/domain rules
docs/            — reference material and supporting context
.agents/         — Codex-adjacent agent assets and reusable local helper surfaces
.codex/          — Codex-specific local configuration and overrides
```

This repository is intentionally trimmed to the core assets that help Codex and similar agents work more consistently.

## Success Metrics

- The user is unblocked quickly.
- The change is correct, minimal, and easy to understand.
- Verification matches the actual risk of the task.
- Security and data-handling mistakes are avoided.
