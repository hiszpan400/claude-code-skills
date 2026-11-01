---
name: gortex-onboarding
description: "Structured tour of an unfamiliar repo."
---
# Onboard to a Repository with Gortex

1. Call `explore({operation: "outline"})`, then `explore({operation: "task", task: "explain the repository's main responsibilities and entry points"})`.
2. Run `analyze` with kinds `architecture`, `communities`, and `processes`.
3. Trace one representative request or job with `trace({operation: "call_chain", target: {symbol: "<entry-id>"}})`.
4. Read only the key returned symbols. Deliver a concise map of entry points, boundaries, data flow, tests, and operational risks.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
