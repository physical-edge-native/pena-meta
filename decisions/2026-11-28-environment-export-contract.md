# Dyne's environment export is a contract between dyne and erg

- Date: 2026-11-28
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: dyne (owner), erg (user)
- Issue: physical-edge-native/pena-meta#15

## Context

erg loads Dyne's exported room (USD, and the new MJCF export in dyne#193) to train and evaluate its robot in
MuJoCo. The room is a place to train only, not an input to the policy.

## Decision

Option (A): list the environment export in `contracts.md`, owned by dyne and used by erg. Its frame is Z up and
its units are metres, the same for USD and MJCF. A change to the formats, frame or units is a cross-repository
change and starts with a proposal here.

## Reasons

erg relies on the frame and units; a silent change would break training in the room.

## Options considered

- **(A) list it in `contracts.md` — chosen**; (B) do not list it, and erg follows whatever its pinned Dyne commit
  exports.
