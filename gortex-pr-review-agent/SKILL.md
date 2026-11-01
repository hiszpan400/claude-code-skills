---
name: gortex-pr-review-agent
description: "Coding-agent review verdict via the gortex review verb."
---
# Review a Change as a Sub-Agent

## MCP-capable harness

Native Gortex MCP is mandatory. Call `review({operation: "run", source: {scope: "<scope>"}})`, then use `change` operations `guards`, `tests`, and `contract`. When the proposed signature is known, run operation `verify` before mutation. If the configured callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or use the Bash path below.

## Bash-only harness

Use this path only when the harness has no MCP transport by design:

```bash
gortex review --audience agent --format json
```

In either mode, return `VERDICT: clean` or `VERDICT: findings` followed by actionable findings with severity and `file:line`. Do not replace graph-backed review with ad-hoc `git diff` inspection.
