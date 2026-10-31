## zn: the local security layer for coding agents

Use Claude Code, Codex CLI, Cursor or OpenCode without exposing your secrets, your data or your systems. **zn-gate** runs on your machine, between your agent and the tools and content it touches. It is open source (MIT), runs locally with no account, and sends nothing off your machine by default.

```bash
npx -y zn-gate init
```

`init` finds the coding agents on your machine and sets up each one after you confirm it. Then `npx -y zn-gate check` shows whether each agent is protected.

- **Scrubber**: keeps secret values (API keys, tokens, private keys, database passwords) out of what your agent sends to its model.
- **Galvanize**: checks what your agent reads and calls for prompt injection with a local rules engine; prompts can also go to the Galvanize 3 cloud classifier ([open weights on Hugging Face](https://huggingface.co/usezn/Galvanize-3)), only if you turn it on. On our own test set of 3,309 examples it catches 89.6% of attacks at a 0.6% false positive rate, and it flags 2.9% of 658 long legitimate documents; these figures are for the cloud classifier only, not for the local rules.
- **Scan**: checks MCP servers, prompt templates and agent config files (`AGENTS.md`, `SKILL.md`) for injection traps and leaked secrets.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/usezn/zn/main/docs/diagrams/data-flow-dark.svg">
  <img alt="Flow diagram. The agent, zn-gate and the tools or MCP servers run on your machine, and tool calls and prompts go through zn-gate. Tool output comes back redacted. Nothing leaves the machine by default. Only with ZN_CLOUD=1 and ZN_API_KEY set (or the Claude Code plugin's API key option), prompts with detected secrets removed go to api.usezn.com, the Galvanize 3 classifier." src="https://raw.githubusercontent.com/usezn/zn/main/docs/diagrams/data-flow-light.svg" width="800">
</picture>

**Links:** [usezn.com](https://usezn.com) · [Docs](https://usezn.com/docs/) · [zn-gate on GitHub](https://github.com/usezn/zn) · [Galvanize 3 on Hugging Face](https://huggingface.co/usezn/Galvanize-3) · [Galvanize 2 (previous model) on Hugging Face](https://huggingface.co/usezn/Galvanize-2) · [Prompt-injection evaluation corpus on Hugging Face](https://huggingface.co/datasets/usezn/zn-prompt-injection-bench) · [Security policy](https://github.com/usezn/zn/blob/main/SECURITY.md)
