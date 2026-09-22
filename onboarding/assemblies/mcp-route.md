## Get started

{% include "blocks/pitch.md" %} This repository is how a chat or a coding agent reaches it.

Pick one server for a given host: the **workshop** wherever there is a filesystem, the **console** everywhere else. Never both — the two deployments register the same tool names.

**Hosted console** — {% include "blocks/connect/hosts-console.md" %}. {% include "blocks/connect/remote-connector.md" %}

**Local workshop** — {% include "blocks/connect/hosts-workshop.md" %}.

{% include "blocks/connect/stdio.md" %}

On Claude Code and Codex the [Pipelex plugin](https://github.com/Pipelex/pipelex-plugins) already declares the workshop, so install the plugin instead and skip the command above.

**Then ask for something.** On the console, attach a file first:

{% include "blocks/first-run/chat-host-ask.md" %}

On the workshop, where the server reaches the files you are writing:

{% include "blocks/first-run/workshop-ask.md" %}

{% include "blocks/first-run/run-id.md" %}

{% include "blocks/links.md" %} · {% include "blocks/links-tail/discord.md" %}
