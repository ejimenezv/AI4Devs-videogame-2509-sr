# Game Development Prompts - AI4Devs Assignment

This folder contains a structured set of prompts designed to guide you through creating a complete browser-based video game using Claude Code.

## Overview

The prompt system is organized into **8 specialized phases**, each handled by an expert AI persona:

1. **Game Concept Consultant** - Define your game idea
2. **Game Design Architect** - Create technical specifications
3. **Frontend Developer** - Build HTML/CSS structure
4. **Game Logic Engineer** - Implement game mechanics
5. **QA Tester** - Test and identify bugs
6. **Debug Specialist** - Fix issues
7. **Polish Specialist** - Add professional touches
8. **Documentation Specialist** - Create required documentation

## How to Use These Prompts

### Option 1: Master Orchestrator (Recommended)

The easiest way to use these prompts is through the **Master Orchestrator**, which automatically guides you through all phases in order.

**In Claude Code, use this prompt:**

```
I want to develop a browser-based video game following the structured process.

Please read and execute the master orchestrator prompt located at:
zombie-survival-EJV/prompts/00-master-orchestrator.md

This will guide me through all 8 phases of game development from concept to completion.
```

The orchestrator will:
- Load each prompt file in sequence
- Guide you through every phase
- Collect all artifacts for documentation
- Ensure you complete all assignment requirements
- Help you create the final pull request

### Option 2: Manual Phase-by-Phase

If you prefer more control, you can execute each prompt individually:

**Phase 1: Game Concept**
```
Read the prompt file: zombie-survival-EJV/prompts/01-game-concept-consultant.md

Execute this prompt to help me define my game concept.
```

**Phase 2: Game Design**
```
Read the prompt file: zombie-survival-EJV/prompts/02-game-design-architect.md

Using the game concept we created, execute this prompt to create detailed technical specifications.
```

**Phase 3: Frontend Development**
```
Read the prompt file: zombie-survival-EJV/prompts/03-frontend-developer.md

Using the game design document, execute this prompt to create the HTML/CSS structure.
```

**Phase 4: Game Logic**
```
Read the prompt file: zombie-survival-EJV/prompts/04-game-logic-engineer.md

Using the HTML structure, execute this prompt to implement the game logic.
```

**Phase 5: QA Testing**
```
Read the prompt file: zombie-survival-EJV/prompts/05-qa-tester.md

Execute this prompt to guide me through comprehensive testing of the game.
```

**Phase 6: Debugging** (if needed)
```
Read the prompt file: zombie-survival-EJV/prompts/06-debug-specialist.md

I found these bugs during testing: [list bugs]

Execute this prompt to help me fix them.
```

**Phase 7: Polish**
```
Read the prompt file: zombie-survival-EJV/prompts/07-polish-specialist.md

Execute this prompt to help me add professional polish to the game.
```

**Phase 8: Documentation**
```
Read the prompt file: zombie-survival-EJV/prompts/08-documentation-specialist.md

Execute this prompt to help me create all required documentation including prompts.md.
```

## File Structure

```
zombie-survival-EJV/
├── prompts/
│   ├── README.md                        # This file
│   ├── 00-master-orchestrator.md        # Master prompt that executes all phases
│   ├── 01-game-concept-consultant.md    # Phase 1: Game concept
│   ├── 02-game-design-architect.md      # Phase 2: Technical design
│   ├── 03-frontend-developer.md         # Phase 3: HTML/CSS/JS structure
│   ├── 04-game-logic-engineer.md        # Phase 4: Game logic implementation
│   ├── 05-qa-tester.md                  # Phase 5: Testing
│   ├── 06-debug-specialist.md           # Phase 6: Bug fixing
│   ├── 07-polish-specialist.md          # Phase 7: Polish and UX
│   └── 08-documentation-specialist.md   # Phase 8: Documentation
├── index.html                           # Your game (created during process)
└── prompts.md                           # Required documentation (created in Phase 8)
```

## What You'll Create

By following this process, you'll create:

### Required Deliverables (per assignment)
- ✅ `index.html` - Complete working game in a single HTML file
- ✅ `prompts.md` - Documentation of all prompts used and development process
- ✅ Pull request with game description

### Technical Requirements Met
- ✅ Single HTML file with inline CSS and JavaScript
- ✅ Vanilla JavaScript (no external libraries)
- ✅ Works in major browsers (Chrome, Firefox, Safari, Edge)
- ✅ Interactive gameplay with keyboard/mouse controls
- ✅ Clear win/lose conditions
- ✅ Score tracking
- ✅ Start and restart functionality

## Process Flow

```
START
  ↓
[01] Define Game Concept
  ↓ (Game idea + mechanics defined)
[02] Create Technical Design
  ↓ (Architecture + specifications)
[03] Build HTML/CSS Structure
  ↓ (Visual structure + styling)
[04] Implement Game Logic
  ↓ (Working game)
[05] Test the Game
  ↓ (Bug reports)
[06] Fix Bugs
  ↓ (Stable game)
[07] Add Polish
  ↓ (Professional game)
[08] Document Everything
  ↓ (Complete documentation)
SUBMIT PULL REQUEST
```

## Key Features of This System

### 🎯 Granular & Focused
Each prompt handles a specific aspect of development, making complex tasks manageable.

### 👥 Expert Personas
Each phase is handled by a specialized expert (consultant, architect, developer, etc.), providing domain-specific guidance.

### 📚 Educational
You'll learn game development principles, best practices, and professional workflows.

### ✅ Complete
The process ensures you meet all assignment requirements and create submission-ready work.

### 🔄 Iterative
You can loop back to previous phases if you need to make changes.

### 📝 Documentation-First
The system tracks all prompts and decisions, making the final documentation phase straightforward.

## Tips for Success

### 1. Follow the Order
The phases build on each other. Don't skip ahead.

### 2. Take Your Time
Quality over speed. A simple, polished game is better than a complex, buggy one.

### 3. Test Frequently
Don't wait until Phase 5 to test. Try your game after Phase 4 and whenever you make changes.

### 4. Save Everything
Keep track of the prompts you actually use, challenges you face, and decisions you make. You'll need this for `prompts.md`.

### 5. Ask Questions
If you're unsure about something, ask the AI for clarification, examples, or alternatives.

### 6. Start Simple
Choose a manageable game concept. You can always add features later.

### 7. Document as You Go
Make notes during development rather than trying to remember everything in Phase 8.

## Example Session Flow

Here's what a typical session looks like:

1. **Start**: Open Claude Code
2. **Load Orchestrator**: Use the master orchestrator prompt
3. **Phase 1**: Discuss game ideas, choose concept (10-15 min)
4. **Phase 2**: Review technical design, confirm approach (15-20 min)
5. **Phase 3**: Generate HTML/CSS structure, review visuals (15-20 min)
6. **Phase 4**: Implement game logic, test basic functionality (30-45 min)
7. **Phase 5**: Systematic testing, identify issues (15-20 min)
8. **Phase 6**: Fix bugs if found (10-30 min)
9. **Phase 7**: Add polish and improvements (20-30 min)
10. **Phase 8**: Create documentation, prepare PR (20-30 min)

**Total Time**: ~2-4 hours depending on game complexity

## Troubleshooting

### "The game isn't working"
- Go back to Phase 6 (Debug Specialist)
- Use browser DevTools console to check for errors
- Test in different browsers

### "I want to change my game concept"
- You can restart from Phase 1 at any time
- Or make incremental changes and re-execute later phases

### "The prompts are too complex"
- Use the Master Orchestrator - it manages everything for you
- Ask Claude Code to simplify or explain any confusing parts

### "I'm stuck on a phase"
- Ask for examples or alternatives
- Simplify your current objective
- Skip optional features and come back later

## Assignment Requirements Checklist

Before submitting, ensure you have:

- [ ] `index.html` - Single HTML file with your complete game
- [ ] `prompts.md` - Documentation of prompts used and development process
- [ ] Game works in Chrome, Firefox, and Edge (minimum)
- [ ] Game uses only vanilla HTML, CSS, and JavaScript
- [ ] Clear game instructions (in game or in documentation)
- [ ] Pull request with game description
- [ ] Game is interactive and playable
- [ ] No console errors or major bugs

## Support

If you encounter issues with the prompts themselves:

1. Check that you're reading the correct prompt file
2. Ensure you've completed previous phases
3. Try the Master Orchestrator instead of manual execution
4. Simplify your game concept if too complex

## Credits

- **Prompt System Design**: Created for AI4Devs assignment
- **AI Assistant**: Claude Code by Anthropic
- **Inspired By**: Snake game example in `snake-EHS` folder
- **Assignment**: AI4Devs video game final project

## License

These prompts are provided for educational purposes as part of the AI4Devs program.

---

**Ready to create your game? Start with the Master Orchestrator!** 🚀

```
Read and execute: zombie-survival-EJV/prompts/00-master-orchestrator.md
```

Good luck and have fun! 🎮
