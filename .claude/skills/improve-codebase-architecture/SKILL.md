# Improve Codebase Architecture

Explore a codebase like an AI would, surface architectural friction, discover opportunities for improving testability, and propose module-deepening refactors as GitHub issue RFCs.

A **deep module** (John Ousterhout, "A Philosophy of Software Design") has "a small interface hiding a large implementation." Deep modules enhance testability, AI-navigability, and enable boundary-level testing rather than internal testing.

## Process

### 1. Explore the codebase

Use the Agent tool with subagent_type=Explore to navigate organically. Do NOT follow rigid heuristics — note friction points:

- Understanding one concept requires bouncing between many small files?
- Modules so shallow that interface complexity rivals implementation complexity?
- Pure functions extracted for testability, but real bugs hide in call patterns?
- Tightly-coupled modules creating integration risk at seams?
- Untested or hard-to-test parts?

The friction you experience IS the signal.

### 2. Present candidates

Present a numbered list of deepening opportunities. For each candidate, show:

- **Cluster**: Which modules/concepts are involved
- **Why they're coupled**: Shared types, call patterns, co-ownership of a concept
- **Dependency category**: See [REFERENCE.md](REFERENCE.md) for the four categories
- **Test impact**: What existing tests would be replaced by boundary tests

Ask the user: "Which of these would you like to explore?"

### 3. User picks a candidate

### 4. Frame the problem space

Write a user-facing explanation of the problem space for the chosen candidate:

- The constraints any new interface would need to satisfy
- The dependencies it would need to rely on
- A rough illustrative code sketch to make the constraints concrete

Show this to the user, then proceed to Step 5.

### 5. Design multiple interfaces

Spawn 3+ sub-agents in parallel using the Agent tool. Each must produce a **radically different** interface for the deepened module.

Prompt each sub-agent with a separate technical brief. Give each agent a different design constraint:

- Agent 1: "Minimize the interface — aim for 1-3 entry points max"
- Agent 2: "Maximize flexibility — support many use cases and extension"
- Agent 3: "Optimize for the most common caller — make the default case trivial"
- Agent 4 (if applicable): "Design around the ports & adapters pattern for cross-boundary dependencies"

Each sub-agent outputs:

1. Interface signature (types, methods, params)
2. Usage example showing how callers use it
3. What complexity it hides internally
4. Dependency strategy (how deps are handled — see [REFERENCE.md](REFERENCE.md))
5. Trade-offs

Present designs sequentially, then compare them. Provide your own recommendation: which design is strongest and why. Propose hybrids if beneficial. Be opinionated.

### 6. User picks an interface (or accepts recommendation)

### 7. Create GitHub issue

Create a refactor RFC as a GitHub issue using `gh issue create`. Use the template in [REFERENCE.md](REFERENCE.md). Just create it and share the URL.
