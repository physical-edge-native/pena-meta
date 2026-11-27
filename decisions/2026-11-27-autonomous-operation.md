# Agents work without waiting; the coordinator decides routine questions

- Date: 2026-11-27
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: all repositories and pena-meta

## Context

Each repository (dyne, erg, gauss, poise, the website) has its own AI agent, and pena-meta has a coordinating
agent. Until now every decision waited for the maintainer, so work stopped whenever the maintainer could not
answer. The maintainer wants the agents to keep working, the coordinator to settle routine questions, and to be
asked only about decisions that matter.

## Decisions

### 1. Three levels of decision

| Level | Who decides | Examples | How |
|---|---|---|---|
| 0 | The repository's agent | Small implementation choices within the agreed scope, tests, documentation fixes, how to research | Decide, proceed, report afterwards in the issue or pull request |
| 1 | **The coordinator** | Priorities within an agreed plan, resolving inconsistencies between repositories, choosing among options within an agreed scope and budget, opening issues that follow an agreed plan | The agent labels the issue `needs-coordinator`; the coordinator answers in the issue and records significant answers in `decisions/` |
| 2 | **The maintainer** | Changing scope, spending money (orders), changing public claims, licenses, contact with people outside the project, new repositories, anything that cannot be undone | The agent labels the issue `needs-maintainer` and continues with other work; the coordinator notifies the maintainer |

When unsure between two levels, use the higher one.

### 2. Never idle

While a question waits, an agent continues with other issues. When nothing is ready, it researches the
repository's question (papers, existing designs) and writes notes in English in the repository
(`docs/research/`), so knowledge accumulates.

### 3. Pull requests and merging

- Agents create branches and pull requests without asking first, each linked to an issue.
- **The coordinator may merge** a pull request only when all of the following hold; otherwise it goes to the
  maintainer:
  - CI (Linux, macOS, Windows, where the repository has CI) is green and the coordinator has read the diff;
  - the change is limited to tests, documentation fixes, research notes, or a small fix within an agreed scope;
  - it does not touch contracts in `contracts.md` (exchange format, file formats), public claims (README status,
    the website), licenses, `CLAUDE.md`, CI configuration, pinned commits or submodules, new dependencies, or
    releases;
  - the coordinator has no doubt about it.
- Other pull requests are reviewed by the coordinator, who adds a recommendation, and are merged by the
  maintainer, normally in one batch a day.

### 4. Work that needs the maintainer's hands

Agents label issues that need the maintainer in person (experiments on hardware, ordering parts, assembly)
`hands-on`, with the time needed, the equipment, and what must be done first. The coordinator gathers them across
repositories. When about one day of such work has accumulated, it proposes a "hands-on day" with an ordered plan
(steps, things to bring, items to order) and asks the maintainer for a date (level 2).

### 5. How often agents run

Agents run as scheduled tasks in the cloud, at night and in the early morning, when the maintainer is usually
not at the keyboard (the maintainer works with the agents directly around 10:00–17:00 and 20:00–24:00, Japan
time):

- each of dyne, erg, gauss and poise at 1:00, 3:00, 5:00, 7:00 and 9:00;
- the website once a night;
- the coordinator 45 minutes after each repository run (1:45, 3:45, 5:45, 7:45, 9:45), so that the
  Maintainer inbox is up to date when the maintainer starts.

Each run takes up the state from issues, branches and pull requests. The runs must stay within the
maintainer's subscription: no paid extra usage. The schedule or the model used for routine runs will be adjusted
if usage limits are reached.

### 6. The coordinator's channel to the maintainer

The coordinator talks to the maintainer through pena-meta only, separate from any other conversation:

- a pinned issue **"Maintainer inbox"** in pena-meta lists every open `needs-maintainer` question, pull requests
  waiting for the maintainer's merge, and proposed hands-on days, with links;
- a phone notification when something new is added to the inbox;
- the maintainer answers in the linked issues (or in the inbox), and can open a separate chat session on pena-meta
  for longer discussions.

The coordinator uses only information in the organization's repositories. It does not use the maintainer's
personal, financial or contract information.

## Reasons

- Work should not stop because the maintainer is busy or away; state already lives in GitHub, so agents can resume
  at any time.
- Most questions are routine and can be settled from the agreed plans and `contracts.md`; the maintainer's time is
  kept for decisions that change scope, money, claims or anything irreversible.
- Gathering hands-on work into days saves the maintainer's time and lets orders be timed.
- Keeping the coordinator's channel inside pena-meta keeps project decisions public and separate from private
  matters.

## Options considered

- Pull requests: (a) agents create freely, the maintainer merges in a daily batch, the coordinator merges a limited
  set **chosen**; (b) the coordinator merges only documentation and tests; (c) keep asking before every branch and
  pull request.
- Hands-on days: (a) the coordinator proposes a day when enough work has accumulated **chosen**; (b) a fixed weekday.
- Research notes: public, in English, in each repository **chosen by default**; private repositories remain for
  documents that must not be public.
