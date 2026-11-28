# Which glossary is canonical, and the definition of "boundary"

- Date: 2026-11-28 (choices made by the maintainer on 2026-11-25, confirmed on 2026-11-28)
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: all repositories, especially dyne
- Issue: physical-edge-native/pena-meta#22 (from physical-edge-native/dyne#189)

## Context

dyne's CLAUDE.md named two canonical sources for terms: its own glossary and pena-meta's `glossary.md`. They
defined 境界 (boundary) on different bases, which part when a device in the middle leaves (a hole), when a PC
joins temporarily to forecast, and with a transparent boundary condition. dyne needs the settled wording for a
figure in the 2027-02-21 results presentation (dyne#195).

## Decisions

1. pena-meta's `glossary.md` is canonical for terms used in more than one repository; a repository's own glossary
   is canonical for terms used only there; a repository term that uses the same word as a shared term must mean
   the same thing, or be renamed.
2. Boundary (of the domain) / 境界: the edge of the region the devices currently compute, including the edges of
   holes left by devices that have left. Boundary conditions close the computation there. When a PC joins
   temporarily to forecast, it only helps inside that region; the boundary does not move.

## Options considered

- Canonical source: "pena-meta only"; "each repository wins inside itself"; **the split by scope above — chosen**.
- Boundary: dyne's definition (does not cover a PC computing outside the observed area); renaming dyne's term
  (large changes, still misses holes); **the definition above — chosen**.

## What follows

dyne aligns its glossary and CLAUDE.md through a dyne issue, so that no word means different things in the two
glossaries.
