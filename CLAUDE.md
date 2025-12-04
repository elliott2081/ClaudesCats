# Claude Instructions for ClaudesCats

This file explains how the cat toy app works so you can help users customize it.

## Overview

`cat-app.html` is a single-file HTML/CSS/JS app with no dependencies. It displays animated emoji characters that bounce around the screen, with different themes and interactive features.

## Code Structure

### Themes Object (line ~100)

All themes are defined in the `themes` object. Each theme has:

```javascript
themeName: {
  name: '🎨 Display Name',     // Button label
  bg: '#000000',               // CSS background (color or gradient)
  main: '🐱',                  // Main character emoji
  mainSize: 80,                // Font size in pixels
  mainStyle: '',               // Optional: CSS for non-emoji main (like laser dot)
  targets: ['🐟', '🐠'],       // Array of target emojis to catch
  targetSize: 40,              // Target font size
  particles: 'bubbles',        // Particle effect type
  scoreLabel: '🐟',            // Emoji shown with score
  shooter: false               // If true, tapping fires bullets
}
```

### Particle Types

Available particle effects (in `createParticle` function):
- `'bubbles'` - Rising bubbles
- `'stars'` - Twinkling stars
- `'leaves'` - Falling leaves
- `'ripples'` - Expanding water ripples
- `'fluff'` - Floating fluff particles
- `'none'` - No particles

### Key Variables

- `x, y` - Main character position
- `vx, vy` - Main character velocity
- `speedMultiplier` - Speed slider value (0.3 to 3)
- `targets[]` - Array of target DOM elements
- `bullets[]` - Array of bullet objects (for shooter mode)
- `score` - Current score

### Key Functions

- `init()` - Reset game state
- `applyTheme()` - Apply current theme visuals
- `spawnTarget()` - Create a new target
- `catchTarget(el)` - Handle catching/destroying a target
- `fireBullet(tx, ty)` - Fire bullet toward coordinates (shooter mode)
- `createExplosion(x, y)` - Big explosion effect
- `createParticle()` - Spawn ambient particle
- `animate()` - Main game loop

## Common Customization Tasks

### Add a New Theme

Add an entry to the `themes` object:

```javascript
mice: {
  name: '🐭 Mice',
  bg: 'linear-gradient(135deg, #8B4513 0%, #654321 100%)',
  main: '🐱',
  mainSize: 80,
  targets: ['🐭', '🐁'],
  targetSize: 35,
  particles: 'fluff',
  scoreLabel: '🐭'
}
```

### Change Colors

- Background: Edit the `bg` property (CSS color or gradient)
- For the laser dot theme, edit the `mainStyle` property with CSS

### Adjust Speed Range

Find the speed slider creation (~line 510):
```javascript
min="0.3" max="3" step="0.1" value="1"
```

### Add a New Particle Type

1. Add a new case in `createParticle()` function
2. Reference it in your theme's `particles` property

### Make a Shooter Theme

Set `shooter: true` in the theme. The rocket/ship will fire bullets when user taps.

### Change Main Character to Custom Element

Use `mainStyle` instead of `main` for CSS-based characters:

```javascript
mainStyle: 'width:40px;height:40px;background:green;border-radius:50%;'
```

## Tips

- All graphics are emoji - they work on every device
- The app auto-detects touch vs mouse input
- Fullscreen uses the browser's Fullscreen API
- Score only shows if `scoreLabel` is set
- Targets respawn 1-3 seconds after being caught
- The main character bounces off screen edges with slight randomness

## Testing Changes

The easiest way to test is to run a local server:
```bash
python3 -m http.server 8888
```
Then open http://localhost:8888/cat-app.html

For Android testing via ADB:
```bash
adb push cat-app.html /sdcard/Download/
```
