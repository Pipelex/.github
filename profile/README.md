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

A method is written once in the [MTHDS](https://mthds.ai) open standard and runs anywhere Pipelex does: on your machine with the `pipelex` runtime, on a server you host with `pipelex-api`, or on the hosted Pipelex API.

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

This installs the local toolchain and runs methods on your machine. To run them on the hosted Pipelex API instead, install [`pipelex-plugins`](#use-the-hosted-pipelex-api) — nothing to install locally beyond the plugin.

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

1. Install the [VS Code extension](https://go.pipelex.com/vscode) for `.mthds` syntax highlighting — Cursor and other VS Code forks get it from [Open VSX](https://open-vsx.org/extension/Pipelex/pipelex)
2. Browse methods on the [MTHDS Hub](https://mthds.sh) and in the [public method library](https://github.com/Pipelex/methods) for inspiration
3. Author your own `.mthds` methods
4. Validate with `pipelex validate bundle your_method.mthds`
5. Run with `pipelex run bundle your_method.mthds`

A method from the public library runs by its address, with nothing to install first:

```bash
pipelex run method github.com/Pipelex/methods/doc_summarizer --inputs inputs.json
```

---

## Use the Hosted Pipelex API

The hosted Pipelex API at `api.pipelex.com` runs methods durably — start a run, poll it, fetch the result — with file storage and a method catalog on top. It is currently in **private beta**: [join the waitlist](https://go.pipelex.com/waitlist), then get an API key at [app.pipelex.com](https://app.pipelex.com). The SDKs and starter templates below also work against a self-hosted [`pipelex-api`](https://github.com/Pipelex/pipelex-api) pointed to by `PIPELEX_BASE_URL`.

Three ways in:

**From a coding agent — [`pipelex-plugins`](https://github.com/Pipelex/pipelex-plugins).** Skills and hooks for Claude Code, Codex, and Mistral Vibe, with no local toolchain: methods are validated and run through the Pipelex MCP server, which the plugin launches for you.

```
claude plugin marketplace add Pipelex/pipelex-plugins
claude plugin install pipelex@pipelex-plugins
```

For Codex, `codex plugin marketplace add Pipelex/pipelex-plugins`, restart, then `/plugins` to install `pipelex` (Codex 0.141+). Then `/pipelex-design A method to …` builds a method, `/pipelex-inputs` prepares its inputs and offers to run it, and `/pipelex-integrate` wires it into your codebase with generated types.

**From any MCP host — [`@pipelex/mcp`](https://github.com/Pipelex/pipelex-mcp).** One capability core, two servers: a local workshop that coding agents spawn with `npx` and that reads `.mthds` files straight from disk, and a hosted console you add as a custom connector in ChatGPT, claude.ai, or Claude Desktop, with nothing to install.

```bash
claude mcp add pipelex --env PIPELEX_API_KEY=plx_sk_... -- npx -y @pipelex/mcp
```

**From your own code — the SDKs.** [`@pipelex/sdk`](https://www.npmjs.com/package/@pipelex/sdk) for TypeScript and [`pipelex-sdk`](https://pypi.org/project/pipelex-sdk/) for Python cover the MTHDS Protocol routes, the durable run lifecycle, storage, and the product surface, and both ship an offline check that keeps generated types in sync with your methods.

```bash
npm install @pipelex/sdk
pip install pipelex-sdk
```

---

## Starter Templates

Two ready-to-fork templates, one per language, both calling the Pipelex API. Click *Use this template* on GitHub, then run the bundled `/bootstrap` skill in Claude Code to make the project yours.

- **[`pipelex-starter-js`](https://github.com/Pipelex/pipelex-starter-js)** — Next.js 16 + TypeScript app calling the Pipelex API via [`@pipelex/sdk`](https://www.npmjs.com/package/@pipelex/sdk). Best when you want a TypeScript frontend or backend that talks to a remote Pipelex runner. Ships with demo pipelines, from text entity extraction and PDF summaries to image generation, plus a method pulled in from the public library by address.
- **[`pipelex-starter-python`](https://github.com/Pipelex/pipelex-starter-python)** — Python CLI calling the Pipelex API via [`pipelex-sdk`](https://pypi.org/project/pipelex-sdk/), with no local runtime to install. Best when you want a script, service, or command-line tool that runs methods remotely and prints structured JSON with a cost report.

To run methods in-process from Python instead, install the [`pipelex`](https://pypi.org/project/pipelex/) runtime and start from the [Cookbook](https://github.com/Pipelex/pipelex-cookbook).

---

## Configure AI Access

- **[Pipelex Gateway](https://app.pipelex.com/) (Recommended)** — Free credits, single API key for LLMs, OCR / document extraction, and image generation across all major providers.
- **Bring Your Own Keys** — Use existing API keys from OpenAI, Anthropic, Google, Mistral, etc. See [Configure AI Providers](https://docs.pipelex.com/latest/setup/configure-ai-providers/).
- **Local AI** — Ollama, vLLM, LM Studio, or llama.cpp — no API keys required. See [Configure AI Providers](https://docs.pipelex.com/latest/setup/configure-ai-providers/).

---

## Examples

- **[Cookbook](https://github.com/Pipelex/pipelex-cookbook)** — Ready-to-run methods for the `pipelex` runtime: classification, extraction, analysis, generation, and more.
- **[Public method library](https://github.com/Pipelex/methods)** — Packaged methods you run by address, from document extraction and invoice processing to slide design and image generation.

## Community & Support

- **[Discord](https://go.pipelex.com/discord)** — Get help, share methods, meet the team
- **[Documentation](https://docs.pipelex.com/)** — Guides and reference
- **[GitHub Issues](https://github.com/Pipelex/pipelex/issues)** — Report bugs and request features
- **[security@pipelex.com](mailto:security@pipelex.com)** — Security and privacy concerns

## Key Repositories

**Runtime and servers**

| Repository | Description |
|:-----------|:------------|
| [`pipelex`](https://github.com/Pipelex/pipelex) | Python runtime — build and run AI methods (PyPI: `pipelex`) |
| [`pipelex-api`](https://github.com/Pipelex/pipelex-api) | REST API server that runs methods — the reference implementation of the MTHDS Protocol (Docker Hub: `pipelex/pipelex-api`) |
| [`pipelex-mcp`](https://github.com/Pipelex/pipelex-mcp) | MCP servers over the Pipelex API — a local workshop for coding agents and a hosted console for ChatGPT and Claude (npm: `@pipelex/mcp`) |

**Agent plugins**

| Repository | Description |
|:-----------|:------------|
| [`pipelex-plugins`](https://github.com/Pipelex/pipelex-plugins) | Skills and hooks for Claude Code, Codex, and Mistral Vibe — CLI-free, built for the hosted API and the MCP server |
| [`mthds-plugins`](https://github.com/mthds-ai/mthds-plugins) | Claude Code + Codex skills plugin for building, running, and editing methods with the local toolchain |

**SDKs and starters**

| Repository | Description |
|:-----------|:------------|
| [`pipelex-sdk-js`](https://github.com/Pipelex/pipelex-sdk-js) | TypeScript SDK for the Pipelex API (npm: `@pipelex/sdk`) |
| [`pipelex-sdk-python`](https://github.com/Pipelex/pipelex-sdk-python) | Python SDK for the Pipelex API (PyPI: `pipelex-sdk`) |
| [`pipelex-starter-js`](https://github.com/Pipelex/pipelex-starter-js) | Starter template — Next.js + TypeScript app calling the Pipelex API via `@pipelex/sdk` |
| [`pipelex-starter-python`](https://github.com/Pipelex/pipelex-starter-python) | Starter template — Python CLI calling the Pipelex API via `pipelex-sdk` |
| [`n8n-nodes-pipelex`](https://github.com/Pipelex/n8n-nodes-pipelex) | n8n community node that runs methods on a Pipelex API server (npm: `n8n-nodes-pipelex`) |

**Methods and examples**

| Repository | Description |
|:-----------|:------------|
| [`methods`](https://github.com/Pipelex/methods) | The public method library — packaged methods, run by address |
| [`pipelex-cookbook`](https://github.com/Pipelex/pipelex-cookbook) | Production-ready examples and tutorials |
| [`cocode`](https://github.com/Pipelex/cocode) | Codebase analysis CLI built on Pipelex — changelogs, doc updates, drift proofreading (PyPI: `cocode`) |

**The MTHDS standard**

| Repository | Description |
|:-----------|:------------|
| [`mthds`](https://github.com/mthds-ai/mthds) | The MTHDS open standard — specification and docs ([mthds.ai](https://mthds.ai)) |
| [`mthds-js`](https://github.com/mthds-ai/mthds-js) | The `mthds` CLI and SDK — install methods, set up a runner, call any MTHDS API (npm: `mthds`) |
| [`mthds-python`](https://github.com/mthds-ai/mthds-python) | Python implementation of the MTHDS Protocol — typed client and the base structures methods are defined in (PyPI: `mthds`) |
| [`mthds-starter-js`](https://github.com/mthds-ai/mthds-starter-js) | Starter template — Next.js app running methods through the `mthds` SDK against any MTHDS API |

**Tooling and libraries**

| Repository | Description |
|:-----------|:------------|
| [`vscode-pipelex`](https://github.com/Pipelex/vscode-pipelex) | VS Code / Cursor extension, the `plxt` formatter and linter, and the language server for `.mthds` (PyPI: `pipelex-tools`) |
| [`mthds-ui`](https://github.com/Pipelex/mthds-ui) | React graph viewer for method pipelines (npm: `@pipelex/mthds-ui`) |
| [`mthds-form`](https://github.com/Pipelex/mthds-form) | Headless form kernel and React controls for method inputs (npm: `@pipelex/mthds-form`) |
| [`kajson`](https://github.com/Pipelex/kajson) | Universal JSON encoder/decoder for Python with pydantic v2 support — the serialization layer under `pipelex` (PyPI: `kajson`) |

---

## License

The runtime and the servers that run methods — [`pipelex`](https://github.com/Pipelex/pipelex), [`pipelex-api`](https://github.com/Pipelex/pipelex-api) and [`pipelex-mcp`](https://github.com/Pipelex/pipelex-mcp) — are source-available under the **Elastic License 2.0** (ELv2). You may embed them in your own products, including services whose features run your methods, and run them for your own team or company; what the license rules out is hosting a service that runs methods for others. The [license page](https://docs.pipelex.com/latest/license/) explains how we read it, with concrete examples. Every version of them released before the switch stays under MIT.

The SDKs, the starter templates, the public method library, the cookbook, the UI libraries, the VS Code extension, the n8n node, `cocode` and the [MTHDS open standard](https://github.com/mthds-ai/mthds) are **MIT licensed**. [`kajson`](https://github.com/Pipelex/kajson) and [`pipelex-plugins`](https://github.com/Pipelex/pipelex-plugins) are licensed under **Apache 2.0**. Each repository's `LICENSE` file carries its terms.

**"Pipelex" is a trademark of Evotis S.A.S.**
