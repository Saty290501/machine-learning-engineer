# Agentic Workflow Assistant

**Goal:** build a bounded workflow that uses tools under explicit policies.

## Planned engineering scope
- Define a narrow task and allowed tool set.
- Model state transitions with LangGraph or an equivalent explicit workflow.
- Validate tool inputs and outputs; add timeouts and retries.
- Require human approval for consequential actions.
- Add traces, test cases, failure injection, and task-success metrics.
- Document prompt-injection and data-exfiltration threat models.

**Status:** Planned. Do not grant broad credentials or unrestricted tool access.

