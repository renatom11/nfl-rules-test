# Three Bugs in the 2026 NFL Rulebook's Kickoff Code

*A rules-analyst write-up. Draft for circulation.*

**Source:** *2026 Official Playing Rules of the National Football League* (operations.nfl.com). Citations use the rulebook's Rule-Section-Article form; quotations are verbatim. The NFL's *Official Casebook* is not publicly available, so an unpublished Approved Ruling might already address some of this. If so, the printed rulebook still says what's quoted below.

---

## Why kickoffs?

The NFL rebuilt the kickoff in 2024 (the "dynamic kickoff") and has patched it every year since:
- **2025:** trailing teams may declare onside kicks at any time.
- **2026:** a touchback after a kickoff *from the 50* comes out to the 20 (6-1-5), and **any team may declare an onside kick at any time** (6-1-6).

The new rules use fixed field geometry and new vocabulary. They sit alongside much older rules that were written for a kickoff with one restraining line per team and no "landing zone". All three bugs below come from that seam.

---

## Bug 1 — When a penalty moves the kickoff, only the kicker moves

### The text
- **6-1-2(a):** "'Kicker's Restraining Line' — the restraining line for the kick by the kicking team shall be its 35-yard line for a kickoff … **unless it is adjusted because of a distance penalty.**"
- **6-1-2(b):** "'Kicking Team's Restraining Line' — the restraining line for the remaining 10 players of the kicking team shall be **the receiving team's 40-yard line.**"
- **6-1-2(c)–(e):** receiving team's restraining line = **its 35**; setup zone = **its 35 to its 30**; landing zone = **its 20 to its goal line**. None of these is adjustable.
- **6-1-3(a)(1):** "All kicking team players other than the kicker must be lined up with their front foot on the kicking team's restraining line."
- **6-1-5 (2026):** "if the kickoff is from **the 50-yard line** and the play results in a touchback, then the dead ball spot is the 20-yard line." Otherwise a ball that reaches the end zone in the air and is downed is a touchback at the **35**.
- **6-2-4, Penalty** (kick out of bounds): "The receiving team may elect to take possession of the ball **25 yards … from the spot of the kick** … [or] at the out of bounds spot…"

The League has confirmed this reading. Its 2024 dynamic-kickoff explainer: *"The landing zone and setup zone will not change if a penalty is carried over to a kickoff… Only the spot of the kick moves."*

### How the kick spot gets past midfield
Several rules carry Team B fouls to the next kickoff, and each is enforced separately:
- **11-3-3 Item 4(a):** Team B fouls during a successful Try → "the ensuing kickoff".
- **11-3-3 Item 7:** fouls after the Try → "the succeeding free kick".
- **14-2-3:** personal fouls during an opponent's FG → "the succeeding free kick".
- **14-4-9:** fouls between downs → the succeeding spot.
- Half-distance (14-2-1) only limits penalties toward the *offender's* goal.

The "kickoff from the 50" (one carried foul) has already happened several times since 2024. It is why the 2026 touchback fix exists: teams had been kicking out of bounds from the 50, because "25 yards from the spot of the kick" (the receiving 25) beat a 35-yard touchback.

### The scenario
Team A scores a touchdown and kicks the extra point. Team B is flagged for roughing the holder on the kick (enforced on the kickoff) and then for an unsportsmanlike scuffle after the Try (also enforced on the kickoff).

**Kick spot: A35 → A50 → B35.**

```
 B goal  ══════════════════════════════════════
 B10 ··· receiving team's ball if A kicks it OOB (25 yds from kick spot)
 B20 ─────────────── front of the landing zone (fixed)
 B30 ─────────────── back of the setup zone (fixed)
 B35 ════ KICKER ════ also the RECEIVING team's restraining line (fixed)
 B40 ─ x x x x x   x x x x x ─  kicking team's other 10 players (fixed),
                                now standing 5 yards BEHIND their kicker
```

What the rules now require:
1. The kicker's ten teammates must line up 5 yards **behind** the ball (6-1-3(a)(1)).
2. The receivers' front row must stand on the **same yard line as the kicker** (6-1-3(b)).
3. The kicker "may not cross the vicinity of the 50-yard line" (6-1-3(a)(4)), but he starts 15 yards past it.
4. A touchback goes to the **35**. The 2026 fix only covers kicks "from the 50-yard line".
5. If the kicking team kicks the ball **out of bounds on purpose** (low, into the sideline inside the 10), the receiving team's best option is the ball **25 yards from the kick spot: its own 10.** That is the same out-of-bounds tactic the League closed at the 50, back in a stronger form.
6. With a third carried foul (kick from B20), "25 yards from the spot of the kick" is a point **5 yards inside the receiving team's end zone**, and the rule has no answer.

### Suggested fix (Competition Committee style)
> **6-1-2:** *"If enforcement of a distance penalty would place the kicker's restraining line beyond the 50-yard line, the kick shall be made from the 50-yard line, and the remaining yardage shall be enforced from the succeeding spot after the kick."*
> **6-1-5:** replace "from the 50-yard line" with "**from the 50-yard line or beyond**."

---

## Bug 2 — Is an onside kick a "kickoff"? The rulebook says both

### The text
- **3-17-5:** "A free kick is a kickoff, safety kick, or onside kick…"
  - *Item 1:* "A **kickoff** is a kick that puts the ball in play at the start of each half, at the start of overtime, **after a try, and after a successful field goal.**"
  - *Item 3:* "An **onside kick** is a free kick that the kicking team attempts to legally recover…"

A kickoff is defined by *when* it happens. An onside kick is defined by *what the kicking team intends*. An onside kick after a touchdown satisfies both definitions, and nothing says which wins.

### Reading 1: an onside kick *is* a kickoff → every onside kick fails by rule
- **7-2-1(k):** the ball is dead "when a **kickoff** or safety kick first touches the ground or a player in advance of the front yard line of the landing zone."
- **6-2-4:** "The kicking team may not … (c) kick the ball which first touches the ground or a player in advance of the front yard line of the landing zone." The receiving team then takes the ball 25 yards from the kick spot. This applies to all free kicks, with no onside exception.

An onside kick is meant to travel 10–25 yards, so it always lands short of the landing zone. Under this reading every onside kick is dead when it lands, and the receiving team gets the ball at its 40.

### Reading 2: an onside kick is *not* a kickoff → overtime breaks
- **16-1-5(c):** "**A kickoff** is the opportunity to possess for the receiving team. If the kicking team legally recovers the kick, the receiving team is considered to have had its opportunity."
- **16-1-3(b)/16-1-4(b):** "After each team has had an opportunity to possess the ball, if one team has more points than its opponent, it is the winner."

**Scenario.** Overtime, 2026. Team A receives first and kicks a field goal (A 23–20). Because of the 2026 change, Team A may now declare an onside kick even though it is leading. It does, and recovers.
- *If the onside kick is a "kickoff":* Team B has had its opportunity. **Game over: Team A wins without Team B ever running a play.** This was impossible in 2024–25, when only a trailing team could onside-kick.
- *If it is not a "kickoff":* 16-1-5(c) doesn't apply, nothing else says whether Team B's opportunity has been used up, and a playoff game turns on the Referee's improvisation.

A similar question applies to an onside kick to *open* overtime. 16-1-3(a) and 16-1-4(a) refer to "the team **kicking off** to start the overtime period".

*Is it a good play?* Usually not. League onside recovery rates were about 6% in 2024 and about 6–7% in 2025, and my rough model says the walk-off onside needs about a third of onside kicks recovered to pay off. The rule should still not be ambiguous about whether a game is over.

### Suggested fix
> **3-17-5 Item 3:** *"An onside kick is a kickoff or safety kick that the kicking team has declared under 6-1-6. Except as provided in 6-1-6, all rules governing kickoffs and safety kicks apply, other than 6-1-4(d)(3), 6-2-4(c) and 7-2-1(k)."*
> **16-1-5(c):** *"A kickoff (including an onside kick) is the opportunity to possess…"*, or, if the League does not want walk-off onsides, *"…except that a kicking-team recovery of an onside kick does not constitute the receiving team's opportunity."*

---

## Bug 3 — A ball at rest in the end zone has three different rulings

### The text
- **7-2-1(i):** the ball is dead "when a loose ball comes to rest anywhere in the field, and no player attempts to recover it… Any legal (or illegal) kick is awarded to the receivers, and any other ball is awarded to the team last in possession. **When awarded to a team behind a goal line, the ball is placed on the one-yard line.**"
- **6-1-4(e):** "If the live ball comes to rest anywhere in the landing zone **or in the end zone**, and no player attempts to possess it, the ball becomes dead and belongs to the receiving team **at the dead ball spot.**"
- **3-37 / 11-6-1:** "It is a touchback if the ball is dead on or behind the goal line a team is defending, provided that the impetus comes from an opponent, and that it is not a touchdown or an incomplete forward pass." There is no possession requirement.
- **6-1-5(a):** a kickoff touchback to the 20 requires the ball to be "**downed** in the end zone by the receiving team or [go] out of bounds behind the receiving team's goal line". A ball that simply stops is neither.

### Scenario A — the dying squib
A low kickoff lands at the receiving 4, skips into the end zone and stops three yards deep. Both returners leave it alone, expecting it to roll out the back. The rules give three answers:

| Rule | Ruling |
|---|---|
| 6-1-4(e) | Receiving team's ball "at the dead ball spot", which is inside the end zone. You can't snap from there. |
| 7-2-1(i) | Receiving team's ball **on the one-yard line**. |
| 3-37 + 6-1-5 | **Touchback**, ball at the **20**. |

Read literally, two of the three rules punish the receiving team by 19 yards for not touching a ball that the kicking team put in its end zone.

### Scenario B — the trickling fumble
A runner fumbles at the opponent's 2. The ball trickles into the end zone and stops while players on both teams believe the play is over.

| Rule | Ruling |
|---|---|
| 7-2-1(i) | "Any other ball is awarded to the team last in possession", so the **fumbling team** keeps it, "on the one-yard line". The text doesn't say whose one-yard line; by context, the opponent's 1. |
| 3-37 / 11-6-1 | **Touchback:** the *defense's* ball at its own 20. |

The two readings differ in both possession and field position by about 80 yards.

### Suggested fix
> **7-2-1(i):** replace the last sentence with *"If the ball comes to rest on or behind a goal line, the result shall be determined under Rule 11 as though the ball had been declared dead there in possession of the team to which it is awarded."*
> **6-1-4(e):** delete "or in the end zone"; **6-1-5(a):** after "downed in the end zone by the receiving team" insert ", comes to rest in the end zone,".

---

## What I didn't find

The same audit tested about 80 classic "loopholes" (the 2015 Patriots ineligible-receiver trick, A-11 numbering, fake kneels, kicker-icing with illegal timeouts, multiple-foul clock drains, fake-punt pass interference). The NFL has closed or documented almost all of them. The kickoff code is where the new-meets-old bugs are.

*Full working papers (118 candidates, citations, kill reasons) are available on request.*
