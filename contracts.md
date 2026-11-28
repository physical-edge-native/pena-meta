# Contracts between repositories

Interfaces and versions that more than one repository depends on. A change to any row is a
cross-repository change: open a proposal here first (see README).

Last checked: 2026-11-28 (erg moved its Dyne pin to `v0.2.0` in erg#91; the crates erg uses changed only their version numbers since `85a9efd`).

## Interfaces owned by dyne

| Contract | Where it is defined | Current version | Used by |
|---|---|---|---|
| Wire format for values exchanged between devices | `dyne/crates/dyne-wire` (`VERSION`) | **2** (24-byte header; no sequence number or CRC inside the format) | dyne, erg |
| Envelope around the wire format on real radios | `dyne/crates/dyne-wire/src/envelope.rs` (`ENV_VERSION`) | **1** | dyne |
| Solver interface (WebAssembly solver ABI: configuration keys, modes, faces, boundary kinds) | `dyne/crates/dyne-wire/src/abi.rs` | as of dyne `v0.2.0` (`2919654`) | dyne, erg |
| Model file for learned solvers (`.dynm`) | `dyne/crates/mlp-core` (magic `DYNM`) | as of dyne `v0.2.0` (`2919654`) | dyne, erg |
| Learned-solver WebAssembly component | `dyne/crates/mlp-actor` | as of dyne `v0.2.0` (`2919654`) | dyne, erg |
| Deterministic virtual network (loss, delay, partitions; seeded) | `dyne/crates/dyne-core` | as of dyne `v0.2.0` (`2919654`) | dyne, erg |
| Rules for a device leaving and rejoining | dyne docs (`docs-site/concepts.md`) | two modes, chosen per run ([decision](decisions/2026-11-28-leaving-and-rejoining.md)): *wait and restore* (bit-exact with a fault-free run) and *continue and rejoin as new* (equals a simulator run with the same leave and join). Rejoin into the computation is **not yet** implemented on hardware (dyne #131) | dyne, erg |
| Environment export (room geometry for robot simulators: USD, MJCF) | dyne export tools | frame: Z up, units: metres, as of the dyne commit erg pins ([decision](decisions/2026-11-28-environment-export-contract.md)) | dyne, erg |

Dyne is not published on crates.io. Other repositories depend on it at a **fixed commit**.

## Pinned commits

| Repository | Depends on | Pinned commit | How | Updated |
|---|---|---|---|---|
| erg | dyne | `v0.2.0` (`2919654`) | git submodule `third_party/dyne` | 2026-11-28 (erg#91) |
| gauss | erg (robot model `models/quadruped.xml`) | `7c2f070` (merge of erg#67, body L1 model) | fetched by script, checked by SHA-256 ([decision](decisions/2026-11-28-gauss-uses-ergs-model.md)) | 2026-11-29 (gauss#48) |
| poise | — | — | — | — |

Rule: moving a pin is its own issue and pull request, and every bit-exact check in the dependent
repository must pass before merging.

## Shared conventions

| Convention | Value |
|---|---|
| License | MIT OR Apache-2.0, files `LICENSE-MIT` and `LICENSE-APACHE`, in every repository including the website and `.github` (code and text; [decision](decisions/2026-11-25-license-for-website-and-profile.md)) |
| Copyright line in `LICENSE-MIT` | `Copyright (c) 2026 The Physical-Edge Native contributors` |
| `CITATION.cff` license field | `Apache-2.0` with a comment that the work is dual-licensed (a list or `MIT OR Apache-2.0` breaks the Zenodo import) |
| Repository names | units of the CGS system (dyne, barye, erg, poise, gauss) for projects; descriptive names for infrastructure |
| User-facing documentation | English; internal working notes may be Japanese |
| Development flow | Issue → branch `<issue>-<short-english>` → pull request with `Closes #N` → CI green on Linux, macOS, Windows → merge |
| Change log | fragments in `changelog.d/`; `CHANGELOG.md` is generated |
| AI assistance | commits with agent-written code keep `Co-Authored-By:`; design records state that an AI assistant helped |
| Claims | no repository claims superiority over centralised or GPU-based approaches; measured differences are the result |
| Data hygiene | no secrets, personal data, or real MAC addresses of other people's devices in any public repository |
| Primary bit-exact check | split solution equals single-domain solution, bit for bit, also across operating systems |
| Outside contributions | through forks and pull requests; accepted under the repository's license (inbound = outbound), no sign-off or CLA ([decision](decisions/2026-11-26-outside-contributors.md)) |
| Where people go | questions: GitHub Discussions; conversation: Discord; bugs: Issues (listed in `SUPPORT.md`) |
| Review | `CODEOWNERS` names the maintainer for every file |
| Organization settings | members read-only and cannot create repositories; fork workflows need approval; GitHub recommended security configuration on all repositories; ruleset `protect-main-all` on every default branch |
