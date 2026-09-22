# Pipelex/.github

This repository is the Pipelex organisation's shared public face. It holds two things, and neither is code.

`profile/README.md` is the organisation profile — the page GitHub renders at [github.com/Pipelex](https://github.com/Pipelex) above the repository list. GitHub reads it from `main`, so a change is live at the merge.

`onboarding/` is the source of the onboarding text every public Pipelex surface carries: the blocks a reader meets, the assemblies each class of surface includes, and the manifest saying which surface takes which. A README quick start, a documentation page, a marketplace description and a repository About all take their words from there rather than each writing their own, which is why the tree lives in a repository that belongs to no single product. Start at [`onboarding/README.md`](onboarding/README.md), which says how a surface includes an assembly and what is expected of a surface that cannot.

Pull requests here target `dev`, as everywhere in the organisation; `dev` is then promoted to `main`, which is what the organisation serves and what a consumer's drift check fetches by raw URL.
