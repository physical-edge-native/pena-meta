# Which changes to another repository are proposed in pena-meta first

- Date: 2026-11-25
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: all repositories that depend on another (erg and dyne now)
- Proposal: [#6](https://github.com/physical-edge-native/pena-meta/issues/6)

## Decision

"Changes that affect other repositories", which `cross-repo-rules.md` asks to propose in pena-meta first, are:

- changes to a contract listed in [`contracts.md`](../contracts.md) (wire format version, solver interface,
  `.dynm` model file, learned-solver component, virtual network, rules for leaving and rejoining), and
- changes to a public claim (what a repository says it shows or does not show).

A request that adds to another repository **without** changing a listed contract or a public claim (a new part,
a feature, a bug fix) is proposed directly as an issue in that repository. When unsure, propose in pena-meta.

## Reasons

erg depends on dyne wherever possible (decision of 2026-11-24), so requests from erg to dyne will be frequent.
Routing every small addition through pena-meta would slow them down without protecting anything; what other
repositories rely on is what `contracts.md` lists. Drawing the line at `contracts.md` makes the choice mechanical.

## Options considered

- (a) Everything through pena-meta.
- (b) Only changes to listed contracts or public claims through pena-meta; other requests directly. **Chosen.**
- (c) Always directly to the other repository, informing pena-meta afterwards.

Found while adding the cross-repository rules to erg (physical-edge-native/erg#17).
