## Get started

Pipelex runs your AI methods — write a method once, then run it from your agent via MCP, turn it into a webapp, or use it via API in any software. This repository is how a chat or a coding agent reaches it.

Pick one server for a given host: the **workshop** wherever there is a filesystem, the **console** everywhere else. Never both — the two deployments register the same tool names.

**Hosted console** — ChatGPT, claude.ai, Claude Desktop, Cowork. Add Pipelex as a custom connector by its URL, then sign in with your Pipelex account when the host asks. Nothing to install, and no key at all — the connector runs on your signed-in session:

```
https://mcp.pipelex.com/mcp
```

**Local workshop** — Claude Code, Codex, Cursor.

```bash
claude mcp add pipelex --env PIPELEX_API_KEY=plx_sk_... -- npx -y @pipelex/mcp
```

The server runs on your own machine, so it carries an API key of its own — create one in your console at [app.pipelex.com](https://app.pipelex.com). Needs Node.js 24 or later; the host fetches the server on demand, so there is nothing to install globally.

On Claude Code and Codex the [Pipelex plugin](https://github.com/Pipelex/pipelex-plugins) already declares the workshop, so install the plugin instead and skip the command above.

**Then ask for something.** On the console:

> What methods do I have?
>
> Run the invoice method on https://example.com/invoice.pdf

On the workshop, where the server reaches the files you are writing:

> Validate the bundle in `./methods/invoices` and run it on `invoice.pdf`.

You get a run id straight away, and you can ask for its status, its results or the files it produced at any time.

Give the file as a URL the connector can reach. In ChatGPT you can attach it to the conversation instead and ask for a run on it; the other connector hosts have no channel yet for handing a server the file you attached.

**Next:** [what Pipelex is](https://go.pipelex.com/product) · [documentation](https://go.pipelex.com/docs) · [your console](https://app.pipelex.com) · [Discord](https://go.pipelex.com/discord)
