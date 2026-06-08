# Sandaolu — Game Design Document

## 1. Core Concept & Vision

- **Main Objective**: Destroy the enemy's "Hive" (located in the middle of their base).
- **Game Format**: A tactical, lane-pushing board game inspired by Dota. A 2-10 player game that ranges from 1v1 to 5v5.
- **Progression**: Players draft heroes, manage action and reaction points, farm pawns/neutrals for gold and XP, buy items, and coordinate to breach the enemy base.

## 2. Map Layout & Board Design

- **Grid Style**: Hexagonal grid.
- **Lanes**: 3 lanes (Top, Middle, Bottom) containing Towers that block access to the base.
- **Jungle**: A jungle area containing 3 neutral camps on each side of the map.
- **River**: A river area running diagonally/across the middle of the map.
- **Shops**:
  - Base Shops (at each team's starting fountain).
  - Side/Off-lane Shops (one located near each off-lane for forward purchases).
  - **Availability**: All items in the game are available for purchase at all shops (both Base and Side Shops).
- **Roshan Pit**: A boss pit (name TBD — placeholder "Roshan").
- **Ancient Camp**: A camp for powerful neutrals (name TBD — placeholder "Ancients").

## 3. Heroes, Stats & Progression

### 3.1 Team Size & Movement

- **Team Size**: 3v3 (6 players/heroes total, Player 1–6).
- **Movement**:
  - **Normal Movement**: A player can move up to **5 spaces (hexes)** per turn.
  - **First Round Boost**: For the very first round of the game, all players start with **12 movement** and **1 AP** to speed up rollout and laning setups.
- **Action Points**: A player's max AP scales with their hero level:

  | Level | Max AP |
  |-------|--------|
  | 1–4   | 1      |
  | 5–9   | 2      |
  | 10–14 | 3      |
  | 15–18 | 4      |

  _Start with 1 AP. Gain +1 AP at levels 5, 10, and 15._

### 3.2 Teleportation (Town Portal)

- All heroes have the inherent ability to teleport to any allied structure.
- **Cooldown**: 3 rounds.

### 3.3 Leveling & XP

- **Max Hero Level**: 18.
- **XP Requirement**: **10 XP** per level.

### 3.4 Starting Gold

- Each hero starts the game with **20 gold**.

### 3.5 Health & Mana

- **Health (HP)**:

  $$\text{HP} = \text{Base HP} + (\text{Hero Level} \times 5)$$

  _Base HP is approximately 15, differing slightly per hero._

- **Mana**:

  $$\text{Mana} = \text{Base Mana} + (\text{Hero Level} \times 5)$$

  _Base Mana differs per hero based on magic reliance._

### 3.6 Health & Mana Recovery

- **Fountain Healing**: Remaining inside the base fountain for at least **1 full turn** (cannot run in and out during the same turn) restores all HP and Mana to maximum.
- **Passive Regeneration**: All heroes gain HP and Mana equal to their current **Hero Level** at the end of each round. (This passive regeneration can be augmented by specific items and abilities.)

### 3.7 Attack Damage & Defense

- **Attack Damage**: Defined per hero. All heroes gain **+1 attack damage** at levels 3, 6, 9, 12, 15, and 18 (every 3 levels).
- **Defense**: Defined per hero. All heroes gain **+1 defense** at levels 6, 12, and 18 (every 6 levels).
- **Defense Mechanic**: Defense is a flat reduction. Incoming basic attack damage is reduced by the hero's defense value, to a minimum of 1 damage. Defense does not reduce spell or ability damage unless specified.

### 3.8 Hero Board & Planning

Each hero is represented by a **hero board** with 7 planning slots hidden behind a **planning cover** (similar to a DM screen). Players plan their turns in secret by placing tokens into these slots.

#### Board Layout

```
┌───────────────────────────────────────────────────┐
│                  PLANNING COVER                     │
│         (hides all 7 slots until lifted)            │
│                                                     │
│  [Movement]   [AP1] [AP2] [AP3] [AP4]   [R1] [R2]  │
│   (1 slot)    (action slots)      (reaction slots)  │
└───────────────────────────────────────────────────┘
```

#### Token Types

| Token | Slot | Description |
|---|---|---|
| Numbered Movement (1–5, 12) | Movement | Commit a maximum movement amount for this turn |
| Attack | AP1–AP4 | Declare a basic attack |
| Spell 1 | AP1–AP4 | Declare the hero's first basic ability (Q) |
| Spell 2 | AP1–AP4 | Declare the hero's second basic ability (W) |
| Spell 3 | AP1–AP4 | Declare the hero's third basic ability (E, future heroes) |
| Ultimate | AP1–AP4 | Declare the hero's ultimate ability (R) |

#### Reaction Slots

The two reaction slots (R1, R2) hold tokens that define what the hero can do as a reaction during opponents' turns. Valid reaction tokens are:
- **Movement token** (value 1) — spend to move 1 hex as a reaction.
- **Spell token** (Spell 1, Spell 2, Spell 3, or Ultimate) — spend the appropriate spell as a reaction.

Only the specific spell committed to the reaction slot may be used. A movement reaction always provides exactly 1 hex of movement, regardless of the committed movement token's value.

#### Planning Flow

Planning occurs **simultaneously** for all players, twice per full round:

| Timing | Plans for |
|---|---|
| Start of **Phase 2** (Ascending) | All turns in Phase 2 (A→X→B→Y→C→Z) |
| Start of **Phase 4** (Pendulum) | All turns in Phase 4 (Z→C→Y→B→X→A) |

All players place tokens behind their covers at the same time. Once planning is complete, the turn sequence begins. When a player's turn arrives, they **lift the cover** and execute.

#### Execution Rules

- **Movement**: The player may move **up to** the committed movement value. The actual path and hexes are decided at execution time (not pre-planned).
- **AP Slots**: Slots resolve in order (AP1 → AP2 → AP3 → AP4). If an action becomes impossible at execution time (no valid target, target out of range, etc.), the **AP is lost but mana is not spent and the ability does not go on cooldown**. The player then proceeds to the next AP slot.
- **Targeting**: The specific target or hex is chosen at execution time. Only the action *type* is pre-committed.
- **Max AP**: The number of usable AP slots is capped by the hero's max AP for their current level (see §3.1). Only the first N slots are resolved; excess tokens are ignored.

#### Interaction with Reveal Abilities

Abilities that reveal an enemy's planning cover (e.g., Soren's **Unveil**) allow all players to see the target's hidden tokens before that enemy's turn, exposing their intended movement, action sequence, and reaction reserves.

## 4. Game Loop & Round Structure

A full round of the game represents a cycle of active lane pushes, neutral farming, and defensive reactions. It is structured into 5 distinct phases:

### 4.1 Phase 1: Round Start (Spawn & Setup)

1. **Advance Round Counter**: Increment the game round tracker by 1.
2. **Shift the Start Token**: Pass the "Round Start" token clockwise to the next player. This player will lead the next turn cycle.
3. **Spawn Phase**:
   - **Pawns (Lane Creeps)**: Spawn at the starting generators of each lane (commences at the start of Round 2, and spawns every round thereafter).
   - **Neutrals (Jungle Creeps)**: Spawn at empty camp hexes every **3rd round** (Rounds 3, 6, 9, 12, etc.).
4. **Determine Rotation**: Establish the player turn sequence starting with the holder of the Start Token. Turn order alternates between teams (e.g., Green Team [A, B, C] and Red Team [X, Y, Z]).
   - _Example sequence (Player A of Green Team has Start Token)_: The ascending alternating sequence is A (Green) → X (Red) → B (Green) → Y (Red) → C (Green) → Z (Red).
5. **Planning Phase**: All players plan simultaneously behind their planning covers for the ascending half-round (Phase 2). Players place movement, AP, and reaction tokens into their hero board slots (see §3.8).

### 4.2 Phase 2: First Half-Round (Ascending Play)

- Players take their turns in ascending alternating order (e.g., A → X → B → Y → C → Z).
- **Active Turn Structure**:
  1. **Lift Cover & Reset Resources**: The active player lifts their planning cover, revealing their tokens to all players. Their movement is set to the value of their committed movement token (up to 5 hexes, or 12 in Round 1) and their action points are set to their **max AP** for their current level (see §3.1).
  2. **Active Actions**: The player spends their movement and AP to perform actions (see Action Economy below).
  3. **End of Turn**: Spent tokens are discarded. Unused movement and AP are lost. Reaction tokens remain in their slots and may be used during other players' turns for the rest of this half-round.

### 4.3 Phase 3: Half-Round Checkpoint (Turnaround)

1. **Planning Phase**: All players plan simultaneously behind their covers for the descending half-round (Phase 4). Players place movement, AP, and reaction tokens into their hero board slots (see §3.8).
2. **Backpack Cooldown Progress**: As player turns progress, swapped backpack items tick down their **6-turn cooldown** (equal to the number of players). Any swaps made at the start of Phase 2 become active here.

### 4.4 Phase 4: Second Half-Round (Pendulum Play)

- Players take their turns in descending/reverse alternating order (e.g., Z → C → Y → B → X → A).
- **Active Turn Structure**:
  - Same structure as Phase 2 (lift cover, reset movement and AP, active actions, end of turn).
  - Items swapped in Phase 2 are now active. Any items swapped in Phase 4 are placed on cooldown until the end of Phase 5.

### 4.5 Phase 5: Round End & Cleanup

1. **Passive Regeneration**: All heroes gain HP and Mana equal to their current **Hero Level**.
2. **Passive Gold**: All heroes receive **2 passive gold**.
3. **Courier Deliveries**: Any couriers dispatched in the previous round arrive at their destination heroes.
4. **Reaction Carryover**: Unused stored reactions carry over to the next round (still subject to the max 2 limit).
5. **Effects Resolution**: Round-duration temporary buffs, debuffs, or cooldown ticks resolve.

### 4.6 Action Economy Reference

During their turn, a player spends AP to perform the following actions:

| Action | AP Cost |
|---|---|
| Basic Attack | 1 AP |
| Use Spell or Ability | Typically 1 AP (ultimates may cost 2 AP) |
| Use Item | Varies (some items cost 0 AP) |
| Buy Item from Shop | 1 AP |
| Sell Item to Shop | 1 AP |

### 4.7 Reaction & Dodging Mechanics

- **Storing Reactions**:
  - Up to **2 reaction tokens** can be placed in the reaction slots (R1, R2) during the planning phase (see §3.8).
  - Valid reaction tokens are **movement tokens** (value 1) and **spell tokens** (Spell 1, Spell 2, Spell 3, or Ultimate).
  - **Strict Usage**: You may only use the exact token stored. A movement reaction always grants exactly **1 hex** of movement. A spell reaction allows you to cast that specific spell only.
  - **Reaction Carryover**: Reaction tokens unused by the end of the round carry over to the next round's planning phase (still subject to the max 2 limit).
- **Dodging**:
  - Attacks and abilities can miss if a player uses stored movement reactions to move out of the range of the attack/spell during the attacker's turn.
  - **Attacker Penalty**: If a defender dodges an attack this way, the attacker still loses their Action Point and the action is wasted.

### 4.8 Courier System

- Each player can courier items to themselves if they are away from a shop.
- Delivery takes **1 full round** to arrive (arriving during Phase 5 of the next round).

## 5. Economy & Progression (Gold & XP)

| Source | Durability | Gold (Killer) | XP (Shared, ≤3 hexes) | Damage to Attacker |
|---|---|---|---|---|
| **Pawns (Lane Creeps)** | 1 attack | 5 gold | 10 XP (all allied) | — |
| **Neutrals (Jungle Creeps)** | 2 attacks | 10 gold | 8 XP (all allied) | 2 per attack |
| **Ancient Neutrals** | 5 attacks | 30 gold | 20 XP (all allied) | 3 per attack |
| **Tower Destruction** | Varies (see §6) | 15 gold each (team) | — | Varies (see §6) |

- **Pawn Spawn**: Spawns at the start of Round 2, and at the start of every round thereafter.
- **Neutral Spawn**: Spawns every 3rd round.
- **Passive Income**: All heroes receive **2 passive gold** at the end of each round.

## 6. Objectives & Win Conditions

To win, a team must gain access to and destroy the enemy **Hive**.

### 6.1 Hive

- The Hive itself does not attack.
- It takes **20 attacks** to be destroyed.

### 6.2 Towers

There are **3 towers in each lane**, which must be destroyed sequentially:

| Tower Tier | Attacks to Destroy | Damage Dealt |
|---|---|---|
| Tier 1 (outermost) | 5 | 3 |
| Tier 2 (middle) | 7 | 4 |
| Tier 3 (inside base) | 9 | 5 |

- **Durability Formula**: $\text{Attacks to destroy} = 3 + (\text{Tower tier} \times 2)$
- **Damage Formula**: $\text{Tower Damage} = 2 + \text{Tower Tier}$

### 6.3 Tower Mechanics & Protection

- **Access Requirement & Sequence**: Access to the Hive is blocked until **all towers in at least 1 lane** are destroyed. Towers must be destroyed sequentially in each lane; you can only attack the lowest-tier tower still standing (e.g., if the Tier 1 tower is still up, you cannot attack or damage the Tier 2 tower).
- **Backdoor Protection**: A tower cannot be attacked or damaged if there is an **enemy pawn** (relative to the attacker) still alive in that lane.
- **Tower Territory Defense**: If a hero moves within the range of a tower while the enemy pawn in that lane is still alive, they take **damage equal to the Tower's Damage** per movement space moved within tower range.
- **Pushing with Allied Pawns (Tanking)**:
  - If you attack a tower while your own **allied pawn** is alive in that lane, your pawn "tanks" the tower's defense. The tower takes damage, but your allied pawn is killed. The defending team's heroes within **3 hexes of the tower being attacked** gain the XP from the killed pawn (10 XP split), but no gold.
  - If your **allied pawn is dead** in that lane, the tower has no creep wave to tank it; therefore, each attack you make against the tower deals **damage equal to the Tower's Damage** directly to you (the attacking hero).
- **Tower Aggro**: If a hero attacks an enemy hero while within **2 hexes** of the tower, the attacking hero takes **damage equal to the Tower's Damage** per attack.

## 7. Combat, Abilities & Items

### 7.1 Basic Attacks

- **Melee**: 1 hex range.
- **Ranged**: 2 hexes range.

### 7.2 Abilities (Spells)

- **AP Cost**: Typically **1 AP**. Ultimates and high-impact abilities may cost **2 AP**. Spells will also be balanced by other factors such as cooldowns.
- **Range**: Specified individually per ability.

### 7.3 Items & Inventory

- **Inventory Size**: Each hero has **3 active item slots** and **1 backpack slot**.
- **Usage AP Cost**: Some items may cost **0 AP** to activate (specified per item).
- **Backpack Rules**:
  - Items in the backpack slot cannot be used and have no passive effects.
  - Swapping an item between the backpack and an active slot costs **0 AP**.
  - **Cooldown**: An item swapped into an active slot is placed on cooldown for **6 player turns** (equal to the total number of players). It cannot be used or provide passive benefits during this cooldown.

### 7.4 Item Economy & Pricing Guidelines

Based on the game's gold sources (2g passive/round, 5g pawns, 10g neutrals, 15g towers), items are categorized into four pricing tiers:

| Tier | Price Range | Purpose |
|---|---|---|
| Tier 1: Consumables | 5–10 Gold | One-time use items for health/mana restoration or quick map movement. |
| Tier 2: Starter/Basic | 15–30 Gold | Permanent early-game items providing minor stats or core utility. |
| Tier 3: Mid-Tier Upgrades | 45–80 Gold | Major mid-game items that require pooling gold from waves or camps. |
| Tier 4: Legendary | 120–180+ Gold | Game-winning power spikes and powerful active abilities. |

**Example Items:**

- **Tier 1 — Consumables**
  - **Healing Salve (8g)**: Active (0 AP) — Consume to restore 10 HP.
  - **Mana Potion (6g)**: Active (0 AP) — Consume to restore 10 Mana.
- **Tier 2 — Starter/Basic**
  - **Boots of Speed (25g)**: Passive — +1 normal movement speed (normal movement becomes 6 hexes).
  - **Ring of Protection (20g)**: Passive — Attacking heroes take −1 damage from basic attacks.
  - **Circlet (15g)**: Passive — +2 Max HP, +2 Max Mana.
- **Tier 3 — Mid-Tier**
  - **Bracer / Wraith Band / Null Talisman (50g)**: Passive — +6 Max HP (Bracer) or Max Mana (Null), and +1 basic attack damage.
  - **Ring of Health (65g)**: Passive — Increases round-end passive HP regeneration by +2.
  - **Point Booster (75g)**: Passive — +10 Max HP, +10 Max Mana.
- **Tier 4 — Legendary**
  - **Blink Dagger (130g)**: Active (0 AP) — Teleport up to 4 hexes. Cooldown: 3 rounds. Cannot be used if you have taken damage this round.
  - **Heart of Tarrasque (180g)**: Passive — +25 Max HP, round-end HP regeneration increased by +5.
  - **Daedalus (150g)**: Passive — Attacks deal +3 damage.

### 7.5 Skill Shots

Some abilities are designated as **Skill Shots** — they require a dice roll to determine whether they hit.

- **Mechanic**: Roll **1d6**. The result must be **≥ the number of hexes between the attacker and the target** for the skill shot to land.
- **Declaration**: The attacker must declare the target and commit the AP and mana before rolling.
- **On Miss**: The AP and mana are lost. The ability has no effect.
- **Reaction Interaction**: If the target uses a stored **movement reaction** to reposition after the skill shot is declared but before it resolves:
  - The effective range is recalculated based on the target's new position.
  - If the target moves out of range entirely, the skill shot automatically misses.
  - If the target moves farther but remains in range, the required roll increases (1d6 ≥ new distance).

## 8. Open Questions & Design Challenges

### 8.1 Hero & Ability Designs

- Hero designs are tracked separately in `heroes.md`. Remaining archetypes to design: agility carry, intelligence spellcaster, support heroes.
- Ability interactions and balance need playtesting.
