## zn: the local security layer for coding agents

Use Claude Code, Codex CLI, Cursor or OpenCode without exposing your secrets, your data or your systems. **zn-gate** runs on your machine, between your agent and the tools and content it touches. It is open source (MIT), runs locally with no account, and sends nothing off your machine by default.

```bash
npx -y zn-gate init
```

`init` finds the coding agents on your machine and sets up each one after you confirm it. Then `npx -y zn-gate check` shows whether each agent is protected.

- **Scrubber**: keeps secret values (API keys, tokens, private keys, database passwords) out of what your agent sends to its model.
- **Galvanize**: checks what your agent reads and calls for prompt injection with a local rules engine; prompts can also go to the Galvanize 2 cloud classifier, only if you turn it on.
- **Scan**: audits prompt templates, `AGENTS.md` / `SKILL.md` files and configs for injection traps and leaked secrets.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/usezn/zn/main/docs/diagrams/data-flow-dark.svg">
  <img alt="Flow diagram. The agent, zn-gate and the tools or MCP servers run on your machine, and tool calls and prompts go through zn-gate. Tool output comes back redacted. Nothing leaves the machine by default. Only with ZN_CLOUD=1 and ZN_API_KEY set (or the Claude Code plugin's API key option), prompts with detected secrets removed go to api.usezn.com, the Galvanize 2 classifier." src="https://raw.githubusercontent.com/usezn/zn/main/docs/diagrams/data-flow-light.svg" width="800">
</picture>

**Links:** [usezn.com](https://usezn.com) · [Docs](https://usezn.com/docs/) · [zn-gate on GitHub](https://github.com/usezn/zn) · [Galvanize 2 on Hugging Face](https://huggingface.co/usezn/Galvanize-2) · [Security policy](https://github.com/usezn/zn/blob/main/SECURITY.md)
