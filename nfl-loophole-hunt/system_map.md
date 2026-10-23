# System Map — how the 2026 NFL rulebook's subsystems interact

Pass 1 deliverable. All citations are to the 2026 Official Playing Rules (R-S-A). This maps the rulebook as you would map a codebase: modules, shared state, interfaces, and the "global variables" every module reads. The ⚠ markers point to interaction seams that Pass 2 mined for candidates.

```
                    ┌────────────── Rule 3 DEFINITIONS (shared vocabulary) ──────────────┐
                    │ possession · impetus · kick types · pass direction · change of poss │
                    └───────┬─────────────┬──────────────┬──────────────┬────────────────┘
                            │             │              │              │
   ┌──────────┐   ┌─────────▼──┐  ┌───────▼──────┐ ┌─────▼──────┐ ┌─────▼───────┐
   │ R5 people│──▶│ R7 snap /  │─▶│ R8 passes /  │ │ R6 free    │ │ R9/10 scrim.│
   │ numbering│   │ formation  │  │ fumbles      │ │ kicks      │ │ kicks, FC   │
   └──────────┘   └─────┬──────┘  └──────┬───────┘ └─────┬──────┘ └─────┬───────┘
                        └──────────┬─────┴──────┬────────┴──────┬───────┘
                                   ▼            ▼               ▼
                           R11 SCORING    R12 CONDUCT     R4 CLOCK & TIMEOUTS
                                   └──────┬─────┴───────┬───────┘
                                          ▼             ▼
                                 R14 PENALTY ENFORCEMENT (dispatcher)
                                          │
                       ┌──────────────────┼──────────────────┐
                       ▼                  ▼                  ▼
                  R15 REPLAY        R16 OVERTIME       R17 UNFAIR ACTS (exception handler)
```

## 1. Shared state ("global variables")

| State | Owner | Readers | Seam |
|---|---|---|---|
| Team A / Team B, offense / defense | 3-35 | almost everything | A and B are fixed for the down, but "offense" flips on a change of possession. Rules that say "offense" (4-8-2(b), 4-3-2(e)(3), 14-3-6) vs "Team A" (14-1-2) behave differently after turnovers. |
| Change of possession | 3-35-3 | 4-4(i), 4-3-2(a)(1), 5-2-9, 5-3-2(h), 8-1-2, 14-1-2, 14-5 | ⚠ 3-35-3(e) says a *missed field goal* is a change of possession even when the kicking team recovers behind the line (9-3-1 Item 1 says the series continues). |
| Two-minute warning (2MW) | 3-41, 4-4(h) | 4-3-2, 4-5-4, 4-7, 5-2-10, 7-4-2 Item 6, 8-7-2, 8-7-6, 15-1-2, 15-5-2 | ⚠ Defined only for "the second and fourth periods". Overtime periods inherit it only through 16-1-3(e) (regular season: "fourth quarter" provisions) and 16-1-4(h) (postseason: "timing rules… as at the end of the first half / fourth period"). |
| "Last five minutes of the second half" | 4-3-2(a)(3), (e)(2) | clock restarts | ⚠ Creates a 5:00 to 2:00 window where every foul stops the clock until the snap but the anti-clock-conservation rule (4-7-1) does not yet apply. |
| Kick classification | 3-17-5, 6-1-1 | 6-1-2..6-3-1, 7-2-1(k)(l), 14-4-7, 16-1-5(c) | ⚠ "Kickoff" is defined by *when* it happens and "onside kick" by *intent*, so the two sets overlap. Rules written for "kickoff or safety kick" may or may not reach onside kicks. |
| Restraining lines & zones | 6-1-2, 6-1-6(b)(g)(h), 11-4-3 | formations, touching, blocking, enforcement | ⚠ Only the kicker's line moves with distance penalties; the B40/B35/setup/landing geometry is absolute. |
| Touchback spot | 6-1-5, 9-5-1 Note a, 11-6-3, 14-2-2, 14-4-4 | many | ⚠ 20 vs 35 vs 20-if-from-the-50; several kick outcomes in the end zone aren't assigned a spot. |
| Possession requirement for safety/touchback | 3-28, 3-37, 11-5, 11-6 | 7-2-1(i) | ⚠ A ball at rest that nobody tries to recover has its own award rule (7-2-1(i): one-yard line), which collides with the touchback definition. |
| Eligibility (numbers + position + reporting) | 5-1-2, 5-3, 7-5-1, 8-1-5/6 | passing, formation fouls | ⚠ Two different reference points: T-formation QB measured from the *snapper* (3-42), eligibility measured from the *line* (8-1-5(c)). |

## 2. Subsystems

### 2.1 Formations and eligibility (5-1-2, 5-3, 7-5, 8-1-5/6)
- Seven or more on the line, eligible ends, interior players ineligible (7-5-1). Eligible numbers are 0–49 and 80–89. Reporting lets either kind of number play the other kind of position (5-3-1). An eligible number reporting ineligible must line up inside the five-man core; this is the patch that closed New England's 2015 trick.
- Reverting after reporting is triggered by any of nine events, including "a foul" and "a kick from scrimmage" (5-3-2).
- **No scrimmage-kick numbering exception exists in the NFL**, so the A-11 high-school loophole has no NFL analog (killed candidate).
- Interfaces: snap (7-6: any lineman may snap; a snap that hits the ground may be recovered by any player), passing eligibility (8-1-5: everyone becomes eligible after a defensive touch), ineligible downfield (8-3).

### 2.2 Numbering and reporting (5-1-2, 5-3-1..3)
- Kickers and punters may wear 90–99, but a backfield player wearing 50–79 or 90–99 must report (7-5-1(e)). ⚠
- The helmet-radio quarterback must report on every entry (5-3-3).

### 2.3 Motion, shifts, snap timing (7-4)
- One-second set after a shift. Only one backfield player may be moving at the snap, and never toward the line. After the 2MW with the clock running, a shift foul becomes a false start, which is a dead-ball foul with a runoff (7-4-2 Item 6).
- Defensive feints are delay of game (4-6-5(d)). Disconcerting signals are unsportsmanlike conduct (12-3-1(i)). In the last two minutes, a snap made while a defender is still on the offense's side is a neutral zone infraction (7-4-4(c)).

### 2.4 Neutral zone, offside, restraining lines (3-18, 3-19, 7-4-3..5)
- Offside is defined twice (3-19 and 7-4-5), and only one definition includes the fair-catch-kick line ⚠.

### 2.5 Forward and backward passes (3-21, 8-1, 8-2, 8-7)
- Definitions overlap ⚠ (a ball that "initially moves forward" but is first touched behind the release point).
- Illegal forward passes come in three penalty flavours. Passes thrown after a change of possession carry no loss of down (there is no down to lose), and 8-1-4 still returns an "incomplete (legal or illegal)" pass to the *previous spot* ⚠.
- Grounding: the outside-pocket exception, and the spike exception only for a T-formation QB.
- Backward pass out of bounds after the 2MW: **loss of down + 5** (8-7-2, 14-1-2 Item 2) vs. **5 yards** (4-7-1) ⚠.
- Fumbles: the 4th-down / 2MW / Try rule lets only the fumbler advance (8-7-5, 8-7-6). It does not apply to backward passes or snaps.

### 2.6 Contact rules on receivers (8-4, 8-5, 12-1-5/6)
- Illegal contact exists only while the snap-receiver is in the pocket with the ball. It ends on a handoff, pitch, pass, fumble or tackle, and the text never says it restarts ⚠ (trick plays).
- In punt formation, illegal-contact acts are permitted (8-4-7) and pass-interference-type acts against gunners are permitted "before the ball is kicked" (8-5-3(f)). On a fake punt the ball is never kicked ⚠.

### 2.7 Kicking plays
**Free kicks (Rule 6, 2024 dynamic kickoff + 2026 changes).**
- Kickoff and safety kick: kicker on own 35 (safety kick: own 20). The other 10 kickers stand at B40; receivers have ≥9 in the setup zone (B35–B30) and up to 2 returners behind B20.
- The ball must land in the landing zone (B20 to goal). A kick that is short or out of bounds gives B the ball 25 yards from the kick spot (6-2-4). A kick in the air into the end zone that is downed is a touchback at the 35; one that lands in the landing zone and then goes into the end zone is a touchback at the 20; after a kick from the 50, every touchback is at the 20 (6-1-5, new).
- Formation rules are asymmetric. The receiving team must balance by area and side; the kicking team's kickoff formation has **no per-side requirement** ⚠ (onside formation does: ≤5 per side).
- Onside kick (6-1-6, new "any time"): it must be declared; the restraining lines are 10 yards apart; receivers put 8–9 players in a 15-yard zone; if the kick is untouched beyond that zone, B gets the ball and an unsportsmanlike-conduct penalty of 15 yards.
- Fair catch is available on free kicks (3-9, 10-2-1).

**Scrimmage kicks (Rule 9).**
- A second kick from behind the line is legal if the ball hasn't crossed the line and come back.
- Only ends and flexed eligibles may release before the kick.
- Defensive formation restrictions apply only against a "standard" punt or FG formation ⚠ (wording).
- First touching is a violation. The kicking team's recovery beyond the line kills the ball. A kick that touches the ground in the end zone untouched is a touchback.
- Post-possession fouls.

**Fair catch & fair catch kick (Rule 10, 11-4-3).**
- After a fair catch, the receiving team may snap or attempt a fair catch kick. The FCK uses the *onside* free-kick formation ⚠ (which in 2026 includes width requirements).
- Fair catch at the end of a period allows an untimed FCK (4-8-2(e), 10-2-5).

### 2.8 Possession and fumbles (3-2-5..7, 7-2-1(i), 8-7)
- A ball at rest that nobody tries to recover goes to the receivers if it was kicked, otherwise to the team last in possession, and "behind a goal line → one-yard line" (7-2-1(i)) ⚠ vs touchback/safety.
- Forward fumble out of bounds returns to the spot of the fumble; a forward fumble through the opponent's end zone is a touchback.

### 2.9 Clock and timeouts (Rule 4, 15-5)
- Starts and stops: 4-3, 4-4.
- Timeouts: 3 per half, 2 in regular-season OT, 3 per "half" in postseason OT. An excess timeout costs nothing the first time, then 5 yards. Injury rules differ before and after the 2MW. 10-second runoffs apply only against the offense.
- Anti-clock-manipulation patches are layered by era:
  - (i) 4-7: after the 2MW, time-conserving acts → runoff.
  - (ii) 12-3-3: **multiple** fouls in one down → 15 yards + clock reset.
  - (iii) 4-3-2(e)(3): an offensive pre-snap foul in the 4th period restarts the clock on the snap.
  - (iv) 4-5-1 Item 4 and 12-3-1(v): the freeze-kicker rule.
- ⚠ The gaps between patches are: single fouls, the window between 5:00 and the 2MW, and overtime periods that the text never names.

### 2.10 Penalty enforcement (Rule 14)
- A dispatcher keyed on play type: snap, running, passing, fumble/backward pass, free kick, scrimmage kick, dead ball, between downs.
- Overrides: half-distance (supersedes everything except grounding and palpably unfair acts); foul behind a goal line; foul during a score (take the points or the penalty); personal-foul dead-ball-spot option.
- Number of the down: **every Team B foul = first down unless listed** (14-1-2 Item 5) ⚠.
- Fouls tied to scores are deferred to the Try or the kickoff (11-3-3, 14-2-3, 14-4-9). ⚠ Several deferred fouls can stack on one kickoff while the kickoff geometry stays fixed.

### 2.11 Replay (Rule 15)
- Challenges need a timeout. Booth reviews apply after the 2MW, in OT, on scores and on turnovers. Clock restoration only happens for a team trailing by 8 or fewer. 10-second runoff after a reversal. The officiating department can assist on objective facts and on some fouls.

### 2.12 Overtime (Rule 16)
- Both teams get an "opportunity to possess". **A kickoff is the receiving team's opportunity, and a kicking-team recovery counts as that opportunity** (16-1-5(c)).
- ⚠ Combined with 2026's onside-any-time rule, the team kicking off can now try to end the receiving team's opportunity without letting it run a single play. Whether an onside kick is a "kickoff" is exactly the ambiguity from §1.
- Regular-season OT is 10 minutes and inherits "fourth quarter" timing. Postseason OT uses 15-minute periods, and its timing is mapped to "first half / fourth period" only at the ends of OT2 and OT4.

### 2.13 Exception handlers (12-3-4, 13-1-7, 17-2, 19-2)
- Palpably unfair act: any penalty, any score.
- The Commissioner's "extraordinarily unfair… outside the accepted tactics" power, applied after the fact.
- Every Track A survivor must be checked against these. They are discretionary, so the risk is political rather than textual.

## 3. Interaction hot-spots (where Pass 2 looked hardest)

1. **2024–2026 kickoff rewrite × older enforcement rules** (6-1 × 11-3-3 × 14-2-3 × 14-4-9 × 10-2-4 × 7-2-1(i)): the new fixed-geometry zones meet old "enforce on the kickoff" and "touchback = 20" language.
2. **Onside-any-time (2026) × overtime "opportunity" (16-1-5(c)) × kick-type definitions (3-17-5).**
3. **Clock-patch layering** (4-3-2(e) × 4-7 × 12-3-3 × 12-3-1(n)): which deliberate fouls are priced, and which are free.
4. **Restriction-ending triggers** (8-4-7 handoff, 8-5-3(f) "before the ball is kicked", 3-17-7 Item 1 "any action… deemed from SKF"): conditions that end or start a restriction but never restore it.
5. **Change-of-possession definition** (3-35-3(d)(e)) used as a trigger by clock, substitution, reporting and enforcement rules.
6. **Duplicate definitions drifting apart** (offside 3-19 vs 7-4-5; spike "after a score" 4-6-5(e) vs "after a touchdown" 4-7-1(e); backward-pass OOB penalty 4-7-1 vs 8-7-2).
7. **Counting assumptions** ("three charged team timeouts", "fifth and subsequent excess timeout") that break when OT gives two timeouts.
