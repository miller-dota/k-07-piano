# K-07 Piano


![GitHub stars](https://img.shields.io/github/stars/miller-dota/k-07-piano?style=flat-square) ![GitHub forks](https://img.shields.io/github/forks/miller-dota/k-07-piano?style=flat-square) ![GitHub issues](https://img.shields.io/github/issues/miller-dota/k-07-piano?style=flat-square) ![Repo size](https://img.shields.io/github/repo-size/miller-dota/k-07-piano?style=flat-square) [![Live Demo](https://img.shields.io/badge/demo-live-brightgreen?style=flat-square)](https://miller-dota.github.io/k-07-piano)

A pixel-faithful interactive browser piano inspired by the **K-07** hardware keyboard. Play it with your mouse, touch screen, or keyboard — no downloads, no installs, no plugins required.

Built on [Tone.js](https://tonejs.github.io/), it handles audio synthesis, polyphony, and octave management automatically. One click to play, zero friction to jam.

---
<p align="center">
  <img src="K07 piano.png" alt="isolated" width="600"/>
</p>


---

> **💡 Tip**
>
> **🆕 NEW: Full Keyboard Shortcut Support!**
>
> Play the K-07 Piano directly from your keyboard — no mouse needed! Use `A S D F G H J` for white keys and `W E T Y U` for black keys. Switch octaves on the fly with the `◄ ►` buttons.
>
> **Latest engine:** Tone.js 14.7.77 · Triangle8 oscillator · Polyphonic (up to 8 simultaneous voices) · Works on Chrome, Firefox, Safari, and Edge 🎉

---

### Quick Links

- [Live Demo →](https://miller-dota.github.io/k-07-piano) — Play it now in your browser
- [Releases →](https://github.com/miller-dota/k-07-piano/releases) — Download the latest version
- [Report a Bug →](https://github.com/miller-dota/k-07-piano/issues) — Found something? Let us know

---

## Features

- 🎹 **Native Browser Experience** — Clean HTML/CSS interface that feels right at home in any modern browser
- 🎵 **Real Audio Synthesis** — Powered by Tone.js with natural attack, decay, sustain, and release envelope
- ⌨️ **Full Keyboard Support** — Play white and black keys using `A–J` and `W/E/T/Y/U` shortcuts
- 🔢 **Octave Switching** — Navigate octaves 1–7 with the `◄ ►` nav buttons on the device header
- 💡 **Live LED Indicator** — Amber LED glows whenever a key is active, just like the real hardware
- 🖱️ **Mouse & Touch Ready** — Pointer events work seamlessly on desktop and mobile
- 🎨 **Pixel-Faithful Design** — Neumorphic warm-gray aesthetic replicating the original K-07 hardware
- ⚡ **Zero-Latency Input** — Web Audio API triggered on pointer/key down for instant response
- 📦 **Self-Contained** — Single `index.html` file, one CDN dependency, no build step required

---

## Installation

### Requirements

- Any modern browser (Chrome 80+, Firefox 75+, Safari 14+, Edge 80+)
- No Node.js, no build tools, no server required

### Download Pre-built Release (Recommended)

1. Go to the [Releases](https://github.com/miller-dota/k-07-piano/releases) page
2. Download the latest `k-07-piano.zip`
3. Extract the archive
4. Open `index.html` in your browser — done 🎹

> **✅ No server required** — Runs directly from your local filesystem.

### Clone from Source

```bash
git clone https://github.com/miller-dota/k-07-piano.git
cd k-07-piano
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### Deploy to GitHub Pages

Fork this repo → **Settings → Pages** → select `main` branch → `/ (root)` → Save.
Your piano will be live at `https://miller-dota.github.io/k-07-piano` within minutes.

---

## Usage

### First Launch

1. Open `index.html` in any modern browser
2. Click any key — the browser activates the Web Audio context on first interaction
3. The amber LED in the header confirms audio is live
4. Play!

### Authentication

No authentication needed — the K-07 Piano is fully client-side. No accounts, no API keys, no data collection.

### Octave Management

- **`◄`** button → shift down one octave
- **`▶`** button → shift up one octave
- **Range:** Octave 1 (lowest) to Octave 7 (highest)
- Current octave shown in the hint bar beneath the device

---

## Requirements

- macOS 10.15+ / Windows 10+ / Linux (any modern distro)
- Chrome 80+, Firefox 75+, Safari 14+, or Edge 80+

---

## Development

### Project Structure

```
k-07-piano/
├── index.html              # App entry point — markup, styles, and script
│   ├── <style>             # Neumorphic device + key styling
│   ├── .device             # Hardware shell component
│   ├── .white-keys-row     # White key container
│   ├── .black-keys-overlay # Black key absolute-position layer
│   └── <script>            # Tone.js synth + keyboard/pointer logic
└── README.md               # This file
```

### Key Components

- **AppShell** — Neumorphic `<div>` replicating the K-07 hardware enclosure with warm-gray palette
- **White Keys** — Dynamically rendered `<button>` elements, width computed via flexbox
- **Black Keys** — Absolutely positioned overlay; left/width calculated from white key geometry at runtime
- **LED Indicator** — CSS radial-gradient circle; gains amber `box-shadow` glow on any active note
- **PolySynth** — Lazy-initialized Tone.js instance; complies with browser autoplay policy
- **KeyMap** — `keydown`/`keyup` document listeners mapped to note names relative to current octave

### Modifying the Sound

Open `index.html` and edit the synth block:

```javascript
synth = new Tone.PolySynth(Tone.Synth, {
  oscillator: { type: 'triangle8' },  // try: sine, square, sawtooth, fatsawtooth
  envelope: {
    attack:  0.015,  // seconds — fade-in speed
    decay:   0.12,   // seconds — drop after peak
    sustain: 0.35,   // 0–1    — held volume level
    release: 0.7     // seconds — fade after key release
  }
}).toDestination();
```

---

## Tech Stack

| Technology | Purpose |
|---|---|
| HTML5 / CSS3 | UI structure and neumorphic device styling |
| Vanilla JavaScript (ES2020) | Key rendering, event handling, octave logic |
| [Tone.js 14.7.77](https://tonejs.github.io/) | Web Audio synthesis and polyphony |

---

## Credits

K-07 Piano is built on top of [Tone.js](https://tonejs.github.io/), an excellent Web Audio synthesis framework with support for polyphony, envelopes, and effects.

Special thanks to the Tone.js contributors for making browser-based music creation accessible.

---

## License

MIT — see [LICENSE](LICENSE) for details.

---

## Support

- 🐛 **Report Issues:** [GitHub Issues](https://github.com/miller-dota/k-07-piano/issues)
- 🌐 **Live Demo:** [miller-dota.github.io/k-07-piano](https://miller-dota.github.io/k-07-piano)

---

*© 2026 K-07 Piano. All rights reserved.*
