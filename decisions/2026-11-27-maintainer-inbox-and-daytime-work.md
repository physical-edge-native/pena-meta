# Maintainer inbox, daytime work, and the weekly check

- Date: 2026-11-27
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: all repositories and pena-meta
- Related: [`2026-11-27-autonomous-operation.md`](2026-11-27-autonomous-operation.md) (details of sections 5 and 6)

## Context

Agents now run on a schedule at night and in the early morning, and the coordinator keeps a pinned
"Maintainer inbox" issue in pena-meta. Two details were left open: how the inbox stays readable as items pile up,
and how scheduled runs avoid interfering with work the maintainer is doing with an agent during the day.

## Decisions

1. **The inbox is rewritten, not appended to.** On every run the coordinator replaces the inbox body. It lists
   only items that are still open, in order of priority:
   1. questions for the maintainer that block other work;
   2. other questions for the maintainer (`needs-maintainer`), oldest first;
   3. pull requests waiting for the maintainer's merge;
   4. proposed hands-on days;
   5. issues marked `in-progress` with no activity for seven days or more.

   If there are more than ten items, it shows the first ten and "N more", with a link to the full list.
2. **Notifications only for new items.** The coordinator records the listed items in a hidden comment in the
   inbox body and sends a phone notification only when an item appears that was not listed before.
3. **Daytime work is marked and skipped.** When the maintainer starts on an issue with an agent during the day,
   that session labels the issue `in-progress` (assigning the issue to the maintainer has the same effect).
   Scheduled runs do not act on such issues or on their branches and pull requests: no answers, label changes,
   comments or merges. Only the maintainer or a daytime session removes `in-progress`.
4. **Labels in every repository:** `needs-coordinator`, `needs-maintainer`, `hands-on`, `in-progress`.
5. **The weekly consistency check moves into the coordinator's Monday 3:45 run.** The separate weekly scheduled
   task is paused (not deleted). The weekly report is committed on a branch and opened as a pull request, which
   the maintainer merges.
6. **Model.** Scheduled runs use the same model as interactive work (Claude Opus), because the development work in
   these repositories needs it. After two or three nights the coordinator reports usage and proposes changes to
   the schedule if needed; the maintainer decides.

## Reasons

- An inbox that only grows becomes unreadable; a rewritten list of open items, in priority order, can be read in
  a minute.
- Notifying on every run would train the maintainer to ignore notifications.
- A scheduled run that answers or merges something the maintainer is working on would cause conflicting work.
- One coordinator run that also does the weekly check avoids two sessions reading the same repositories with
  different instructions.

## Options considered

- Marking daytime work: (a) a label `in-progress` **chosen**, with assignment accepted as well; (b) assignment only.
- Weekly check: (a) fold into the Monday 3:45 coordinator run **chosen**; (b) keep a separate weekly task.
- Model for scheduled runs: (a) Claude Opus everywhere **chosen**; (b) a lighter model for repository runs.
