## Get started

Pipelex runs your AI methods — write a method once, then run it from your agent via MCP, turn it into a webapp, or use it via API in any software. This repository is the Pipelex MCP: it connects your chatbot to your Pipelex account and the methods saved there.

**Chatbots** — ChatGPT, Claude. Add the Pipelex MCP in your chatbot's settings by the address below — in Claude, that is **Add custom connector** — then sign in with your Pipelex account when asked. Nothing to install and no key: the Pipelex MCP runs on your signed-in session.

```
https://mcp.pipelex.com/mcp
```

**Coding agents** — Claude Code, Codex. Install the [Pipelex plugin](https://github.com/Pipelex/pipelex-plugins) instead: it brings the same tools, and the skills that build methods beside them. Claude Code also loads what you have added to your Claude account, so if the Pipelex MCP is there, turn it off in Claude Code with `/mcp`: an agent with the plugin never takes both, since they register the same tool names.

**Then ask your chatbot:**

> What methods do I have?
>
> Run the invoice method on https://example.com/invoice.pdf

You get a run id straight away, and you can ask for its status, its results or the files it produced at any time.

Give the file as a URL the Pipelex MCP can reach. In ChatGPT you can attach it to the conversation instead and ask for a run on it; Claude has no way yet to hand the Pipelex MCP a file you attached.

Other hosts, and the reference for developers, start at [Which server, for which host](#which-server-for-which-host).

**Next:** [what Pipelex is](https://go.pipelex.com/product) · [documentation](https://go.pipelex.com/docs) · [your console](https://app.pipelex.com) · [Discord](https://go.pipelex.com/discord)
