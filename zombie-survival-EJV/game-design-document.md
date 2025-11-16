# Game Design Document: Zombie Survival

## Technical Overview
- **Rendering Method**: Canvas API (better performance for multiple moving entities)
- **Game Loop**: `requestAnimationFrame` (smooth 60 FPS rendering)
- **Frame Rate**: 60 FPS target
- **Play Area**: 800x600 pixels (centered on page)
- **Coordinate System**: (0,0) at top-left of canvas

## Game Mechanics

### Player System
- **Movement**: Free 8-directional movement (WASD or Arrow Keys)
- **Speed**: 3 pixels per frame (180 pixels/second at 60 FPS)
- **Controls**:
  - W/↑: Move up
  - A/←: Move left
  - S/↓: Move down
  - D/→: Move right
  - Mouse position: Aim direction
  - Left mouse click: Shoot
- **Starting Position**: Center of canvas (400, 300)
- **Size**: 20x20 pixel square
- **Health**: 1 HP (instant death on collision)
- **Attributes**:
  ```javascript
  {
    x: 400,
    y: 300,
    width: 20,
    height: 20,
    speed: 3,
    alive: true
  }
  ```

### Weapon System (Pistol)
- **Fire Rate**: 0.5 second cooldown between shots
- **Bullet Speed**: 8 pixels per frame (480 pixels/second)
- **Bullet Size**: 5x5 pixel square
- **Max Bullets**: 5 bullets on screen simultaneously
- **Bullet Lifetime**: Despawn when off-screen
- **Direction**: Fired toward mouse cursor position at time of click
- **Bullet Structure**:
  ```javascript
  {
    x: number,
    y: number,
    dx: number, // velocity x
    dy: number, // velocity y
    width: 5,
    height: 5
  }
  ```

### Enemy System (Zombies)
- **Type**: Single zombie type (green shambling zombie)
- **Behavior**: Always move directly toward player's current position
- **Speed**: 1.5 pixels per frame (90 pixels/second - slower than player)
- **Size**: 20x20 pixel square
- **Spawn Location**: Random position just outside visible canvas area
- **Spawn Logic**:
  - **Initial Rate**: 1 zombie every 3 seconds
  - **Difficulty Scaling**: Every 60 seconds (1 minute), decrease spawn interval by 0.2 seconds
  - **Cap**: Minimum spawn interval of 0.5 seconds (2 zombies/second max)
- **Health**: 1 HP (one bullet kills)
- **Damage**: Instant death on contact with player
- **Zombie Structure**:
  ```javascript
  {
    x: number,
    y: number,
    width: 20,
    height: 20,
    speed: 1.5
  }
  ```

### Scoring System
- **Time Survived**: +1 point per second
- **Zombies Killed**: +10 points per zombie eliminated
- **Total Score**: Time points + Kill points
- **High Score**: Stored in localStorage, persists between sessions
- **Display**: Real-time score in HUD

### Collision Detection
- **Method**: Axis-Aligned Bounding Box (AABB) rectangle intersection
- **Player vs. Zombies**: Game Over (instant death)
- **Bullets vs. Zombies**: Zombie destroyed, bullet removed, +10 score
- **Entities vs. Boundaries**:
  - Player: Cannot move outside canvas bounds (clamped)
  - Zombies: Continue moving (will enter from off-screen)
  - Bullets: Despawn when off-screen

### Game States
1. **START**:
   - Display title, instructions, high score
   - "Click to Start" message
   - No game objects active

2. **PLAYING**:
   - Active gameplay
   - All systems running
   - Score counting

3. **GAME_OVER**:
   - Display final score, high score
   - "Click to Restart" message
   - Game loop stopped

## Data Structures

### Player Object
```javascript
const player = {
  x: 400,
  y: 300,
  width: 20,
  height: 20,
  speed: 3,
  alive: true
};
```

### Weapon State
```javascript
const weapon = {
  lastShotTime: 0,
  cooldown: 500, // milliseconds
  bulletSpeed: 8,
  maxBullets: 5
};
```

### Arrays
```javascript
let bullets = [];    // Active bullets
let zombies = [];    // Active zombies
```

### Game State Variables
```javascript
let gameState = 'START'; // 'START' | 'PLAYING' | 'GAME_OVER'
let score = 0;
let zombiesKilled = 0;
let survivalTime = 0; // in seconds
let highScore = 0;
let lastScoreUpdate = 0;
let lastZombieSpawn = 0;
let zombieSpawnInterval = 3000; // milliseconds, decreases over time
let difficultyTimer = 0;
```

### Input State
```javascript
const keys = {
  w: false,
  a: false,
  s: false,
  d: false,
  ArrowUp: false,
  ArrowLeft: false,
  ArrowDown: false,
  ArrowRight: false
};

const mouse = {
  x: 400,
  y: 300
};
```

### Game Configuration Constants
```javascript
const CONFIG = {
  CANVAS_WIDTH: 800,
  CANVAS_HEIGHT: 600,
  PLAYER_SIZE: 20,
  PLAYER_SPEED: 3,
  ZOMBIE_SIZE: 20,
  ZOMBIE_SPEED: 1.5,
  BULLET_SIZE: 5,
  BULLET_SPEED: 8,
  FIRE_COOLDOWN: 500,
  MAX_BULLETS: 5,
  INITIAL_SPAWN_INTERVAL: 3000,
  SPAWN_DECREASE_RATE: 200, // per minute
  MIN_SPAWN_INTERVAL: 500,
  DIFFICULTY_INCREASE_INTERVAL: 60000, // 1 minute
  POINTS_PER_SECOND: 1,
  POINTS_PER_KILL: 10
};
```

## User Interface Specification

### Layout Structure
```
┌─────────────────────────────────────┐
│         Game Title (h1)             │
├─────────────────────────────────────┤
│  HUD: Score | Kills | Time | High   │
├─────────────────────────────────────┤
│                                     │
│         Canvas (800x600)            │
│         [Game Area]                 │
│                                     │
├─────────────────────────────────────┤
│     Instructions / Status Text      │
└─────────────────────────────────────┘
```

### Canvas Elements
- **Background**: Dark gray (#2a2a2a)
- **Player**: Blue square (#3498db) facing mouse cursor
- **Zombies**: Green squares (#27ae60)
- **Bullets**: Yellow squares (#f1c40f)
- **Grid/Borders**: Optional subtle grid lines

### HUD Elements
- **Score**: "Score: [number]"
- **Kills**: "Kills: [number]"
- **Time**: "Time: [seconds]s"
- **High Score**: "High: [number]"
- Display at top of canvas or above it

### Typography
- **Font**: 'Arial', sans-serif
- **Title**: 32px, bold, white
- **HUD**: 16px, white
- **Instructions**: 14px, light gray

### Color Palette
- **Primary (Player)**: #3498db (blue)
- **Enemy (Zombie)**: #27ae60 (green)
- **Bullet**: #f1c40f (yellow)
- **Background**: #2a2a2a (dark gray)
- **Text**: #ffffff (white)
- **UI Background**: #1a1a1a (darker gray)
- **Accent**: #e74c3c (red for game over)

## Game Flow Diagram

```
[Page Load]
     ↓
[Initialize Canvas & Variables]
     ↓
[START State]
 - Show title & instructions
 - Display high score
 - Wait for click
     ↓
  [User Clicks]
     ↓
[Initialize Game]
 - Reset score, arrays
 - Spawn player at center
 - gameState = 'PLAYING'
     ↓
[Game Loop] ←──────────────┐
     ↓                     │
[Handle Input]             │
 - Update keys object      │
 - Track mouse position    │
     ↓                     │
[Update Game State]        │
 - Move player             │
 - Move bullets            │
 - Move zombies            │
 - Spawn new zombies       │
 - Update timers           │
     ↓                     │
[Check Collisions]         │
 - Bullets vs Zombies      │
 - Player vs Zombies       │
     ↓                     │
[Increase Difficulty]      │
 - Reduce spawn interval   │
     ↓                     │
[Update Score]             │
 - Time survived           │
     ↓                     │
[Render Frame]             │
 - Clear canvas            │
 - Draw all entities       │
 - Draw HUD                │
     ↓                     │
[Player Alive?] ───────────┘
     ↓ (No)
[GAME_OVER State]
 - Show final score
 - Update high score
 - Show "Click to Restart"
     ↓
  [User Clicks]
     ↓
[Return to START State]
```

## Detailed Game Logic

### Initialization
```javascript
// On page load:
1. Get canvas context
2. Load high score from localStorage
3. Set gameState = 'START'
4. Add event listeners (keydown, keyup, mousemove, click)
5. Start render loop with requestAnimationFrame
```

### Player Movement
```javascript
// Each frame when PLAYING:
1. Check keys object for active directions
2. Calculate dx and dy based on pressed keys
3. Normalize diagonal movement (multiply by 0.707)
4. Update player.x and player.y
5. Clamp position to canvas boundaries
```

### Shooting Mechanic
```javascript
// On mouse click when PLAYING:
1. Check if enough time since last shot (cooldown)
2. Check if bullets.length < MAX_BULLETS
3. Calculate angle from player to mouse cursor
4. Create bullet object with velocity components
5. Add to bullets array
6. Update lastShotTime
```

### Zombie Spawning
```javascript
// Each frame when PLAYING:
1. Check if time since lastZombieSpawn > zombieSpawnInterval
2. Choose random edge (top, right, bottom, left)
3. Generate random position along that edge (just off-screen)
4. Create zombie object
5. Add to zombies array
6. Update lastZombieSpawn timestamp
```

### Zombie AI
```javascript
// Each frame for each zombie:
1. Calculate angle from zombie to player
2. Set zombie velocity toward player
3. Move zombie by ZOMBIE_SPEED
4. (No pathfinding - simple direct pursuit)
```

### Collision Detection Algorithm
```javascript
function checkCollision(rect1, rect2) {
  return rect1.x < rect2.x + rect2.width &&
         rect1.x + rect1.width > rect2.x &&
         rect1.y < rect2.y + rect2.height &&
         rect1.y + rect1.height > rect2.y;
}
```

### Difficulty Scaling
```javascript
// Every 60 seconds:
1. Decrease zombieSpawnInterval by 200ms
2. Enforce minimum of 500ms (cap)
3. Increment difficulty level counter
```

### Score Calculation
```javascript
// Every second (1000ms elapsed):
1. Add 1 to score (time bonus)
2. Increment survivalTime

// On zombie kill:
1. Add 10 to score
2. Increment zombiesKilled
```

## File Structure

Single HTML file structure:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Zombie Survival</title>
  <style>
    /* All CSS here */
  </style>
</head>
<body>
  <div id="game-container">
    <h1>Zombie Survival</h1>
    <div id="hud">
      <!-- Score, kills, time, high score -->
    </div>
    <canvas id="gameCanvas" width="800" height="600"></canvas>
    <div id="instructions">
      <!-- Controls and status messages -->
    </div>
  </div>

  <script>
    /* All JavaScript here */
  </script>
</body>
</html>
```

## Event Handling

### Keyboard Events
```javascript
// keydown event:
- Set keys[event.key] = true
- Prevent default for arrow keys (stop page scroll)

// keyup event:
- Set keys[event.key] = false
```

### Mouse Events
```javascript
// mousemove event:
- Update mouse.x and mouse.y relative to canvas position
- Account for canvas offset on page

// click event:
- If gameState === 'START': start game
- If gameState === 'PLAYING': attempt to shoot
- If gameState === 'GAME_OVER': restart game
```

## Performance Considerations

### Entity Cleanup
- Remove bullets when they leave canvas bounds
- Remove destroyed zombies immediately
- Cap zombie array size if needed (e.g., max 100 zombies)

### Optimization Strategies
- Use `requestAnimationFrame` for efficient rendering
- Calculate angles/distances only when needed
- Simple AABB collision (fast for small entity counts)
- No complex physics or particle systems in MVP

### Browser Compatibility
- Canvas API supported in all modern browsers
- `requestAnimationFrame` widely supported
- No ES6+ features that require transpilation
- localStorage supported universally

## Edge Cases to Handle

### Input Edge Cases
- Multiple simultaneous key presses (diagonal movement)
- Rapid clicking (fire rate cooldown prevents spam)
- Mouse outside canvas (clamp bullet direction)
- Keys held during game state transitions (reset keys object)

### Gameplay Edge Cases
- Player cornered by zombies (game over, no escape needed)
- Bullet hits multiple zombies (remove all hit zombies)
- Zombie spawns on top of player (unlikely with off-screen spawn)
- Score overflow (unlikely in reasonable play time)

### State Management
- Restart game without page reload (clear all arrays, reset variables)
- Update high score only if current score beats it
- Prevent actions in wrong game state (e.g., shooting in START state)

## Testing Checklist

### Functional Tests
- [ ] Player moves in all 8 directions
- [ ] Player cannot move outside canvas
- [ ] Mouse aiming works correctly
- [ ] Bullets fire toward cursor
- [ ] Fire rate cooldown works
- [ ] Max bullet limit enforced
- [ ] Zombies spawn off-screen
- [ ] Zombies move toward player
- [ ] Collision detection accurate
- [ ] Score increases with time
- [ ] Score increases on kills
- [ ] Difficulty increases over time
- [ ] Game over on collision
- [ ] Restart works properly
- [ ] High score saves and loads

### Visual Tests
- [ ] All entities render correctly
- [ ] Canvas centered on page
- [ ] HUD displays accurate info
- [ ] Colors match palette
- [ ] No flickering or tearing

### Browser Tests
- [ ] Chrome
- [ ] Firefox
- [ ] Safari
- [ ] Edge

---

## Summary

This design provides:
- ✅ Clear technical specifications for all systems
- ✅ Concrete data structures and constants
- ✅ Detailed game flow and state management
- ✅ Canvas-based rendering for smooth performance
- ✅ Scalable difficulty with reasonable cap
- ✅ Simple but complete MVP scope
- ✅ All mechanics defined and ready to implement

**Ready for Phase 3: Frontend Developer**

The next phase will create the HTML structure, CSS styling, and JavaScript scaffolding based on this design document.
