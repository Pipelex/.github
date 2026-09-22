# Pipelex/.github

This repository is the Pipelex organisation's shared public face. It holds two things, and neither is code.

`profile/README.md` is the organisation profile — the page GitHub renders at [github.com/Pipelex](https://github.com/Pipelex) above the repository list. GitHub reads it from `main`, so a change is live at the merge.

`onboarding/` carries the published onboarding text every public Pipelex surface takes its words from: what Pipelex is, how to sign up, which command to run first. A README quick start, a documentation page, a marketplace description and a repository About all read it from here rather than each writing their own, which is why it is published by a repository that belongs to no single product. The files are generated and are not edited here — [`onboarding/README.md`](onboarding/README.md) says how a surface carries one and where to report something wrong with it.

Pull requests here target `dev`, as everywhere in the organisation; `dev` is then promoted to `main`, which is what the organisation serves and what a consumer's drift check fetches by raw URL.
