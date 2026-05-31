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
