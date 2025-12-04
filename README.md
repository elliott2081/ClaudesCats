# ClaudesCats

A simple HTML cat toy app - no build tools, no dependencies, just one HTML file you can open on any device.

## What is this?

An interactive toy for your cat (or yourself!) featuring animated objects bouncing around the screen. Tap to attract them or shoot them depending on the theme.

**Built entirely with Claude Code** - and designed so you can customize it with your own Claude!

## Themes

1. **🐱 Fish** - Cat swimming underwater catching fish
2. **🔴 Laser** - Classic red dot on black background
3. **🦆 Ducks** - Paw prints chasing ducks on a pond
4. **🚀 Space** - Rocket collecting stars
5. **🦋 Garden** - Cat catching butterflies with falling leaves
6. **🧶 Yarn** - Cat chasing yarn balls
7. **👾 Invaders** - Space shooter! Tap to fire bullets at aliens

## Features

- Speed slider (🐢 slow to 🐇 fast)
- Fullscreen button
- Tap anywhere to attract the main character
- Works on phones, tablets, and desktop browsers
- No internet required after download

## How to Use

### On a computer
Just open `cat-app.html` in any browser.

### On Android tablet/phone

**Option 1: Direct file access**
1. Copy `cat-app.html` to your device
2. Open in Chrome (may need to grant file access permission)

**Option 2: Via ADB**
```bash
adb push cat-app.html /sdcard/Download/
adb shell am start -a android.intent.action.VIEW -d "file:///sdcard/Download/cat-app.html" -t "text/html"
```

**Option 3: Local server**
```bash
python3 -m http.server 8888
adb reverse tcp:8888 tcp:8888
# Open http://localhost:8888/cat-app.html on device
```

## Customize with Claude!

This repo includes a `CLAUDE.md` file that explains the code structure to Claude. Just open this repo in Claude Code and ask for customizations like:

- "Add a new theme with mice"
- "Make the laser dot green"
- "Add sound effects"
- "Create a theme with my cat's name"

See `CLAUDE.md` for details on how the code is structured.

## License

MIT - do whatever you want with it!
