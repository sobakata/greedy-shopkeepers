# Greedy Shopkeepers — Design Document
*v1.0 Draft*

## The Pitch

Fantasy shopkeepers must defeat monsters and loot items before opening their shop. Players compete to build the best shop by the end of the game.

**Core fantasy:** Players feel like they're doing their best to open a great shop, navigating a world where others are trying to do the same. The game is neither strictly cooperative nor competitive — players can choose either approach — but there is one winner based on final scoring.

**Target audience:** Teens and up. Easy to pick up for beginners, with enough depth for experienced players to optimize their score. A playthrough should take ~30 minutes.

**Inspirations:**
- *7 Wonders* — Players can focus on their own strategy OR pay attention to others and subvert them; both are valid. The entire scoring system is inspired by 7 Wonders' green cards mechanic, expanded into a full system.
- *Hack & Slash video games* — The general feeling of looting items and managing inventory.

---

## Components

### The Deck

- **Total cards:** 140 double-faced cards
- **Each card is dual-sided:** Monster face on one side, Item face on the other

**Rarity distribution:**

| Rarity | Color | Count |
|--------|-------|-------|
| Common | Green | 50 |
| Uncommon | Blue | 40 |
| Rare | Purple | 30 |
| Epic | Orange | 20 |

**Level distribution:**

| Level | Count |
|-------|-------|
| 1 | 14 |
| 2 | 16 |
| 3 | 14 |
| 4 | 16 |
| 5 | 14 |
| 6 | 16 |
| 7 | 14 |
| 8 | 16 |
| 9 | 10 |
| 10 | 10 |

### Monster Face

Each card's Monster face shows: Level, Monster Type, Rarity (as card color/frame), and art.

**Monster Types:**

| Type | Count |
|------|-------|
| Goblin | 30 |
| Undead | 30 |
| Beast | 30 |
| Elemental | 30 |
| Duck | 20 |

Monster Types have no mechanical meaning in the prototype. May be added later.

### Item Face

Each card's Item face shows: Level, Item Type, Rarity (as card color/frame), and art.

**Item Types:**

| Type | Count |
|------|-------|
| Weapon | 30 |
| Armor | 30 |
| Consumable | 30 |
| Trinket | 30 |
| Luxury | 20 |

Item Types only matter for scoring (set bonuses). No other mechanical meaning in the prototype.

### Other Components

Player dashboards with zones for: hand, loot pile, stash. (Player abilities area to be added later.)

---

## Setup

1. Shuffle the full 140-card deck and place it Monster-face-up as the draw pile.
2. Each player draws 10 cards as their starting hand.
3. Set up Wave 1 (see Wave Patterns below).
4. Choose a random starting player; play proceeds clockwise.

**Player count:** No setup differences between player counts in the prototype. Each player always starts with 10 cards.

---

## Game Structure

A full game consists of **5 waves**, each with two phases:

> **Fight & Loot → Stash**

After Wave 5's stash phase, the game moves to the **Final Scoring Phase**.

---

## The Wave Phase

### Wave Patterns

Monsters are arranged in piles face-up in the center. Only the **top card of each pile** is visible and can be fought.

There are always **8 face-up piles**, giving players meaningful choice about which monster to fight.

Total monsters scale with player count and wave number:

`total = (6 × players) + (1 × players × (wave − 1))`

| Wave | Solo | 2 players | 4 players |
|------|------|-----------|-----------|
| 1 | 6 | 12 | 24 |
| 2 | 7 | 14 | 28 |
| 3 | 8 | 16 | 32 |
| 4 | 9 | 18 | 36 |
| 5 | 10 | 20 | 40 |

The formula is intentionally gentle — monster counts stay slightly below what a player can realistically fight, so forfeiting is possible but never forced.

Monsters are distributed as evenly as possible across the 8 piles. When the total is not divisible by 8, the first N piles receive one extra monster.

All players fight the same shared monster piles, taking turns.

### Turn Order

A random player goes first; turns proceed clockwise for the duration of the wave.

### Actions on Your Turn

A player must take exactly one of:

1. **Defeat a Monster** — Play cards from hand to defeat any one visible (top-of-pile) monster.
2. **Forfeit** — If unable to defeat any monster, draw 1 card from the draw pile. This card goes to hand and can be used next turn.

No other actions exist in the prototype.

### Combat Rules

To defeat a monster, a player plays item cards from their hand whose **combined level equals or exceeds the monster's level**.

**Single card:** A level 5 item defeats any monster of level 5 or lower.

**Multi-card combo:** Multiple cards of the **same rarity (color)** can be combined, summing their levels. Example: a level 2 Blue + level 5 Blue = level 7, defeats any monster up to level 7.

- Cards of **different rarities cannot be combined**.
- Monster Type and Item Type have no effect on combat in the prototype.

### After Defeating a Monster

All item cards played in combat go to the player's **loot pile** (not discarded).

The player also takes **1 card from the bottom of the draw pile** and places it in their loot pile. (Bottom of deck — so no one knows what's coming next.)

**Loot Embargo:** Cards in the loot pile **cannot be used from hand during the current wave**. They sit in the loot pile zone until the Stash Phase.

### Wave End

The wave ends when **all monsters in all piles have been defeated**. There is no other end condition in the prototype. If no player can defeat anything, players keep forfeiting and drawing until someone can.

---

## The Stash Phase

Occurs after every wave (including after Wave 5, before Final Scoring).

Each player looks at their loot pile and chooses **one** of:

- **Quality Stash:** Stash **1–5 item cards** of any level, freely chosen.
- **Quantity Stash:** Stash **any number of item cards** whose combined level total is **≤ 10**. There is no card-count limit — this option intentionally supports low-level card farming strategies.

A player must always stash — it's never beneficial to skip (all stashed cards count toward final scoring).

**After stashing:**
- Stashed cards go to the player's permanent stash zone.
- All remaining loot pile cards return to the player's hand.
- If the player's hand has fewer than 10 cards, draw from the draw pile until at 10.
- If the player's hand has more than 15 cards, they must discard down to 15 before their first turn of the new wave. The player chooses which cards to discard.
- There is no maximum stash size.

---

## Hand Management Summary

| Moment | What happens |
|--------|-------------|
| Game start | Draw 10 cards |
| During wave | Play cards to fight; loot goes to loot pile (embargoed) |
| Forfeit turn | Draw 1 card from draw pile to hand |
| End of stash phase | Loot pile returns to hand; draw up to 10 from draw pile |
| Wave start (if >15 cards) | Discard down to 15 before first turn (player's choice) |

Hands are **not hidden** — players may look at each other's hands at any time.

---

## Final Scoring Phase

After Wave 3's stash phase, players assemble **sets** from their stashed cards.

**Each card may only be used in one set.**

**Base score:** Sum of all stashed card levels (regardless of sets).

**Set types (each has its own scoring table):**

| Set Type | Description |
|----------|-------------|
| Matching Rarity | Multiple cards of the same rarity |
| Matching Level | Multiple cards of the same level |
| Matching Item Type | Multiple cards of the same item type |
| Rarity Rainbow | One card of each rarity (Green, Blue, Purple, Orange) |
| Item Type Rainbow | One card of each item type (Weapon, Armor, Consumable, Trinket, Luxury) |
| Level Straight | Cards with consecutive levels (like a poker straight, any length) |

Multiple sets of the same type are allowed.

**Placeholder scoring values (to be tuned during playtesting):**

Scoring uses **lookup tables** indexed by set size, so the physical game can include a printed reference sheet. Committing more cards to a single set is increasingly rewarding.

**Matching sets** (same rarity / same level / same item type):

| Cards in set | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|
| Points | 3 | 7 | 14 | 25 | 42 | 65 | 95 | 133 | 180 |

**Level Straight** (min 3 consecutive levels):

| Cards in run | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|
| Points | 10 | 20 | 34 | 52 | 74 | 100 | 130 | 164 |

**Fixed bonuses:**
| Set Type | Points |
|----------|--------|
| Rarity Rainbow (one of each rarity, 4 cards) | 15 pts |
| Item Type Rainbow (one of each item type, 5 cards) | 20 pts |

*All values are starting points for tuning. They live in a single CONFIG object in the code.*

**Winner:** Player with the highest total score. Tie-breaking is undefined — treat as a shared win for the prototype.

---

## Solo Mode

One player plays through all 3 waves alone, defeating all monsters and stashing. At the end, they assemble sets and record their score. Solo mode exists purely for playtesting the core loop.

---

## Card Visual Design

- **Level:** Large number in top-left and bottom-right corners (like a standard playing card).
- **Rarity:** Colored card frame or background (Green / Blue / Purple / Orange).
- **Type:** Text label (Monster Type or Item Type).
- **Art:** Emoji placeholder for the prototype. Final version will be hand-drawn pixel art in the style of 90s point-and-click adventure games.

---

## Out of Scope for This Prototype

The following are planned for future design iterations and should **not** be built now:

- Unique player character abilities
- Trading between players
- Monster Type or Item Type combat interactions
- Wave pattern scaling by player count
- Any per-player setup differences

---

## Open Design Questions

- **Scoring balance:** All point values are guesses. Playtesting will determine the right numbers.
- **Card counts:** The 140-card deck and its distribution are based on intuition and need playtesting.
- **Wave patterns:** The 3-wave pattern is a starting point; total card count should be validated so the draw pile never empties.
- **Player abilities:** Future feature — each player picks a character with a unique ability before the game starts.

---

## Decision Log

| Date | Change | Rationale |
|------|--------|-----------|
