# Pipelex — Declarative language for repeatable AI workflows

**Think Dockerfile or SQL for multi-step LLM pipelines:** you declare what to do, not how. The runtime handles execution across any model or provider. **The Pipelex language (.plx) is an open standard (MIT license)** designed to be both human-readable and LLM-friendly.

**Quick links:**
**[Website](https://www.pipelex.com/)** • **[Docs](https://docs.pipelex.com/)** • **[Discord](https://go.pipelex.com/discord)** • [Cookbook](https://github.com/Pipelex/pipelex-cookbook) • [Demo (2min)](https://go.pipelex.com/demo) • **[VS Code Extension](https://open-vsx.org/extension/Pipelex/pipelex)**

---

## What's in this organization?

### Core Components

* **[`pipelex`](https://github.com/Pipelex/pipelex) — Runtime & PLX language** 
  The Python library and language specification. Build, run, and compose AI workflows with structured I/O and validation.

* **[`pipelex-api`](https://github.com/Pipelex/pipelex-api) — FastAPI server & Docker** 🚀
  Deploy Pipelex as a REST API. Self-host with Docker or integrate into your infrastructure.

* **[`pipelex-mcp`](https://github.com/Pipelex/pipelex-mcp) — Model Context Protocol server** 🤖
  Let Claude, Cursor, and other MCP-compatible agents run and build Pipelex workflows.

* **[`n8n-nodes-pipelex`](https://github.com/Pipelex/n8n-nodes-pipelex) — n8n automation node** ⚡
  Integrate Pipelex workflows into n8n for no-code automation and orchestration.

### Resources & Tools

* **[`pipelex-cookbook`](https://github.com/Pipelex/pipelex-cookbook) — Examples & recipes**
  Ready-to-run pipelines: classification, extraction, analysis, generation, and more.

* **[`pipelex-starter`](https://github.com/Pipelex/pipelex-starter) — Project template**
  Bootstrap new projects with batteries included: Makefile, tests, environment setup.

> **LLM Access:** Use **[Pipelex Inference](https://docs.pipelex.com/pages/configuration/config-technical/inference-backend-config/)** (free tier available) for unified access to OpenAI, Anthropic, Google, Mistral, and more—or bring your own API keys.

---

## Choose your deployment

### 🐍 **Local Development** — Python library

```bash
pip install pipelex
# Optional: provider-specific extras
pip install "pipelex[anthropic,google,mistralai]"
```

```python
from pipelex import run_pipeline

result = run_pipeline("my_workflow.plx", {"input": "data"})
```

### 🐳 **API Server** — Docker or self-hosted

```bash
# Using Docker
docker pull pipelex/pipelex-api:latest
docker run -p 8081:8081 \
  -e API_KEY=your-api-key-here \
  -e PIPELEX_INFERENCE_API_KEY=your-pipelex-key \
  pipelex/pipelex-api:latest

# Or clone and run locally
git clone https://github.com/Pipelex/pipelex-api
cd pipelex-api
docker-compose up
```

### 🤖 **AI Agents** — MCP server

```bash
# Install the MCP server
pip install pipelex-mcp

# Configure in Claude Desktop or Cursor
# Agents can now run AND build Pipelex workflows
```

### ⚡ **Automation** — n8n node

Install the Pipelex node in n8n to integrate AI workflows into your automation pipelines. Connect with 400+ apps and services.

---

## Quick starts

### 1) **Try examples** (Cookbook)

```bash
git clone https://github.com/Pipelex/pipelex-cookbook
cd pipelex-cookbook
make install
cp .env.example .env  # Add your API keys

# Run an example
python examples/classification/sentiment.py
```

### 2) **Start a new project** (Template)

```bash
# Use GitHub template
# Visit: https://github.com/Pipelex/pipelex-starter
# Click "Use this template" → Create your repo

git clone <your-new-repo>
cd <your-new-repo>
make install
```

### 3) **Let AI build your workflow** 🪄

```bash
# Install Pipelex with CLI
pip install pipelex

# Describe what you want, get a working pipeline
pipelex build pipe "Extract product features from reviews and rate importance 1-10"

# Run the generated pipeline
pipelex run product_features.plx --input "review.txt"
```

> 💡 **Pro tip:** Install **[`vscode-pipelex`](https://open-vsx.org/extension/Pipelex/pipelex)** for syntax highlighting in VS Code, Cursor, Windsurf, and BlackboxAI.

## Contributing

We welcome contributions! Here's how to get involved:

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
