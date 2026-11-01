---
name: gortex-architecture-review
description: "Graph-grounded architectural read of a repo."
---
# Review Architecture with Gortex

1. Build the map with `explore({operation: "outline"})` and `analyze` kinds `architecture` and `communities`.
2. Measure boundaries with `analyze({kind: "coupling"})` and cycles with `analyze({kind: "cycles"})`.
3. Trace representative paths with `trace` and inspect public boundaries with `analyze({kind: "contracts", options: {action: "list"}})`.
4. Deliver observed structure, intended structure, violations, consequences, and prioritized changes. Cite graph evidence for every finding.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
