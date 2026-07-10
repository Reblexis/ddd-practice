# DDD Practice

A specific way to practice [docs-driven development](https://github.com/Reblexis/docs-driven-development): adopting it in existing projects, and developing with AI agents.

- [`docs/practice.md`](docs/practice.md), the governing doc (minimal, one specification).
- [`implementation/`](implementation/), the implementation of that description: [`adoption.md`](implementation/adoption.md) and [`operating.md`](implementation/operating.md).
- [`skill/`](skill/SKILL.md), an installable skill for AI agents: copy or symlink it into an agent's skills directory.
- [`index.html`](index.html), the human-readable representation of `./docs` (covers the docs and nothing else; the docs win). Open it in a browser.

## License

[MIT](LICENSE)

---

This repo uses [ddd-practice](https://github.com/Reblexis/ddd-practice) (itself): docs are the source of truth, everything else is derived. `./docs` holds one governing document, [`practice.md`](docs/practice.md). The human-readable representation is [`index.html`](index.html) at the repo root, also served at [reblexis.github.io/ddd-practice](https://reblexis.github.io/ddd-practice/).
