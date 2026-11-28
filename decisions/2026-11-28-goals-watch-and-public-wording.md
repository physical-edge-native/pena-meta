# The coordinator watches Dyne's goals for 2027-02-21; public wording is confirmed first

- Date: 2026-11-28
- Decided by: the maintainer. This record was written with an AI assistant.
- Affects: pena-meta (coordinator), all repositories (public wording)

## Decisions

1. **Dyne's goals for 2027-02-21.** On every run the coordinator reads dyne's goals issue ("Goals for 2027-02-21",
   now physical-edge-native/dyne#205) and lists a goal in the Maintainer inbox, at top priority, when it is late:
   its "By 2/21" estimate drops, its state has not changed for seven days, a decision it waits for is past the date
   it is needed by, the preconditions of a planned hardware day are not ready three days before the day, or it is
   expected to miss the end-of-January feature freeze. Goals on track are not listed.
2. **Hardware days combine erg and dyne.** The coordinator plans hardware days from both repositories' `hands-on`
   issues together.
3. **Public wording is confirmed by the maintainer before it is applied.** Repository descriptions and topics, page
   titles and descriptions, the top of a README, and drafts for outside submissions (for example to awesome lists)
   are proposed in an issue labelled `needs-maintainer`; the coordinator explains them to the maintainer in Japanese.
   Nothing is applied before the maintainer confirms. Submissions to other people's repositories are sent by the
   maintainer.
4. **erg's tier 3 (acrobatic motion) stays an estimate only**, as decided on 2026-11-25 and 2026-11-27
   (`2026-11-27-robot-repository-roles.md`); confirmed again, no change.

## Reasons

- The results presentation on 2027-02-21 has fixed commitments; delays are cheaper to handle when seen early.
- Public wording is a public claim (level 2).
