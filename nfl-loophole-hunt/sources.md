# Sources

## Primary source (normative text)

| Document | Version | Retrieved | Location / hash |
|---|---|---|---|
| *2026 Official Playing Rules of the National Football League* (PDF, 91 pp., "Microsoft Word - 02 - Rulebook Tab.docx", PDF created 2026-07-14) | 2026 season | 2026-10-23 | https://static.www.nfl.com/image/upload/fl_attachment/league/tqivdkzt9mu6wdgsh1ku.pdf (linked from https://operations.nfl.com/the-rules/nfl-rulebook/). SHA-256 `144cec5bffd2725bb703a26523f5ccf0b16c59c2fe5c13f6e671f4bddaa87c55`. Local copy: `source/2026_official_playing_rules.pdf` |

Text conversion: `pdftotext` (poppler) → `source/rules_raw.txt`, `source/rules_layout.txt`, `source/rules_clean.txt` (blank lines removed). The split by rule is in `rules_text/rule_NN.md`. The diagram pages (field, signals) don't convert cleanly; none of the citations rely on them.

## Casebook

The **NFL Official Casebook** (the source of "Approved Rulings", per rulebook 3-1) could **not** be obtained. It isn't linked from operations.nfl.com, and web searches on 2026-10-23 found no current public edition. Consequences:
- "Checked against the casebook" in this project means checking the Notes, Exceptions and Supplemental Notes printed in the rulebook.
- Track B category "rulebook vs casebook mismatch" could not be tested.
- Every "Survives" verdict carries the caveat that an unpublished A.R. might already rule on it.

## Documents considered and rejected

| Document | Why rejected |
|---|---|
| https://static.clubs.nfl.com/image/upload/bengals/d88sxopfuvf22ywo1gcx (24-page "RULEBOOK 2026") | NFL **flag football** rulebook, not the NFL playing rules. Deleted. |
| https://media.nfl.com/content/dam/communications/Official%20Playing%20Rules/2026%20Official%20Playing%20Rules.pdf | Blocked by network policy (proxy 403); the static.www.nfl.com copy is the same official document linked from NFL Operations. |

## Access log
- 2026-10-23 04:30 UTC: every NFL host blocked by the environment's network policy (operations.nfl.com, static.www.nfl.com, static.clubs.nfl.com).
- 2026-10-23 ~04:48 UTC: after the user allowed the domains, the official PDF was downloaded from static.www.nfl.com.

## Web sources (Pass 3 verification)
See the section "Web verification sources" below. It is filled in as research completes.
