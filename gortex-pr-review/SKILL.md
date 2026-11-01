---
name: gortex-pr-review
description: "Graph-grounded review of a pending change or PR."
---
# Review a Change with Gortex

1. Project the working tree with `change({operation: "detect", source: {scope: "unstaged"}})`; use `staged` or `compare` only when that is the requested review scope.
2. Build review context with `review({operation: "run", source: {scope: "<scope>"}})` and operation `diff_context` when per-file context is needed.
3. Require `change` operations `guards`, `tests`, and `contract`. When the proposed signature is known, run operation `verify` before mutation.
4. Check wire boundaries with `analyze({kind: "contracts", options: {action: "check"}})` when APIs or events changed.
5. Report only actionable findings with severity, `file:line`, evidence, consequence, and correction. State an explicit clean verdict when none remain.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
