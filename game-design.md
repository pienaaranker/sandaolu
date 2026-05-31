# Dota 2-Inspired Board Game Design Document
Welcome! This is the main design document for your Dota 2-inspired board game. Below are the rules and ideas you have jotted down so far, structured into clear categories, along with identified gaps and design questions to solve next.
---
## 1. Core Concept & Vision
* **Main Objective**: Destroy the enemy's "Hive" (located in the middle of their base).
* **Game Format**: A tactical, lane-pushing board game inspired by Dota 2. A 3v3 team setup (6 players/heroes total).
* **Progression**: Players draft heroes, manage action and reaction points, farm pawns/neutrals for gold and XP, buy items, and coordinate to breach the enemy base.
---
## 2. Map Layout & Board Design
* **Grid Style**: Hexagonal grid (inferred from rules mentioning "hexes" and movement spaces).
* **Lanes**: 3 lanes (Top, Middle, Bottom) containing Towers that block access to the base.
* **Jungle**: A jungle area containing 3 neutral camps on each side of the map.
* **River**: A river area running diagonally/across the middle of the map.
* **Shops**:
  * Base Shops (at each team's starting fountain).
  * Side/Off-lane Shops (one located near each off-lane for forward purchases).
  * **Availability**: All items in the game are available for purchase at all shops (both Base and Side Shops).
* **Roshan Pit**: A boss pit (we will brainstorm a new name for Roshan).
* **Ancient Camp**: A camp for powerful neutrals (we will brainstorm a new name for Ancients).
---
## 3. Heroes, Stats & Progression
* **Team Size**: 3v3 (6 players/heroes total, Player 1-6).
* **Movement & Action Points**:
  * **Normal Movement**: A player can move up to **5 spaces (hexes)** per turn.
  * **Action Points**: A player has **2 Action Points (AP)** per turn.
  * **First Round Boost**: For the very first round of the game, all players start with **12 movement** and **2 actions** to speed up rollout and laning setups.
* **Teleportation (Town Portal)**:
  * All heroes have the inherent ability to teleport to any allied structure.
  * **Cooldown**: 3 rounds.
* **Leveling & XP**:
  * **Max Hero Level**: 18.
  * **XP Requirement**: **10 XP** per level.
* **Starting Gold**:
  * Each hero starts the game with **20 gold**.
* **Health & Mana Formulas**:
  * **Health (HP)**:
    $$\text{HP} = \text{Base HP} + (\text{Hero Level} \times 5)$$
    * *Base HP is approximately 15, differing slightly per hero.*
  * **Mana**:
    $$\text{Mana} = \text{Base Mana} + (\text{Hero Level} \times 5)$$
    * *Base Mana differs per hero based on magic reliance.*
* **Health & Mana Recovery**:
  * **Fountain Healing**: Remaining inside the base fountain for at least **1 full turn** (cannot run in and out during the same turn) restores all HP and Mana to maximum.
  * **Passive Regeneration**: All heroes gain HP and Mana equal to their current **Hero Level** at the end of each round. (This passive regeneration can be augmented by specific items and abilities).
---
## 4. Game Loop & Round Structure
A full round of the game represents a cycle of active lane pushes, neutral farming, and defensive reactions. It is structured into 5 distinct phases:
### Phase 1: Round Start (Spawn & Setup)
1. **Advance Round Counter**: Increment the game round tracker by 1.
2. **Shift the Start Token**: Pass the "Round Start" token clockwise to the next player. This player will lead the next turn cycle.
3. **Spawn Phase**:
   * **Pawns (Lane Creeps)**: Spawn at the starting generators of each lane (commences at the start of Round 2, and spawns every round thereafter).
   * **Neutrals (Jungle Creeps)**: Spawn at empty camp hexes every **3rd round** (Rounds 3, 6, 9, 12, etc.).
4. **Determine Rotation**: Establish the player turn sequence starting with the holder of the Start Token. Turn order alternates between teams (e.g., Green Team [A, B, C] and Red Team [X, Y, Z]).
   * *Example sequence (Player A of Green Team has Start Token)*: The ascending alternating sequence is A (Green) $\rightarrow$ X (Red) $\rightarrow$ B (Green) $\rightarrow$ Y (Red) $\rightarrow$ C (Green) $\rightarrow$ Z (Red).
### Phase 2: First Half-Round (Ascending Play)
* Players take their turns in ascending alternating order (e.g., A $\rightarrow$ X $\rightarrow$ B $\rightarrow$ Y $\rightarrow$ C $\rightarrow$ Z).
* **Active Turn Structure**:
  1. **Reset Resources**: The active player resets their movement to **5 hexes** (12 hexes in Round 1) and resets their action points to **2 AP**.
  2. **Active Actions**: The player spends their movement and AP to perform actions (see Action Economy below).
  3. **Reaction Declaration**: At the end of their turn, the player declares if they are storing unused AP or movement as **Reactions** (max 2 total reactions stored). Any unstored AP/movement is lost.
### Phase 3: Half-Round Checkpoint (Turnaround)
* **Backpack Cooldown Progress**: As player turns progress, swapped backpack items tick down their **6-turn cooldown** (equal to the number of players). Any swaps made at the start of Phase 2 become active here.
### Phase 4: Second Half-Round (Pendulum Play)
* Players take their turns in descending/reverse alternating order (e.g., Z $\rightarrow$ C $\rightarrow$ Y $\rightarrow$ B $\rightarrow$ X $\rightarrow$ A).
* **Active Turn Structure**:
  * Same structure as Phase 2 (reset movement, 2 AP, active actions, and reaction declaration).
  * Items swapped in Phase 2 are now active. Any items swapped in Phase 4 are placed on cooldown until the end of Phase 5.
### Phase 5: Round End & Cleanup
1. **Passive Regeneration**: All heroes gain HP and Mana equal to their current **Hero Level**.
2. **Passive Gold**: All heroes receive **2 passive gold**.
3. **Courier Deliveries**: Any couriers dispatched in the previous round arrive at their destination heroes.
4. **Reaction Carryover**: Unused stored reactions carry over to the next round (still subject to the max 2 limit).
5. **Effects Resolution**: Round-duration temporary buffs, debuffs, or cooldown ticks resolve.
---
### Action Economy Reference
During their turn, a player spends AP to perform the following actions:
* **Basic Attack** (costs 1 AP)
* **Use Spell or Ability** (costs AP, typically 1 AP; ultimates may cost 2 AP)
* **Use Item** (costs AP, some items cost 0 AP)
* **Buy Item from Shop** (costs 1 AP)
* **Sell Item to Shop** (costs 1 AP)
---
### Reaction & Dodging Mechanics
* **Storing Reactions**:
  * Up to **2 reactions** can be stored per hero. These must be declared as specific types when stored (either **Movement** or **Action**).
  * **Strict Usage**: You must explicitly declare the specific action/movement you want to store. If you store 2 action reactions (e.g., to cast spells/attack), you cannot use one of them to move. If you store 2 movement reactions, you cannot use one of them to cast a spell or attack.
  * **Conversion Rate**:
    * **1 stored movement** allows **1 hex of movement** as a reaction.
    * **1 stored action** allows **1 action** (attack, spell, item use) as a reaction.
* **Dodging**:
  * Attacks and abilities can miss if a player uses stored movement reactions to move out of the range of the attack/spell during the attacker's turn.
  * **Attacker Penalty**: If a defender dodges an attack this way, **the attacker still loses their Action Point and the action is wasted**.
---
### Courier System
* Each player can courier items to themselves if they are away from a shop.
* Delivery takes **1 full round** to arrive (arriving during Phase 5 of the next round).
---
---
## 5. Economy & Progression (Gold & XP)
* **Pawns (Lane Creeps)**:
  * **Spawn**: Spawns at the start of Round 2, and at the start of every round thereafter.
  * **Durability**: Killed by **1 attack**.
  * **Rewards**: 
    * The hero who lands the killing blow gains **5 gold**.
    * All allied heroes within **3 hexes** split **10 XP** (rounding up).
* **Neutrals (Jungle Creeps)**:
  * **Spawn**: Spawns every **3rd round**.
  * **Durability**: Requires **2 attacks** to kill.
  * **Combat Cost**: The attacking hero takes **2 damage** per attack they perform.
  * **Rewards**:
    * Gives **10 gold** to the killer.
    * Gives **8 XP**, shared among all allied heroes within **3 hexes**.
* **Ancient Neutrals**:
  * **Durability**: Requires **5 attacks** to kill.
  * **Combat Cost**: The attacking hero takes **3 damage** per attack they perform.
  * **Rewards**:
    * Gives **30 gold** to the killer.
    * Gives **20 XP**, shared among all allied heroes within **3 hexes**.
* **Tower Destruction**:
  * The team that destroys an enemy tower gains **15 gold each** (no XP is awarded).
* **Passive Income**:
  * All heroes receive **2 passive gold** at the end of each round.
---
## 6. Objectives & Win Conditions
To win, a team must gain access to and destroy the enemy **Hive**.
* **Hive Durability**:
  * The Hive itself does not attack.
  * It takes **20 attacks** to be destroyed.
* **Tower Layout**:
  * There are **3 towers in each lane** in sequence:
    * **Tier 1 Tower** (outermost / furthest from the Hive): 5 attacks to destroy.
    * **Tier 2 Tower** (middle): 7 attacks to destroy.
    * **Tier 3 Tower** (inside the base): 9 attacks to destroy.
  * Towers are destroyed and deal damage based on their tier:
    * **Tier Durability Formula**: $\text{Attacks to destroy} = 3 + (\text{Tower tier} \times 2)$
    * **Tower Damage Formula**: $\text{Tower Damage} = 2 + \text{Tower Tier}$
      * **Tier 1 Tower**: 5 attacks to destroy | 3 damage
      * **Tier 2 Tower**: 7 attacks to destroy | 4 damage
      * **Tier 3 Tower**: 9 attacks to destroy | 5 damage
* **Tower Mechanics & Protection**: 
  * **Access Requirement & Sequence**: Access to the Hive is blocked until **all towers in at least 1 lane** are destroyed. Towers must be destroyed sequentially in each lane; you can only attack the lowest-tier tower still standing (e.g., if the Tier 1 tower is still up, you cannot attack or damage the Tier 2 tower).
  * **Backdoor Protection**: A tower cannot be attacked or damaged if there is an **enemy pawn** (relative to the attacker) still alive in that lane.
  * **Tower Territory Defense**: If a hero moves within the range of a tower while the enemy pawn in that lane is still alive, they take **damage equal to the Tower's Damage** per movement space moved within tower range.
  * **Pushing with Allied Pawns (Tanking)**:
    * If you attack a tower while your own **allied pawn** is alive in that lane, your pawn "tanks" the tower's defense. The tower takes damage, but your allied pawn is killed. The defending team's heroes within **3 hexes of the tower being attacked** gain the XP from the killed pawn (10 XP split), but no gold.
    * If your **allied pawn is dead** in that lane, the tower has no creep wave to tank it; therefore, each attack you make against the tower deals **damage equal to the Tower's Damage** directly to you (the attacking hero).
  * **Tower Aggro**: If a hero attacks an enemy hero while within **2 hexes** of the tower, the attacking hero takes **damage equal to the Tower's Damage** per attack.
---
## 7. Combat, Abilities & Items
* **Basic Attack Range**:
  * **Melee**: 1 hex range.
  * **Ranged**: 2 hexes range.
* **Abilities (Spells)**:
  * **AP Cost**: Typically **1 AP**. Ultimates and high-impact abilities may cost **2 AP**. Spells will also be balanced by other factors such as cooldowns.
  * **Range**: Specified individually per ability.
* **Items & Inventory**:
  * **Inventory Size**: Each hero has **3 active item slots** and **1 backpack slot**.
  * **Usage AP Cost**: Some items may cost **0 AP** to activate (specified per item).
  * **Backpack Rules**:
    * Items in the backpack slot cannot be used and have no passive effects.
    * Swapping an item between the backpack and an active slot costs **0 AP**.
    * **Cooldown**: An item swapped into an active slot is placed on cooldown for **6 player turns** (equal to the total number of players). It cannot be used or provide passive benefits during this cooldown.
* **Item Economy & Pricing Guidelines**:
  Based on the game's gold sources (2g passive/round, 5g pawns, 10g neutrals, 15g towers), items are categorized into four pricing tiers:
  1. **Tier 1: Consumables (5–10 Gold)**
     * *Purpose*: One-time use items for health/mana restoration or quick map movement.
     * *Examples*:
       * **Healing Salve (8g)**: Active (0 AP): Consume to restore 10 HP.
       * **Mana Potion (6g)**: Active (0 AP): Consume to restore 10 Mana.
  2. **Tier 2: Starter/Basic Items (15–30 Gold)**
     * *Purpose*: Permanent early-game items providing minor stats or core utility.
     * *Examples*:
       * **Boots of Speed (25g)**: Passive: $+1$ normal movement speed (normal movement becomes 6 hexes).
       * **Ring of Protection (20g)**: Passive: Attacking heroes take $-1$ damage from basic attacks.
       * **Circlet (15g)**: Passive: $+2$ Max HP, $+2$ Max Mana.
  3. **Tier 3: Mid-Tier Upgrades (45–80 Gold)**
     * *Purpose*: Major mid-game items that require pooling gold from waves or camps.
     * *Examples*:
       * **Bracer / Wraith Band / Null Talisman (50g)**: Passive: $+6$ Max HP (Bracer) or Max Mana (Null), and $+1$ basic attack damage.
       * **Ring of Health (65g)**: Passive: Increases round-end passive HP regeneration by $+2$.
       * **Point Booster (75g)**: Passive: $+10$ Max HP, $+10$ Max Mana.
  4. **Tier 4: Legendary Items (120–180+ Gold)**
     * *Purpose*: Game-winning power spikes and powerful active abilities.
     * *Examples*:
       * **Blink Dagger (130g)**: Active (0 AP): Teleport up to 4 hexes. Cooldown: 3 rounds. Cannot be used if you have taken damage this round.
       * **Heart of Tarrasque (180g)**: Passive: $+25$ Max HP, round-end HP regeneration increased by $+5$.
       * **Daedalus (150g)**: Passive: Attacks deal $+3$ damage.
---
## 8. Current Questions, Gaps & Design Challenges
Here are the remaining gaps in the rules we need to resolve to make this playable:
### A. Hero & Ability Designs
* Since we have the leveling scale (up to Level 18) and HP/Mana scaling formulas, we can begin designing the first few heroes. What archetype should we start with? (e.g., a melee tank/initiator, a ranged spellcaster, and a physical carry).