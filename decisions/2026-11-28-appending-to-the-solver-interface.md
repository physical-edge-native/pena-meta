# Appending to a solver's own part of the solver interface

- Date: 2026-11-28
- Decided by: the coordinator (decision level 1), pending the maintainer's review of this record.
  Written by the coordinating agent (an AI assistant).
- Affects: dyne, erg (and any future repository pinned to dyne)
- Related: [`contracts.md`](../contracts.md) (row "Solver interface"),
  [`2026-11-27-autonomous-operation.md`](2026-11-27-autonomous-operation.md) (levels of decision),
  dyne issue #194 (IMU fusion with per-device zero offsets)

## Context

`contracts.md` lists the solver interface (`dyne/crates/dyne-wire/src/abi.rs`) as a contract between dyne and
erg, and says that a change to any row is a cross-repository change. The cross-repository rules also allow
additions that do not change a contract (new features, fixes) to go directly to the repository.

dyne #194 needs two new configuration keys and one new output index for the IMU fusion solver. They would be
appended inside that solver's own module (`pub mod imu`). The question is which of the two rules applies.

## Decision

1. **Appending is an addition, not a contract change**, when all of the following hold:
   - the new keys or output indices are appended inside one solver's own module of `abi.rs`;
   - no existing key, index, mode, face or boundary kind changes its number or meaning;
   - the wire format and the message size do not change;
   - no other repository's pinned commit uses that solver, or the change leaves its results bit for bit the same
     with default settings.

   Such a change goes directly to dyne, through an issue and a pull request. The pull request states that it is
   append-only and lists the new constants. Because it touches `abi.rs`, the maintainer merges it, not the
   coordinator.
2. **Anything else is a contract change** and needs a proposal in pena-meta first: changing or removing an
   existing value, changing the message size or the wire format, or changing a part of the interface that a
   pinned repository uses.
3. `contracts.md` keeps recording the interface "as of" a dyne commit. The row is updated when a dependent
   repository moves its pin, not on every append.

For dyne #194, option (a) qualifies: `CFG_OFFSET_EPOCHS = 7`, `CFG_DEVICES = 8`, `G_FUSED_DEVICES = 22` and
`G_LEN` from 22 to 23, all in `pub mod imu`. erg does not use the IMU solver. Option (b), which would change the
message size, would not qualify.

## Reasons

- A dependent repository only breaks when a value it uses changes. Appending to a module it does not use cannot
  break it, and erg moves its pin only through its own issue with every bit-exact check passing.
- Requiring a proposal for every append would stop dyne's work on each new solver setting for a level 2
  decision, against the aim of the autonomous-operation decision.

## Options considered

- (a) Appends inside one solver's module are additions; other changes need a proposal **chosen**.
- (b) Every change to `abi.rs` needs a proposal, as a literal reading of `contracts.md`.
- (c) Every addition anywhere in `abi.rs` is free, including shared keys. Rejected: a shared key can be used by a
  pinned repository.
