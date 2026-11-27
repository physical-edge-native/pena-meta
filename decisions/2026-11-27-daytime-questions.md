# How agents ask questions while the maintainer is in the conversation

- Date: 2026-11-27
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: all repositories (through `cross-repo-rules.md`)
- Related: [`2026-11-27-autonomous-operation.md`](2026-11-27-autonomous-operation.md) (the three levels of decision)

## Context

The three levels of decision let agents settle routine questions without waiting. In daytime sessions, where the
maintainer is in the conversation, agents still stopped to ask about small choices that belong to level 0 or 1.

## Decisions

The levels do not change when the maintainer is present.

1. **Level 0: decide without asking.** At the end of the reply, list briefly what was decided.
2. **Level 1: do not stop.** State "Proceeding with the recommended option X; say if you want otherwise", and
   proceed. If the maintainer later disagrees, change it then.
3. **Stop and wait only for level 2** (scope, money, public claims, licences, outside contact, new repositories,
   anything that cannot be undone), and then give the options, their effects and a recommendation.
4. **Collect questions at the end of a reply**, not one at a time in the middle of the work. While a level 2
   question waits, continue with other work.
5. "When unsure, use the higher level" applies to what may be changed. When unsure only whether to *ask*,
   proceed with the recommendation and say so, unless the action cannot be undone.

## Reasons

- Work stopped on questions the agents could answer themselves, which costs the maintainer's time.
- Proceeding with a stated recommendation keeps the maintainer in control: anything can be corrected in the next
  message.

## Options considered

- (a) Proceed on levels 0 and 1, stop only on level 2 **chosen**; (b) keep asking whenever the maintainer is present.
