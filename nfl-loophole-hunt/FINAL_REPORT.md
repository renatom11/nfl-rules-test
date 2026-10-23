# NFL Rulebook Loophole Hunt — Final Report

**Baseline:** *2026 Official Playing Rules of the National Football League* (official PDF, 91 pp., created 2026-07-14). All citations are Rule-Section-Article. Quotations are verbatim from that PDF.
**Not available:** the NFL *Official Casebook* (no public edition found). Every verdict below carries the caveat that an unpublished Approved Ruling may already address it.
**Companion files:** `candidates.md` (all 118 ideas with status), `system_map.md`, `rules_index.md`, `sources.md`, `BUG_REPORT_DRAFT.md`, `rules_text/` (rule-by-rule text).

---

## Executive summary

I audited the 2026 rulebook the way you'd audit a large legacy codebase. Pass 1 mapped its subsystems and shared definitions. Pass 2 brainstormed **118 candidates** (82 game exploits, 36 rulebook defects). Pass 3 tried to kill each one against the full text, the in-book Notes, the discretion clauses (12-3-4, 17-2) and web sources. Pass 4 developed the survivors. Pass 5 re-attacked the finalists.

**What the audit found**

1. **The 2024–2026 kickoff rewrite is the softest code in the book.** Fixed-geometry zones (6-1-2) collide with old "enforce it on the kickoff" rules (11-3-3, 14-2-3, 14-4-9). Kick-type definitions (3-17-5) overlap. And the 2026 "onside at any time" change (6-1-6) now reaches the overtime "opportunity to possess" rule (16-1-5(c)). Four of the top findings across both tracks live here.
2. **The clock-manipulation patches are layered, not unified.** 4-7 (after the 2MW), 12-3-3 (multiple fouls *during* a down) and 4-3-2(e)(3) (offensive fouls in Q4) each close one hole. They leave single deliberate **pre-snap** fouls before the two-minute warning priced at just 5 yards.
3. **Definitions drift from usage.** Examples: "charged down" uses *or* where it means *and*; "kicking team's restraining line" names a different line in 6-1-1 than in 6-1-2; a missed FG is *defined* as a change of possession even when the kickers keep the ball; the forward and backward pass definitions overlap.
4. **Most famous loopholes are already closed or already known.** These include the 2015 Patriots ineligible trick, A-11 numbering, the fake kneel, clock-burning multiple fouls, freezing the kicker with illegal timeouts, and fake-punt PI on gunners (2019). The appendix lists 30 killed ideas.

**Results:** Track A has **9 survivor write-ups** (2 special teams, 4 offense, 2 defense, 1 game management). They cover 12 surviving candidate IDs: A02 is merged into A01, A77 into A05, and A14 survives only on paper. There are also 43 known tactics and 27 killed ideas. Track B has **36 defects**: 3 strong, 9 medium, 23 low, and one medium (B10) reclassified as known/intended.

### Top five findings

| # | Track | Finding | Why it matters | Confidence |
|---|---|---|---|---|
| 1 | B (+A) | **Kickoff spot creep.** Penalties move only the kicker. The receivers' lines, setup zone and landing zone never move (the League confirmed this in 2024). Two Team B fouls carried to a kickoff can put the kicker at the receivers' 35, *in front of his own teammates*. The out-of-bounds penalty ("25 yards from the spot of the kick") then hands the receiving team the ball at its own 10. | It turns a rule fixed in 2026 (the Lions' kick-OOB-from-the-50 tactic) back into an exploit. The geometry becomes physically incoherent. | 7/10 |
| 2 | B (+A) | **Is an onside kick a "kickoff"?** If yes, every onside kick is dead and penalized when it lands short of the landing zone (7-2-1(k), 6-2-4(c)). If no, the overtime rule "A kickoff is the opportunity to possess" (16-1-5(c)) doesn't say what an onside recovery does. That is exactly the question a 2026 **overtime walk-off onside kick** turns on. | Overtime results could turn on a definitional gap. The 2026 change made it reachable for the first time since 2023. | 6/10 |
| 3 | B | **Ball at rest in the end zone.** 7-2-1(i) places a ball awarded "behind a goal line" on the one-yard line. 6-1-4(e) says "at the dead ball spot". 3-37/11-6 say touchback. A dead kickoff resting untouched in the end zone has three legal answers (B1, end zone, B20). | Directly contradictory text on a plausible play. | 7/10 |
| 4 | A (D/GM) | **Encroachment timeout.** Between 5:00 and the two-minute warning of Q4, a trailing defense can commit deliberate dead-ball encroachments. Each stops the clock until the snap (4-3-2(e)(2)) for 5 yards with no automatic first down. No patch covers it: 4-7 starts at the 2MW, and 12-3-3 covers only fouls *during* a down. | A legal "timeout" bought with yardage. | 6/10 |
| 5 | A (O/GM) | **False-start timeout.** The 2020 rule that stopped *leading* offenses from burning clock (4-3-2(e)(3)) now freezes the clock for *trailing* offenses that false-start before the 2MW. It costs 5 yards, not a down, and buys a 25-second huddle with the game clock stopped. | A "5-yard spike" usable for most of the fourth quarter and in regular-season OT. | 7/10 |

---

## How to read the labels

- **Legal by the text**: the rulebook's words permit it, and I found no prohibiting clause.
- **Legal by the casebook**: cannot be asserted for anything here, because the casebook is unavailable.
- **Probably legal but untested**: the text permits it, but no ruling, game instance or official commentary was found, and officials have discretion (12-3-4 palpably unfair act; 17-2 Commissioner).
- **Confidence (1–10)**: my estimate, after Pass 5, that officials would allow it *and* that it does what is claimed. It is not a measure of how valuable the play is.

---

# PART 1 — TRACK A: GAME EXPLOITS (ranked)

## A-1. Past-midfield kickoff: kick it out of bounds on purpose   `[Special teams]`

**Status:** Legal by the text, with official supporting guidance. Untested past midfield. **Confidence 7/10** (Pass 5: unchanged).

**Summary.** When Team B's fouls are enforced on a kickoff, only the kicker moves forward; the rest of the kickoff geometry stays put. Once the kick spot is past the receivers' 45, deliberately kicking the ball out of bounds pins the receiving team deeper than any touchback or average return. From the receivers' 35, the receiving team gets the ball at its own **10**.

**Rules that make it legal**
- 6-1-2(a): "'Kicker's Restraining Line' … shall be its 35-yard line for a kickoff … **unless it is adjusted because of a distance penalty**." No such clause exists for (b) "the receiving team's 40-yard line", (c) "the receiving team's 35-yard line", (d) the setup zone, or (e) the landing zone "from the receiving team's 20-yard line extending to its goal line".
- League guidance (NFL.com 2024 dynamic-kickoff explainer): "The landing zone and setup zone will not change if a penalty is carried over to a kickoff… **Only the spot of the kick moves.**"
- Penalties that are carried to the kickoff, each enforced separately:
  - 11-3-3 Item 4(a): Team B fouls during a successful Try go to "the ensuing kickoff".
  - 11-3-3 Item 7: "If there is a foul by either team after a Try, it is enforced on the succeeding free kick."
  - 14-2-3: personal fouls during an opponent's FG or safety go to "the succeeding free kick".
  - 14-4-9: fouls between downs are enforced from the succeeding spot.
  - 14-2-1: half-distance is measured only toward the *offender's* goal line. From B35, 15 yards → B20 (no cap reached).
- 6-2-4 Penalty: for a free kick out of bounds, "The receiving team may elect to take possession of the ball **25 yards … from the spot of the kick** … [or] at the out of bounds spot…"
- 6-1-5: touchback rules. A kick in the air into the end zone and downed is a touchback at the **35**. Only a kick "from the 50-yard line" produces a 20-yard touchback, so from beyond the 50 a touchback reverts to the 35.

**Why nothing blocks it**
- A deliberate out-of-bounds kickoff is not unsportsmanlike: the Lions reportedly did it twice from the 50 (vs. Washington, 2025). The League's response was a 2026 rule change (6-1-5's touchback-to-the-20 when kicking from the 50), not a penalty or an unfair-act ruling.
- That 2026 fix is keyed to the exact phrase "from the 50-yard line". It doesn't touch the 25-yard out-of-bounds rule or kick spots beyond the 50.

**Outcome table (kickoff spot → best result for the kicking team)**

| Kick spot | Touchback (6-1-5, literal) | OOB deep, B takes better of "25 yds from kick" or OOB spot | Best play |
|---|---|---|---|
| A35 (normal) | B35 / B20 | B40 | kick in play |
| A50 (one 15-yd foul) | **B20** (2026 fix) | B25 | touchback (fixed) |
| B45 | B35 (literal) | B20 | OOB |
| **B40** | B35 | **B15** | **OOB** |
| **B35** (two 15-yd fouls) | B35 | **B10** | **OOB** |
| B20 (three fouls) | B35 | 25 yds = 5 yds *into* B's end zone: undefined (see Track B-1) | chaos |

**Play design (kick spot B35)**

```
 B's goal line ════════════════════════════════════════  B0
                  ↑ aim: line drive that goes OOB inside B10
 B10 ·············· B's ball here (25 yds from kick spot) ···
 B20 ──────────────────────── front of landing zone ───────
 B30 ─────────── R R R R R R R R R (setup zone, feet planted)
 B35 ══════════════ K ═══ R R R R R  ← kicker's moved line
                                       = receivers' restraining line
 B40 ─ x x x x x     x x x x x ──────  other 10 kickers stay here,
                                       5 yds BEHIND their kicker
```
- **Personnel:** normal kickoff unit. The kicker practises a low, hooking "out-of-bounds pooch" aimed at the sideline between B10 and the goal line. The ball must not go out behind the goal line, because 6-1-5(b) would make that a touchback at the 35.
- **Coverage:** irrelevant. The ball is dead when it goes out of bounds, so nobody needs to run.
- **Alternative:** a declared onside kick (6-1-6(b),(g)) from B35 puts the receivers' restraining line at **B25**. A recovery is first-and-10 at roughly B25. At 2024–25 recovery rates (about 6–7%), this is worse in expected value than the guaranteed B10.

**Situation:** any kickoff where two or more Team B 15-yard fouls have been carried over (personal foul on the Try, then a post-Try scuffle or bench penalty), or after B's foul during a field goal. These are rare but real: kickoffs from the 50 happened several times in 2024–25.
**Counters:** none on the field. The receiving team's only defence is not committing the second foul. The officials' fallback is improvisation under 19-1-3 (Referee's authority).
**Risk:** officials may treat 6-1-5's "50-yard line" as "50 or beyond" (that affects only the touchback column) or invoke 12-3-4. The League would close it within an off-season: closure likelihood 9/10.

**Pass 5 red team**
- *"The receivers can't legally line up on the kicker's line."* True; that is Track B-1, and it doesn't make the OOB kick illegal.
- *"Officials won't let a kickoff happen from B35."* No rule gives them the power to cap it. The League has publicly said only the kick spot moves.
- *"A kick spot like that will never happen."* Possibly. That limits the *value*, not the legality. Score held at 7.

---

## A-2. The false-start timeout   `[Offense / game management]`

**Status:** Legal by the text. No instance of this mirror use was found (Pass 3 web check). **Confidence 7/10.**

**Summary.** In 2020 the League stopped leading offenses from burning clock with repeated pre-snap fouls (Belichick vs. the Jets, 2019) by making any **offensive** pre-snap foul in the fourth period start the clock on the snap. The same rule gives a *trailing* offense a way to freeze the clock for 5 yards instead of a down or a timeout. It works from the start of Q4 until the two-minute warning, and throughout regular-season OT until its two-minute warning.

**Rules**
- 4-3-2(e): after a foul, "the game clock will start as if the foul had not occurred, except that **the clock will start on the snap** if: … (3) the offense commits a foul during the fourth period or regular season overtime after the ball has been made ready for play, causing the clock to stop before a snap."
- 4-4(g): the clock stops "at the time of a foul for which the ball remains dead".
- 4-6-3(a)(5): after penalty enforcement the play clock resets to 25.
- 4-7-1 (the conserve-time penalties and 10-second runoff) applies only "after the two-minute warning".
- 12-3-1(n) bans "two successive **delay-of-game** penalties during the same down"; a false start is not delay of game.
- 12-3-3 covers "multiple fouls **during** the same scrimmage or kick down", and a pre-snap foul is not during a down (3-8-1).

**Why nothing blocks it:** the rule's authors were solving the opposite problem, a leading team spending yards to *drain* time.

**Play design ("Freeze")**
```
 Clock running, Q4, before 2MW, offense trailing, no timeouts wanted.
   t=0   previous play ends in bounds (clock running)
   t≈12s offense hurries to the line, sets
   t≈13s LT (pre-designated) flinches  → whistle, false start, CLOCK STOPS
   t≈13s–(snap)  game clock frozen; play clock 25 s; huddle, substitute,
                 call play with full communication
   snap  clock starts
 Cost: 5 yds (1st&10 → 1st&15). Saves ≈ the 25–30 s the clock
 would otherwise have run.
```
- **Who:** the left tackle or a tight end (the cleanest false start). No reporting needed. Use it only when the offense *needs* the huddle (exhausted personnel, a complex call) and timeouts are precious.
- **Compared with a spike:** a spike costs a down, doesn't give you a huddle, and needs a T-formation QB (8-2-1 Item 3). The false start costs 5 yards and gives a full 25-second huddle with the game clock stopped.

**Best situation:** down two scores with 7:00–2:30 left and fewer than two timeouts, after an in-bounds completion. Also regular-season OT, where the clock is short and timeouts are two.
**Counters:** the defense can decline the penalty (14-1-1), but under 4-3-2(e) the clock still starts on the snap after "enforcement **or declination**", so declining doesn't restart it.
**Risk:** low. It is a routine 5-yard foul with no discretionary hook. Closure likelihood 6/10: the obvious fix is a defensive option to restart on the ready signal in Q4.
**Pass 5 red team:** *"In true hurry-up the clock only runs ~10 s between plays, so the saving is small."* Correct; the value is the huddle, not the seconds. I reduced the value claim but kept confidence at 7, because legality is the strongest of any finding.

---

## A-3. The encroachment timeout   `[Defense / game management]`

**Status:** Legal by the text. Untested (no instance or proposal found). **Confidence 6/10.**

**Summary.** Inside the last five minutes of the fourth period every foul restarts the clock on the snap. The anti-clock rules don't start until the two-minute warning. So between **5:00 and the 2MW**, a trailing defense can stop the clock with a deliberate *dead-ball* pre-snap foul (encroachment or neutral-zone infraction) at a cost of 5 yards and no automatic first down.

**Rules**
- 4-3-2(e)(2): "the clock will start on the snap if: … the foul occurs inside the last five minutes of the second half."
- 7-4-3: encroachment means the officials "blow their whistles immediately", so the ball remains dead.
- 4-4(g): the clock stops at the time of the foul.
- 14-1-2 Item 5 Exceptions (1)–(3): offside, encroachment and NZI give no automatic first down.
- 4-7-1 ("after the two-minute warning"), 4-7-3 ("last 40 seconds") and 12-3-3 ("during the same … down") all fail to reach it. 12-3-1(n) addresses only successive *delay-of-game* penalties, not encroachment or NZI.

**Why nothing blocks it:** the 2017 multiple-foul rule (12-3-3) was written for fouls *during* a play. 4-7 was written for the final two minutes. The window between them was never patched.

**Play design ("Pause")**
```
  Offense (leading) running clock; play clock winding.
       O  O  O  O  O
    D  D  [DT]  D  D        DT pre-designated
  When play clock ≈ 20 (offense set), DT steps into neutral zone and
  touches the guard's hand → encroachment, dead ball, clock STOPS.
  Clock restarts only on the snap; offense has 25 s of play clock
  with the game clock frozen.
  Saves ≈ 20 s per use for 5 yds.
```
- **Use it on long-yardage downs** (2nd & 12+, 3rd & 9+), where 5 yards rarely produces a first down. Never use it on 3rd & 4.
- **Pair it with the 2MW:** one or two "pauses" before 2:00, then the two-minute warning, then your real timeouts.

**Best situation:** trailing by one score, opponent running clock between 5:00 and 2:30, defense with one timeout or none.
**Counters:** the offense can snap faster, accept that the clock stops, or call a quick-count play to catch the defender moving early. Declining the penalty doesn't help: per 4-3-2(e) the clock still starts on the snap.
**Risk:** repeated obvious encroachment invites a discretionary unsportsmanlike or palpably-unfair-act call (12-3-1 preamble, 12-3-4) or later League discipline (17-2). Closure likelihood 8/10 once publicised: extend 4-7-1 to the last five minutes.
**Pass 5 red team:** *"Encroachment requires contact; officials may call a live-ball offside instead and let the play run."* If the defender stays in the neutral zone and draws the snap, the offense gets a free play. The design therefore requires clear contact or a clear NZI (7-4-4(a)/(b)). Confidence lowered from 7 to 6.

---

## A-4. The center-eligible snapper   `[Offense]`

**Status:** Legal by the text. Untested in the NFL (only high-school discussion found). **Confidence 6/10.**

**Summary.** Nothing in the NFL rules makes the snapper ineligible because he snaps. The snap can be made by **any** lineman, the snapper doesn't have to be in the middle, and the player on the end of the line is eligible if he wears 0–49 or 80–89. Put a tight end over the ball on the end of an unbalanced line and he is an eligible receiver.

**Rules**
- 7-6-3: "The snap (3-31) may be made by **any offensive player who is on the line of scrimmage**"; "It is not necessary that the snap be between the snapper's legs."
- 7-5-1(b): "Eligible receivers must be on both ends of the line, and all of the players on the line between them must be ineligible receivers."
- 8-1-5(b): eligible are "Offensive players who are on either end of the line, provided they … have the numbers of eligible players (0–49 and 80–89)".
- 3-18-3 Item 1: other linemen must break the plane of the snapper's belt line. Item 2: the snapper may not be beyond the neutral zone.

**Why nothing blocks it:** NFL eligibility is purely position plus number. The 2015 reporting patch (5-3-1) concerns players *reporting*, and this player doesn't report.

**Play design ("Gate-88", 2-point try)**
```
            ← left                                   right →
   LOS:  [88]  [77] [64] [55] [66] [72]  [87]
          ^S    └──── five ineligibles ──┘  TE (eligible end)
          snapper = TE #88, eligible end
                         QB            (shotgun, 5 yds behind the ball)
                RB                         WR (off line, slot right)
   Snap count: quick count "Set-Hit".
   88: snap, two-count chip, release to the flat / back pylon.
   QB: play-action to RB, boot left, throw to 88.
```
- **No reporting** is required (88 is an eligible number in an eligible position).
- **Practice requirement:** the tight end must deliver accurate shotgun snaps. Alternatively, use a pistol QB at 3 yards to shorten the snap.

**Best situation:** 2-point tries and goal-to-go trick plays, where defenses count the "center" as an ineligible blocker.
**Counters:** a defense that recognises eligibility counts two ends plus four backs, so it can cover. Officials don't announce anything because nothing is reported.
**Risk:** officials might question whether the alignment is "clearly on" the line. Closure likelihood is low (3/10): HS and college rules already live with center-eligible looks.
**Pass 5 red team:** *"The defense will see a #88 over the ball."* Yes, so this is surprise-dependent, like any trick play. *"Is the snapper on the 'end' if the ball is at his inside hip?"* The text keys eligibility to the player, not the ball. Score held at 6.

---

## A-5. Trick-play chuck   `[Defense]`

**Status:** Legal by the text for halfback and receiver passes. Ambiguous for flea-flickers. Untested. **Confidence 5/10.**

**Summary.** The illegal-contact restrictions (no chucking past 5 yards) exist only while the snap-receiver is in the pocket with the ball, and they "end" on a handoff or pitch. Pass interference begins only when the pass is thrown. On a **halfback pass or reverse pass**, defensive backs may therefore legally jam receivers at any depth until the ball is thrown.

**Rules**
- 8-4-2/8-4-3: restrictions apply "if the player who receives the snap **remains in the pocket area with the ball**".
- 8-4-7: "If the quarterback or the receiver of the snap … hands off or pitches the ball to another player … the restrictions on the defensive team prohibiting illegal contact … **will end**, and a defensive player is permitted to use his hands, arms, or body to push, pull, or ward off an offensive receiver, pursuant to Rule 12, Section 1, Article 5."
- 8-5-1: "Defensive pass interference rules apply **from the time the ball is thrown** until the ball is touched."
- 12-1-1: any player may block an opponent "at any time" unless it is a listed foul. Holding (12-1-6) is still listed.

**Why nothing blocks it:** the text has an "end" trigger but no "restart" trigger. For halfback passes the ball never returns to "the player who receives the snap", so there is nothing to restart.

**Play design (coaching rule "Hand-off = hands on")**
```
   CB ──►  X (WR runs go route)
           \  after handoff: CB re-engages, jams X at 12–15 yds,
            \ legally, until RB's arm comes forward
   RB takes handoff → sweeps → pulls up to throw
   S reads "RB eyes downfield" → collisions on any vertical route
```
- **Rule for DBs:** on any handoff or pitch, any receiver releasing vertically may be re-jammed (not held or tackled) until the ball leaves the passer's hand.
- **Flea-flicker caveat:** when the ball is pitched back to the QB, he again "receives… in the pocket"; an official could treat the restrictions as revived. The text never says so. Don't rely on it.

**Best situation:** opponents known for RB or WR passes and double passes, typically in the red zone.
**Counters:** the offense can use the QB as passer (the flea-flicker ambiguity) or run play-action fakes (a *pretended* handoff doesn't end the restrictions).
**Risk:** officials may call DPI early if they judge the pass "about to be thrown", or call holding. Closure likelihood 4/10.
**Pass 5 red team:** *"This is just run-play rules; nobody is 'exploiting' anything."* Partly fair: it's a coaching edge, not a loophole. Value lowered to "modest". Confidence 5.

---

## A-6. Overtime walk-off onside kick   `[Game management / special teams]`

**Status:** Legal by the text **if** an onside kick counts as a "kickoff" for 16-1-5(c) (see Track B-2). No 2026 discussion found. **Confidence 5/10 on legality; usually negative expected value.**

**Summary.** In OT both teams get an "opportunity to possess", and the rule says the receiving team's opportunity is the kickoff, *even if the kicking team recovers it*. In 2026, for the first time since the 2024 kickoff overhaul, the team that just scored may declare an onside kick. If it recovers, the opponent's opportunity is used up, the scorer leads, and the game is over.

**Rules**
- 6-1-6 (2026): "**At any time during the game**, the kicking team may declare an onside kick." (2024: trailing teams in the 4th quarter only; 2025: trailing teams at any time. Both from web reporting.)
- 16-1-5(c): "**A kickoff is the opportunity to possess for the receiving team. If the kicking team legally recovers the kick, the receiving team is considered to have had its opportunity.**"
- 16-1-3(b)/16-1-4(b): "After each team has had an opportunity to possess the ball, if one team has more points than its opponent, it is the winner."
- 3-17-5 Item 1: "A kickoff is a kick that puts the ball in play … **after a try, and after a successful field goal**." An onside kick after a score satisfies this, though Item 3 defines the onside kick as a separate category.

**Play design**
```
  After OT FG (lead +3). Declare onside to Referee before play clock.
  A35 restraining line; R line at A45; R must have 8–9 in A45–A60.
       x  x  x  x  x   K   x  x  x  x  x      (≤5 per side, 2 wide each side)
  A35 ══════════════════════════════════════
  A45 ──── R  R  R  R  R  R  R  R  (R) ─────
  Kicker: high "pop" toward the boundary-side gunners at A47–A50.
```

**Expected value (my illustrative estimates, not data).** League recovery rates were about 6% (3 of 50) in 2024 and about 6–7% in 2025.
- After a FG lead: assume the opponent from its own 30 scores a TD 25% / FG 25% of the time, rising to 38% / 35% from the kicking team's 45 after a failed onside. Normal kickoff → win ≈ 0.63. Onside → ≈ 0.48. Break-even needs about **32%** recovery.
- After a TD+PAT lead, with similar assumptions: break-even is roughly a third (≈33%).

**Best situation:** an opponent with a vastly superior offense, or extreme weather. Only with evidence that your onside recovery rate is far above league average.
**Counters:** the "hands team"; a fair catch on pop-ups (3-9).
**Risk:** a referee ruling that an onside kick isn't a "kickoff" under 16-1-5(c), which would mean no walk-off. Closure likelihood 7/10 (a one-line OT carve-out).
**Pass 5 red team:** *"Pre-2024, teams could always onside after an OT FG, so this isn't new."* Correct: it's **re-enabled**, not new (sportrules.org and a PFT piece describe the opening-OT version). Its novelty is the interaction with the 2026 change and the 3-17-5 definitional split. Value score is low.

---

## A-7. Kickoff overload   `[Special teams]`

**Status:** Legal by the text, contradicted by secondary descriptions. **Confidence 3/10.**

**Summary.** The kicking team's kickoff formation (6-1-3(a)(2)) requires at least two players in each of three lateral bands, **but not on each side of the ball**. The onside formation (6-1-6(c)(2)) explicitly caps five per side. The receiving team, by contrast, must keep people on both sides (6-1-3(b)(1)–(3)). By the text, a kicking team could put 7 of its 10 coverage players on the side it kicks to.

**Rules:** 6-1-3(a)(2): "At least two players must be lined up inbounds between the sideline and the bottom (outside) of the yard-line number, at least two players must be lined up between the top (inside) of the yard-line number and the inbounds lines, and at least two players must be lined up inside the inbounds lines." Contrast 6-1-6(c)(3): "**On each side of the ball**, at least two players…"

**Play design**
```
 B40:  x x x x   x x x   |ball/K|   x x x      (7 left of K, 3 right)
       └ sideline/#s ┘ └ #s-hash ┘  └ inside hashes ┘
 Kick: directional line drive to the left corner of the landing zone.
```
**Why the confidence is low:** 2024 explainers (Fox) describe "five players … lined up on each side", and the officiating mechanics manual (not public) may enforce it. The receivers' own balance rules still let them shift extra players toward the kick side.
**Risk:** an illegal-formation flag (5 yards, re-kick). Closure likelihood 9/10.
**Pass 5 red team:** downgraded from 5 to 3 because published descriptions consistently say 5 per side.

---

## A-8. Switching between kick and 2-point try with your own foul   `[Offense / game management]`

**Status:** Legal by the text. **Confidence 6/10.** Value low.

**Summary.** Once the ball is ready for a Try, the offense may change between the kick (15-yard line) and the 2-point try (2-yard line) only after "a penalty or charged timeout **by either team**" (11-3-1). Its own false start qualifies, so a coach who doesn't like the look can switch without spending a timeout. After a foul on the Try, enforcement can come from either Try spot (11-3-3).

**Play design:** the offense lines up for the PAT, sees a defensive overload on the edge, and the tight end false-starts. Now 2-point try from the 7 (if the 5 yards are enforced from the other Try spot under 11-3-3, which is arguable for a pre-snap foul), or PAT from the 20 (+5 yards on a 33-yard kick).
**Counter:** the defense can decline the false start (14-1-1). Then no foul is administered and the original choice stands (arguable).
**Risk:** low. **Pass 5:** "declining kills it" lowered confidence from 7 to 6.

---

## A-9. Bounce snap to a lineman   `[Offense]`

**Status:** Legal by the text; untested. **Confidence 4/10.** Value low.

**Summary.** "If the ball first strikes the ground … it can be recovered and advanced by **any player**" (7-6-4). A snap is a backward pass (3-31, 8-7-1), not a fumble, so the 4th-down and post-2MW fumble limits (8-7-5/6) don't apply.

**Play design**
```
  [T] [G] [C] [G] [T]   C short-hops snap to the right of the QB;
              QB         RG pulls, scoops on the hop, runs off-tackle.
```
**Counters:** any defender may also recover the loose snap. **Risk:** officials may call snapping to an ineligible player (7-6-4 Penalty) if the "bounce" is judged a sham. **Pass 5:** lowered from 5 to 4.

---

### Track A survivors at a glance

| Rank | ID | Name | Unit | Legal class | Conf. | Value | League would close? |
|---|---|---|---|---|---|---|---|
| 1 | A13 | Past-midfield kickoff OOB | ST | text + League guidance | 7 | high, rare | 9/10 |
| 2 | A04 | False-start timeout | O/GM | text | 7 | moderate | 6/10 |
| 3 | A03 | Encroachment timeout | D/GM | text, untested | 6 | moderate | 8/10 |
| 4 | A11 | Center-eligible snapper | O | text, untested | 6 | moderate | 3/10 |
| 5 | A07 | Trick-play chuck | D | text | 5 | modest | 4/10 |
| 6 | A01/A02 | OT walk-off onside | GM/ST | text, ambiguous | 5 | low (−EV) | 7/10 |
| 7 | A05 | Kickoff overload | ST | text, contradicted | 3 | low | 9/10 |
| 8 | A12 | Try switch via own foul | O/GM | text | 6 | low | 3/10 |
| 9 | A09 | Bounce snap | O | text, untested | 4 | low | 3/10 |

---

# PART 2 — TRACK B: RULEBOOK BUGS (ranked)

Each entry gives the exact text, a triggering scenario, and a one-line fix written for the Competition Committee. The three strongest are written up for public posting in `BUG_REPORT_DRAFT.md`.

## B-1 (B02, Strong). Kickoff geometry breaks when the kick spot moves — "the kicker in front of his own team"

- **Text:**
  - 6-1-2(a): kicker's line is the 35 "unless it is adjusted because of a distance penalty". (b): kicking team's line "shall be the receiving team's 40-yard line". (c): receiving line "the receiving team's 35-yard line". (d): setup zone B35–B30. (e): landing zone B20 to goal.
  - 6-1-3(a)(1): "All kicking team players other than the kicker must be lined up with their front foot on the kicking team's restraining line."
  - 6-1-3(a)(4): "the kicker may not cross the vicinity of the 50-yard line" (Penalty text: "beyond 15 yards from the kicker's restraining line").
  - 6-1-5: "if the kickoff is from the 50-yard line … the dead ball spot is the 20-yard line."
  - 6-2-4 Pen.: "25 yards … from the spot of the kick".
- **Scenario:** Team A scores a TD. Team B commits roughing on the successful PAT (11-3-3 Item 4(a): on the kickoff) and then a dead-ball unsportsmanlike after the Try (11-3-3 Item 7). Kick spot: A35 → A50 → **B35**.
  - The kicker's line is now B35, which is also the receivers' restraining line.
  - His ten teammates must stand on B40, 5 yards *behind* him.
  - The receivers' front row has to stand on the kicker's line.
  - The kicker "may not cross the vicinity of the 50" but starts 15 yards past it.
  - A touchback is at the 35 (not "from the 50").
  - An out-of-bounds kick gives the receivers the ball 25 yards on = **B10**.
  - A third foul (B20) makes "25 yards from the spot of the kick" a point 5 yards into the end zone.
- **The League confirms the zones don't move:** "Only the spot of the kick moves" (NFL.com, 2024).
- **Fix:** *"If enforcement would place the kicker's restraining line beyond the 50-yard line, the kick is made from the 50 and any remaining yardage is enforced from the succeeding spot of the receiving team's first scrimmage down; 6-1-5's 20-yard touchback applies to any kickoff from the 50 or beyond."*

## B-2 (B01, Strong). Is an onside kick a "kickoff"?

- **Text:**
  - 3-17-5: "A free kick is a kickoff, safety kick, or onside kick." Item 1: "A kickoff is a kick that puts the ball in play at the start of each half, at the start of overtime, after a try, and after a successful field goal." Item 3: "An onside kick is a free kick that the kicking team attempts to legally recover…"
  - 7-2-1(k): the ball is dead "when a **kickoff** or safety kick first touches the ground or a player in advance of the front yard line of the landing zone".
  - 6-2-4: "The kicking team may not … (c) kick the ball which first touches the ground or a player in advance of the front yard line of the landing zone" (all free kicks, onside not excepted).
  - 16-1-5(c): "**A kickoff** is the opportunity to possess for the receiving team. If the kicking team legally recovers the kick, the receiving team is considered to have had its opportunity."
- **Scenario 1 (read onside ⊂ kickoff):** after a TD, Team A onside-kicks from its 35. The ball hits the ground at A42. Under 7-2-1(k) it is dead at once, and under 6-2-4 the receivers get it at B40 by penalty. Every onside kick fails by rule.
- **Scenario 2 (read onside ∉ kickoff):** in OT, Team A kicks a field goal, declares onside and recovers. 16-1-5(c) only speaks of "a kickoff", so has Team B had its opportunity? If yes, the game is over (Track A-6). If no, Team B must get a possession nobody can define. Also, 16-1-3(a) speaks of "the team kicking off to start the overtime period", which may not describe a team that onside-kicks to open OT.
- **Fix:** *"Amend 3-17-5: 'An onside kick is a kickoff or safety kick that the kicking team has declared under 6-1-6; except where Article 6-1-6 provides otherwise, rules for kickoffs and safety kicks apply.' Amend 16-1-5(c): 'A kickoff, including an onside kick, is the opportunity…'."*

## B-3 (B03, Strong). Ball at rest in the end zone — three answers

- **Text:**
  - 7-2-1(i): when a loose ball comes to rest and nobody tries to recover it, "Any legal (or illegal) kick is awarded to the receivers, and any other ball is awarded to the team last in possession. **When awarded to a team behind a goal line, the ball is placed on the one-yard line.**"
  - 6-1-4(e): "If the live ball comes to rest anywhere in the landing zone **or in the end zone**, and no player attempts to possess it, the ball becomes dead and belongs to the receiving team **at the dead ball spot**."
  - 3-37 / 11-6-1: "It is a touchback if the ball is dead on or behind the goal line a team is defending, provided that the impetus comes from an opponent…" (no possession requirement).
  - 6-1-5(a): a touchback at the 20 requires that the ball be "downed in the end zone by the receiving team or goes out of bounds behind the receiving team's goal line".
- **Scenario A (kickoff):** a squib kick lands at B4, rolls into the end zone and dies at B-3. Both returners leave it alone, expecting it to roll out. The rules give: the end-zone dead-ball spot (6-1-4(e), not a playable spot), B1 (7-2-1(i)), or a touchback at B20 (3-37 + 6-1-5).
- **Scenario B (fumble):** a runner fumbles at B2; the ball trickles into the end zone and stops while players think the play is dead. 7-2-1(i) awards it to the fumbling team at "the one-yard line" (whose? presumably B1). 3-37 says touchback to B at its 20. That is a 99-yard swing in field position plus possession.
- **Fix:** *"7-2-1(i): replace the last sentence with 'If the ball comes to rest on or behind a goal line, the result is a touchback, safety or touchdown as determined by Rule 11 as though the team last in possession (or, for a kick, the receivers) had downed it there.' Delete 'or in the end zone' from 6-1-4(e)."*

## B-4 (B05, Medium). Backward pass out of bounds after the 2MW: a down, or no down?

- **Text:** 4-7-1: "(d) throwing a backward pass out of bounds … **Penalty:** For illegally conserving time: **Loss of five yards** unless a larger distance penalty is applicable" (plus a 10-s runoff, Item 1). 8-7-2: "Penalty: For a backward pass out of bounds before a change of possession during a play that starts after the two-minute warning. **Loss of down and 5 yards.**" 14-1-2 Item 2(c) lists it as a combination penalty.
- **Scenario:** 1:15 left in Q4, 3rd & 8. The QB pitches to the RB, who flips the ball backward out of bounds to stop the clock. 4-7-1 gives 3rd & 13 plus a runoff. 8-7-2 gives **4th** & 13.
- **Fix:** *"4-7-1 Penalty: add 'and, for (b), (c) and (d), loss of down (see 8-2-1, 8-1-2, 8-7-2)'."*

## B-5 (B06, Medium). A missed field goal is a "change of possession" even when the kickers keep the ball

- **Text:** 3-35-3: "A change of possession includes … (e) when the offensive team misses a field goal attempt." 9-3-1 Item 1: "If the ball has returned behind the line untouched by the receiving team beyond the line, and the kicking team catches or recovers the ball, the existing series of downs continues."
- **Scenario:** 0:30 left in Q2. On 3rd down, Team A's FG is blocked and the holder recovers behind the line. By 3-35-3(e) a change of possession happened. So 4-4(i) stops the clock, which would otherwise keep running. 5-2-9 then *forbids* Team A from snapping the re-kick before the defense matches personnel. 4-6-2(a) sets a 25-second clock. 5-3-2(h) lets reported players revert. The kicking team gains clock but loses its quick re-kick.
- **Fix:** *"3-35-3(e): 'when a missed field goal attempt is awarded to the receiving team (11-4-2).'"*

## B-6 (B04, Medium). "Charged down" says *or* where it means *and*

- **Text:** 3-8-4: "A charged down is a scrimmage down that is not nullified by a penalty, **or** during which there is not a change of possession. It counts as a down in a series of downs."
- **Scenario:** 3rd & 5, offensive holding, penalty accepted. The down *was* nullified, but there was no change of possession, so the second clause makes it "charged" and the next down would be 4th. 14-1-2 Item 1 says "the number of the ensuing down remains the same". The definition contradicts the enforcement rule for every accepted foul.
- **Fix:** *"3-8-4: replace 'or' with 'and'."*

## B-7 (B07, Medium). Kickoff fair catch or interference in the end zone

- **Text:** fair catches of free kicks are allowed (3-9; 10-2-1). 6-1-5 assigns the 20 when the ball touched the landing zone and was "downed", and the 35 when it "lands at or beyond the goal line and is downed". 11-6-3 points to 6-1-5. 10-2-4 enforces fair catch interference in the end zone "from the receiving team's **20-yard line**". 6-3-1 Exc (b) says FCI is enforced "from the spot of the foul". 14-2-2(c): offensive (kicking-team, per 14-4-7) fouls behind the defensive goal line are enforced "from the goal line".
- **Scenario:** a kickoff hangs over the goal line and the returner fair-catches at B-2, never "landed", never "downed". The touchback spot could be 20 or 35. If a cover man hits him (FCI), the answer is B35 (20 + 15, 10-2-4) or B15 (goal line + 15, 14-2-2(c)). Under the 10-2-4 reading the kicking team's 15-yard foul costs exactly nothing compared with the 35 touchback.
- **Fix:** *"6-1-5(d): 'lands at or beyond the goal line, or is caught (including a fair catch) behind the goal line'; 10-2-4: 'from the touchback spot (6-1-5 or 9-5-1)'."*

## B-8 (B12/B13, Medium). Timeout counting hard-codes "three" and "fifth"

- **Text:**
  - 4-5-4(a): "If a team has not used its **three** charged team timeouts, the team of the injured player will be charged a team timeout"; (b) "If a team has used its **three** charged team timeouts, an excess team timeout…".
  - 4-5-4 Penalty: "For the **second** and each subsequent excess team timeout…" vs Note 2 / 14-1-2 Item 4 / 14-1-3: "a **fifth** and subsequent excess timeout for injury".
  - 12-3-1(v)(2): "exhausted its **three** charged team timeouts that are permitted in a half".
  - Regular-season OT gives "two timeouts" (4-5-1 Item 1; 16-1-3(e)).
- **Scenario:** regular-season OT, after the OT two-minute warning. Team B has used both OT timeouts, and a player is injured. B "has not used its three charged team timeouts", so 4-5-4(a) charges a timeout B doesn't have instead of an excess timeout. B then calls a third excess timeout to ice the kicker. 12-3-1(v)(2) doesn't fit ("three… in a half"), so only 4-5-1 Item 4 applies.
- **Fix:** *"Replace 'three charged team timeouts' with 'its permitted charged team timeouts' throughout; replace 'fifth and subsequent excess timeout' with 'second and subsequent excess timeout'."*

## B-9 (B21, Medium). 4-8-2(b): "a score by the offense is not counted"

- **Text:** "If there is a foul by the offense, there shall be no extension of the period. If the foul occurs on the last play of the half, a score by the offense is not counted."
- **Problems:** (1) The sentence isn't conditioned on the foul being *accepted*, unlike 14-1-1 ("play proceeds as though no foul had been committed"). (2) "Offense" is the team in possession (3-35-1), which flips on a turnover. On a last-play interception returned for a TD, after the passing team held, the returning team is "the offense" when it scores.
- **Fix:** *"'…if the penalty is accepted, a score by the team that committed the foul is not counted.'"*

## B-10 (B09, Medium). Forward and backward pass definitions overlap

- **Text:** 3-21-3/8-1-1: forward if "(a) The ball initially moves forward … **or** (b) first touches … at a point nearer the opponent's goal line". 3-21-4: "It is a backward pass if the yard line at which the ball is first touched by a player, or the ground is parallel to or behind the yard line at which the ball leaves the passer's hand."
- **Scenario:** a hooked shovel pass leaves the hand moving forward, but crosswind or spin brings it back, and it is first touched a yard behind the release point. It is forward by 3-21-3(a) and backward by 3-21-4. This decides intentional grounding, a second-forward-pass foul, and fumble-like recovery rights.
- **Fix:** *"3-21-4: 'A pass that is not a forward pass under 3-21-3 is a backward pass.'"*

## B-11 (B36, Medium). "Kicking team's restraining line" means two different lines

- **Text:** 6-1-1: a free kick "must be made from any point on the **kicking team's restraining line**". 6-1-2(b): "'Kicking Team's Restraining Line' — the restraining line for the remaining 10 players … shall be the **receiving team's 40-yard line**." The kick itself comes from the separately defined "Kicker's Restraining Line" (6-1-2(a)).
- **Fix:** *"6-1-1: 'from any point on the kicker's restraining line (or, for an onside kick, the restraining line in 6-1-6(b))'."*

## B-12 (B32, Medium). The clock-manipulation patch covers only fouls *during* a down

- **Text:** 12-3-3: "A team may not commit multiple fouls **during the same scrimmage or kick down** in an attempt to manipulate the game clock." 12-3-1(n) (successive delay penalties) and 4-7 (after the 2MW) leave pre-snap fouls from 15:00 to 2:00 of Q4 unaddressed (Track A-2, A-3).
- **Fix:** *"12-3-3: 'during or between downs'; extend 4-7-1(a) to 'inside the last five minutes of the second half'."*

## Remaining Track B findings (low severity)

| ID | Defect | Text | Fix |
|---|---|---|---|
| B14 | Two-minute warning is defined only "in the second and fourth periods" (3-41). Postseason OT gets one only indirectly (16-1-4(h)). 4-3-2(e)(3) names only "regular season overtime". | 3-41, 16-1-4(h), 4-3-2(e)(3) | "…and in the second and fourth overtime periods of a postseason game and the regular-season overtime period." |
| B15 | Spiking after the down: allowed "after a score" (4-6-5(e)) vs only "after a touchdown" (4-7-1(e)). | 4-6-5(e), 4-7-1(e) | Harmonize to "after a score". |
| B16 | Offside defined twice; 7-4-5 omits the fair-catch-kick line that 3-19 includes. | 3-19, 7-4-5 | Delete 7-4-5's definition; cross-reference 3-19. |
| B17 | Try defined as 1 pt (FG) / 2 pts (TD), omitting the 1-pt safety and defensive scores. | 3-40 vs 11-3-2 | "…to score one or two points as provided in 11-3-2." |
| B18 | Live ball only when "legally" kicked or snapped, yet "a free kick play begins with a legal or illegal free kick". | 3-2-3, 7-1-1, 3-24-1 | "legally or illegally kicked". |
| B19 | Stale cross-reference: reporting cited as "5-1-2"; it is 5-3-1. | 8-1-5(b),(c) | "(see 5-3-1)". |
| B20 | T-formation QB measured from the *snapper*, eligibility from the *line*. The spike exception depends on the former. | 3-42, 8-1-5(c), 8-2-1 Item 3 | Measure 3-42 from the line of scrimmage. |
| B22 | 14-1-2 Item 5 gives *every* Team B foul an automatic first down unless listed. Specific penalties restate it selectively, and some (e.g., defensive illegal bat/kick) are silent. | 14-1-2 Item 5, 12-5 | Add "(see 14-1-2 Item 5)" uniformly, or list exceptions in each penalty. |
| B23 | Penalty Summary limits loss of down for illegal bat/kick to "behind the line"; 12-5 applies it to any Team A bat/kick before possession changes (except beyond the line on a scrimmage kick). | Summary vs 12-5 | Conform the Summary. |
| B24 | "Standard punt formation… one player split out wide **to either side**" is ambiguous: one gunner total, or one per side? | 9-1-3 Item 1 Note | "…one player split out wide on each side." |
| B25 | Kickers may wear 90–99 (5-1-2(b)), but a backfield player with such a number must report (7-5-1(e)), so every FG or punt formation with a #9X kicker is illegal unless he reports. No such kicker found yet. | 5-1-2(b), 7-5-1(e) | Exempt kickers, holders and punters from 7-5-1(e) in scrimmage-kick formation. |
| B26 | "Any forward pass (legal **or illegal**) is incomplete … and the ball returns to the previous spot" literally sends an illegal pass after an interception return back to the original line of scrimmage. | 8-1-4 | "…a legal forward pass … previous spot; an illegal pass after a change of possession is dead at the spot of the pass." |
| B27 | Kickoff uses list omits overtime (6-1-1(a)); 3-17-5 includes it. | 6-1-1(a) | Add "at the start of overtime". |
| B28 | Kicker restriction stated as "vicinity of the 50" vs "15 yards from the kicker's restraining line"; these diverge when the kick spot moves. | 6-1-3(a)(4) & Pen. | Use the 15-yard formulation in both. |
| B29 | Regular-season OT coin toss incorporates 4-2-2, whose deferral option is "to the second half". | 16-1-2, 4-2-2 | State deferral rules for OT explicitly. |
| B30 | Dead-ball personal fouls after the end of the 2nd/4th period carry to "the second-half kickoff or the kickoff in overtime". Postseason OT2→OT3 breaks aren't addressed. | 14-4-9 Exc | Add "or the kickoff beginning the next overtime period". |
| B31 | Taunting "at any time" is a dead ball foul (3-13-1(b)). Does a live-ball taunt before a turnover spoil the intercepting team's "clean hands" (14-5-2)? | 3-13-1(b), 14-5-2 | Specify. |
| B35 | Snapper protections apply "during any scrimmage kick" (12-2-9(a)(11)), so on a fake punt (no kick) the snapper arguably has none. | 12-2-9(a)(11), 3-17-2 | "…from a scrimmage kick formation". |
| B10 | Gunner PI permitted "before the ball is kicked" (8-5-3(f)), which never ends on a fake punt. Known since 2019 and applied that way, so intentional; kept as a drafting note. | 8-5-3(f) | If intended, say "during a down in which Team A is in punt formation". |
| B11 | Illegal-contact restrictions "end" on a handoff and are never restored (flea-flicker). | 8-4-7 | Specify revival when the ball returns to the passer in the pocket. |

---

# PART 3 — PASS 5 RED-TEAM LOG

| Finding | Strongest objection | Response | Score change |
|---|---|---|---|
| A-1 past-midfield kickoff | "Officials will never allow a kick from B35." | No text caps it, and the League has said only the kick spot moves. Officials would have to improvise (19-1-3). | 7 → 7 |
| A-2 false-start timeout | "Seconds saved are small in hurry-up." | True; the value is the frozen-clock huddle. Legality is clean. | 8 → 7 |
| A-3 encroachment timeout | "Repeated deliberate fouls get UNS / palpably unfair." | Real risk; 12-3-4 is discretionary. Also requires a clean dead-ball foul. | 7 → 6 |
| A-4 center-eligible | "Defense will see it." | Trick-play surprise value only; legality unaffected. | 6 → 6 |
| A-5 trick-play chuck | "That's just run-play rules." | Fair; reframed as a coaching edge. Flea-flicker case ambiguous. | 6 → 5 |
| A-6 OT walk-off onside | "Negative expected value; not new." | Agreed. Kept for its legal interaction (re-enabled in 2026, definitional gap). | 6 → 5 |
| A-7 kickoff overload | "Everyone says 5 per side." | Downgraded; text may be incomplete rather than permissive. | 5 → 3 |
| A-8 Try switch | "Defense declines the foul." | Lowered. | 7 → 6 |
| A-9 bounce snap | "Sham bounce = illegal snap." | Lowered. | 5 → 4 |
| B-1 kickoff geometry | "Will never happen." | It needs two carried-over 15-yard fouls; kickoffs from the 50 already happen several times a season. | strong |
| B-2 onside = kickoff? | "Officials obviously know what's meant." | Formation rules can tolerate intent-reading; an OT result can't. | strong |
| B-3 ball at rest | "Officials will just rule touchback." | Probably, but three provisions say three different things. | strong |
| B-6 charged down | "Specific rule (14-1-2) controls." | Yes; the defect is still textual and trivially fixable. | medium |

---

# APPENDIX A — Notable killed ideas (and why)

| Idea | Killed by |
|---|---|
| **2015 Patriots "ineligible eligible"**: eligible numbers report ineligible and line up outside | 5-3-1: must line up "within the normal five-player core"; 5-3-2 Penalty. |
| **A-11 offense**: scrimmage-kick formation numbering exception | The NFL has no such exception; 7-5-1(e) applies in every formation. |
| **Fake kneel-down** | 7-2-1(c): ball dead when QB "simulates dropping to his knee". |
| **Shotgun spike** | 8-2-1 Item 3 exempts only a T-formation QB → grounding. |
| **Freeze the kicker with an excess/second timeout** | 4-5-1 Item 4, 12-3-1(v): UNS 15. |
| **Multiple kicking-team fouls on a final punt to burn time** | 12-3-3 (2017/2023) and 4-8-2(b)(5) (untimed down). |
| **Belichick dead-ball clock drain** (repeated offensive pre-snap fouls) | 4-3-2(e)(3) (2020): clock starts on the snap. |
| **12 defenders on a Hail Mary** | 4-8-2(a): accepted defensive foul extends the period. |
| **12 offensive players in formation for <3 s to disguise** | 5-2-11 and 12-3-1(k) (simulated substitution). |
| **Sideline hideout** in front of own bench | 12-3-1(l). (In front of the opponent's bench it's legal by text but useless: jersey colour gives it away.) |
| **Fair catch kick as an onside kick** | 11-4-3 Note: kickers can't possess until receivers touch. |
| **Punted onside safety kick** | Legal-looking, but receivers can fair catch any free kick in the air (3-9, 10-2-1). |
| **Intentionally throwing to an ineligible lineman** (5 yds, no loss of down) | It's also grounding (not to an *eligible* receiver), and the defense chooses. |
| **Using 8-1-4 to send an illegal pass back to the original line** | The offended team simply accepts the 5-yard penalty. |
| **Defender lingering offside to slow a hurry-up** | 4-7-1 Item 2: offense may start the clock on the snap. |
| **Defensive excess timeout after 2MW** | Clock restarts on the ready signal unless the offense elects the snap. |
| **Leading defense fouling in the last 40 s** | 4-7-3: half ends only if the defense has no timeouts and the offense doesn't elect otherwise. Net zero. |
| **Punt formation on 3rd down to bar defenders over the center** | Requires an "obvious" kick (3-17-7), and strips your receivers of contact protection (8-4-7, 8-5-3(f)). |

# APPENDIX B — Known tactics confirmed legal

These include fake-punt PI immunity for gunners (8-5-3(f); 2019 Saints–49ers), the setup-zone knock-down giving the ball at B40 (6-1-4(d)(3); 2024 explainers), the fumblerooski (legal per Jerry Markbreit), the tush push (12-1-4 bans only pulling; no 2026 ban proposal), the tackle-eligible, the fair catch kick, intentional safeties, kicking a FG on 3rd down to allow a re-kick, taking points off the board (14-2-3), declining yardage while accepting loss of down (14-1-1), and post-2MW laterals (8-7-6 covers only fumbles). Full list: `candidates.md`.

# APPENDIX C — Method and limitations

- **Text:** 2026 PDF → `pdftotext`, split into `rules_text/`. Diagram pages (signals, field) don't convert, and no citation relies on them.
- **No casebook:** "legal by the casebook" could not be established for anything. All survivors are "legal by the text" or "probably legal but untested".
- **Web verification:** two research passes (Pass 3). Several sites returned only search snippets, so article dates are as reported in snippets. See `sources.md`.
- **Expected-value figures** in A-6 are illustrative assumptions, labelled as such, not modelled from play-by-play data.
- **Sportsmanship:** every survivor is checked against 12-3-4 (palpably unfair act) and 17-2 (Commissioner's "extraordinarily unfair… outside the accepted tactics"). A-1 and A-3 are the most likely to provoke an immediate rule change.
