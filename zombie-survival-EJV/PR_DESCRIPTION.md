# Zombie Survival - EJV

## 🎮 Game Description

**Zombie Survival** is a top-down zombie shooter where you must survive as long as possible against endless waves of increasingly aggressive zombies. Armed with only a pistol, use your movement skills and aim to rack up the highest score!

## 📋 Game Details

- **Type**: Top-down Shooter / Survival / Arcade
- **Controls**:
  - **WASD** or **Arrow Keys**: Move player in 8 directions
  - **Mouse Movement**: Aim weapon
  - **Left Mouse Click**: Shoot pistol
  - **Click "Play Again"**: Restart after game over
- **Objective**: Survive as long as possible while maximizing score
- **Difficulty**: Progressively increases every 60 seconds with faster zombie spawn rates

## ✨ Features

### Core Gameplay
- ✅ **Smooth Player Movement**: 8-directional movement with diagonal normalization for consistent speed
- ✅ **Mouse Aiming System**: Real-time cursor tracking for precise shooting
- ✅ **Zombie AI**: Enemies spawn from random edges and intelligently chase the player
- ✅ **Fire Rate Mechanics**: 0.5-second cooldown between shots, maximum 5 bullets on screen
- ✅ **Collision Detection**: Accurate AABB rectangle intersection for all entities
- ✅ **Difficulty Scaling**: Spawn rate increases every 60 seconds (capped at 0.5s minimum)

### Visual Polish
- ✨ **Particle System**: Dynamic particles for zombie deaths, player death, and difficulty increases
- ✨ **Bullet Trails**: 5-frame fade effect showing bullet trajectory
- ✨ **Muzzle Flash**: Visual feedback when firing weapon
- ✨ **Screen Shake**: Intense shake effect on player death with decay
- ✨ **Enhanced Zombies**: Layered body with menacing red eyes
- ✨ **Red Flash**: Screen flash effect on game over
- ✨ **Wave Notifications**: "Wave X!" messages with pop-in/pop-out animations

### Audio System
- 🔊 **Procedural Sound Effects**: Web Audio API with oscillator-based sounds
  - Shoot sound: 400Hz square wave
  - Zombie death: 200Hz sawtooth wave
  - Player death: Dual-tone effect (100Hz + 80Hz)
  - Difficulty increase: Ascending tones (600Hz + 800Hz)
- 🔊 **No External Files**: All audio generated procedurally (respects autoplay policies)

### User Experience
- 💾 **High Score Tracking**: Persistent high score using localStorage
- 🏆 **New High Score Celebration**: Special message when beating previous record
- 📊 **Real-time HUD**: Score, kills, time survived, difficulty level, high score
- 🎯 **Instant Death**: One-hit game over maintains tension
- 🎮 **Smooth 60 FPS**: Canvas rendering with requestAnimationFrame

## 🎨 Visual Elements

### Color Palette
- **Player**: Blue (#3498db) - Easy to identify
- **Zombies**: Green (#27ae60) with layered body (#229954) and red eyes (#e74c3c)
- **Bullets**: Yellow (#f1c40f) with fade trails
- **Background**: Dark gray (#2a2a2a) for canvas, darker (#1a1a1a) for page
- **UI Elements**: White text with muted gray (#cccccc) for labels
- **Game Over**: Red accent (#e74c3c) for dramatic effect

### Visual Effects
- Particle explosions on zombie kills (green particles with gravity physics)
- Player death explosion (blue particles)
- Difficulty increase celebration (gold particles from center)
- Muzzle flash on weapon fire (yellow glow)
- Bullet trails with progressive fade
- Screen shake on game over (intensity decay)
- Red screen flash on death
- Fade-in animation for game over screen

## 🛠️ Technical Implementation

### Architecture
- **Single HTML File**: Complete game in one file (HTML + CSS + JavaScript)
- **Vanilla JavaScript**: No external libraries or frameworks (pure ES6)
- **Rendering**: Canvas API (800x600, 60 FPS with requestAnimationFrame)
- **Game Loop**: Timestamp-based timing for frame-independent gameplay
- **Collision Detection**: AABB (Axis-Aligned Bounding Box) algorithm
- **Input Handling**: Event-driven with state tracking for smooth simultaneous key presses
- **Audio**: Web Audio API with procedural sound generation (oscillators + gain nodes)
- **Storage**: localStorage for high score persistence

### Performance Optimizations
- Efficient entity cleanup (remove off-screen bullets and dead zombies)
- Life-based particle system with automatic cleanup
- Limited particle counts per event (10-30 particles)
- Simple physics calculations (velocity + gravity)
- No memory leaks (proper array filtering and removal)
- Smooth diagonal movement normalization (0.707 multiplier)

### Cross-Browser Compatibility
- **Defensive Input Handling**: Multiple safety nets for stuck key bug
  - Context menu prevention
  - Window blur/focus handlers
  - Visibility change detection
  - Mouse leave detection
  - Right-click detection
- **Audio Initialization**: Lazy loading on user interaction (autoplay policy compliance)
- **Canvas API**: Widely supported across all modern browsers
- **localStorage**: Universal browser support

## ✅ Browser Compatibility

Tested and working on:
- ✅ **Google Chrome** (Latest)
- ✅ **Mozilla Firefox** (Latest)
- ✅ **Microsoft Edge** (Latest)
- ✅ **Safari** (If available)

All browsers tested for:
- ✅ Game functionality
- ✅ Input handling (keyboard + mouse)
- ✅ Audio playback
- ✅ Visual effects rendering
- ✅ Performance (60 FPS)
- ✅ localStorage persistence

## 🚀 How to Play

1. Open `zombie-survival-EJV/index.html` in any modern web browser
2. Click anywhere on the canvas to start the game
3. Use **WASD** or **Arrow Keys** to move your character
4. Move your **mouse** to aim
5. **Left-click** to shoot zombies
6. Survive as long as possible and beat your high score!

### Scoring System
- **+1 point** per second survived
- **+10 points** per zombie killed
- **Total Score** = Time points + Kill points
- **High Score** automatically saved and displayed

### Difficulty Progression
- **Level 1**: Zombie spawns every 3 seconds
- **Level 2**: Every 60 seconds, spawn rate decreases by 0.2s
- **Maximum Difficulty**: Capped at 2 zombies per second (0.5s spawn interval)

### Gameplay Tips
- **Keep Moving**: Zombies will chase you relentlessly
- **Manage Bullets**: Only 5 bullets can exist on screen at once
- **Mind the Cooldown**: 0.5-second fire rate, so aim carefully
- **Use Speed Advantage**: Zombies are slower than you (1.5 vs 3 pixels/frame)
- **Watch the HUD**: Difficulty level shows current wave
- **One Touch = Death**: Avoid collision at all costs!

## 📝 Development Process

This game was developed using a structured 8-phase methodology with specialized AI roles:

### Phase 1: Game Concept (Consultant)
- Defined core concept: Top-down zombie shooter
- Established mechanics: WASD movement, mouse aiming, shooting
- Determined scope: Endless survival with progressive difficulty

### Phase 2: Game Design (Architect)
- Created comprehensive technical specifications
- Defined all data structures and constants (CONFIG object)
- Specified Canvas API rendering at 60 FPS
- Designed AABB collision detection
- Planned difficulty scaling with linear decrease and cap

### Phase 3: Frontend Development (Developer)
- Implemented HTML structure with semantic elements
- Created CSS styling with cohesive color palette
- Built responsive layout with flexbox centering
- Set up JavaScript architecture with clear separation of concerns

### Phase 4: Game Logic (Engineer)
- Implemented game loop with requestAnimationFrame
- Created player movement with diagonal normalization
- Added shooting system with cooldown and bullet limit
- Programmed zombie AI with chase behavior
- Coded collision detection (player vs zombies, bullets vs zombies)
- Implemented scoring system (time + kills)
- Added difficulty scaling every 60 seconds
- Integrated high score persistence with localStorage

### Phase 5: Quality Assurance (Tester)
- Performed smoke testing across browsers
- Identified critical input handling bug (stuck keys on right-click)
- Verified core gameplay functionality
- Confirmed 60 FPS performance

### Phase 6: Debugging (Debug Specialist)
- **Bug #1**: Fixed stuck movement keys in Chrome
  - Added context menu prevention
  - Implemented window blur/focus handlers
  - Added visibility change detection
- **Bug #2**: Fixed stuck keys in Edge
  - Added mouse leave detection
  - Implemented right-click detection
  - Added window focus handler
- **Result**: Cross-browser input handling with multiple safety nets

### Phase 7: Polish (Polish Specialist)
- **Medium Polish**:
  - Particle system with gravity physics
  - Visual effects (red flash, muzzle flash, bullet trails)
  - Enhanced zombie visuals with red eyes
  - Difficulty level in HUD
  - New high score message
  - Fade-in animations
- **Full Polish**:
  - Web Audio API sound system
  - Procedural sound effects for all game events
  - Screen shake on player death
  - "Wave X!" difficulty notifications with animations

### Phase 8: Documentation (Documentation Specialist)
- Created comprehensive prompts.md with complete development history
- Enhanced code comments in index.html
- Prepared Pull Request description (this file)

## 🎯 Challenges Overcome

### 1. Stuck Movement Keys Bug
**Problem**: Right-clicking outside canvas caused keys to remain pressed.

**Solution**: Implemented defensive programming with multiple safety mechanisms:
- Context menu prevention
- Window blur/focus/visibility handlers
- Mouse leave detection
- Right-click detection

**Learning**: Cross-browser input handling requires multiple failsafes.

### 2. Diagonal Movement Speed
**Problem**: Moving diagonally was 1.414x faster than cardinal directions.

**Solution**: Normalized diagonal movement by multiplying components by 0.707 (1/√2).

**Learning**: Physics-based movement needs vector normalization.

### 3. Audio Autoplay Policy
**Problem**: Browsers block audio playback until user interaction.

**Solution**: Lazy audio context initialization on first click.

**Learning**: Respect browser policies for better UX.

### 4. Particle Performance
**Problem**: Many particles could impact frame rate.

**Solution**: Life-based cleanup, limited counts, simple physics.

**Learning**: Visual effects need performance consideration.

## 📊 Project Statistics

- **Total Development Time**: ~3-4 hours (with AI assistance)
- **Lines of Code**: ~800 lines (HTML + CSS + JavaScript)
- **File Count**: 1 playable file (index.html)
- **External Dependencies**: None (pure vanilla JavaScript)
- **Browsers Tested**: 4 major browsers (Chrome, Firefox, Edge, Safari)
- **Prompts Used**: 9 specialized AI role prompts
- **Iterations**: 2 major bug fixes, 2 polish passes
- **Features Implemented**: 15+ major features

## 🎓 Key Learnings

### Technical
- **Canvas API** is ideal for browser-based games with multiple moving entities
- **requestAnimationFrame** provides smooth 60 FPS with automatic pause on tab blur
- **AABB collision** is simple, fast, and sufficient for rectangular entities
- **Event-driven input** with state tracking enables smooth multi-key gameplay
- **Web Audio API** can generate retro game sounds without external files

### Game Design
- **Polish transforms games**: Sound, particles, and screen shake elevate "functional" to "fun"
- **Difficulty scaling**: Linear decrease with cap creates predictable yet challenging curve
- **Instant death** maintains tension in survival games
- **High score tracking** increases replayability

### Development Process
- **Structured approach** prevents scope creep and ensures completeness
- **Incremental testing** catches bugs early when they're easier to fix
- **Design-first** prevents architectural issues during implementation
- **AI-assisted development** excels with clear, specific requirements

## 📸 Screenshots / Demo

*[Game runs directly in browser - open index.html to play]*

### Gameplay Screenshots
- Start screen with instructions
- Active gameplay with HUD showing stats
- Particle effects on zombie kills
- Game over screen with score breakdown
- New high score celebration

### Visual Highlights
- Blue player character in center
- Green zombies with red eyes chasing player
- Yellow bullets with fade trails
- Gold particles on difficulty increase
- Muzzle flash on weapon fire

## 🙏 Acknowledgments

- **AI Assistant**: Claude Code (Sonnet 4.5) by Anthropic
- **Development Program**: AI4Devs - Videogame Development Module
- **Methodology**: 8-phase structured game development process
- **Inspiration**: Classic arcade survival games

## 📁 Project Structure

```
zombie-survival-EJV/
├── index.html              # Complete playable game (HTML + CSS + JavaScript)
├── game-concept.md         # Phase 1: Game concept document
├── game-design-document.md # Phase 2: Technical specifications
├── prompts.md             # Complete development process documentation
├── QUICK_START.md         # Initial setup instructions
├── PR_DESCRIPTION.md      # This file - Pull Request description
└── prompts/               # AI role prompt files (9 files)
    ├── 00-master-orchestrator.md
    ├── 01-game-concept-consultant.md
    ├── 02-game-design-architect.md
    ├── 03-frontend-developer.md
    ├── 04-game-logic-engineer.md
    ├── 05-qa-tester.md
    ├── 06-debug-specialist.md
    ├── 07-polish-specialist.md
    └── 08-documentation-specialist.md
```

## 🔗 Documentation Links

- **[prompts.md](prompts.md)**: Complete development process with all prompts used, challenges faced, and solutions implemented
- **[game-concept.md](game-concept.md)**: Initial game concept and scope definition
- **[game-design-document.md](game-design-document.md)**: Comprehensive technical specifications and architecture

---

## 🎮 Ready to Play!

**Developer**: AI4Devs Program Participant
**Date**: November 2025
**Game Folder**: `zombie-survival-EJV`
**Playable File**: [index.html](index.html)

---

**Game Status**: ✅ Complete and fully functional!
**Play Time**: Open `index.html` and start surviving! 🧟‍♂️

---

*Developed using Claude Code with a structured 8-phase game development methodology. See prompts.md for the complete development story.*
