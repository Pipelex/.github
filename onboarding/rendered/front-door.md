## Quick start

Pipelex lets you build AI methods with your coding agent and run them anywhere: as an MCP for chatbots, as a webapp for people, or via API for your software.

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

**Run your methods from your chatbot.** The Pipelex MCP is a connector for your chatbot (ChatGPT, Claude): it gives it access to the Pipelex service, so it can list the methods saved in your account and run them right in the conversation. Your methods become your chatbot's tools. To build a method, use the Pipelex plugin in a coding agent such as Claude Code or Codex, as in steps 2 and 3 above.

Add the Pipelex MCP in your chatbot's settings by the address below — in Claude, that is **Add custom connector** — then sign in with your Pipelex account when asked. Nothing to install and no key: the Pipelex MCP runs on your signed-in session.

```
https://mcp.pipelex.com/mcp
```

Then ask your chatbot:

> What methods do I have?
>
> Run the invoice method on https://example.com/invoice.pdf

You get a run id straight away, and you can ask for its status, its results or the files it produced at any time.

Give the file as a URL the Pipelex MCP can reach. In ChatGPT you can attach it to the conversation instead and ask for a run on it; Claude has no way yet to hand the Pipelex MCP a file you attached.

**The other two ways, built by your agent too.** Ask it for a webapp around the method, and `/pipelex-scaffold` creates a new app from the [method-app template](https://github.com/Pipelex/pipelex-method-apps) and leaves it running on your machine. Ask it to call the method from your TypeScript or Python code, and `/pipelex-integrate` generates the method's types and one typed call that runs it, through the TypeScript SDK [`@pipelex/sdk`](https://www.npmjs.com/package/@pipelex/sdk) or the Python SDK [`pipelex-sdk`](https://pypi.org/project/pipelex-sdk/). Any other software runs a method via API through `POST /v1/start`, with any HTTP client.

**Next:** [what Pipelex is](https://go.pipelex.com/product) · [documentation](https://go.pipelex.com/docs) · [your console](https://app.pipelex.com) · [Discord](https://go.pipelex.com/discord)

Prefer to run it yourself? This repository is the Pipelex runtime — its own install and configuration are below.
