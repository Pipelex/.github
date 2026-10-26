## Get started

Pipelex lets you build AI methods with your coding agent and run them anywhere: as an MCP for chatbots, as a webapp for people, or via API for your software. This repository holds the Pipelex tools, which your coding agent gets with the Pipelex plugin: they run your methods and also work with the method files in your project.

**1. Sign up at [app.pipelex.com](https://app.pipelex.com).**

**2. Install the Pipelex plugin in your coding agent.** The plugin gives your agent the skills that build methods, run them and put them in your software, a hook that checks every edit, and the Pipelex tools.

<details open><summary><b>Claude Code</b></summary>

```bash
claude plugin marketplace add Pipelex/pipelex-plugins
claude plugin install pipelex@pipelex-plugins
```

Claude Code asks for an API key when you enable the plugin, and stores it in your OS keychain — create one in your console at [app.pipelex.com](https://app.pipelex.com). The skills, the hook that checks every edit and the Pipelex tools load with it. The plugin's hook and the Pipelex tools run on Node.js, so you need Node.js on your `PATH`.

Claude Code also loads what you have added to your Claude account, so if you added the Pipelex MCP to Claude, Claude Code has it too. An agent with the plugin does not need the Pipelex MCP, and there is nothing to turn off: when both are present, the Pipelex MCP defers to the plugin's tools.

</details>

<details open><summary><b>Codex</b></summary>

```bash
codex plugin marketplace add Pipelex/pipelex-plugins
export PIPELEX_API_KEY=plx_sk_...     # create one in your console at app.pipelex.com
```

Restart Codex, run `/plugins` to install `pipelex`, and trust the plugin hook on first run. Requires Codex 0.141 or later. The plugin's hook and the Pipelex tools run on Node.js, so you need Node.js on your `PATH`.

</details>

**3. Ask your agent for the method you want.**

> Design a method that reads an invoice PDF and returns the supplier, the total and the line items. Then run it on `~/Downloads/invoice.pdf` and save it to my Pipelex account.

`/pipelex-design` writes the method, the hook checks it on every edit, `/pipelex-run` starts it and prints a run id you can come back to, and `/pipelex-catalog` saves it to your account, where your chatbot can run it too.

**Chatbots** — ChatGPT, Claude — take the Pipelex MCP instead, a connector for chatbots that this repository does not hold: add it in your chatbot's settings by its address, `https://mcp.pipelex.com/mcp`.

Other hosts, and the reference for developers, start at [Which server, for which host](#which-server-for-which-host).

**Next:** [what Pipelex is](https://go.pipelex.com/product) · [documentation](https://go.pipelex.com/docs) · [your console](https://app.pipelex.com) · [Discord](https://go.pipelex.com/discord)
