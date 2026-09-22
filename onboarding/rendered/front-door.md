## Quick start

Pipelex runs your AI methods — write a method once, then run it from your agent via MCP, turn it into a webapp, or use it via API in any software.

**1. Sign up at [app.pipelex.com](https://app.pipelex.com).**

**2. Install the plugin for your agent.**

<details open><summary><b>Claude Code</b></summary>

```bash
claude plugin marketplace add Pipelex/pipelex-plugins
claude plugin install pipelex@pipelex-plugins
```

Claude asks for an API key when you enable the plugin, and stores it in your OS keychain — create one in your console at [app.pipelex.com](https://app.pipelex.com). The `.mthds` validation hook and the Pipelex MCP tools load with it; nothing else to install.

</details>

<details><summary><b>Codex</b></summary>

```bash
codex plugin marketplace add Pipelex/pipelex-plugins
export PIPELEX_API_KEY=plx_sk_...     # create one in your console at app.pipelex.com
```

Restart Codex, run `/plugins` to install `pipelex`, and trust the plugin hook on first run. Requires Codex 0.141 or later.

</details>

<details><summary><b>Chat hosts — ChatGPT, claude.ai, Claude Desktop, Cowork</b></summary>

Add Pipelex as a custom connector by its URL, then sign in with your Pipelex account when the host asks. Nothing to install, and no key at all — the connector runs on your signed-in session:

```
https://mcp.pipelex.com/mcp
```

</details>

**3. Ask for the method you want.**

> Design a method that reads an invoice PDF and returns the supplier, the total and the line items. Then run it on `~/Downloads/invoice.pdf`.

`/pipelex-design` writes the method, the hook checks it on every edit, and `/pipelex-run` starts it and prints a run id you can come back to.

**The other two ways.** Turn the method into a webapp with the [method-app template](https://github.com/Pipelex/pipelex-method-apps), or use it via API in any software through `POST /v1/start` — in TypeScript with [`@pipelex/sdk`](https://www.npmjs.com/package/@pipelex/sdk), in Python with [`pipelex-sdk`](https://pypi.org/project/pipelex-sdk/), or with any HTTP client.

**Next:** [what Pipelex is](https://go.pipelex.com/product) · [plans and self-serve](https://go.pipelex.com/pricing) · [documentation](https://go.pipelex.com/docs) · [your console](https://app.pipelex.com) · [Discord](https://go.pipelex.com/discord)

Prefer to run it yourself? This repository is the Pipelex runtime, source-available under the Elastic License 2.0 — its own install and configuration are below.
