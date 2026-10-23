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

## Web verification sources (Pass 3, retrieved 2026-10-23)

Most were checked through search-result snippets: direct page fetches failed for many hosts in this environment. Dates are as shown in the snippet or URL; "n.d." means none was visible.

**Kickoff / onside rules (2024–2026)**
- NFL.com, "NFL announces new playing rules, bylaws, resolutions for 2026" (Mar/Apr 2026): https://www.nfl.com/news/nfl-announces-new-playing-rules-bylaws-resolutions-for-2026
- PFT, "NFL will allow onside kicks any time, any score" (Mar 2026): https://www.nbcsports.com/nfl/profootballtalk/rumor-mill/news/nfl-will-allow-onside-kicks-any-time-any-score
- PFT, "NFL passes rule regarding kickoffs from the 50" (2026): https://www.nbcsports.com/nfl/profootballtalk/rumor-mill/news/nfl-passes-rule-regarding-kickoffs-from-the-50
- CBS Sports, "NFL rule changes 2026": https://www.cbssports.com/nfl/news/nfl-rule-changes-2026
- Rams.com, 2026 rule changes (McKay rationale): https://www.therams.com/news/2026-nfl-rule-bylaw-resolution-changes-onside-kick-and-other-kickoff-adjustments-ability-for-league-personnel-to-consult-with-on-field-officials-when-considering-disqualifications-for-both-flagrant-football-acts-and-non-football-acts-without-being-called-on-the-field-among-those-approved
- SI, "Explaining five new NFL rules for 2026": https://www.si.com/nfl/explaining-five-new-nfl-rules-for-2026-season
- Steelers Depot, 2025 onside change (May 2025): https://steelersdepot.com/2025/05/nfl-passes-onside-kick-rule-change-proposal
- NFL.com, 2024 dynamic kickoff explainer ("Only the spot of the kick moves"): https://www.nfl.com/news/2024-nfl-season-explaining-rules-for-new-dynamic-kickoff
- ESPN, Texans kickoff loophole (2024): https://www.espn.com/nfl/story/_/id/41908327/houston-texans-kickoff-loophole-green-bay-packers-kaimi-fairbairn-week-7
- Pride of Detroit, Lions kick OOB from the 50 (2025): https://www.prideofdetroit.com/detroit-lions-news/148557/how-detroit-lions-exploited-little-known-kickoff-rule-twice
- Football Zebras, kickoff from the 50 and double fouls (Nov 2025): https://www.footballzebras.com/2025/11/kickoff-from-the-50-opens-weird-options-for-double-fouls/
- Football Zebras, 2024 rule changes (setup-zone deflection → B40): https://footballzebras.com/?p=41986
- Fox News, 2024 dynamic kickoff explainer ("five players on each side"): https://www.foxnews.com/sports/nfls-dynamic-kickoff-explaining-new-rules-heading-2024-season
- CBS Sports, onside rate 2024 (3 of 50): https://www.cbssports.com/nfl/news/nfl-plans-to-boost-onside-kick-success-rate-after-all-time-low-excitement
- Yahoo Sports, onside rate 2025 (3 of 45): https://sports.yahoo.com/nfl-revive-dead-onside-kick-171158120.html
- PFF, kickoff field-position data: https://www.pff.com/news/the-data-behind-the-nfls-kick-return-revolution
- sportrules.org, NFL overtime rules (n.d.): https://sportrules.org/american-football/nfl-overtime-rules/
- PFT, "On overtime onside kicks" (n.d., pre-2024): https://www.nbcsports.com/nfl/profootballtalk/rumor-mill/news/on-overtime-onside-kicks

**Clock, contact, formations**
- Football Zebras, 10-second runoffs explainer (Oct 2017): https://www.footballzebras.com/2017/10/everything-need-know-10-second-runoffs/
- ESPN, 2017 multiple-foul clock rule proposal: https://africa.espn.com/nfl/story/_/id/18987087/nfl-competition-committee-proposes-rule-change-prevent-intentional-penalties
- Boston Globe, Belichick dead-ball loophole banned (2020-05-28): https://www.bostonglobe.com/2020/05/28/sports/nfl-banned-bill-belichicks-dead-ball-loophole-drain-time-off-clock
- NBC Sports Bay Area, Saints–49ers fake-punt PI (Dec 2019): https://nbcsportsbayarea.com/nfl/49ers-tarvarius-moore-knew-about-pass-interference-rule-on-fake-punt/1255309
- Football Zebras, Week 9 2017 officiating video (punt-formation PI): https://footballzebras.com/2017/11/week-9-officiating-video-no-pass-interference-punt-formations-legal-contact-penalty-enforcements
- Wikipedia, Fumblerooski (cites Jerry Markbreit, Chicago Tribune 2007): https://en.wikipedia.org/wiki/Fumblerooski
- NFL Ops, overtime rules page: https://operations.nfl.com/the-rules/nfl-overtime-rules
- NFL.com, McKay: no tush-push ban proposal expected in 2026: https://www.nfl.com/news/competition-committee-co-chairman-rich-mckay-doesn-t-expect-tush-push-ban-proposal-in-2026
- Giants.com, 2023 numbering change (kickers 0–49, 90–99): https://www.giants.com/news/nfl-players-can-now-wear-no-0-among-rule-changes
