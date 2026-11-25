# Cloud sessions push work branches without asking; main is protected in every repository

- Date: 2026-11-25
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: all repositories, including pena-meta
- Proposal: [#7](https://github.com/physical-edge-native/pena-meta/issues/7)

## Decision

1. The rule in `cross-repo-rules.md` stays: a cloud session may commit and push to its work branch without asking.
   The user still agrees before a branch is created and before a pull request is opened, and gives permission
   before a merge. Nobody pushes to main. pena-meta's own `CLAUDE.md` follows the same rule.
2. **main is protected in every repository** by a GitHub ruleset that blocks deletion and force pushes, requires a
   pull request, and requires the repository's CI checks to pass.
3. The weekly consistency check verifies that main is protected in every repository.

## Reasons

Pushing without asking keeps work on the branch, so it survives an interruption of the session. That is safe only
if a mistaken push to main is blocked by GitHub, not only by a rule in a text file. On 2026-11-25 erg's main was
not protected at first; the ruleset `protect-main` was then added (deletion, force pushes, pull request required),
and the CI requirement is to be added. pena-meta's main had the same rules without a CI requirement.

## Options considered

- (a) Keep the new rule, align pena-meta, require protection everywhere. **Chosen.**
- (b) Return to asking before every push.
- (c) Keep both rules and let the stricter one win.
