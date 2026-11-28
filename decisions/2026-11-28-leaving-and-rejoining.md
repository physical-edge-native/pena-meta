# Rules for a device leaving and rejoining: two modes, chosen per run

- Date: 2026-11-28
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: dyne (owner of the contract), erg (user)
- Issue: physical-edge-native/pena-meta#23 (from physical-edge-native/dyne#188)

## Context

On 2026-11-21 a device that lost power came back online after about 38 s but could not rejoin the computation,
so the run failed. dyne's 1D simulator supports handover and joining bit for bit; the 2D path that the hardware
runs has neither. erg's fault evaluation (how long until a returning leg controller controls its leg again)
depends on these rules. dyne#141–#144 wait for this decision.

## Decision

Option (d): support two modes, chosen per run.

- **Wait and restore.** The neighbours wait while a device is silent; the returning device restores a snapshot of
  its state. The run stalls while the device is away, and the result is bit-exact with a run without the fault.
- **Continue and rejoin as new.** The run continues without the device and treats its region as unobserved; the
  returning device joins as a new device. There is no stall. The result is not bit-exact with a fault-free run;
  the check is that it equals a simulator run with the same leave and join, bit for bit.

The `contracts.md` row is updated. Rejoin on hardware remains "not yet implemented" until dyne#131 is done.

## Reasons

- Wait and restore keeps the bit-exact claim for experiments where it matters.
- A robot leg cannot stop the whole body while one controller restarts, so erg needs the continuing mode.

## Options considered

- (a) Wait and restore only; (b) warm join from the neighbours' border values (shorter stall, result differs and
  has no simple bit-exact check); (c) continue and rejoin as new only; **(d) both (a) and (c), per run — chosen**.

## What follows

- dyne implements the modes (dyne#141–#144) and keeps `docs-site/concepts.md` consistent with this record.
- dyne's simulator check of leave and rejoin passes bit for bit (dyne#142).
- erg's fault tests pass after it moves its pin.
