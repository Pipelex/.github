## Get started

Pipelex lets you build AI methods with your coding agent and run them anywhere: as an MCP for chatbots, as a webapp for people, or via API for your software. This repository is the Pipelex MCP: it connects your chatbot to your Pipelex account and the methods saved there.

**Chatbots** — ChatGPT, Claude. Sign up at [app.pipelex.com](https://app.pipelex.com). Add the Pipelex MCP in your chatbot's settings by the address below — in Claude, that is **Add custom connector** — then sign in with your Pipelex account when asked. Nothing to install and no key: the Pipelex MCP runs on your signed-in session.

```
https://mcp.pipelex.com/mcp
```

**Coding agents** — Claude Code, Codex. Install the [Pipelex plugin](https://github.com/Pipelex/pipelex-plugins) instead: it brings the skills that build methods, and its own Pipelex tools, which run your methods and also work with the method files in your project. Claude Code also loads what you have added to your Claude account, so if you added the Pipelex MCP to Claude, Claude Code has it too. An agent with the plugin does not need the Pipelex MCP, and there is nothing to turn off: when both are present, the Pipelex MCP defers to the plugin's tools.

**Then ask your chatbot:**

> What methods do I have?
>
> Run github.com/Pipelex/methods/invoice_extraction@v0.1.1 on https://raw.githubusercontent.com/Pipelex/pipelex-cookbook/main/assets/extract_proof_of_purchase/restaurant_invoice.pdf

You get a run id straight away, and you can ask for its status, its results or the files it produced at any time.

Your new account comes with one method to try. A published method, such as those in the [Pipelex methods repository](https://github.com/Pipelex/methods), runs from its address with nothing to save. Your own methods come from the Pipelex plugin: build one in a coding agent and save it to your account, and your chatbot lists it and runs it by name.

Give the file as a URL the Pipelex MCP can reach. In ChatGPT you can attach it to the conversation instead and ask for a run on it; Claude has no way yet to hand the Pipelex MCP a file you attached.

Other hosts, and the reference for developers, start at [Which server, for which host](#which-server-for-which-host).

**Next:** [what Pipelex is](https://go.pipelex.com/product) · [documentation](https://go.pipelex.com/docs) · [your console](https://app.pipelex.com) · [Discord](https://go.pipelex.com/discord)
