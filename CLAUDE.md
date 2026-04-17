# Greedy Shopkeepers — Browser Prototype

A browser-based playtest prototype for a physical board game. Goal: validate the core loop, not ship production software.

## Project Goal

Build a playable in-browser prototype (single HTML file or simple React app — no backend, no build pipeline if avoidable). Solo mode first, then 2–4 player hot-seat multiplayer.

## Design Document

Full game rules are in `design-doc.md`. Read it in full before planning or writing any code.

## Prototype Scope

Build only what's in the design doc. Do not build:
- Player character abilities
- Trading between players
- Monster/Item type combat interactions
- Wave scaling by player count

## Key Implementation Notes

- All scoring values live in a single config object so they can be tweaked without hunting through code
- Use emoji as placeholder art/icons throughout (no image assets needed)
- Cards are dual-faced; in the data model a card always has both a monster side and an item side
- The draw pile is always accessed from the bottom for loot bonus draws
- Hands are not hidden between players

## Prototype Priorities (in order)

1. Solo mode — full core loop playable end-to-end
2. Final scoring phase — set assembly UI is the most complex part
3. Hot-seat multiplayer (2–4 players on one screen)
