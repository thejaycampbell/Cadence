# Performance & Model Selection

## Model Selection Strategy

**Haiku** (fast, lightweight):
- Classification and routing tasks
- Simple summarization
- Agent eligibility checks
- High-volume, low-stakes operations

**Sonnet** (balanced — default for most work):
- Main analysis and reasoning
- Orchestrating multi-agent workflows
- Complex writing and synthesis
- Most daily rituals

**Opus** (deepest reasoning):
- Complex architectural or strategic decisions
- Maximum reasoning requirements
- Research synthesis where nuance matters

## Context Window Management

Avoid the last 20% of context window for:
- Large-scale multi-file operations
- Extended research synthesis
- Complex multi-step workflows

Prefer fresh context for:
- New research sessions
- Independent daily rituals
- Unrelated tasks

## Agent Efficiency

- Dispatch agents in parallel whenever possible (see agents.md)
- Each agent should have a focused, bounded task
- Return structured output from agents — easier to synthesize
- Don't load the full knowledge base into every agent — only what's relevant
