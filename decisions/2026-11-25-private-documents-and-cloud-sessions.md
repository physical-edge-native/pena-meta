# Private working documents: one private GitHub repository per repository, the most sensitive data local only

- Date: 2026-11-25
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: every repository that keeps private working documents (erg now; others when they need them)
- Proposal: [#5](https://github.com/physical-edge-native/pena-meta/issues/5)

## Decision

1. A repository that needs private working documents has its **own private GitHub repository**, named
   `<repository>-private` (for example `erg-private`) in the organization. It holds the documents a cloud session
   must be able to continue: internal notes, plans, meeting notes, drafts of talks.
2. The **most sensitive data stays on the maintainer's PC only**, in a local git repository that is never pushed
   to GitHub: spending records (including the prices actually paid for parts), notes with the MAC addresses of
   real devices, and anything close to contract work. It is also kept per repository.
3. A cloud session never commits private content to a public repository. When it produces something that belongs
   in the local-only store, it hands the text to the user instead of committing it.
4. When it is unclear whether something is public or private, a cloud session does not commit it anywhere; it
   hands it to the user and asks.

Each repository's CLAUDE.md is updated to match in a follow-up issue labelled `cross-repo`. In erg, the existing
local-only `erg-private` takes the name of the new private GitHub repository; how its content is split between the
GitHub repository and the local-only store, and what the local-only store is called, are settled in erg's follow-up issue.

## Reasons

- Implementation is done mainly in cloud sessions (`cross-repo-rules.md`). A cloud session cannot reach a
  repository that exists only on the maintainer's PC, so plans kept there could not be continued after an
  interruption, and private notes were at risk of being put in a public repository instead.
- Spending records and real MAC addresses gain nothing from being reachable in the cloud and are safer off GitHub.
- **One private repository per repository, not one for the organization**: when several repositories need the
  same kind of hardware, a shared store would make it easy for one repository to count on hardware bought for
  another, and end up with too few parts. Separate stores keep each repository's purchases and needs apart.

## Options considered

Where private documents live:

- (a) A private GitHub repository for everything (reachable from the cloud; the most sensitive data held by GitHub).
- (b) Local only, as before; cloud sessions never write private notes and hand them to the user.
- (c) Split: what must be resumable in a private GitHub repository, the most sensitive data local only. **Chosen.**

How the private GitHub repositories are divided:

- (A) One repository for the organization (`pena-private`).
- (B) One per repository (`<repository>-private`). **Chosen**, for the reason above.
