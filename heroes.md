# Heroes

## Zarok — Demon Enforcer

> _Once the most feared warden of the Nether Pits, Zarok reigned over the damned with an iron chain and a cruel grin. For eons, not a single soul slipped his grasp — until his own sadism undid him. Lost in the screams of a heretic prince he was flaying, Zarok failed to notice a cunning thief picking her shackles. By the time he turned from his work, the cell stood empty and his reputation lay in ruins._
>
> _Stripped of rank and cast out by the Lord of the Damned, Zarok now walks the mortal plane in search of the one who escaped. Not for redemption, nor duty — but because her freedom is the only torment he has ever failed to deliver. And failure, to Zarok, is the most exquisite pain of all._

**Role:** Strength Initiator / Frontliner
**Attack:** Melee (1 hex)

### Stats

| Stat | Base | Scaling |
|---|---|---|
| HP | 20 | +5 per level |
| Mana | 12 | +5 per level |
| Attack Damage | 2 | +1 at levels 3, 6, 9, 12, 15, 18 |
| Defense | 2 | +1 at levels 6, 12, 18 |

### Abilities

#### Passive — Intimidation

Aura (2 hex radius). Enemies within range take **+1 damage** from all sources (attacks, spells, and item effects).

#### 1 — Neck Chain

| Field | Value |
|---|---|
| Type | Skill Shot |
| AP Cost | 1 |
| Mana Cost | 5 |
| Cooldown | 2 rounds |
| Range | 4 hexes |

**Hit:** Roll 1d6 ≥ distance in hexes. On success, deal **2 damage** and pull the target to an adjacent hex of Zarok (Zarok chooses which adjacent hex). On miss, the AP and mana are lost.

**Reaction interaction:** See skill shot rules in `game-design.md` §7.5.

#### 2 — Crippling Gaze

| Field | Value |
|---|---|
| Type | Targeted AoE |
| AP Cost | 1 |
| Mana Cost | 3 |
| Cooldown | 1 round |
| Range | 2 hex radius (centered on Zarok) |

All enemies within radius suffer **−1 movement** for 1 round. No damage.

#### Ultimate — Burning Shackles

| Field | Value |
|---|---|
| Type | Single Target |
| AP Cost | 2 |
| Mana Cost | 10 |
| Cooldown | 4 rounds |
| Range | 1 hex |

The target enemy hero is shackled to Zarok for **1 round**. The target is forced to follow 1 hex behind Zarok along his movement path for the duration (Zarok does not need to remain adjacent — the target follows the same path). The target cannot move independently while shackled.

**Damage:** The shackled hero takes **3 damage** per hex Zarok moves during the duration. This damage is dealt as it occurs (per hex).

**Break:** The shackle ends early if Zarok or the target dies.

#### Innate — Town Portal

Cooldown: 3 rounds. Teleport to any allied structure.

---

## Vex — The Unchained

> _The streets birthed her and the streets named her. Orphaned before she could walk, Vex ran with the Gutter Court — child-thieves who taught her to read a mark's breathing, to vanish into a crowd like rain into a river. By twelve her fingers were legend among the pickpockets of the Lower Warrens. By sixteen, her fingers had found deadlier work. Nobles, merchants, rival guildmasters — her blade did not discriminate. Gold was gold._
>
> _The contract was unremarkable in every way but one: the price. Enough gold to vanish, become someone else, never need another job again. The target was a recluse on the edge of the city — no guards, no family, no questions asked. She found him alone in a candlelit study, his back turned. Her blade was an inch from his throat when he spoke her name. Her given name, found on a scrap of paper kept in her pocket since childhood, the only remnant of her parents._
>
> _She never saw him move. "A feeble attempt," he whispered in her ear. For the first time in her life, Vex froze as the man behind her walked calmly to the cabinet nearby. He poured himself a drink. "A mortal," he said, disappointed. The last thing Vex saw was a raised hand and two fingers snapping, then darkness._
>
> _It took her three years to claw her way back to the living world. She does not speak of the Pits. The scars beneath her sleeves say enough._
>
> _Now she walks the mortal plane with one name burning in her chest: Aviton, the broker who sold her. The one who wrote her name on a death warrant and handed her the pen. She intends to return it — point first._

**Role:** Agility Hybrid Carry / Escape
**Attack:** Melee (1 hex)

### Stats

| Stat | Base | Scaling |
|---|---|---|
| HP | 14 | +5 per level |
| Mana | 15 | +5 per level |
| Attack Damage | 3 | +1 at levels 3, 6, 9, 12, 15, 18 |
| Defense | 1 | +1 at levels 6, 12, 18 |

### Abilities

#### Passive — Backstab

Attacks made from the hex directly opposite the target's facing direction deal **+1 damage**.

#### 1 — Shadow Step

| Field | Value |
|---|---|
| Type | Targeted Blink |
| AP Cost | 1 |
| Mana Cost | 5 |
| Cooldown | 1 round |
| Range | Up to 3 hexes |

Blink to any hex within range. Deal **1 damage** to any enemy occupying or adjacent to the destination hex (Vex chooses one if multiple are in range).

#### 2 — Garrote

| Field | Value |
|---|---|
| Type | Targeted |
| AP Cost | 1 |
| Mana Cost | 4 |
| Cooldown | 1 round |
| Range | 1 hex |

Usable only from the hex directly opposite the target's facing direction (behind them). The target is **silenced** for 1 round — they cannot cast spells or use active abilities.

#### Ultimate — Escape the Nether

| Field | Value |
|---|---|
| Type | Self-Buff |
| AP Cost | 2 |
| Mana Cost | 10 |
| Cooldown | 3 rounds |
| Duration | 1 round |

Vex becomes **untargetable** for the duration. She cannot be the target of attacks, spells, or abilities. She gains **+1 movement** and may move through hexes occupied by enemies without penalty.

#### Innate — Town Portal

Cooldown: 3 rounds. Teleport to any allied structure.

---

## Soren — The Word Smith

> _Reality, Soren discovered, is a language. Not a metaphor — a grammar. The world runs on statements older than matter, and he spent thirty years with five colleagues learning to read them. On the night they solved the Final Equation, he spoke it aloud. The words were true — so true that reality corrected itself around them. When the light faded, the five were gone. The Equation never explained whether it erased them, translated them, or simply moved them to a place where the math still permits their existence._
>
> _Something survived the correction. Fragments of the Equation lodged themselves in his voice. When he speaks them now the world hesitates — walls forget their edges, distance loses its nerve,_ _the space between things forgets what it was supposed to be. He doesn't know why the fragments chose him, or whether they're a gift or a splinter. He only knows the sentence is incomplete. He tells himself he's searching for the rest. He tells himself he wants an answer. A good scientist knows the difference between a hypothesis and a prayer. He stopped being sure which this was a century ago._

**Role:** Intelligence Reality Editor / Controller
**Attack:** Ranged (2 hexes)

### Stats

| Stat | Base | Scaling |
|---|---|---|
| HP | 13 | +5 per level |
| Mana | 20 | +5 per level |
| Attack Damage | 1 | +1 at levels 3, 6, 9, 12, 15, 18 |
| Defense | 1 | +1 at levels 6, 12, 18 |

### Abilities

#### 1 — Gnosis

| Field | Value |
|---|---|
| Type | Targeted |
| AP Cost | 1 |
| Mana Cost | 7 |
| Cooldown | 3 rounds |
| Range | 2 hexes |

Lift the target enemy's **planning cover** for all players to see for **1 round**, exposing their planned movement, AP tokens, and reaction tokens. Deal **2 spell damage**.

#### 2 — Reticence

| Field | Value |
|---|---|
| Type | Targeted Curse |
| AP Cost | 1 |
| Mana Cost | 5 |
| Cooldown | 3 round |
| Range | 4 hexes |

Place a mark on target enemy. On their next turn:
- **If they cast a spell:** The mark detonates, dealing **4 spell damage** and **silencing** them for 1 round.
- **If they do not cast a spell:** At the end of their turn, the mark expires and deals **2 spell damage**.

#### 3 — Pillar

| Field | Value |
|---|---|
| Type | Terrain Creation |
| AP Cost | 1 |
| Mana Cost | 4 |
| Cooldown | 2 rounds |
| Range | 3 hexes |

Target a hex. Soren raises a pillar on it. For **1 round**, the target hex is **impassable** to all units. Enemies occupying a hex adjacent to the pillar when it is raised take **1 spell damage** and are pushed **1 hex** away from the pillar (Soren chooses the push direction for each affected enemy).

#### Ultimate — Collapse

| Field | Value |
|---|---|
| Type | Targeted AoE |
| AP Cost | 2 |
| Mana Cost | 10 |
| Cooldown | 4 rounds |
| Range | 5 hexes |

Target a hex. After a **1-round delay** (resolves at the start of Soren's next turn), all enemies within **2 hexes** of the target point take **4 spell damage** and are **silenced** for 1 round. The detonation point is marked and visible to all players — enemies may move out of the zone before it detonates.

#### Innate — Town Portal

Cooldown: 3 rounds. Teleport to any allied structure.
