# Actuators for an acrobatic quadruped at about ¥100,000: a future task

- Date: 2026-11-25
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: erg, gauss, and a new repository when the work starts
- Proposal: [#9](https://github.com/physical-edge-native/pena-meta/issues/9)

## Decision

1. Developing motors and actuators that make an acrobatic quadruped (jumps, backflips) buildable for **about
   ¥100,000 in parts** is a future task of the organization. It is listed in [`roadmap.md`](../roadmap.md).
2. It is not started now. A repository for it is opened only when the maintainer decides to start, after a
   proposal here.
3. Acrobatic motion is outside the scope of erg (decided in erg on 2026-11-25, physical-edge-native/erg#27) and of
   gauss.

## Reasons

- Acrobatic motion needs actuators that control torque directly and survive landing impacts. erg's hobby serial
  bus servos (about ¥3,000 each; position control through a high gear ratio) cannot jump.
- With parts on the market, a quadruped that can do this costs roughly ¥450,000 to ¥1,500,000 to build: one open
  design reported under $3,000 in parts (2019); commercial torque-controlled actuators were listed at about $500
  each, twelve per robot. A commercial robot that does backflips costs about ¥420,000 complete, but runs on one
  central computer, so control split over the legs cannot be tried on it.
- Inside erg, it would raise the robot's cost about five to twenty times, against erg's aim of a cheap robot.
  gauss compares control architectures on industrial-size robots, not the cost of actuators.
- Lowering the cost of actuators that can jump is a question of its own, in the spirit of finding how far the cost
  of building robots can be lowered. ¥100,000 for twelve joints leaves under about ¥8,000 per joint, which is
  hard with parts on the market today; a failure to reach it is also a result.

Prices are approximate, from public listings checked on 2026-11-25, at about ¥150 per US dollar.

## Options considered

- (A) Record it as a future task in `roadmap.md` and the scope boundary here; open a repository only when work
  starts. **Chosen.**
- (B) Open a new repository now.
- (C) Put it inside erg.
- (D) Put it inside gauss.
