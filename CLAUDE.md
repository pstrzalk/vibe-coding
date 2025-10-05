# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Vibe Coding** is an experimental repository exploring AI-generated educational games and interactive learning tools. The project demonstrates what's possible with "vibe coding" - rapid prototyping of interactive educational experiences using AI assistance.

### Key Philosophy
- These are experimental, fun projects - not production-ready applications
- Each game is a single self-contained HTML file with embedded CSS and JavaScript
- Games are created through conversational AI coding (primarily with Gemini 2.5 Pro Experimental)
- Focus on educational value for children (language learning, mathematics)

## Repository Structure

```
/vibes/                           # All educational games/apps
  ├── learn-irregular-english-verbs.html    # 2D space shooter for learning irregular verbs
  ├── piggy-multiplication.html             # Pig-themed multiplication practice game
  ├── save-a-wolf.html                      # 3D adventure game (multiplication + ThreeJS)
  └── images/                               # Screenshots for README
```

## Development Approach

### Single-File Architecture
All games in `/vibes/` follow this pattern:
- **Single HTML file** containing everything (HTML, CSS, JavaScript)
- **No external dependencies** except CDN-hosted libraries
- **Standalone** - download and run in any modern browser
- **No build process** required

### Technology Patterns

**2D Games** (piggy-multiplication.html, learn-irregular-english-verbs.html):
- Vanilla JavaScript with Canvas API
- Inline SVG graphics
- CSS3 animations and transitions
- Modal-based UI interactions

**3D Games** (save-a-wolf.html):
- ThreeJS via ES6 modules from CDN (`https://unpkg.com/three@0.160.0/build/three.module.js`)
- Import maps for module resolution
- Uses ThreeJS scene graph, lighting, shadows, and camera systems

### Game Design Patterns

All games share common elements:
1. **Educational quiz mechanics** - multiplication tables or verb conjugations
2. **Visual feedback** - particles, animations, color-coded responses
3. **Progressive difficulty** - towers shrink, monsters spawn, scores increase
4. **Attempt management** - typically allow 1-2 attempts before consequences
5. **Win/lose conditions** - clear victory/defeat states with visual celebration

## Common Commands

**Testing games:**
```bash
# Open any game in default browser (macOS)
open vibes/piggy-multiplication.html

# Or use Python's built-in server
python3 -m http.server 8000
# Then navigate to http://localhost:8000/vibes/
```

**Git operations:**
```bash
git status
git add vibes/
git commit -m "Add new educational game"
```

## Important Technical Considerations

### When Modifying Games

1. **Preserve self-containment** - Keep everything in one HTML file
2. **Maintain accessibility** - Games should work without internet (except for CDN libraries)
3. **Polish focus is minimal** - These are prototypes; over-engineering is counter to the vibe coding philosophy
4. **Educational accuracy matters** - Verify verb forms, multiplication results, etc.

### ThreeJS Considerations (from lessons learned)

- **Avoid ThreeJS for simple games** - Canvas 2D is much easier for collision detection, camera management, and game rules
- **If using ThreeJS**:
  - Keep camera simple (third-person follow camera)
  - Use basic collision detection (distance checks, not raycasting)
  - Prefer simple geometries (boxes, cylinders, cones)
  - Shadow maps add visual polish but increase complexity

### Known Issues/Patterns from Lessons Learned

From README.md insights:
- **CSS width issues are easier to fix manually** than through AI iteration
- **Gemini 2.5 Pro generates better graphics/UX** than Gemini 2.0
- **First iterations are often the best** - avoid feature creep
- **Context usage can grow large** (50k-150k+ tokens per game)

## File Conventions

### HTML Games
- Use descriptive titles in Polish or English based on target audience
- Include meta viewport tag for responsive behavior
- Inline all styles in `<style>` tags
- Inline all scripts (except external library imports)

### Commit Messages
Recent patterns suggest informal, descriptive messages:
- "Add Piggy Multiplication"
- "Add Vibes (folder)"
- "Correct typos in Readme"

## Educational Content

### Irregular Verbs Game
- Dataset: 100+ irregular English verbs with Polish translations
- Verb structure: `[polish, base, past_simple, past_participle]`
- Game mechanic: Space shooter where correct verb forms defeat enemies

### Multiplication Games
- Piggy: Polish UI, configurable multipliers (2, 3, 4, 5)
- Wolf: 3D adventure, Yellow cubes (4-9) × Cyan cubes (2-5)
- Mistake handling: Show hints, allow retries, then penalize

## Special Notes

- **Language mixing**: Some games use Polish UI (target audience is Polish children)
- **No test suite**: These are experimental prototypes
- **No linting/formatting**: Prioritize rapid iteration over code quality
- **Screenshots in README**: Update when games change significantly
