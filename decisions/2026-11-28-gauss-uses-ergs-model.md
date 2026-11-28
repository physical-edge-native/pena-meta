# gauss uses erg's robot model at a pinned commit

- Date: 2026-11-28
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: gauss (user), erg (owner of the model)
- Issue: physical-edge-native/pena-meta#27 (for physical-edge-native/gauss#25)

## Context

`2026-11-27-robot-repository-roles.md` (item 3) has gauss start with a quadruped of erg's size and check its
simulation against erg before widening to other robots.

## Decision

Option (A).

1. gauss fetches erg's robot model (`models/quadruped.xml`, MIT OR Apache-2.0) by script at a **pinned erg commit**
   and checks it by SHA-256. The model file is not copied into gauss's history.
2. The pinned commit is one after erg's body L1 model is merged (erg#67). The row in `contracts.md` is filled in
   by gauss's pull request that sets the pin.
3. Moving the pin is its own issue and pull request in gauss, with gauss's standing and determinism tests passing.
4. gauss writes the tolerances for the check against erg before comparing.

## Reasons

- One source for the robot keeps the check against erg meaningful and keeps the license with the file.

## Options considered

- **(A) pin erg's model — chosen**; (B) gauss keeps its own copy of an erg-size model (no contract, but the two
  models drift apart).
