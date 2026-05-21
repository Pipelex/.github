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

Open Claude Code and paste this. Claude does the rest.

```
Install mthds: run bash -c 'npm install -g mthds && mthds-agent bootstrap && claude plugin marketplace add mthds-ai/mthds-plugins && claude plugin install mthds@mthds-plugins'. Then tell me to /reload-plugins.
```

Then build your first method:

```
/mthds-build A method to summarize articles with key takeaways for different audiences
```

Run it:

```
/mthds-run
```

---

## Get Started with Codex

Open Codex and paste this. Codex does the rest.

```
Install mthds: run bash -c 'npm install -g mthds && mthds-agent bootstrap && mthds-agent codex apply-config && codex plugin marketplace add mthds-ai/mthds-plugins'. Then tell me to restart Codex and run /plugins to install mthds.
```

Requires Codex 0.130.0+ (`npm install -g @openai/codex@latest` if needed). See the [mthds-plugins README](https://github.com/mthds-ai/mthds-plugins) for what `mthds-agent codex apply-config` does and manual install steps.

---

## Get Started without an AI Coding Agent

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

## Starter Templates

Two ready-to-fork templates depending on how you want to run methods:

- **[`pipelex-starter-python`](https://github.com/Pipelex/pipelex-starter-python)** — Python project embedding the [`pipelex`](https://pypi.org/project/pipelex/) runtime directly. Best when you want to run methods in-process from a Python service, script, or notebook. Click *Use this template* on GitHub.
- **[`pipelex-starter-js`](https://github.com/Pipelex/pipelex-starter-js)** — Next.js 16 + TypeScript app that calls a Pipelex API server via the [`mthds`](https://www.npmjs.com/package/mthds) SDK. Best when you want a TypeScript frontend/backend that talks to a remote (hosted or self-hosted) Pipelex runner. Ships with three demo pipelines (text entities, PDF summary, image generation).

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
| [`mthds-plugins`](https://github.com/mthds-ai/mthds-plugins) | Claude Code + Codex skills plugin for building, running, and editing methods |
| [`pipelex-starter-python`](https://github.com/Pipelex/pipelex-starter-python) | Starter template — Python project embedding the `pipelex` runtime |
| [`pipelex-starter-js`](https://github.com/Pipelex/pipelex-starter-js) | Starter template — Next.js + TypeScript app calling the Pipelex API via the `mthds` SDK |
| [`pipelex-cookbook`](https://github.com/Pipelex/pipelex-cookbook) | Production-ready examples and tutorials |

---

## License

All repositories are **MIT licensed** unless otherwise specified. See individual `LICENSE` files for details.

**"Pipelex" is a trademark of Evotis S.A.S.**
