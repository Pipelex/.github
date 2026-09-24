<div align="center">
  <a href="https://www.pipelex.com/"><img src="https://raw.githubusercontent.com/Pipelex/pipelex/main/.github/assets/logo.png" alt="Pipelex Logo" width="400" style="max-width: 100%; height: auto;"></a>

  <br/>
  <br/>
  <h2 align="center">Turn your expertise into an AI-powered App/MCP/API</h2>
  <p align="center">Pipelex runs your AI methods. Write a method once: a webapp runs it for your team or as SaaS for your customers, your agent runs it over MCP, your software runs it over the API.</p>

  <div>
    <a href="https://go.pipelex.com/demo"><strong>Demo</strong></a> -
    <a href="https://docs.pipelex.com/"><strong>Documentation</strong></a> -
    <a href="https://mthds.sh"><strong>Hub</strong></a> -
    <a href="https://go.pipelex.com/discord"><strong>Discord</strong></a>
  </div>
</div>

<br/>

<!-- onboarding: front-door -->
<!-- Generated from the Pipelex onboarding source; this region is replaced from https://raw.githubusercontent.com/Pipelex/.github/main/onboarding/rendered/front-door--open_source-org.md — do not edit it here. -->
## Quick start

Pipelex lets you build AI methods with your coding agent and run them anywhere — from your agent or your chatbot via MCP, as a webapp, or via API in any software.

**1. Sign up at [app.pipelex.com](https://app.pipelex.com).**

**2. Install the Pipelex plugin in your coding agent.** The plugin is how you build methods: it gives your agent the skills that write and run them, a hook that checks every edit, and the Pipelex tools.

<details open><summary><b>Claude Code</b></summary>

```bash
claude plugin marketplace add Pipelex/pipelex-plugins
claude plugin install pipelex@pipelex-plugins
```

Claude Code asks for an API key when you enable the plugin, and stores it in your OS keychain — create one in your console at [app.pipelex.com](https://app.pipelex.com). The skills, the hook that checks every edit and the Pipelex tools load with it; nothing else to install.

Claude Code also loads what you have added to your Claude account, so if the Pipelex MCP is there, turn it off in Claude Code with `/mcp`: an agent with the plugin never takes both, since they register the same tool names.

</details>

<details><summary><b>Codex</b></summary>

```bash
codex plugin marketplace add Pipelex/pipelex-plugins
export PIPELEX_API_KEY=plx_sk_...     # create one in your console at app.pipelex.com
```

Restart Codex, run `/plugins` to install `pipelex`, and trust the plugin hook on first run. Requires Codex 0.141 or later.

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

**The other two ways.** Turn the method into a webapp with the [method-app template](https://github.com/Pipelex/pipelex-method-apps), or use it via API in any software through `POST /v1/start` — in TypeScript with [`@pipelex/sdk`](https://www.npmjs.com/package/@pipelex/sdk), in Python with [`pipelex-sdk`](https://pypi.org/project/pipelex-sdk/), or with any HTTP client.

**Next:** [what Pipelex is](https://go.pipelex.com/product) · [documentation](https://go.pipelex.com/docs) · [your console](https://app.pipelex.com) · [Discord](https://go.pipelex.com/discord)

Prefer to run it yourself? The [Pipelex runtime](https://github.com/Pipelex/pipelex) runs your methods on your own machine — it and the rest of our repositories are listed below.
<!-- /onboarding -->

## What a method looks like

A method is a reusable, typed AI procedure, written in [MTHDS](https://mthds.ai/latest/), an open standard, and saved as a `.mthds` file. Each step is explicit, each output is structured, and every run is repeatable.

```toml
domain    = "articles"
main_pipe = "summarize_article"

[pipe.summarize_article]
type        = "PipeLLM"
description = "Summarize an article for a given audience"
inputs      = { article = "Text", audience = "Text" }
output      = "Text"
prompt      = "Summarize $article in three bullet points for $audience."
```

From here, Pipelex handles model routing across providers, structured output parsing, and pipeline orchestration.

## Run it yourself

The [Pipelex runtime](https://github.com/Pipelex/pipelex) runs methods on your own machine, against the model providers you choose or a local model; its README carries the install, the configuration and the first run. [`pipelex-api`](https://github.com/Pipelex/pipelex-api) is the runner API you host yourself, and the editor extension highlights and checks `.mthds` files, from the [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=pipelex.pipelex) or the [Open VSX Registry](https://open-vsx.org/extension/Pipelex/pipelex) for Cursor, Windsurf and other VS Code forks.

## Repositories

**Build and run your methods**

| Repository | Description |
|:-----------|:------------|
| [`pipelex-plugins`](https://github.com/Pipelex/pipelex-plugins) | The Pipelex plugin for Claude Code and Codex: skills that build and run methods, a hook that checks every edit, and the Pipelex tools |
| [`pipelex-mcp`](https://github.com/Pipelex/pipelex-mcp) | The Pipelex MCP, which ChatGPT or Claude adds to run the methods saved in your account |
| [`pipelex-method-apps`](https://github.com/Pipelex/pipelex-method-apps) | Template for turning a method into a webapp, with its input form and result view generated from the method |
| [`pipelex-sdk-js`](https://github.com/Pipelex/pipelex-sdk-js) | TypeScript SDK for the Pipelex API (npm: `@pipelex/sdk`) |
| [`pipelex-sdk-python`](https://github.com/Pipelex/pipelex-sdk-python) | Python SDK for the Pipelex API (PyPI: `pipelex-sdk`) |
| [`pipelex-starter-js`](https://github.com/Pipelex/pipelex-starter-js) | Starter template: a Next.js app that runs methods through `@pipelex/sdk`, with worked examples to copy |
| [`pipelex-starter-python`](https://github.com/Pipelex/pipelex-starter-python) | Starter template: a Python CLI that runs methods through `pipelex-sdk` |
| [`n8n-nodes-pipelex`](https://github.com/Pipelex/n8n-nodes-pipelex) | n8n community node that runs methods on a Pipelex API server (npm: `n8n-nodes-pipelex`) |

**Run it yourself**

| Repository | Description |
|:-----------|:------------|
| [`pipelex`](https://github.com/Pipelex/pipelex) | The Pipelex runtime, which runs methods on your own machine (PyPI: `pipelex`) |
| [`pipelex-api`](https://github.com/Pipelex/pipelex-api) | The runner API you host yourself, the reference implementation of the MTHDS Protocol (Docker Hub: `pipelex/pipelex-api`) |
| [`vscode-pipelex`](https://github.com/Pipelex/vscode-pipelex) | The VS Code and Cursor extension, the `plxt` formatter and linter, and the language server for `.mthds` (PyPI: `pipelex-tools`) |

**Methods and examples**

| Repository | Description |
|:-----------|:------------|
| [`methods`](https://github.com/Pipelex/methods) | The public method library: packaged methods to run by their address or to fork |
| [`pipelex-cookbook`](https://github.com/Pipelex/pipelex-cookbook) | Examples and tutorials for the Pipelex runtime |
| [`cocode`](https://github.com/Pipelex/cocode) | Codebase analysis CLI built on Pipelex: changelogs, doc updates, drift proofreading (PyPI: `cocode`) |

**The MTHDS standard**

| Repository | Description |
|:-----------|:------------|
| [`mthds`](https://github.com/mthds-ai/mthds) | The MTHDS open standard: specification and docs ([mthds.ai](https://mthds.ai)) |
| [`mthds-js`](https://github.com/mthds-ai/mthds-js) | The `mthds` CLI and SDK for any MTHDS API (npm: `mthds`) |
| [`mthds-python`](https://github.com/mthds-ai/mthds-python) | Python implementation of the MTHDS Protocol: a typed client and the base structures methods are defined in (PyPI: `mthds`) |
| [`mthds-starter-js`](https://github.com/mthds-ai/mthds-starter-js) | Starter template: a Next.js app running methods through the `mthds` SDK against any MTHDS API |

**Libraries**

| Repository | Description |
|:-----------|:------------|
| [`mthds-ui`](https://github.com/Pipelex/mthds-ui) | React graph viewer for method pipelines (npm: `@pipelex/mthds-ui`) |
| [`mthds-form`](https://github.com/Pipelex/mthds-form) | Headless form kernel and React controls for method inputs (npm: `@pipelex/mthds-form`) |
| [`kajson`](https://github.com/Pipelex/kajson) | JSON encoder and decoder for Python with pydantic v2 support, the serialization layer under `pipelex` (PyPI: `kajson`) |

## Community

- **[Discord](https://go.pipelex.com/discord)**: get help, share methods, meet the team
- **[Documentation](https://docs.pipelex.com/)**: guides and reference
- **[GitHub Issues](https://github.com/Pipelex/pipelex/issues)**: report bugs and request features
- **[security@pipelex.com](mailto:security@pipelex.com)**: security and privacy concerns

## License

The runtime and the servers that run methods — [`pipelex`](https://github.com/Pipelex/pipelex), [`pipelex-api`](https://github.com/Pipelex/pipelex-api) and [`pipelex-mcp`](https://github.com/Pipelex/pipelex-mcp) — are source-available under the **Elastic License 2.0** (ELv2). You may embed them in your own products, including services whose features run your methods, and run them for your own team or company; what the license rules out is hosting a service that runs methods for others. The [license page](https://docs.pipelex.com/latest/license/) explains how we read it, with concrete examples. Every version of them released before the switch stays under MIT.

The SDKs, the starter templates, the public method library, the cookbook, the UI libraries, the VS Code extension, the n8n node, `cocode` and the [MTHDS open standard](https://github.com/mthds-ai/mthds) are **MIT licensed**. [`kajson`](https://github.com/Pipelex/kajson) and [`pipelex-plugins`](https://github.com/Pipelex/pipelex-plugins) are licensed under **Apache 2.0**. Each repository's `LICENSE` file carries its terms.

**"Pipelex" is a trademark of Evotis S.A.S.**
