# Claude Development Notes

This file contains important information and tips for working with the Lost Game project.

## Project Structure

### Root Files
- **README.md** - Comprehensive project overview with game features and controls
- **CHANGELOG.md** - Chronological list of all changes made to the project
- **CLAUDE.md** - This file - development notes and tips for AI assistance
- **BUGS.md** - Known issues and bugs to be addressed (currently clean)

### Game Files
- **lost.html** - Complete game implementation (1051 lines) - FULLY FUNCTIONAL
- **Lostalt.html** - Alternative/backup version (currently empty)

### Documentation Folder
- **Architecture.md** - Detailed technical architecture and implementation analysis
- **Security.md** - Comprehensive security analysis and recommendations
- **Product.md** - Complete product roadmap with current features and future plans

## Game Overview for Development

### Core Mechanics Understanding
The Lost Game is a sophisticated survival game with multiple interconnected systems:

1. **World System**: 140×60 procedurally generated map with terrain types
2. **Time System**: Real-time progression with 15-minute increments
3. **Resource System**: Wood, stone, food with collection and consumption
4. **Fire System**: Dynamic spreading based on terrain with realistic behavior
5. **Survivor System**: 15 AI entities with behavior patterns and safety requirements
6. **Building System**: 5 structure types with resource costs and placement rules
7. **Station System**: 5 Dharma stations with progressive unlocking mechanics
8. **Objective System**: 14 sequential goals with authentic Lost TV show quotes

### Key Code Sections (`lost.html`)

**Game Initialization**
- Lines 116-141: Global variables and game state
- Lines 162-229: World generation (`genMap()`)
- Lines 922-970: Main game initialization and event handlers

**Core Game Loop**
- Lines 241-291: Main update function with rendering
- Lines 584-605: Time advancement and system updates
- Lines 973-984: Real-time interval loop

**Player Movement & Actions**
- Lines 304-352: Movement logic with boundary checking
- Lines 354-416: Action handling (collect, interact, build)
- Lines 924-968: Keyboard input event handling

**AI & Simulation Systems**
- Lines 607-650: Fire spreading algorithm
- Lines 699-767: Survivor AI with fire avoidance
- Lines 769-792: Animal movement and trap interaction

**Building & Construction**
- Lines 987-1046: All building action functions
- Lines 418-481: Dharma station activation system

### Development Guidelines

#### Code Modification Best Practices
1. **Test Movement First**: Any changes should preserve basic arrow key movement
2. **Preserve Game Balance**: Resource costs and timings are carefully balanced
3. **Maintain AI Behavior**: Survivor and animal logic is complex - modify carefully
4. **Fire System Integrity**: Fire spreading is performance-critical - test thoroughly
5. **State Consistency**: All game state changes should maintain internal consistency

#### Common Development Tasks

**Adding New Building Types**
1. Add new key handler in event listener (lines 924-968)
2. Create action function following existing patterns (lines 987-1046)
3. Add terrain symbol and CSS styling (lines 55-68)
4. Update legend display (lines 76-99)

**Modifying Game Balance**
1. Resource costs: Check all `wood--`, `stone--`, `food--` operations
2. Time progression: Modify `advanceTime()` function (lines 584-605)
3. Fire behavior: Adjust spread probabilities in `handleFireSpreading()` (lines 607-650)
4. Survivor behavior: Modify movement logic in `updateSurvivors()` (lines 699-767)

**Adding New Objectives**
1. Add to `focuses` array (lines 145-160)
2. Implement check function logic
3. Add authentic Lost TV show quote
4. Test objective progression sequence

#### Performance Considerations
- **Large Arrays**: survivors (15), animals (30), fires (variable), camps, traps
- **Heavy Loops**: Fire spreading, survivor AI, rendering loop
- **DOM Updates**: Main rendering function updates entire game area
- **Memory Management**: Entity cleanup prevents accumulation

#### Testing Checklist
- [ ] Player movement in all directions
- [ ] Resource collection from trees and rocks
- [ ] Building placement and functionality
- [ ] Fire spreading and survivor reactions
- [ ] Dharma station activation sequence
- [ ] Win/lose conditions
- [ ] Score calculation accuracy
- [ ] Time progression and day/night cycles

### Code Quality Notes

#### Strengths
- Well-structured function organization
- Consistent naming conventions
- Comprehensive game mechanics
- Good error handling with try-catch blocks
- Realistic simulation systems

#### Areas for Improvement
- Some functions are quite large (could be refactored)
- Magic numbers could be converted to named constants
- Save/load functionality not implemented
- Limited accessibility features

### Development Workflow

#### Making Changes
1. **Read relevant code sections first** - Game is complex, understand before modifying
2. **Test in browser immediately** - Visual feedback is crucial
3. **Check console for errors** - Game has error handling but watch for issues
4. **Test all related systems** - Changes often have cascade effects
5. **Update documentation** - Keep Architecture.md current with changes

#### Debugging Tips
1. **Use browser console** - Game logs useful debugging information
2. **Check game state variables** - `px`, `py`, `wood`, `stone`, `food`, etc.
3. **Monitor arrays** - `surv`, `anim`, `fires`, `camps`, `traps`
4. **Watch rendering loop** - Performance issues usually show here
5. **Test edge cases** - Boundary conditions, resource depletion, etc.

### Integration Notes

#### File Dependencies
- **Single File**: Everything is in `lost.html` - no external dependencies
- **CSS Embedded**: All styling is inline in `<style>` section
- **JavaScript Embedded**: All game logic is inline in `<script>` section
- **No Build Process**: Direct file editing and browser refresh

#### Browser Compatibility
- Modern browsers only (ES6+ features used)
- Tested on Chrome, Firefox, Safari, Edge
- Mobile support limited (keyboard-only controls)
- No polyfills included

### Future Development Considerations

#### High-Priority Enhancements
1. **Save/Load System**: Use localStorage for game persistence
2. **Mobile Support**: Touch controls and responsive design
3. **Audio System**: Background music and sound effects
4. **Accessibility**: Screen reader support and keyboard navigation improvements

#### Code Refactoring Opportunities
1. **Constants File**: Extract magic numbers to named constants
2. **Module Organization**: Split large functions into smaller, focused functions
3. **Configuration Object**: Centralize game settings and balance values
4. **Event System**: Implement observer pattern for better decoupling

## Working with the Codebase

- **Always test changes immediately** - Game complexity means small changes can have big effects
- **Update CHANGELOG.md** when making significant changes
- **Document architectural decisions** in documentation/Architecture.md
- **Track any new bugs** in BUGS.md
- **Consider security implications** and update documentation/Security.md
- **Update Product.md roadmap** when adding new features

## Quick Reference

### Key Functions
- `genMap()` - World generation
- `update()` - Main rendering loop
- `move(dx, dy)` - Player movement
- `action()` - Player interaction
- `advanceTime()` - Time progression
- `activateStation(station)` - Dharma station logic

### Key Variables
- `px, py` - Player position
- `wood, stone, food` - Resources
- `day, hr, min` - Time tracking
- `score` - Player score (starts at 100)
- `hatchCountdown` - Critical timing mechanic
- `surv[]` - Survivor array
- `m[][]` - Map data (140×60)

### Key Game States
- `hatchFound, hatchOpen` - Hatch progression
- `carryingCorpse` - Player carrying state
- `freighterSignaled, helicopterReached` - End-game states
- `survivorsRescued` - Victory condition tracking