# Adoption: making an existing project docs-driven

Implementation of [docs/practice.md](../docs/practice.md) — elaboration is this document's freedom; where it overlaps the [idea](https://github.com/Reblexis/docs-driven-development/blob/master/docs/idea.md), the idea is the source and wins. An existing project is an implementation whose docs don't exist yet. Adoption gives it docs and inverts the authority: from the moment the docs exist, they are the source of truth and the code has no special status — not even the parts that work.

Adoption is three moves. They can be done in an afternoon; the third one starts a loop that never ends.

## 1. Declare

State, in the project's governing docs — which live in `./docs` per the idea; create the root document there if nothing qualifies — that the project is docs-driven: the docs are the source of truth, all code is a derived artifact that exists to satisfy them, code is wrong wherever they disagree, and behavior changes start as doc changes. Link the [core idea](https://github.com/Reblexis/docs-driven-development) so the words have a definition. The declaration doubles as the contributing guide: `./docs` states that anyone developing or contributing here follows [ddd-practice](https://github.com/Reblexis/ddd-practice) — docs first, everything else conforms.

The root README becomes a derived summary of what the repo is and contains, strictly per the docs, linking into `./docs` — it holds nothing normative. Its only mention of the practice is the footer (the practice link, the `./docs` structure, the human-readable representation's location); beyond that the repo reads like any repo with docs, and being docs-driven shows only on deeper inspection, unless the repo's own docs specify otherwise.

The declaration matters because it changes what every later divergence *means*. Before it, a doc that disagrees with code is a stale doc. After it, it is a bug in the code.

If the project already has a doc-update convention ("update the doc in the same commit as the change"), the declaration inverts its direction: doc first, code conforms — same commit at the latest, never after.

## 2. Bootstrap

Build the doc hierarchy out of three sources: the docs that already exist, the code as it actually behaves, and the owner's intent — the one input only the owner can provide.

- **Promote, don't duplicate.** Most existing projects already have fragments of the hierarchy under other names: a vision statement, an API reference, per-component notes. Promote them into their layer under `./docs` rather than writing parallel documents. A project that ends up with two documents claiming the same territory has made its own source of truth ambiguous.
- **A pre-existing `./docs` is raw material, not a fait accompli.** Being in the right directory grants nothing: every file already there gets the same triage as docs found anywhere else. Rework what is genuinely governing (intent, contracts, component specs) into the standard hierarchy — restructured, merged, made minimal, not kept in its old shape. What isn't governing — research notes, generated output, tutorials, meeting records, design explorations, anything descriptive rather than authoritative — moves out of `./docs` to a fitting home in the repo (`notes/`, `research/`, beside the code it describes). If the moved material matters to the project, the docs describe it abstractly and point to it; if not, moving it is enough. After bootstrap, `./docs` contains only the governing hierarchy.
- **Write top-down, precisely where it hurts.** Broad intent at the root; below it, contracts — the interfaces, protocols, and invariants other components or agents depend on; below those, per-component detail only where detail matters. Precision is spent where divergence is expensive (money, protocols, irreversible actions) and withheld everywhere else. Many components need no doc of their own beyond the contracts they participate in.
- **The owner writes intent, agents write everything else.** Agents can draft any layer from the code, but a bootstrapped doc that merely describes the current code has recorded the accident, not the intent. The owner's pass over the drafts — "this is what it *should* do" — is what turns description into specification.

## 3. Reconcile

Run the first conformance audit (the loop described in [operating.md](operating.md)): audit the code against every checkable doc claim, classify each divergence, fix each on its own side — code bugs in code, doc bugs in docs, ambiguities by tightening one sentence.

Do this immediately, not eventually. The first reconciliation is what proves the declaration is real, and in practice it finds things: undocumented behavior other components already depend on, documented behavior that was never built, security invariants the docs state and the code quietly dropped. Every finding is either the docs getting truer or the code getting corrected — both are adoption working.

A project is adopted when the loop has run once and the rule "behavior changes start as doc changes" governs the next change made.
