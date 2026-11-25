# pena-meta

The single source of truth for everything that spans more than one repository of the
[Physical-Edge Native Architecture](https://physical-edge-native.github.io/) (PENA) project.

Each repository decides its own internals. Anything that two or more repositories must agree on —
shared interfaces, pinned versions, licenses, terms, cross-repository decisions, and the status shown on
the project website — is written here, and only here. When a repository disagrees with this
repository, this repository wins until a decision recorded here says otherwise.

| File | Contents |
|---|---|
| [contracts.md](contracts.md) | Interfaces and versions that repositories depend on (wire format, solver interface, model file format, pinned commits) |
| [repos.md](repos.md) | Every repository: its question, status, maintainer, dependencies. The source for the website's repository table |
| [decisions/](decisions/) | Decisions that affect more than one repository, with date, reasons and options considered |
| [glossary.md](glossary.md) | Terms used across repositories, in English and Japanese |
| [roadmap.md](roadmap.md) | Project-wide plan and milestones |
| [reports/](reports/) | Weekly consistency reports written by the coordinating agent |
| [cross-repo-rules.md](cross-repo-rules.md) | The section every repository's `CLAUDE.md` includes |

## How changes happen

1. Anyone who needs a change to something listed here opens an issue in this repository using the
   **Cross-repository proposal** template, naming the repositories affected.
2. The maintainer decides. The decision is written to `decisions/` and, if needed, to `contracts.md`.
3. Follow-up issues labelled `cross-repo` are opened in each affected repository and linked back.

## The coordinating agent

An AI agent (Claude) checks once a week that the repositories agree with this repository, writes a report
to `reports/`, and proposes issues. It reads every repository but changes none of them; decisions stay
with the maintainer. Its instructions are in [CLAUDE.md](CLAUDE.md).

## License

Licensed under either of Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE)) or MIT license
([LICENSE-MIT](LICENSE-MIT)) at your option.
