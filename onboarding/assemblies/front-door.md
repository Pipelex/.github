## Quick start

{% include "blocks/pitch.md" %}

**1. {% include "blocks/sign-up.md" %}**

**2. Install the plugin for your agent.**

<details open><summary><b>Claude Code</b></summary>

{% include "blocks/install/claude-code.md" %}

</details>

<details><summary><b>Codex</b></summary>

{% include "blocks/install/codex.md" %}

</details>

<details><summary><b>Chat hosts — {% include "blocks/connect/hosts-console.md" %}</b></summary>

{% include "blocks/connect/remote-connector.md" %}

</details>

**3. Ask for the method you want.**

{% include "blocks/first-run/agent-short.md" %}

**On a chat host**, where methods are run rather than built:

{% include "blocks/first-run/chat-host.md" %}

**The other two ways.** Turn the method into a webapp with the [method-app template](https://github.com/Pipelex/pipelex-method-apps), or use it via API in any software through `POST /v1/start` — in TypeScript with [`@pipelex/sdk`](https://www.npmjs.com/package/@pipelex/sdk), in Python with [`pipelex-sdk`](https://pypi.org/project/pipelex-sdk/), or with any HTTP client.

{% include "blocks/links.md" %} · {% include "blocks/links-tail/discord.md" %}

{% include "blocks/open-source.md" %}
