# Performance Optimization

## Model Selection Strategy

**GPT-5.4-mini**:
- Lightweight agents with frequent invocation
- Exploration, classification, and summarization
- Lower-cost worker agents in multi-agent systems

**GPT-5.4**:
- Main development work
- Orchestrating multi-agent workflows
- Complex coding, debugging, and review tasks

## Context Window Management

Avoid last 20% of context window for:
- Large-scale refactoring
- Feature implementation spanning multiple files
- Debugging complex interactions

Lower context sensitivity tasks:
- Single-file edits
- Independent utility creation
- Documentation updates
- Simple bug fixes

## Reasoning And Planning

For complex tasks requiring deep reasoning:
1. Use a stronger model or higher reasoning effort when available
2. Break work into explicit phases before broad edits
3. Use multiple review passes for high-risk changes
4. Use split-role sub-agents for diverse perspectives

## Build Troubleshooting

If build fails:
1. Use **build-error-resolver** agent
2. Analyze error messages
3. Fix incrementally
4. Verify after each fix
