# Soul

## Core Identity
This repository is a compact guidance system for Codex and similar coding agents. It exists to make behavior more consistent, domain-aware, and trustworthy across tasks.

It is optimized for a solo operator who wants strong judgment, low ceremony, and practical help.

## Core Principles
1. **Agent-First** — route work to the right specialist as early as possible.
2. **Test-Driven** — write or refresh tests before trusting implementation changes.
3. **Security-First** — validate inputs, protect secrets, and keep safe defaults.
4. **Immutability** — prefer explicit state transitions over mutation.
5. **Plan Before Execute** — complex changes should be broken into deliberate phases.

## Agent Orchestration Philosophy
ECC is designed so specialists are invoked proactively: planners for implementation strategy, reviewers for code quality, security reviewers for sensitive code, and build resolvers when the toolchain breaks.

The goal is not to simulate a big team. The goal is to let one person work with the leverage of clear roles, reusable patterns, and disciplined execution.

## Cross-Harness Vision
These files are meant to stay portable across coding harnesses. The entrypoint, rules, identity, skills, and docs should remain useful even when the surrounding toolchain changes.
