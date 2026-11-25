# Contracts between repositories

Interfaces and versions that more than one repository depends on. A change to any row is a
cross-repository change: open a proposal here first (see README).

Last checked: 2026-11-25 (initial version, from dyne `85a9efd` and erg `7348aa9`).

## Interfaces owned by dyne

| Contract | Where it is defined | Current version | Used by |
|---|---|---|---|
| Wire format for values exchanged between devices | `dyne/crates/dyne-wire` (`VERSION`) | **2** (24-byte header; no sequence number or CRC inside the format) | dyne, erg |
| Envelope around the wire format on real radios | `dyne/crates/dyne-wire/src/envelope.rs` (`ENV_VERSION`) | **1** | dyne |
| Solver interface (WebAssembly solver ABI: configuration keys, modes, faces, boundary kinds) | `dyne/crates/dyne-wire/src/abi.rs` | as of dyne `85a9efd` | dyne, erg |
| Model file for learned solvers (`.dynm`) | `dyne/crates/mlp-core` (magic `DYNM`) | as of dyne `85a9efd` | dyne, erg |
| Learned-solver WebAssembly component | `dyne/crates/mlp-actor` | as of dyne `85a9efd` | dyne, erg |
| Deterministic virtual network (loss, delay, partitions; seeded) | `dyne/crates/dyne-core` | as of dyne `85a9efd` | dyne, erg |
| Rules for a device leaving and rejoining | dyne docs (`docs-site/concepts.md`) | rejoin into the computation is **not yet** implemented on hardware (dyne #131) | dyne, erg |

Dyne is not published on crates.io. Other repositories depend on it at a **fixed commit**.

## Pinned commits

| Repository | Depends on | Pinned commit | How | Updated |
|---|---|---|---|---|
| erg | dyne | `85a9efd` | git submodule `third_party/dyne` | 2026-11-24 |
| gauss | — | — | — | — |
| poise | — | — | — | — |

Rule: moving a pin is its own issue and pull request, and every bit-exact check in the dependent
repository must pass before merging.

## Shared conventions

| Convention | Value |
|---|---|
| License (code) | MIT OR Apache-2.0, files `LICENSE-MIT` and `LICENSE-APACHE` |
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
