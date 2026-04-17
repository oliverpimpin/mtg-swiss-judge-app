# MTG 1v1 Swiss Judge App

A lightweight, offline-friendly tournament tool for running **1v1 Swiss Magic: The Gathering events** without spreadsheets, paper tracking, or internet dependency.

Built specifically for judges and organizers who want **accurate pairings, clean round control, and the ability to fix mistakes without breaking the tournament**.

---

## Purpose

This app is designed to run **1v1 Swiss tournaments (Best-of-3)** with:

- automatic Swiss pairings
- round-by-round control
- manual result entry via dropdown
- standings with proper tiebreakers
- round locking and correction tools
- drop / undrop player functionality
- offline use on mobile or desktop

It replaces the need for Excel sheets or external tournament software while keeping the judge fully in control.

---

## Core Design Philosophy

This app is built around:

- **Swiss integrity first** (no rematches, proper standings)
- **Simple inputs, reliable outputs**
- **Rounds must be finalized before standings update**
- **Mistakes should be fixable without breaking the event**
- **Mobile-friendly, fast interaction**
- **No hidden pairing or scoring behavior**

---

## Tournament Structure

### Swiss Rounds

The app automatically determines the number of rounds based on player count:

- 4–8 players → 3 rounds
- 9–16 players → 4 rounds
- 17–32 players → 5 rounds
- 33+ players → 6 rounds

### Top Cut

After Swiss rounds complete:

- 8 or fewer players → **No top cut**
- 9–16 players → **Top 4**
- 17+ players → **Top 8**

The app automatically handles this transition.

---

## Match Result System

Match results are entered using a dropdown system instead of manual scoring.

### Supported Results

- `2-0-0` → Player A wins 2–0
- `2-1-0` → Player A wins 2–1
- `1-2-0` → Player B wins 2–1
- `0-2-0` → Player B wins 2–0
- `1-1-1` → Draw
- `1-0-1` → Player A wins with one game draw
- `0-1-1` → Player B wins with one game draw
- `0-0-1` → Match draw (no wins)
- `ID` → Intentional draw
- `BYE` → Automatic win (assigned by system)

---

## Scoring System

The app follows standard MTG tournament scoring:

### Match Points
- Win → 3 points
- Draw → 1 point
- Loss → 0 points

### Tiebreakers (in order)
1. Match Points
2. Opponent Match Win Percentage (OMW%)
3. Game Win Percentage (GWP%)
4. Opponent Game Win Percentage (OGW%)

### Important Notes

- BYEs grant match points but are **excluded from OMW% calculations**
- Intentional Draws are treated as standard draws
- All scoring updates only occur after round finalization

---

## Main Controls

### Build Round 1
Generates the first round with randomized pairings.

### Build Next Round
Generates the next Swiss round based on standings.

Requirements:
- Current round must be fully completed
- Current round must be finalized

### Finalize Round
Locks the current round and updates standings.

This prevents:
- partial scoring affecting rankings
- accidental pair generation from incomplete data

### Reopen Current Round
Unlocks the most recently finalized round.

Use this when:
- results were entered incorrectly
- a match needs correction before the next round is built

### Undo Last Round
Removes the most recent round entirely.

Use this when:
- pairings were incorrect
- player changes require a rebuild
- you need to back up and repair the event

Undo works **one round at a time**.

### Drop / Undrop Player
Marks a player as dropped or restores them.

Dropped players:
- remain in standings/history
- are excluded from future pairings

### Add Player (Pre-event)
Adds players before Round 1 is built.

---

## Round Control System

The app enforces a structured round flow:

1. Build round
2. Enter results
3. Finalize round
4. Build next round

You cannot:
- build a new round without finalizing the current one
- finalize a round with missing results
- modify locked rounds without reopening

This ensures tournament integrity at all times.

---

## Pairing Logic

The Swiss pairing system:

- pairs players by match points
- avoids repeat matchups
- assigns BYEs when needed
- ensures no player receives more than one BYE
- distributes pairings top-down based on standings

The system prioritizes fairness while maintaining practical pairing speed.

---

## Standings

The standings table updates only after round finalization and includes:

- Rank
- Player name
- Match points
- Tiebreakers (OMW%, GWP%, OGW%)

This ensures standings always reflect a **complete and valid round state**.

---

## Typical Judge Workflow

### Normal flow
1. Add players
2. Build Round 1
3. Enter match results
4. Finalize round
5. Build next round
6. Repeat until Swiss ends
7. Run top cut (if applicable)

---

### If results are incorrect
1. Reopen Current Round
2. Fix results
3. Finalize again

---

### If pairings are incorrect
1. Undo Last Round
2. Adjust players if needed
3. Build round again

---

### If a player drops
1. Finalize current round
2. Drop player
3. Build next round

---

## What This App Is Not Trying To Be

This app is intentionally **not**:

- a fully automated tournament platform with syncing
- a deck tracking system
- a judge rules engine
- a replacement for official WotC software at high-level events

It is designed as a **practical, reliable judge tool** for local and mid-level events.

---

## Recommended Use

Best suited for:

- Local game store tournaments
- Casual competitive events
- Commander side events (1v1 duel)
- Judges who want a simple, controlled Swiss system
- Offline tournament environments

---

## Notes

- Designed to run fully **offline**
- No account or internet required
- Save frequently during events if using browser storage
- Refresh browser if GitHub Pages appears cached

---

## Future Maintenance Notes

Any future updates should preserve:

- Swiss pairing integrity
- round lock / finalize workflow
- dropdown-based scoring
- no hidden scoring or pairing logic
- ability to undo and repair safely
