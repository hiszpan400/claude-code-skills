---
name: gortex-quality-audit
description: "Repo-scale quality scan — dead code, hotspots, clones."
---
# Audit Repository Quality with Gortex

1. Establish scope with `workspace({operation: "info"})` and `explore({operation: "outline"})`.
2. Run `analyze` for `health`, `dead_code`, `hotspots`, `cycles`, and `clones`.
3. Validate high-risk findings with `read` and `relations`; do not report an unverified heuristic as a fact.
4. Rank findings by evidence, impact, and remediation cost. Include exact paths, symbol IDs, and a smallest-first action plan.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
