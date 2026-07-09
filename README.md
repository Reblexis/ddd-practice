# DDD Practice

A specific way to practice [docs-driven development](https://github.com/Reblexis/docs-driven-development): how to adopt it in an existing project, and how to use and develop with it when AI agents write the code.

The core idea deliberately specifies nothing beyond itself — no doc structure, no conformance process, no migration path. This repo is one derived design that fills those in. It is opinionated where the core is silent; where it disagrees with the core, this repo is wrong. Your project may derive a different practice; its own docs win over this one.

## This repo follows its own standard

This README is the source of truth for this repository. Everything below it in the hierarchy is derived from it and is wrong wherever it disagrees with it. Changes to this practice happen here first, then flow downward.

The repo consists of this README and two lower-layer documents it governs:

- [`docs/adoption.md`](docs/adoption.md) must describe how an existing project becomes docs-driven, in three moves: **declare** (state in the project's most authoritative doc that docs govern), **bootstrap** (build the doc hierarchy out of existing docs, existing code, and the owner's intent — reusing, never duplicating), and **reconcile** (run the first conformance audit and fix what it finds). It must treat existing code as an implementation whose docs don't exist yet, with no special status once they do.

- [`docs/operating.md`](docs/operating.md) must describe day-to-day development with agents once adopted: every behavior change starts as a doc edit; agents conform code to docs and never the reverse; conformance is verified by a party other than the code's author; each divergence found is classified as a code bug (doc right, code wrong — fix the code), a doc bug (code sensible, doc stale — fix the doc), an ambiguity (two plausible readings — tighten the one sentence that caused it), or unspecified behavior (write it into the docs if others depend on it, leave it as freedom if not). It must describe how docs layer — broad intent at the top, precision concentrated at the boundaries other components and agents depend on — and how rules learned from bugs get promoted into the docs so they survive rewrites. It must state that the human is spoken to in terms of docs and observable behavior, never code, and that decisions brought to the human are framed as proposed doc edits.

Anything the lower documents say beyond this specification is their freedom, provided it contradicts neither this README nor the core idea.

## License

[MIT](LICENSE)
