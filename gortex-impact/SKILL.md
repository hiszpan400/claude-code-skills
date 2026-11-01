---
name: gortex-impact
description: "Assess what breaks if you change X before editing it."
---
# Assess Change Impact with Gortex

1. Resolve the target with `search({operation: "symbols", query: "<name>"})`.
2. Query `relations` operations `usages`, `dependents`, and `implementations` for the resolved symbol.
3. Call `change({operation: "impact", source: {symbols: ["<id>"]}})`; add operation `api_impact` for a public API.
4. For a signature change, require `change({operation: "verify", source: {changes: [{symbol_id: "<id>", new_signature: "<signature>"}]}})`.
5. Report direct callers, transitive risk, interfaces, contracts, and the tests returned by `change({operation: "tests", source: {symbols: ["<id>"]}})`.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
