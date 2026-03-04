# Pipelex — AI Methods for Claude Code

**Repeatable, version-controlled AI workflows as a Claude Code plugin.** Declare multi-step LLM pipelines, run them from your terminal, and get consistent results every time.

**Quick links:**
**[Website](https://www.pipelex.com/)** • **[Docs](https://docs.pipelex.com/)** • **[Discord](https://go.pipelex.com/discord)** • [Cookbook](https://github.com/Pipelex/pipelex-cookbook) • [Demo (2min)](https://go.pipelex.com/demo)

---

## Get started

Install the plugin in Claude Code:

```
/plugin marketplace add mthds-ai/skills
/plugin install mthds@mthds-ai-skills
```

Then ask Claude: **"Please setup mthds"**

## Build your first method

Ask Claude to build a method for you:

```
Build me a method that extracts key insights from customer reviews and rates them by importance
```

Or use the CLI shortcut:

```
/mthds-build
```

---

## Manual installation

### Python library

```bash
pip install pipelex
# Optional: provider-specific extras
pip install "pipelex[anthropic,google,mistralai]"
```

### API Server (Docker)

```bash
docker pull pipelex/pipelex-api:latest
docker run -p 8081:8081 \
  -e API_KEY=your-api-key-here \
  -e PIPELEX_INFERENCE_API_KEY=your-pipelex-key \
  pipelex/pipelex-api:latest
```

See [`pipelex-api`](https://github.com/Pipelex/pipelex-api) for full setup instructions.

### MCP server

```bash
pip install pipelex-mcp
```

Configure in Claude Desktop or Cursor. See [`pipelex-mcp`](https://github.com/Pipelex/pipelex-mcp).

### n8n node

Install the Pipelex node in n8n to integrate AI workflows into your automation pipelines. See [`n8n-nodes-pipelex`](https://github.com/Pipelex/n8n-nodes-pipelex).

> **LLM Access:** Use **[Pipelex Inference](https://docs.pipelex.com/pages/configuration/config-technical/inference-backend-config/)** (free tier available) for unified access to OpenAI, Anthropic, Google, Mistral, and more — or bring your own API keys.

---

## Examples

Ready-to-run pipelines are available in the **[Cookbook](https://github.com/Pipelex/pipelex-cookbook)**: classification, extraction, analysis, generation, and more.

## Community & support

- 💬 **[Discord](https://go.pipelex.com/discord)** — Get help, share workflows, meet the team
- 📚 **[Documentation](https://docs.pipelex.com/)** — Complete guides and API reference
- 🐛 **[GitHub Issues](https://github.com/Pipelex/pipelex/issues)** — Report bugs and request features
- ✉️ **[security@pipelex.com](mailto:security@pipelex.com)** — Security and privacy concerns

---

## License

All repositories are **MIT licensed** unless otherwise specified. See individual `LICENSE` files for details.

**"Pipelex" is a trademark of Evotis S.A.S.**

---

<p align="center">
  <strong>Built by developers who were tired of rewriting the same AI patterns.</strong><br>
  Now you don't have to.
</p>
