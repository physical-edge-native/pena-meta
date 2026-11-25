# Preparing the organization for outside contributors

- Date: 2026-11-26 (organization settings changed on 2026-11-25)
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: all repositories

## Context

About ten people joined the project's Discord server, from beginners to engineers experienced with ESP32
microcontrollers, and some want to contribute. Before inviting them to work in the repositories, the
organization was prepared so that outside contributions are safe and easy.

## Organization settings (done by the maintainer on 2026-11-25)

1. Members' base permission is **Read**, and members cannot create repositories. Outside contributors work
   through forks and pull requests, not as organization members.
2. GitHub Actions workflows from fork pull requests **need the maintainer's approval for all external
   contributors**. The default workflow token is read-only, and Actions may not create or approve pull requests.
3. The **GitHub recommended** security configuration is applied to all repositories and is the default for new
   ones: secret scanning with push protection, code scanning, Dependabot alerts and security updates. Private
   repositories get only the free features. Repository owners cannot switch features off individually.
4. An organization ruleset **`protect-main-all`** applies to the default branch of every repository, including
   future ones: no deletion, no force pushes, pull request required (0 approvals). The rulesets of individual
   repositories stay; CI checks remain required per repository where CI exists.

## Decisions

1. **Contributions are licensed inbound = outbound.** A pull request is accepted under the repository's license,
   MIT OR Apache-2.0, as stated in CONTRIBUTING. No sign-off line and no contributor license agreement.
2. **Where to go**: questions in GitHub Discussions, conversation and help in Discord, bugs as Issues. SUPPORT.md
   lists all three, including the Discord invite link.
3. **Review**: CODEOWNERS names the maintainer for every file in every repository for now; trusted contributors
   can be added for parts later.

## Reasons

Forks and pull requests let anyone contribute without giving write access. Approval before running fork
workflows and push protection prevent the most likely accidents (unexpected code on CI, committed Wi-Fi
passwords or keys). An organization ruleset protects repositories created later. Inbound = outbound is the usual
practice in Rust projects and asks nothing extra of contributors. The Discord link can be public now because
the earlier condition (people gathering) is met.

## Options considered

- License of contributions: (a) inbound = outbound **chosen**; (b) also require a sign-off line (DCO);
  (c) contributor license agreement.
- Support: (a) Discussions, Discord and Issues, with the Discord link public **chosen**; (b) Discussions and
  Issues only.
- Review: (a) maintainer for everything **chosen**; (b) add other reviewers per area (possible later).

## Follow-up

- `.github`: organization-wide CONTRIBUTING, SECURITY, SUPPORT, issue and pull request templates.
- Each repository: CODEOWNERS; labels `good first issue` and `help wanted`.
- dyne: three to five first issues for newcomers (without hardware, and with ESP32 boards).
- Then decide on a shared repository where contributors can experiment freely.
