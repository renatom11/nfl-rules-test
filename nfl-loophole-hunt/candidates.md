# Candidates Log (Pass 2 brainstorm → Pass 3 verdicts)

Baseline: 2026 NFL Official Playing Rules. Citations are R-S-A. Status key:
- **Survives**: no prohibiting text found and no published ruling found. Sub-tagged **[text]** = legal by the text; **[untested]** = probably legal but no known ruling or use; **[ambiguous]** = turns on an unresolved wording question.
- **Known**: already used, documented, or deliberately provided for by the rules.
- **Killed**: a rule, Note, discretion clause or practical problem defeats it (reason given).
- **Bug**: Track B finding (rulebook defect). Severity: S (strong), M (medium), L (low).

The Casebook is unavailable (see `sources.md`), so no verdict could be checked against unpublished Approved Rulings. Web checks are cited in `sources.md` and `FINAL_REPORT.md`.

## Track A — Game exploits

Tags: **O** offense · **D** defense · **ST** special teams · **GM** game management.

| ID | Tag | One-line description | Rules involved | Status | Verdict note |
|---|---|---|---|---|---|
| A01 | GM/ST | **Overtime walk-off onside.** After scoring first in OT, declare an onside kick. If you recover, the receiving team "has had its opportunity" and you lead, so the game ends. | 6-1-6 (2026 "any time"), 16-1-3(a)(b), 16-1-4(a)(b), 16-1-5(c), 3-17-5 | **Survives [text][ambiguous]** | Not possible in 2024–25 (onside kicks limited to a trailing team in the 4th quarter). Hinges on whether an onside kick is a "kickoff" for 16-1-5(c) (see B01). |
| A02 | GM/ST | Onside kick to open OT. A recovery uses up the receiver's opportunity; the kicking team then needs only a score. | same as A01 | **Survives [text][ambiguous]** | Low expected value. Failure hands the opponent a short field and the first possession. |
| A03 | D/GM | **Encroachment timeout.** Between 5:00 and the 2MW of Q4, a trailing defense commits a deliberate pre-snap foul. The clock stops until the snap, it costs 5 yards, and it isn't a 10-second runoff situation. | 4-3-2(e)(2), 4-7-1 (after 2MW only), 4-7-3 (last 40 s), 12-3-3 (multiple fouls *during a down*), 12-3-1(n) (offense only), 14-1-2 Item 5 Exc 1–3 | **Survives [text]** | No patch covers repeated defensive pre-snap fouls before the 2MW. Repeated use could be called a palpably unfair act (12-3-4) or 17-2. |
| A04 | O/GM | **False-start timeout.** A trailing offense in Q4 (before the 2MW) or reg-season OT commits a deliberate false start. The clock stays stopped until the snap. | 4-3-2(e)(3), (e)(2), 4-7-1, 12-3-1(n) (DOG only) | **Survives [text]** | Written to stop a *leading* offense burning clock. Its mirror effect gives a trailing offense a 5-yard clock stop. |
| A05 | ST | **Kickoff overload.** The kickoff formation has no per-side minimum for the kicking team, while the receiving team must balance. Stack 7–8 coverage players on the side you kick to. | 6-1-3(a)(2) vs 6-1-3(b)(1)–(3); contrast 6-1-6(c)(2)(3) | **Survives [text]** | The onside formation explicitly says "on each side of the ball"; the kickoff formation does not. |
| A06 | ST | **Setup-zone catch.** A receiving player standing in the setup zone (feet planted) catches or touches a low line-drive kickoff. It has "first touched a player in advance of the landing zone", so it's dead and B gets the ball 25 yds from the kick spot (B40). | 6-1-4(d)(3), 6-2-4(c) + Pen., 7-2-1(k), 6-1-3(c), 12-5-1(a) | **Known** | 2024 explainers (Football Zebras, Sportsnaut) say setup-zone players may knock down a low kick with feet planted, and it's penalized as a kick not reaching the landing zone (B40). A catch isn't documented but follows the same rule. Batting toward opponent's goal = illegal bat. |
| A07 | D | **Trick-play chuck.** Once the QB hands off or pitches, the illegal-contact restrictions "end" and never restart. On flea-flickers and halfback passes, DBs may chuck receivers past 5 yds until the pass is thrown. | 8-4-7, 8-4-1..3, 8-5-1 (DPI starts at throw), 12-1-5, 12-1-6 | **Survives [text]** | Holding still prohibited (12-1-6). |
| A08 | D | **Gunner mugging on fake punts.** In punt formation, PI-type acts against the end men/gunners are permissible "before the ball is kicked". On a fake-punt pass the ball is never kicked. | 8-5-3(f), 8-4-7, 3-17-7 Item 1 | **Known** | Saints–49ers, Dec 8 2019: no PI on a fake-punt pass to the widest player (Blandino on Fox); league officiating video Week 9 2017. |
| A09 | O | **Bounce snap to a lineman.** A snap that first strikes the ground "can be recovered and advanced by any player". Bounce it to a pulling guard. A snap is a backward pass, not a fumble, so the 4th-down/2MW fumble limits don't apply. | 7-6-4, 3-31, 8-7-1, 8-7-5/6 | **Survives [text][untested]** | Defense may also recover; low expected value. |
| A10 | O | Fumblerooski: QB sets the ball on the ground for a lineman. | 3-2-5, 8-7-3 Item 1, 8-7-5/6, 3-14 | **Known** | Legal per former referee Jerry Markbreit (via Wikipedia/Chicago Tribune 2007). On 4th down or after the 2MW, only the fumbler may recover (8-7-5/6). |
| A11 | O | Center-eligible swinging gate: the snapper lines up on the end of the line wearing an eligible number and runs a route. | 7-6-3, 7-5-1(b), 8-1-5(b), 3-18-3 Item 2 | **Survives [text][untested]** | No NFL instance found (HS discussions only). |
| A12 | O | Use your own pre-snap foul on a Try as a free "switch" between kick and 2-point try (no timeout needed). | 11-3-1 last para, 11-3-3 intro | **Survives [text]**, low value | Costs 5 yds on whichever option you choose. |
| A13 | ST | **Past-midfield kickoff.** Team B fouls carried to a kickoff can move the kick spot past midfield (B40/B35/B20) while all zones stay fixed. Kick it out of bounds on purpose (B takes the ball 25 yds from the kick spot, e.g. B10) or onside it (recoverable at B25). | 6-1-2(a), 6-1-6(b)(g), 11-3-3 Items 4, 7, 14-2-3, 14-4-9, 14-2-1 | **Survives [text]**, conditional | **Upgraded:** from a spot past B45, kick deliberately out of bounds; B's best option is the ball 25 yds from the kick spot (B10 when kicking from B35). NFL.com (2024): "Only the spot of the kick moves." Requires two Team B fouls carried to the kickoff. |
| A14 | O | "Sideline hideout" in front of the **opponent's** bench (12-3-1(l) bans only your own bench area). | 12-3-1(l), 5-2-5 | **Survives [text]**, Killed in practice | Opposite-color jersey defeats the concealment; 12-3-1(k) still applies to substitution tricks. |
| A15 | ST | Kick a FG on 3rd down late so a blocked kick recovered behind the line can be re-kicked. | 9-1-1 Note 2, 9-3-1 Item 1 | **Known** | Standard practice. |
| A16 | ST/GM | Fair catch kick at end of half. | 10-2-4, 10-2-5, 11-4-3, 4-8-2(e) | **Known** | Note 2026 interaction: FCK now uses the onside formation (6-1-6). |
| A17 | GM | Intentional safety to burn clock / improve field position. | 3-28, 11-5-1, 11-5-2 | **Known** | |
| A18 | GM | Take points off the board for a better penalty. | 14-2-3 | **Known** | |
| A19 | GM | Accept loss of down, decline yardage. | 14-1-1 | **Known** | |
| A20 | O | 2015 Patriots: eligible numbers report ineligible and line up outside. | 5-3-1, 5-3-2 Pen. | **Killed** | Patched: eligible-number reporting ineligible must be inside the 5-man core. |
| A21 | O | A-11-style numbering exception from scrimmage kick formation. | 3-17-7, 5-1-2, 7-5-1(e) | **Killed** | The NFL has **no** SKF numbering exception. |
| A22 | O | Tackle-eligible: ineligible number reports eligible and lines up anywhere. | 5-3-1 | **Known** | No alignment limit in that direction. |
| A23 | O | 12 in the offensive formation for <3 s to disguise personnel. | 5-1-1, 5-2-5(b), 5-2-11, 12-3-1(k) | **Killed** | Simulated-substitution UNS. |
| A24 | O | After the 2MW, substitute and snap before the defense can match (12-men trap). | 5-2-10 (before 2MW only) | **Known** | Common hurry-up tactic. |
| A25 | O | Snap before defense matches after timeout/change of possession. | 5-2-9 | **Killed** | Replay + warning + UNS. |
| A26 | O | Sideline hideout in front of own bench. | 12-3-1(l) | **Killed** | Explicit UNS. |
| A27 | O | Fake kneel-down. | 7-2-1(c) | **Killed** | Simulated kneel = dead ball. |
| A28 | O | Fake spike. | 8-2-1 Item 3 (n/a) | **Known** | Legal play (e.g., 1994 Marino). |
| A29 | O | Spike from shotgun. | 8-2-1 Item 3 | **Killed** | Exception only for a T-formation QB; otherwise grounding. |
| A30 | O | QB sneak with pushers ("tush push"). | 12-1-4 (bans only *pulling*) | **Known** | See web check in report. |
| A31 | D | Tackle the faked-to back in the pocket on play-action. | 8-4-6, 12-1-6(a) | **Known** | Legal by express text. |
| A32 | D | Freeze the kicker with an excess/second timeout. | 4-5-1 Item 4, 12-3-1(v) | **Killed** | UNS 15. |
| A33 | D/GM | Feigned injury for a free timeout. | 4-5-4 Note 8 | **Known** | "Deprecated", no penalty. |
| A34 | D | 12+ defenders in coverage on a final Hail Mary. | 5-1-1, 4-8-2(a) | **Killed** | Accepted defensive foul gives an untimed down. |
| A35 | D | Defender lingers on the offense's side in the last 2 min to delay a hurry-up snap. | 7-4-4(c), 4-7-1 Item 2 | **Killed** | Offense may elect the clock to start on the snap; net gain ≈ 0. |
| A36 | D | Defensive excess timeout after 2MW to stop clock. | 4-5-1 Item 3 Pen. | **Killed** | Clock restarts on ready unless offense elects snap. |
| A37 | D | Repeated fouls at the goal line to prevent a score. | 12-3-2 | **Killed** | Score awarded after warning. |
| A38 | ST/GM | Multiple kicking-team fouls on a final punt to run clock. | 12-3-3, 4-8-2(b)(5) | **Killed** | 2023 patch + untimed down for receivers. |
| A39 | O/GM | Single deliberate offensive foul on final play to protect a lead. | 4-8-2(b), 14-1-1 | **Killed** | Defense simply declines if it benefits; no gain. |
| A40 | O | Use punt formation on non-punt downs to bar defenders over the center. | 9-1-3 Item 1, 3-17-7, 8-4-7, 8-5-3(f) | **Killed** | Requires "obvious" kick; also strips your receivers of contact protection. |
| A41 | ST | Quick kick (no roughing protection). | 12-2-12(c) | **Known** | |
| A42 | ST | Drop-kick PAT / kickoff. | 3-17-1 Item 1, 6-1-1(a), 11-4-1 | **Known** | |
| A43 | ST | Fair catch an onside kick (protection from collisions). | 3-9, 10-2-1 | **Known** | |
| A44 | ST/GM | In OT, kicking team recovering a muffed kick counts as receiver's opportunity. | 16-1-5(c) | **Known** | Express text. |
| A45 | ST | Choose FG vs punt by the "B20 or spot of kick" missed-FG rule. | 11-4-2 | **Known** | |
| A46 | GM | Kneel at the 1 instead of scoring. | — | **Known** | |
| A47 | GM | Deliberately allow a TD to get the ball back. | — | **Known** | |
| A48 | O | Hail Mary DPI in end zone → ball at 1-yard line, untimed down. | 8-5 Pen., 4-8-2(a) | **Known** | |
| A49 | O/GM | Offense without timeouts uses an injury excess timeout (cost: 10-s runoff). | 4-5-4(b) & Notes 1, 3 | **Known** | |
| A50 | O | Intentionally throw to an ineligible lineman (5-yd illegal touching, no loss of down) instead of grounding. | 8-1-8(a), 8-2-1 | **Killed** | Pass is not to an *eligible* receiver, so grounding is also available to the defense. |
| A51 | D | Exploit 8-1-4 "incomplete illegal pass returns to previous spot" after a turnover return. | 8-1-4, 8-1-2 Pen.(c) | **Killed** | Offended team accepts the 5-yd penalty from the spot of the pass. (Text defect → B26.) |
| A52 | ST | Punted onside safety kick (safety kicks may be punts; onside allowed any time). | 6-1-1(b)(c), 11-5-2, 6-1-6 | **Killed** | Legal-looking but receivers can fair catch any free kick in the air (3-9). |
| A53 | ST | Squib kick that comes to rest untouched in the landing zone. | 6-1-4(e) | **Killed** | Belongs to receivers at the dead ball spot. |
| A54 | ST | Returner fair-catches in the end zone to "force" a 35-yd touchback. | 6-1-5, 10-2-4, 11-6-3 | **Killed** (as exploit) | Downing it already gives the 35; spot is ambiguous (B07). |
| A55 | ST | Use a fair catch kick as a de facto onside kick. | 11-4-3 Note, 6-1-6(e) | **Killed** | Kickers can't possess until receivers touch. |
| A56 | ST | Fair-catch an onside kick, then attempt a 60+ yd fair catch kick at end of half. | 10-2-1, 10-2-4, 11-4-3 | **Known** (low value) | |
| A57 | D | Leading defense commits a pre-snap foul inside the last 40 s. | 4-7-3 | **Killed** | Half ends unless defense has timeouts. |
| A58 | O | Laterals instead of fumbles after the 2MW (teammates may recover). | 8-7-6 (fumbles only), 8-7-1 | **Known** | |
| A59 | ST | Kick-catch interference on last play → receivers get an untimed down. | 4-8-2(d), 10-1-1 Pen.(a) | **Known** | |
| A60 | GM | Kick off (not receive) to start OT under both-possess rules. | 16-1-3, 16-1-4 | **Known** | Analytics debate. |
| A61 | GM | Regular-season OT: first possession drains the 10 minutes. | 16-1-3(d) | **Known** | |
| A62 | D | Return a blocked PAT / Try turnover for 2 points. | 11-3-2(b) | **Known** | |
| A63 | D | One-point safety on a Try. | 11-3-2(c) | **Known** | |
| A64 | O | Commit a cheap foul to let a reported player revert to his number's status. | 5-3-2(d) | **Killed** | No advantage over simply substituting. |
| A65 | O | Pick/rub routes inside 1 yd of the line. | 8-5-1 | **Known** | |
| A66 | GM | Snap quickly to prevent an opponent's challenge. | 15-1-1(a) | **Known** | |
| A67 | GM | Take a timeout to avoid a replay 10-s runoff. | 15-5-2 Note | **Known** | |
| A68 | D | Ice the kicker with a legal (first) timeout. | 4-5-1 Item 4 | **Known** | |
| A69 | D | Illegal defensive formation vs FG (5 yds, no auto first down). | 9-1-3, 14-1-2 Item 5 Exc 10 | **Known** | |
| A70 | ST | After a Team B foul on a Try, kick off from the 50 (2026: touchback → 20). | 6-1-5, 11-3-3 Item 4 | **Known** | The 2026 change itself. |
| A71 | ST | Declared onside kick popped up high to drop at the far edge of the setup zone. | 6-1-6 | **Known** | |
| A72 | D | Chuck receivers beyond 5 yds whenever A is in punt formation (fake punt). | 8-4-7 last para | **Known** | Express text; see A08 for the stronger PI version. |
| A73 | O | Throw from beyond the LOS on purpose to avoid PI/ineligible-downfield rules. | 8-1-2 Pen.(a), 8-5-1, 8-3-1 | **Killed** | Loss of down + 5. |
| A74 | ST | Kick off with the ball resting against the tee (onside only). | 6-1-1 Note | **Known** | |
| A75 | GM | Burn the 40-s play clock then commit a delay of game to restart on ready (Q4). | 4-3-2(e)(3), 12-3-1(n) | **Killed** | This is exactly what (e)(3) closed. |
| A76 | O | Shift to a "neither on nor off" alignment with two players directly behind the snapper. | 7-5-1(d) | **Killed** | Only one such player allowed. |
| A77 | ST | Kicking team overload + directional squib to a corner (combo of A05 with landing-zone rules). | 6-1-3, 6-1-4, 6-2-4 | **Survives [text]** | Folded into A05 write-up. |
| A78 | D | Receiving team "keeps clean hands" (no fouls before a turnover) to retain possession in double fouls. | 14-5-2 | **Known** | |
| A79 | ST | Deliberate first touching by kicking team near goal line to pin receivers (receivers' option). | 9-2-2 | **Known** | Receivers get the option; it's a known pinning tactic. |
| A80 | ST | Snap/hold for a FG from a "swinging gate" so the defense's FG-formation restrictions don't apply. | 9-1-3 Item 2 Note | **Killed** | Non-standard formation *removes* protections for A; no gain. |
| A81 | GM | Use a coach's challenge as a pseudo-timeout. | 15-1-1(d)(e), 15-6-1 | **Known** | Costs a timeout if unsuccessful. |
| A82 | O | Hand the ball forward to an eligible receiver behind the line (forward handoff "pop pass"). | 8-7-4 | **Known** | |

## Track B — Rulebook bugs

| ID | Sev | Type | One-line description | Rules involved | Status |
|---|---|---|---|---|---|
| B01 | S | Contradiction / gap | **Is an onside kick a "kickoff"?** 3-17-5 defines kickoff by timing and onside by intent, so the sets overlap. If yes, every onside kick is dead and penalized the moment it lands short of the landing zone (7-2-1(k), 6-1-4(d)(3), 6-2-4(c)). If no, 16-1-5(c) ("A kickoff is the opportunity to possess…") doesn't say whether recovering an onside kick in OT uses up the receiver's opportunity. | 3-17-5, 6-1-1, 6-1-4, 6-1-6, 6-2-4, 7-2-1(k), 16-1-3(a), 16-1-5(c) | **Bug** |
| B02 | S | Absurd result | **Kickoff spot creep.** Penalties move only the kicker's restraining line; the B40/B35 lines, setup zone and landing zone are fixed. Stacked enforcements can put the kick spot at B35 or B20: kicker in front of his own teammates, "25 yards from the spot of the kick" behind the receivers' goal line, the 50-yard touchback rule skipped. | 6-1-2, 6-1-3(a)(4)+Pen., 6-1-5, 6-2-4, 6-1-6(b)(g), 11-3-3 Items 4 & 7, 14-2-3, 14-4-9, 14-2-1 | **Bug** |
| B03 | S | Contradiction | **Ball at rest in the end zone.** 7-2-1(i): a ball awarded "behind a goal line" is placed on the one-yard line, which contradicts the touchback definition (3-37/11-6-1) and the free-kick touchback spots (6-1-5). For free kicks 6-1-4(e) adds a third answer: "at the dead ball spot". | 7-2-1(i), 6-1-4(e), 6-1-5, 3-37, 11-6, 3-28, 11-5-1 | **Bug** |
| B04 | M | Wording error | **Charged down uses "or" instead of "and".** Read literally, a down nullified by penalty is still "charged" if possession didn't change. | 3-8-4 vs 14-1-2, 7-3 | **Bug** |
| B05 | M | Contradiction | Backward pass OOB after the 2MW: **5 yards** (4-7-1) vs **loss of down + 5** (8-7-2, 14-1-2 Item 2(c), Penalty Summary). | 4-7-1(d)+Pen., 8-7-2, 14-1-2 Item 2 | **Bug** |
| B06 | M | Contradiction | **A missed FG is a "change of possession" by definition** (3-35-3(e)) even when the kicking team recovers behind the line and keeps the series (9-3-1 Item 1). This triggers clock (4-4(i), 4-3-2(a)(1)), reporting (5-3-2(h)) and 25-s play clock (4-6-2(a)) rules. | 3-35-3(e), 9-3-1 Item 1, 4-4(i), 4-6-2(a), 5-3-2(h) | **Bug** |
| B07 | M | Gap / stale | **Kickoff caught (fair catch) or interfered with in the end zone.** 6-1-5 assigns no touchback spot (20 or 35?). 10-2-4 enforces FCI "from the receiving team's 20-yard line" (written for punts), so the 15-yd foul nets the 35, the same as an untouched touchback (free foul). 14-2-2(c) would enforce from the goal line instead. | 6-1-5, 10-2-4, 11-6-2(e), 11-6-3, 14-2-2, 6-3-1 Exc (b) | **Bug** |
| B08 | L | Gap | 6-1-5's "from the 50-yard line" covers only exactly the 50; kicks from beyond it (and safety kicks from the 50) revert to 35-yd touchbacks. | 6-1-5 | **Bug** (folded into B02 write-up) |
| B09 | M | Overlapping definitions | Forward vs backward pass: "initially moves forward" (3-21-3(a), 8-1-1(a)) vs "first touched… parallel to or behind" (3-21-4). A ball released forward that hooks back is both. The backward test also omits "official/anything else". | 3-21-3, 3-21-4, 8-1-1, 3-12-2 | **Bug** |
| B10 | M | Absurd result | "Before the ball is kicked" (8-5-3(f)) never ends on a fake punt, so there is no PI protection for gunners on fake-punt passes. | 8-5-3(f), 8-5-1, 3-17-7 Item 1 | **Known/intended** (2019 controversy; the league applies it on fakes). Kept as a drafting note. |
| B11 | L | Gap | Illegal-contact restrictions "end" on a handoff/pitch and are never restored when the ball comes back to a passer. | 8-4-7, 8-4-2..3 | **Bug** (Track B face of A07) |
| B12 | M | Stale counting | "**Fifth** and subsequent excess timeout for injury" (4-5-4 Note 2; 14-1-2 Item 4 Exc; 14-1-3 Exc 1) assumes 3 timeouts + 1 free excess. The penalty itself is for the "second and each subsequent" excess timeout, and reg-season OT has only 2 timeouts. | 4-5-4 Pen. & Note 2, 14-1-2 Item 4, 14-1-3, 4-5-1 Item 1, 16-1-3(e) | **Bug** |
| B13 | L | Stale counting | Freeze-the-kicker UNS (12-3-1(v)(2)) applies when a team "has exhausted its **three** charged team timeouts that are permitted in a **half**", which doesn't cover regular-season OT (2 timeouts, not a half). | 12-3-1(v), 4-5-1 Items 1 & 4, 16-1-3(e) | **Bug** |
| B14 | M | Gap | **Two-minute warning in overtime.** 3-41 defines it only "in the second and fourth periods". Postseason OT is mapped only indirectly (16-1-4(h)). Rules keyed to the 2MW (8-7-6 fumble rule, 8-7-2, 4-7, 5-2-10, 7-4-2 Item 6, 4-5-4) and to "fourth period" (4-3-2(e)(3)) have unclear reach in postseason OT. | 3-41, 4-3-2(e)(3), 4-7, 8-7-2, 8-7-6, 16-1-3(e), 16-1-4(h), 16-1-5(f) | **Bug (downgraded to L)**: NFL Ops overtime page and 16-1-4(h) confirm 2MW in OT2/OT4 in practice; the text gap remains. |
| B15 | L | Mismatch | Spiking after the down: allowed "after a score" (4-6-5(e)) vs only "after a touchdown" (4-7-1(e)). | 4-6-5(e), 4-7-1(e) | **Bug** |
| B16 | L | Mismatch | Offside defined twice; only 3-19 includes the fair-catch-kick line. | 3-19, 7-4-5, 11-4-3 | **Bug** |
| B17 | L | Stale definition | 3-40 Try = "one point (by a field goal) or two points (by a touchdown)", omitting the 1-point safety and defensive scoring (11-1-2(d), 11-3-2). | 3-40, 11-1-2(d), 11-3-2 | **Bug** |
| B18 | L | Inconsistency | Ball becomes live only when "legally" kicked (3-2-3, 7-1-1), but "a free kick play begins with a legal or illegal free kick" (3-24-1), and 6-1-1 penalizes an "illegal free kick" as a live-ball event. | 3-2-3, 7-1-1, 3-24-1, 6-1-1 Pen. | **Bug** |
| B19 | L | Stale cross-ref | 8-1-5(b),(c) cite "(see 5-1-2)" for reporting; the reporting procedure is 5-3-1. | 8-1-5, 5-1-2, 5-3-1 | **Bug** |
| B20 | L | Ambiguity | T-formation QB measured from the **snapper** (3-42) while eligibility is measured from the **line** (8-1-5(c)); the spike exception depends on it (8-2-1 Item 3). | 3-42, 8-1-5(c), 8-1-6(d), 8-2-1 Item 3, 7-4-2 Item 3 | **Bug** |
| B21 | M | Ambiguity | 4-8-2(b): "If the foul occurs on the last play of the half, a score by the offense is not counted" is not conditioned on the penalty being accepted, and "offense" changes meaning after a turnover (3-35-1). | 4-8-2(b), 3-35-1, 14-1-1 | **Bug** |
| B22 | L | Redundancy / ambiguity | 14-1-2 Item 5 gives an automatic first down for **every** Team B foul not on its list, yet individual penalties restate "automatic first down" selectively (silent for, e.g., defensive illegal bat/kick, 12-5). | 14-1-2 Item 5, 12-5-1/2 Pen., 9-1-3 | **Bug** |
| B23 | L | Appendix mismatch | Penalty Summary lists loss of down for illegal bat/kick "behind the line of scrimmage" only; 12-5 imposes it for any Team A illegal bat/kick before possession changes (except beyond the line on a scrimmage kick). | Penalty Summary, 12-5-1, 12-5-2 Pen. | **Bug** |
| B24 | L | Ambiguity | "Standard punt formation… one player split out wide **to either side**": one gunner total, or one on each side? Determines whether the defense's alignment restriction applies to the normal two-gunner punt. | 9-1-3 Item 1 Note | **Bug** |
| B25 | L | Absurd result | Kickers/punters may wear 90–99 (5-1-2(b)), but any backfield player with a 90s number must report (7-5-1(e)), so every punt/FG is an illegal formation unless the kicker reports first. | 5-1-2(b), 7-5-1(d)(e), 8-1-5(c), 5-3-1 | **Bug** |
| B26 | L | Absurd result | 8-1-4: "Any forward pass (legal **or illegal**) is incomplete… and the ball returns to the previous spot", which for an illegal pass after an interception or kick return is the original line of scrimmage. | 8-1-4, 8-1-2 Item 1(d) & Pen.(c), 8-6 Note 2 | **Bug** |
| B27 | L | Omission | 6-1-1(a) lists when a kickoff is used (start of each half, after Try, after FG) and omits **overtime**, which 3-17-5 Item 1 includes. | 6-1-1(a), 3-17-5 Item 1, 16-1-3/4 | **Bug** |
| B28 | L | Mismatch | Kicker restriction stated two ways: "may not cross the vicinity of the 50" (6-1-3(a)(4)) vs penalty for "moving beyond 15 yards from the kicker's restraining line" (6-1-3 Pen.). These diverge when the kick spot moves. | 6-1-3(a)(4), 6-1-3 Pen. | **Bug** (in B02 write-up) |
| B29 | L | Gap | Regular-season OT coin toss "in accordance with… 4-2-2", whose only deferral option is "to the second half", which doesn't exist in reg-season OT. | 16-1-2, 4-2-2, 16-1-4(e) | **Bug** |
| B30 | L | Gap | Dead-ball personal fouls after the end of the 2nd or 4th period carry to "the second-half kickoff or the kickoff in overtime". Postseason OT period breaks (OT2→OT3, which starts with a new choice/kickoff) aren't addressed. | 14-4-9 Exc, 16-1-4(e)(h) | **Bug** |
| B31 | L | Ambiguity | Taunting "at any time" is a dead ball foul (3-13-1(b), 14-4-9). Does a live-ball taunt by the team that later gains possession break its "clean hands" (14-5-2)? | 3-13-1(b), 14-4-9, 14-5-2, 14-5-3 | **Bug** |
| B32 | M | Patch-scope gap | The 2023 anti-clock-manipulation rule covers only "multiple fouls **during** the same scrimmage or kick down"; pre-snap fouls are never "during a down", and 12-3-1(n) bans successive delay fouls only by the offense. | 12-3-3, 12-3-1(n), 4-3-2(e), 4-7-1 | **Bug** (Track B face of A03/A04) |
| B33 | L | Ambiguity | Onside-kick classification means 6-3-1 ("a foul at or during a **kickoff or safety kick**") and the dead-ball-spot option may not cover receiving-team fouls on onside kicks. | 6-3-1, 14-4-7, 3-17-5 | **Bug** (folded into B01) |
| B34 | L | Ambiguity | 7-2-1(i) "placed on the one-yard line" doesn't say *whose*; read literally, a fumble that rests untouched in the opponent's end zone goes to the fumbling team at the opponent's 1 instead of being a touchback. | 7-2-1(i), 11-6-1 | **Bug** (folded into B03) |
| B36 | M | Definition/usage mismatch | 6-1-1 says a free kick "must be made from any point on the **kicking team's restraining line**", but 6-1-2(b) defines "Kicking Team's Restraining Line" as the **receiving team's 40** (the kicker's line is the separately defined "Kicker's Restraining Line"). | 6-1-1, 6-1-2(a)(b) | **Bug** |
| B35 | L | Gap | "Kicker" is defined as one who **legally** kicks (3-17-2), and the "receiver"/"kicker" team labels attach to downs with a kick. On a fake punt (no kick) protections keyed to "during any scrimmage kick" (12-2-9(a)(11), snapper defenseless) arguably never switch on. | 3-17-2, 12-2-9(a)(11), 12-2-12 | **Bug** |

**Totals:** 82 Track A candidates + 36 Track B candidates = 118.
- Track A (after Pass 3 web checks): 10 Survive (A01–A05, A07, A09, A11–A13; A77 folded into A05; A14 survives only on paper), 42 Known, 30 Killed.
- Track B: 36 entries (5 folded into others, 1 reclassified as known/intended); 3 strong, 11 medium, 21 low.
