# Game Concept: Zombie Survival

## Overview
- **Genre**: Top-down Shooter / Survival
- **Tagline**: Survive the zombie apocalypse in an endless battle for survival

## Core Gameplay
- **Player Control**:
  - Movement: WASD or Arrow Keys (top-down 2D movement)
  - Aiming: Mouse cursor position
  - Shooting: Left mouse click (pistol)
- **Main Mechanic**: Dodge and shoot zombies that spawn around the player and chase them down
- **Objective**: Survive as long as possible with increasing difficulty
- **Challenge**: Zombies spawn faster over time (increased spawn rate every minute)

## Game Elements
- **Player/Character**: Single survivor character (person with a pistol)
- **Enemies/Obstacles**: Zombies that spawn randomly outside the screen and move toward the player
- **Collectibles/Power-ups**: None (MVP scope)
- **Environment**: Empty open field (no obstacles or terrain)

## Visual Style
- **Theme**: Zombie apocalypse survival
- **Color Scheme**: To be determined in design phase (suggest: dark/gritty tones)
- **Art Style**: Simple DOM-based elements styled with CSS

## Technical Scope
- Single HTML file implementation
- Keyboard (WASD/Arrows) + Mouse controls
- DOM-based rendering (HTML elements positioned with CSS)
- Estimated complexity: **Medium**

## Game Loop
1. Player spawns in center of play area
2. Zombies spawn randomly outside visible screen area
3. Zombies move toward player position
4. Player moves with keyboard, aims with mouse, shoots with click
5. Bullets travel in direction of mouse cursor when fired
6. Zombies die when hit by bullets
7. Spawn rate increases every minute
8. Game ends when player is caught by a zombie
9. Score based on survival time and/or zombies killed

## Win/Lose Conditions
- **Win**: N/A (endless survival)
- **Lose**: Player collides with a zombie
- **Score**: Time survived and/or number of zombies eliminated

## Constraints Met
✅ Single HTML file with inline CSS and JavaScript
✅ Vanilla JavaScript (no libraries)
✅ Works in major browsers
✅ Keyboard + Mouse controls
✅ Medium complexity - achievable scope

---

**Status**: Concept approved and ready for technical design phase
