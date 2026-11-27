# Roles of erg, gauss and poise; erg's performance tiers

- Date: 2026-11-27
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: erg, gauss, poise
- Related: [`2026-11-25-acrobatic-quadruped-actuators.md`](2026-11-25-acrobatic-quadruped-actuators.md) (unchanged)

## Context

erg's first learned walking policy was unstable in simulation, and the frame has a high centre of mass and an
uneven shape. The maintainer decided to redesign erg from the frame up and sent new requirements to erg, gauss
and poise. The shared aims are: measure the merits and drawbacks that PENA brings to robot design and control;
show that one developer from a software background, using AI, can build a cheap four-legged robot whose control
they can change freely, and train it on CPUs only; and show the value of Dyne as a library.

## Decisions

1. **erg — a small real quadruped.** Performance targets in three tiers:
   1. a learned policy (PPO) walks stably on the real robot and follows speed and heading commands;
   2. it also recovers from pushes, handles steps and slopes, and follows commands sharply;
   3. acrobatic motion (jumps, getting up).

   erg builds tiers 1 and 2. **Tier 3 stays outside erg's scope**, as decided on 2026-11-25; erg only estimates
   what tier 3 would cost, as input to the future actuator task. The parts budget is set from the chosen tier,
   not the other way round: erg estimates the parts list and cost per tier, and the maintainer chooses.
   Until the end-of-project review on 2027-02-21, erg's requirements are frozen; new ideas go to a list for
   later.
2. **Where the computation runs (erg and gauss).** The work that a GPU computer (for example an NVIDIA Jetson) does
   on commercial development quadrupeds is split: running the control policy and estimating the robot's state
   happen on one small microcontroller per leg, exchanging values with neighbouring legs only; training happens
   on a PC's CPU in simulation, not on the robot; no camera, no vision. A place for an extra computer is kept for
   later. How far this reaches is measured, drawbacks included.
3. **gauss — comparison across sizes and kinds of robots, in simulation.** gauss's question is widened from
   industrial-size robots to a range of public robot models: a small quadruped (erg's size, to check against
   erg), a mid-size quadruped, an industrial quadruped, a robot arm and a humanoid. It compares control split
   over joints or limbs with one central policy, under the same model, sensors and training budget. No hardware.
4. **poise — research and design only until February 2027.** Survey physical reservoir computing and computation
   by the body's shape and softness for legged robots, and design parts that erg can attach later (soft legs or
   feet, sensing of their deformation, read out on microcontrollers with Dyne). No parts are bought before March.
5. **Comparisons with commercial robots** are reference comparisons, not controlled ones: the bodies and budgets
   differ. The comparison point is a development model that lets users run their own control. Metrics are written
   in the design record before the experiment; no claim of being better.

## Reasons

- Setting the budget first would cap performance; tiers let the maintainer match performance to the money that
  can be spent and when.
- The earlier scope decision on acrobatic motion still holds: hobby serial servos cannot jump, and actuators that
  can would multiply erg's cost.
- gauss needs a small model to connect its simulations with erg's real robot before widening to larger robots.
- poise's work is still at the research stage; buying parts now would take money and time from erg before the
  February review.

## Options considered

- Acrobatic motion: (a) keep it outside erg, estimate its cost only **chosen**; (b) bring it into erg's scope.
- gauss: (a) widen to a range of sizes and kinds in simulation **chosen**; (b) keep industrial size only and do
  small-robot simulation in erg.
- erg's budget: (a) estimate cost per performance tier, then choose **chosen**; (b) fix a budget first.
