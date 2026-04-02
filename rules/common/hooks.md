# Local Automation And Verification

These rules describe recommended local automation points for Codex workflows.
They are guidance, not executable hook registrations. In this repository,
automation should live in repo-local scripts, task runners, editor actions,
git hooks, CI jobs, or explicit verification commands run by the agent.

## Recommended Phases

- **Before editing**: Validate scope, locate the owning package or project, and choose the smallest safe verification command.
- **After editing**: Run formatting, linting, type checks, or package-level verification for the files you changed.
- **Before finishing**: Run the narrowest final check that matches the risk of the change.

## Permissions And Automation

Use automation with caution:
- Prefer repo-local commands over machine-global configuration
- Prefer narrowly scoped checks over broad, expensive runs
- Do not bypass Codex approval and sandbox controls with unsafe global automation
- If a check is important and repeatable, encode it in the repo with scripts, `Makefile`, or package manager commands

## Planning Best Practices

For multi-step work:
- Keep a short task plan
- Verify the goal before broad edits
- Surface risky or blocking checks early
- Record what was actually verified before finishing

A good plan helps reveal:
- Steps in the wrong order
- Missing verification
- Unnecessary work
- Overly broad edits
- Misread requirements
