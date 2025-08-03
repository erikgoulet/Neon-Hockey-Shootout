# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Neon Hockey Shootout is a single-file web game that simulates first-person hockey shooting with 3D physics. The entire application is contained within `index.html` with zero external dependencies.

## Development Commands

Since this is a pure HTML/CSS/JavaScript project with no build process:

- **Run locally**: Open `index.html` directly in a browser or use a local server:
  ```bash
  python -m http.server 8000
  # or
  npx serve .
  ```

- **Deploy**: Push to main branch triggers automatic GitHub Pages deployment

- **Test**: Manual testing only - open in browser and play the game

## Architecture

### Single-File Structure
All code resides in `index.html`:
- Lines 1-150: HTML structure and CSS styles
- Lines 150+: JavaScript game logic

### Key Components

1. **Game Loop** (search for "gameLoop"): RequestAnimationFrame-based with delta time handling
2. **3D Projection System**: Custom perspective calculations for 2D canvas (search for "project3D")
3. **Physics Engine**: Gravity, friction, and collision detection (search for "updatePuck")
4. **AI Goalie**: Predictive movement based on puck trajectory (search for "updateGoalie")
5. **Particle System**: Object pooling with 150 max particles (search for "particles")

### Game State Management
- Game modes: Classic (5 shots), Time Attack (60s), Sudden Death, Practice
- Shot types: Wrist (high accuracy), Slap (high power), Backhand (deceptive)
- Difficulty levels affect goalie speed and prediction accuracy

### Performance Considerations
- Two canvases: static background and dynamic game elements
- Object pooling for particles to avoid garbage collection
- Image smoothing disabled for pixel art aesthetic
- 60 FPS target with deltaTime-based updates

### Mobile Support
- Touch events unified with pointer events
- Responsive design with viewport scaling
- PWA manifest for app installation
- Haptic feedback via Vibration API

## Important Notes

- **No build process**: Edit `index.html` directly
- **No dependencies**: Uses only web standard APIs
- **Testing approach**: Manual playtesting in browser
- **Deployment**: GitHub Pages serves files as-is
- **Mobile testing**: Use responsive mode or actual devices

### QGIT

```
Add all changes to staging, create a commit, and push to remote.
Follow Conventional Commits format and do not refer to Claude or Anthropic.
NEVER add Claude or Anthropic to commit message.
NEVER add │   🤖 Generated with [Claude Code](https://claude.ai/code)                                                     │
│                                                                                                               │
│   Co-Authored-By: Claude <noreply@anthropic.com>"
```