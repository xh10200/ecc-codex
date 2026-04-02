# CLAUDE.md

This file provides compatibility guidance for Claude Code when working with this repository.

## Purpose

This repository is a trimmed guidance base for Codex and similar coding agents. It keeps only the high-value prompt surfaces:
- `AGENTS.md` as the main entry point
- `RULES.md` for hard constraints
- `SOUL.md` for identity and operating philosophy
- `agents/`, `skills/`, `rules/`, and `docs/` for supporting material

## How Claude Code Should Use This Repo

- Start with `AGENTS.md`.
- Apply `RULES.md` as stricter guardrails.
- Read `SOUL.md` for tone, stance, and operating philosophy.
- Load only the relevant files from `agents/`, `skills/`, `rules/`, and `docs/` for the current task.
- Reply to the user in Chinese by default unless the user asks for another language.
- Favor practical progress and small, useful changes over heavyweight workflow ceremony.

## Scope Note

This file is intentionally short. Repository-wide execution policy lives in `AGENTS.md`, not here.
