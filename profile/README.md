<div align="center">
  <a href="https://www.pipelex.com/"><img src="https://raw.githubusercontent.com/Pipelex/pipelex/main/.github/assets/logo.png" alt="Pipelex Logo" width="400"></a>

  <br/>
  <br/>
  <h2 align="center">Executable AI Methods</h2>
  <p align="center">Declare multi-step AI methods in typed <code>.mthds</code> files — deterministic orchestration, structured outputs, repeatable results.</p>

  <div>
    <a href="https://go.pipelex.com/demo"><strong>Demo (2min)</strong></a> -
    <a href="https://docs.pipelex.com/"><strong>Docs</strong></a> -
    <a href="https://mthds.sh"><strong>Hub</strong></a> -
    <a href="https://go.pipelex.com/discord"><strong>Discord</strong></a>
  </div>
  <br/>

  <a href="https://github.com/Pipelex/pipelex/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT License"></a>
  <a href="https://pypi.org/project/pipelex/"><img src="https://img.shields.io/pypi/v/pipelex?logo=pypi&logoColor=white&color=blue&style=flat-square" alt="PyPI"></a>
  <a href="https://go.pipelex.com/discord"><img src="https://img.shields.io/badge/Discord-5865F2?logo=discord&logoColor=white" alt="Discord"></a>
</div>

<br/>

## What a Method Looks Like

```toml
[pipe.summarize_article]
type    = "PipeLLM"
inputs  = { article = "Text", audience = "Text" }
output  = "Text"
prompt  = "Summarize $article in three bullet points for $audience."
```

From here, Pipelex handles model routing across 60+ models, structured output parsing, and pipeline orchestration.

---

## Get Started with Claude Code

Install the `mthds` CLI, it's required by the plugin for method validation and execution:

```bash
npm install -g mthds
```

Start Claude Code:

```bash
claude
```

Tell Claude to install the MTHDS plugins marketplace:

```
/plugin marketplace add mthds-ai/mthds-plugins
```

Then install the MTHDS Claude Code plugin:

```
/plugin install mthds@mthds-plugins
```

Then reload plugins:

```
/reload-plugins
```

If that doesn't work, exit Claude Code and reopen it:

```
/exit
```

Build your first method:

```
/mthds-build A method to summarize articles with key takeaways for different audiences
```

Run it:

```
/mthds-run
```

---

## Get Started without Claude Code

```bash
uv tool install pipelex
pipelex init
```

1. Install the [VS Code extension](https://go.pipelex.com/vscode) for `.mthds` syntax highlighting
2. Browse methods on the [MTHDS Hub](https://mthds.sh) for inspiration
3. Author your own `.mthds` methods
4. Validate with `pipelex validate bundle your_method.mthds`
5. Run with `pipelex run bundle your_method.mthds`

---

## Configure AI Access

- **[Pipelex Gateway](https://app.pipelex.com/) (Recommended)** — Free credits, single API key for LLMs, OCR / document extraction, and image generation across all major providers.
- **Bring Your Own Keys** — Use existing API keys from OpenAI, Anthropic, Google, Mistral, etc. See [Configure AI Providers](https://docs.pipelex.com/latest/setup/configure-ai-providers/).
- **Local AI** — Ollama, vLLM, LM Studio, or llama.cpp — no API keys required. See [Configure AI Providers](https://docs.pipelex.com/latest/setup/configure-ai-providers/).

---

## Examples

Ready-to-run methods in the **[Cookbook](https://github.com/Pipelex/pipelex-cookbook)**: classification, extraction, analysis, generation, and more.

## Community & Support

- **[Discord](https://go.pipelex.com/discord)** — Get help, share methods, meet the team
- **[Documentation](https://docs.pipelex.com/)** — Guides and reference
- **[GitHub Issues](https://github.com/Pipelex/pipelex/issues)** — Report bugs and request features
- **[security@pipelex.com](mailto:security@pipelex.com)** — Security and privacy concerns

## Key Repositories

| Repository | Description |
|:-----------|:------------|
| [`pipelex`](https://github.com/Pipelex/pipelex) | Python runtime — build and run AI methods |
| [`mthds`](https://github.com/mthds-ai/mthds) | The MTHDS open standard — specification and docs |
| [`mthds-plugins`](https://github.com/mthds-ai/mthds-plugins) | Claude Code plugin — skills for building, running, and editing methods |
| [`pipelex-cookbook`](https://github.com/Pipelex/pipelex-cookbook) | Production-ready examples and tutorials |

---

## License

All repositories are **MIT licensed** unless otherwise specified. See individual `LICENSE` files for details.

**"Pipelex" is a trademark of Evotis S.A.S.**
