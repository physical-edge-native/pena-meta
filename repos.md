# Repositories

The source for the repository table on the project website and the organization profile.
Update this file first; the coordinating agent checks that the website and the profile match it.

Last checked: 2026-11-25.

| Repository | The question it answers | Status | Depends on | Maintainer |
|---|---|---|---|---|
| [dyne](https://github.com/physical-edge-native/dyne) | Can a physical model be split across many small devices, kept bit-exact with a single computer through loss, delay, joining and leaving, and fed by local sensors? | research prototype, v0.1.0 (DOI 10.5281/zenodo.24241009) | — | gunjou-like |
| [erg](https://github.com/physical-edge-native/erg) | On the same cheap four-legged robot without vision, how does control split over the legs (neighbour-only exchange) differ from one central policy? | just started: skeleton, Dyne submodule, bit-exact check, CI | dyne | gunjou-like |
| [gauss](https://github.com/physical-edge-native/gauss) | The same comparison as a pure question of model architecture, at the size of industrial robots | just started: README only | — | gunjou-like |
| [poise](https://github.com/physical-edge-native/poise) | Can a soft robot body be used as part of the computation (physical reservoir computing) for control? | just started: README only | — | gunjou-like |
| [physical-edge-native.github.io](https://github.com/physical-edge-native/physical-edge-native.github.io) | The project website | live | — | gunjou-like |
| [.github](https://github.com/physical-edge-native/.github) | Organization profile, shared issue templates, code of conduct | live | — | gunjou-like |
| [barye](https://github.com/physical-edge-native/barye) | (merged into dyne on 2026-11-16) | archived | — | — |
| pena-meta | Cross-repository contracts and decisions | this repository | — | gunjou-like |

## Starting a new repository

A new repository is created only after a proposal here states:
1. the question only that repository answers, and its relation to PENA;
2. why it is not part of an existing repository;
3. who maintains it.

New repositories start with `LICENSE-MIT`, `LICENSE-APACHE`, a README with a status line, and a row in
this table.
