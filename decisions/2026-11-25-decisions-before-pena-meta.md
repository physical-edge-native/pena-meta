# Decisions taken before pena-meta existed

Date of this record: 2026-11-25. Decided by the maintainer; this record was written with an AI assistant.
Each entry gives the original date. Details live in the linked repositories.

| Date | Decision | Reasons (short) | Affects |
|---|---|---|---|
| 2026-11-07 | The design for computing a physical space with the many small devices in it is called the **Physical-Edge Native Architecture** (PENA). Dyne is its first implementation | gives the work a name independent of one tool | all |
| 2026-11-07 | The GitHub organization is `physical-edge-native` | — | all |
| 2026-11-15 | **No patents.** Code is released under **MIT OR Apache-2.0** | patents would not help the career plan or the aim of a shared, royalty-free architecture; publication also prevents others from patenting the ideas | all |
| 2026-11-15 | Wi-Fi scan data had MAC addresses replaced by pseudonyms across the whole Dyne history before publication | privacy of neighbours' devices | dyne, all future data |
| 2026-11-16 | **barye is merged into dyne** and archived | CPU field solvers that exchange border values are a mature technique with established tools; the open question is on the device side | dyne, barye |
| 2026-11-16 | A central computer may join **only for forecasting**: it takes over the assimilated state with the same solver bits and leaves; it never collects raw data or becomes the everyday computer | keeps the twin on the devices while allowing faster-than-real-time prediction | dyne, future repositories |
| 2026-11-16 | Dyne's forecasting is "assimilation and forecasting connected to a real space", not general-purpose field physics; detailed prediction is exported to specialised tools | do not compete with mature solvers on accuracy | dyne |
| 2026-11-18 | Project website at `physical-edge-native.github.io`; Dyne documentation built from the dyne repository and published under `/dyne/`; English only | documentation changes travel with code changes | dyne, website |
| 2026-11-24 | Robot control is split into **erg** (cheap legged robot, split vs central control, no vision), **gauss** (same comparison at industrial size, as model architecture) and **poise** (physical reservoir computing with a soft body). Control that uses physical fields as input is erg's future direction | each answers a question the others cannot answer on equal terms | erg, gauss, poise |
| 2026-11-24 | erg depends on dyne wherever possible (solver components, wire format, virtual network, leave/rejoin rules), pinned at a fixed commit | avoid re-implementing shared parts | erg, dyne |
| 2026-11-24 | Others may start repositories in the organization after a proposal (question, why separate, maintainer); inactive repositories may be archived after about six months, after asking the maintainer | grow the community without fragmenting it | all |
| 2026-11-25 | Cross-repository contracts and decisions live in **pena-meta**; a coordinating agent checks consistency weekly and only proposes | repositories are worked on by separate agents | all |
