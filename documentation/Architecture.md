# Architecture Overview

This document describes the technical architecture of the Lost Game.

## Overview

The Lost Game is a sophisticated browser-based survival game built using vanilla HTML5, CSS3, and JavaScript. The entire game runs client-side with no server dependencies, featuring a complete game engine with real-time mechanics, dynamic world simulation, and complex state management.

## Technology Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript (ES6+)
- **Rendering**: DOM manipulation with CSS classes for styling
- **Storage**: Browser memory (no persistence)
- **Deployment**: Static web hosting
- **Browser Support**: Modern browsers (Chrome, Firefox, Safari, Edge)

## Application Structure

```
lost-game/
├── lost.html           # Complete game implementation (1051 lines)
├── Lostalt.html       # Alternative/backup version
├── documentation/     # Technical documentation
├── README.md          # Project overview
├── CHANGELOG.md       # Version history
├── CLAUDE.md          # Development notes
└── BUGS.md           # Issue tracking
```

## Core Components

### 1. Game Engine (`lost.html:115-984`)

**World Management**
- 140×60 tile-based world with procedural generation
- Dynamic fog of war system with visibility tracking
- Real-time map updates with color-coded terrain types

**State Management**
- Global game state variables (resources, time, player position)
- Multiple entity arrays (survivors, animals, fires, camps, traps)
- Complex object tracking with unique IDs

**Game Loop**
- Primary update cycle (`update()` function)
- Real-time interval loop (1-second intervals)
- Event-driven input handling

### 2. World Generation (`genMap()` - lines 162-229)

**Procedural Generation**
- Coastline generation with variable sea width
- River system with realistic meandering
- Random placement of trees, rocks, and jungle areas
- Strategic placement of Dharma stations

**Initial Setup**
- Airplane crash site with fire hazard
- 15 survivors spawned near crash site
- 30 animals distributed across the map
- Pre-revealed 15×15 area around starting position

### 3. Game Mechanics

**Fire System (`handleFireSpreading()` - lines 607-650)**
- Realistic fire spreading based on terrain type
- Fire life cycle with automatic extinguishing
- Terrain-specific spread probabilities:
  - Jungle: 100% spread chance
  - Trees: 50% spread chance  
  - Grass: 30% spread chance

**Survivor AI (`updateSurvivors()` - lines 699-767)**
- Fire avoidance behavior
- Camp-seeking pathfinding
- Death mechanics with corpse generation
- Automatic respawning to maintain population

**Resource Management**
- Wood collection from trees
- Stone extraction from rocks
- Food gathering from animals and traps
- Dynamic resource regeneration

### 4. Building System (`actionCamp()`, `actionWall()`, etc. - lines 986-1046)

**Structure Types**
- Camps: Safe zones for survivors
- Walls: Defensive barriers
- Bridges: Water crossing points
- Graves: Corpse burial sites
- Traps: Animal catching mechanisms

**Construction Logic**
- Resource requirement validation
- Terrain suitability checking
- Structure state management

### 5. Dharma Station System (`activateStation()` - lines 418-481)

**Station Types and Functions**
- **Swan (H)**: Countdown management and unlimited food
- **Black Rock (B)**: Dynamite collection
- **Pearl (P)**: Map revelation
- **Looking Glass (L)**: Freighter signaling
- **Flame (M)**: Complete map revelation

**Progressive Unlocking**
- Stations unlock new capabilities
- Chain of dependencies for game progression
- End-game rescue sequence activation

### 6. User Interface

**Visual Rendering**
- ASCII character display with CSS styling
- Color-coded entity representation
- Real-time HUD with resource counters
- Dynamic command context menus
- Fullscreen layout utilizing entire viewport
- Responsive design with flexible panels

**Input System**
- Keyboard event handling for all game controls
- Arrow keys and space bar prevent default browser scrolling
- Context-sensitive action availability
- Error handling and user feedback

**Layout System**
- Body overflow hidden to prevent page scrolling
- Flexbox-based layout for responsive fullscreen display
- Game area uses calc() for dynamic height adjustment
- Side panels (legend/commands) maintain fixed width with scrollable content

## Design Patterns

### Entity-Component System
- Entities represented as objects with properties
- Component-like behavior through function composition
- Systems process entities in batch updates

### Observer Pattern
- Event-driven updates for game state changes
- Automatic UI updates on state changes
- Cascading effects from user actions

### State Machine
- Progressive objective system with state transitions
- Game phase management (exploration → rescue → victory)
- Clear win/lose condition checking

### Factory Pattern
- Procedural generation of world elements
- Dynamic entity creation (survivors, animals, fires)
- Structure instantiation with validation

## Performance Considerations

### Optimization Strategies
- Efficient array operations with proper indexing
- Batch processing of similar entities
- Selective rendering updates
- Memory management through object reuse

### Scalability
- Fixed world size prevents memory bloat
- Entity lifecycle management prevents accumulation
- Efficient collision detection using coordinate comparison

### Browser Compatibility
- Vanilla JavaScript avoids framework dependencies
- Standard DOM APIs ensure broad compatibility
- CSS3 features with fallback styling

## Data Flow

```
User Input → Event Handler → Game Logic → State Update → Rendering → Display
     ↑                                                              ↓
     ←——————————————— Game Loop Timer ←————————————————————————————
```

## Security Architecture

- Client-side execution eliminates server attack vectors
- No external API dependencies
- Input validation prevents invalid game states
- No data persistence eliminates storage vulnerabilities

## Future Enhancement Opportunities

### Technical Improvements
- Save/load game state using localStorage
- WebGL rendering for enhanced graphics
- Web Workers for background processing
- Service Worker for offline play

### Feature Additions
- Multiplayer support using WebRTC
- Mobile touch controls
- Audio system integration
- Achievement tracking system

---
*Architecture documented based on complete game implementation analysis.*