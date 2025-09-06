# Pipelex — agent-first AI workflow language

**Pipelex is an agent-first tool for building repeatable AI workflows. Using Pipelex, agents can transform natural language requirements into production-ready AI workflows in minutes.**
The Pipelex language (PLX) is an **open standard**.

**Quick links:**
**[Website](https://www.pipelex.com/)** • **[Docs](https://docs.pipelex.com/)** • [Cookbook (examples)](https://github.com/Pipelex/pipelex-cookbook) • [Starter template](https://github.com/Pipelex/pipelex-starter) • **[VS Code extension: `vscode-pipelex`](https://open-vsx.org/extension/Pipelex/pipelex)**

> 💡 **Recommended editor:** Install **`vscode-pipelex`** to edit `.plx` pipeline files. It works with **VS Code, Cursor, Windsurf, BlackboxAI**, and most VS Code forks.

---

## What’s in this org?

* **`pipelex` — Core library & PLX language**
  Define, run, and compose pipelines (sequences/branches of “pipes”) across one or more LLMs with structured I/O, validation, and clear contracts. PLX—the Pipelex language—is an **open standard** for declaratively specifying AI workflows.

* **`pipelex-cookbook` — Examples & recipes**
  Runnable pipelines you can clone and tweak: quick starts, demos, and best-practice patterns.

* **`pipelex-starter` — New project template**
  A template repo to bootstrap your Pipelex project with batteries included: `Makefile`, env setup, tests, and a minimal pipeline.

* **`cocode` — AI-powered code analysis & docs CLI**
  Command-line tool to analyze local or GitHub repositories, convert codebases into AI-friendly text formats, extract interfaces/imports, and automate docs & release chores—implemented as Pipelex pipelines.

---

## Choose your path

### 1) I want to **discover & run example pipelines** (Cookbook)

```bash
# Clone and install
git clone https://github.com/Pipelex/pipelex-cookbook.git
cd pipelex-cookbook
make install   # creates a virtual environment and uses uv to install pipelex and deps

# Configure secrets
cp .env.example .env
# Add e.g. OPENAI_API_KEY=... (others optional depending on examples)

# Run the Hello World
python quick_start/hello_world.py
```

> 🔧 Tip: Install **[`vscode-pipelex`](https://open-vsx.org/extension/Pipelex/pipelex)** for syntax highlighting and a great editing experience in `.plx` files (VS Code, Cursor, Windsurf, BlackboxAI, and most forks).

---

### 2) I want to **start a new project** (Starter)

1. Open [`pipelex-starter`](https://github.com/Pipelex/pipelex-starter) and click **Use this template**.
2. After GitHub creates your repo:

   ```bash
   git clone <your-new-repo-url>
   cd <your-new-repo>
   make install
   cp .env.example .env  # add your keys (OPENAI_API_KEY is enough to start)
   ```
3. Install **[`vscode-pipelex`](https://open-vsx.org/extension/Pipelex/pipelex)** and start building `.plx` pipelines under `pipelines/` (or your preferred structure).

---

### 3) I want to **use Pipelex in my own code** (Core library)

```bash
# Install the library
pip install pipelex          # or: poetry add pipelex | uv pip install pipelex

# Optional extras for providers/models
pip install "pipelex[anthropic,google,mistralai,bedrock,fal]"
```

**Requirements:**

* Python ≥ **3.10** for the core library.
* Add provider API keys to your environment (`.env` or CI secrets).
* Use **[`vscode-pipelex`](https://open-vsx.org/extension/Pipelex/pipelex)** to edit `.plx` files.

See the **[Docs](https://docs.pipelex.com/)** for the PLX language spec, LLM integrations, and composition patterns.

---

### 4) I want to **analyze & document a codebase** (cocode)

```bash
# Install the CLI
pip install cocode
# Explore commands
cocode --help
```

Use **cocode** to analyze local or GitHub repositories and generate AI-friendly summaries, interfaces, and docs.

---

## Contributing

We ❤️ contributions across the ecosystem:

* **Core library:** see `CONTRIBUTING.md` in `pipelex` (dev setup, tests, PR process).
* **Examples/recipes:** add new pipelines under `pipelex-cookbook` (start with `examples/wip/<your-folder>` and include a short README in your PLX).

---

## Community & support

* 📚 **Docs:** **[https://docs.pipelex.com/](https://docs.pipelex.com/)**
* 🐛 **Issues:** use the repo issue trackers (`pipelex`, `pipelex-cookbook`, `pipelex-starter`)
* ✉️ **Security/Privacy:** [security@pipelex.com](mailto:security@pipelex.com)

---

## License & trademark

* Repos are generally **MIT** (see each repo’s `LICENSE`).
* “Pipelex” is a trademark of **Evotis S.A.S.**
