# Onboarding text, published

The files under `rendered/` are the onboarding text that Pipelex repositories, documentation pages and package listings carry: what Pipelex is, how to sign up, which command to run first. They are published here so that every surface can take the same words from one address, and so that a surface whose copy has fallen behind can be told so by a check that fetches this URL.

**These files are generated, and so is every copy of them.** A repository carries one between a pair of HTML comments, and the text between those markers is replaced wholesale from here rather than edited in place:

```markdown
<!-- onboarding: front-door -->
<!-- Generated from the Pipelex onboarding source; this region is replaced from https://raw.githubusercontent.com/Pipelex/.github/main/onboarding/rendered/front-door.md — do not edit it here. -->
## Quick start

…the rendered text, whose first line is its own `##` heading…
<!-- /onboarding -->
```

A whole get-started text, such as `front-door.md` or `mcp-route.md`, opens with its own `##` heading. `api-key.md` has none: it is the sign-up line and the API-key step, and it sits inside a section of the page that carries it, where a starter, a template or an SDK lists what a reader needs.

So an edit to one of those regions, or to a file here, is an edit the next generation overwrites. If something in it is wrong — a command that fails, a broken link, a step that does not work on your host — please [open an issue](https://github.com/Pipelex/.github/issues) and we will fix it at the source. That is the fastest route, and it fixes it everywhere at once rather than on the page you happened to be reading.
