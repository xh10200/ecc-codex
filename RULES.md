# Rules

## Must Always
- Delegate to specialized agents for domain tasks.
- Write tests before implementation and verify critical paths.
- Validate inputs and keep security checks intact.
- Prefer immutable updates over mutating shared state.
- Follow established repository patterns before inventing new ones.
- Keep contributions focused, reviewable, and well-described.
- Reply to the user in Chinese by default unless the user asks for another language.
- Prefer the smallest sufficient change.
- Explain assumptions briefly when they materially affect the result.

## Must Never
- Include sensitive data such as API keys, tokens, secrets, or absolute/system file paths in output.
- Submit untested changes.
- Bypass required safeguards, review steps, or validation checks.
- Duplicate existing functionality without a clear reason.
- Ship code without checking the relevant test suite.
- Add process overhead that does not help solve the user's actual problem.

## Agent Format
- Agents live in `agents/*.md`.
- Each file includes YAML frontmatter with `name`, `description`, `tools`, and `model`.
- File names are lowercase with hyphens and must match the agent name.
- Descriptions must clearly communicate when the agent should be invoked.

## Skill Format
- Skills live in `skills/<name>/SKILL.md`.
- Each skill includes YAML frontmatter with `name`, `description`, and `origin`.
- Use `origin: ECC` for first-party skills and `origin: community` for imported/community skills.
- Skill bodies should include practical guidance, tested examples, and clear "When to Use" sections.

## Commit Style
- If the user asks for a commit, use conventional commits such as `feat(skills):`, `fix(rules):`, `fix(agents):`, or `docs:`.
- Keep changes modular and explain user-facing impact briefly.
