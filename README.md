# Lost Game

A comprehensive survival game inspired by the TV series "Lost", built entirely in HTML5 and JavaScript.

## Overview

Lost Game is a browser-based ASCII survival game where players must manage survivors, build camps, explore mysterious Dharma stations, and ultimately orchestrate a rescue from a mysterious island. The game features dynamic fire mechanics, resource management, and progressive objectives with authentic Lost TV show quotes.

## Game Features

### Core Gameplay
- **Survival Mechanics**: Manage wood, stone, and food resources
- **Fire System**: Dynamic fire spreading with realistic behavior based on terrain
- **Time Progression**: Day/night cycles with 15-minute increments
- **Dynamic Lighting**: Immersive day/night visual cycle with torches, campfires, and ambient lighting
- **Fog of War**: Explore to reveal the 140x60 game world
- **Survivor Management**: Guide 15 survivors to safety in camps

### Building System
- **Camps** (C key): Establish safe zones for survivors
- **Walls** (W key): Build defensive structures (requires wood)
- **Bridges** (B key): Cross water obstacles (requires wood)
- **Graves** (G key): Bury corpses for score bonuses (requires stone)
- **Traps** (T key): Catch animals for food (requires wood)

### Dharma Stations
- **The Swan (Hatch)**: Reset countdown and unlock unlimited food
- **Black Rock**: Collect dynamite to blow open the hatch
- **The Pearl**: Reveals all Dharma stations on the map
- **Looking Glass**: Signal the freighter for rescue
- **The Flame**: Reveals the entire island map

### Progressive Objectives
1. Escape the initial fire
2. Collect wood and build camps
3. Get survivors to safety
4. Collect food and build defenses
5. Explore and find the Hatch
6. Open the Hatch with dynamite
7. Signal the freighter
8. Reach the helicopter and rescue survivors

## Controls

- **Arrow Keys**: Move player
- **Space**: Interact/collect items/activate stations
- **B**: Build bridge (requires wood)
- **C**: Build camp (requires wood)
- **W**: Build wall (requires wood)
- **G**: Build grave (requires stone + carrying corpse)
- **T**: Lay trap (requires wood)
- **E**: Collect/bury corpse

## Files

- `lost.html` - Complete game with all mechanics
- `Lostalt.html` - Alternative/backup version (currently empty)

## Getting Started

1. Open `lost.html` in any modern web browser
2. The game will fill your entire browser window for an immersive experience
3. Use arrow keys to move your character (*) - arrow keys won't scroll the page
4. Follow the progressive objectives shown at the top
5. Start by escaping the initial fire near the airplane wreckage
6. Collect wood from trees (T) and build your first camp

## Scoring

- Start with 100% score
- Score decreases over time (0.1% per second)
- Lose score when survivors die
- Gain score by burying corpses
- Win by rescuing 75% of survivors (12 out of 15)

## Win Condition

Successfully rescue at least 12 survivors by:
1. Finding and activating the Looking Glass station
2. Signaling the freighter
3. Reaching the helicopter when it arrives
4. Ferrying survivors to safety

## Documentation

See the `/documentation` folder for detailed information about:
- Technical architecture and implementation
- Security considerations
- Product features and roadmap

## Development

This project is feature-complete but open to enhancements. See `CHANGELOG.md` for recent updates and `CLAUDE.md` for development notes.