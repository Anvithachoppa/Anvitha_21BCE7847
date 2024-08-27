# ChessLikeGame

A simple, browser-based game built with Node.js, Express, and Socket.io. Two players take turns moving characters on a grid, aiming to outmaneuver each other. This project features server-side game logic and a basic front-end, making it a great introduction to real-time web apps and game development with JavaScript.

## Characters and Movement

There are three types of characters available:

1. **Pawn:**
   - Moves one block in any direction (Left, Right, Forward, or Backward).
   - **Move commands:** `L` (Left), `R` (Right), `F` (Forward), `B` (Backward)

2. **Hero1:**
   - Moves two blocks straight in any direction.
   - Kills any opponent's character in its path.
   - **Move commands:** `L` (Left), `R` (Right), `F` (Forward), `B` (Backward)

3. **Hero2:**
   - Moves two blocks diagonally in any direction.
   - Kills any opponent's character in its path.
   - **Move commands:** `FL` (Forward-Left), `FR` (Forward-Right), `BL` (Backward-Left), `BR` (Backward-Right)

All moves are relative to the player's perspective.

**Move command format:**
- For Pawn and Hero1: `<character_name>:<move>` (e.g., `P1:L`, `H1:F`)
- For Hero2: `<character_name>:<move>` (e.g., `H2:FL`, `H2:BR`)

## Game Flow

### Initial Setup
- Players deploy all 5 characters on their starting row in any order.
- Character positions are input as a list of character names, placed from left to right.
- Players can choose any combination of Pawns, Hero1, and Hero2 for their team.

### Turns
- Players alternate turns, making one move per turn.

### Combat
- If a character moves to a space occupied by an opponent's character, the opponent's character is removed from the game.
- For Hero1 and Hero2, any opponent's character in their path is removed, not just the final destination.

### Invalid Moves
Moves are considered invalid if:
- The specified character doesn't exist.
- The move would take the character out of bounds.
- The move is not valid for the given character type.
- The move targets a friendly character.

Players must retry their turn if they input an invalid move.

### Game State Display
After each turn, the 5x5 grid is displayed with all character positions. Character names are prefixed with the player's identifier and character type (e.g., `A-P1`, `B-H1`, `A-H2`).

### Winning the Game
The game ends when one player eliminates all of their opponent's characters. The winning player is announced, and players can choose to start a new game.





