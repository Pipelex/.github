# The onboarding source

This is where the words a newcomer reads are written. Every public Pipelex surface that tells someone what Pipelex is, asks them to sign up, or shows them their first command takes its text from here — a README quick start, a documentation page, a marketplace description, a repository About. The text is written once, in this tree, and a surface either includes it verbatim or is hand-written from it and re-read when it moves.

The reason the tree exists is drift. The same instruction was being written independently on every surface, so the install command on one page was a release behind the one on the next, the sign-up sentence had a different shape in each place a reader met it, and the list of hosts a connector reaches was three different lists. One source makes those one thing that can be wrong once and fixed once.

## The three layers

**Blocks** are the atoms, under `blocks/`. One file per block per variant, and a variant exists only along one of three axes: the agent target (`install/claude-code.md`, `install/codex.md`), the MCP host family (`connect/remote-connector.md`, `connect/stdio.md`), and the SDK language (`first-run/api-typescript.md`, `first-run/api-python.md`). A file that varies along a fourth axis — one surface wanting its own wording — is the drift this tree exists to stop, and the answer is to change the block for everyone or to leave the difference in the assembly. A block may include another block, which is how a route's example ask and the sentence closing it stay one text while a surface that needs only the ask can reach for it alone.

**Not every block has a consumer yet.** This tree is the source for every public Pipelex surface, and the assemblies arrive as the surfaces that take them are written. A block that no assembly includes today is waiting for the website, the documentation site or a starter, not dead — the manifest, not the assemblies, is where to read which surfaces are wired up.

**Assemblies** are the ordered sets of blocks a class of surface carries, under `assemblies/`. Each is a Jinja2 template that does nothing but include blocks, with the glue that is the assembly's own written out between them: the numbered step lines, the `<details>` wrappers, the paragraph naming the ways this surface is not showing. `front-door.md` is a Pipelex-branded repository's quick start; `mcp-route.md` is the MCP repository's get-started.

**Rendered assemblies** are those templates rendered, under `rendered/`, committed as build artifacts. They are what a surface actually carries and what a drift check fetches by raw URL, so a consumer reads one file instead of running a renderer. A rendered file is never edited: it is the output of its assembly and its blocks, and a change to it that did not come from them is a change that will be overwritten.

## How a surface includes an assembly

A consumer carries its region between a pair of HTML comments, invisible on the GitHub, PyPI and npm renderings:

```markdown
<!-- onboarding: front-door -->
<!-- Included from https://github.com/Pipelex/.github/blob/main/onboarding/rendered/front-door.md — edit it there, not here. -->
## Quick start

…the rendered assembly, whose first line is its own `##` heading…
<!-- /onboarding -->
```

The opening comment names the assembly, and that name is what a checker matches on and what `surfaces.toml` records. The provenance line is the first line inside the region, so a contributor reading the raw file learns where to edit before they edit the wrong copy; it sits inside the markers rather than above them because the tool rewrites the whole region, and a line outside would drift from the assembly it points at. It names `main` and the rendered file, which is the address a drift check fetches. The closing comment carries no name: a file holds at most one region per assembly, and regions do not nest.

**Nobody edits the text inside a region.** A region that has drifted is fixed by re-applying the assembly, never by editing the surface. Where the marker is present, the surface's own words start after the closing comment.

## How a surface adapts instead

A website's data file, a mkdocs page, a marketplace description field and a bio take no region. They are hand-written from the blocks in the format their surface wants, and `surfaces.toml` records for each one the commit of the rendered assembly it was last re-read against — its stamp. A change here therefore ends with a list of surfaces a person now re-reads by hand, which is the price of a format that cannot take a region.

## The manifest

`surfaces.toml` is every surface that carries text from this tree, with its repository, its path, its mode and its assembly. It is the machine form of the include and adapt rows of the workspace inventory, `docs/marketing/surfaces.md` in the Pipelex meta-repo, which stays the page a person reads.

## Conventions this tree holds itself to

- **A block is included inline as readily as it is included as a paragraph**, so no block file's text ends on a blank line and the renderer drops a block's final newline on include. That is what lets `**1. {% include "blocks/sign-up.md" %}**` produce one bold line.
- **A host list is a block of its own**, `connect/hosts-console.md` and `connect/hosts-workshop.md`, because a list of hosts is the thing most likely to gain a row and the thing that had already drifted into three versions. A surface that names the hosts includes the block; it does not retype the names.
- **A first-run block begins at the example ask.** The sentence introducing it belongs to the surface, because a front door renders it as a numbered step and a standalone section renders it as a sentence, and a block carrying both would be a variant along the surface.
- **A route is only offered where it can be followed.** What a reader can do depends on which server their host talks to — `pipelex-mcp`'s `SPEC.md` marks a tool local-workshop-only or hosted-console-only — so an assembly that offers more than one route renders the first run of each. A step that names a plugin command is a step the connector route cannot take, and a step that names a path on disk is a step the console cannot take. The split goes one level deeper than the two servers: a capability can also depend on the *host*, and `mthds_upload_attachments` is the case — the console registers it, but only ChatGPT supplies the attachment channel it needs, so "run it on the file I attached" is wrong for the other connector hosts. Check the capability against that file before writing a step that assumes it.
- **A block whose subject is the repository carrying it is chosen per repository.** `open-source/` is the only one: its sentence says what this repository is and under which licence, so a shared file would make the second consumer of an assembly publish a false claim about itself. The assembly selects the file — `{% include "blocks/open-source/" ~ (open_source | default("runtime")) ~ ".md" %}` — and a repository that takes the front door adds its own file there and renders its own output. `pipelex-plugins` is not the runtime and is Apache 2.0, so it takes neither that sentence nor that licence, and a front door rendered for it says so or says nothing.
- **An assembly's glue may name its own surface; a block may not.** `mcp-route` says "this repository is how a chat or a coding agent reaches it" because that assembly serves one repository and the manifest says which. A block is included by anything, so a block that describes its host is a claim nobody re-reads when a second surface takes it.
- **A code sample runs as written.** A reader copies the whole fence, so a Python sample carries its `asyncio.run`, a shell sample assigns every variable it reads, and a sample that needs a file says where the file comes from.
- **A command is copied, never retyped.** Every command on every surface comes from a block here, and a command that has changed is changed here first.
- **The words are checked against the marketing guides** in the meta-repo: `docs/marketing/lexicon.md` for the words that are forbidden, `voice.md` for the register, `positioning.md` for the frame.
