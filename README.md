# Chromatrack

[![Live Demo](https://img.shields.io/badge/Live-Demo-brightgreen)](https://consciousnode.github.io/chromatrack/Chromatrack_Final.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)]()
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)]()
[![Web Audio API](https://img.shields.io/badge/Web%20Audio-API-orange)]()

A fully self-contained generative step sequencer built entirely with the Web Audio API. No install. No server. No dependencies. Just one HTML file.

> Open `Chromatrack_Final.html` in any modern browser and make music.

![Chromatrack Interface](Chromatrack (1).png)
![Chromatrack Interface](Chromatrack (1).png)
![Chromatrack Interface](Chromatrack (1).png)
![Chromatrack Interface](Chromatrack (1).png)

---

## Quick Start

1. Download `Chromatrack_Final.html`
2. Open it in Chrome, Edge, or Firefox
3. Click **Play**

That's it.

---

## What's New in v2

- **Row Controls Popup** — every row now has a `≡` button that opens a full control panel with all 15 per-row parameters in one place. The grid stays clean by default.
- **Sample Import** — load any audio file onto a row via the popup or drag-and-drop onto the color dot. Samples are pitch-shifted relative to the row's base note, saved in presets, and shareable via URL.
- **8-Language i18n** — full UI translation: English, Spanish, French, German, Russian, Chinese, Japanese, Korean. Persists across sessions.
- **Help Modal** — press `?` or `H` to open a full in-app guide, translated into all 8 languages.
- **Mute/Solo persistence** — mute and solo state now saves and loads correctly with presets.
- **Step Lock label** — probability popup renamed to "Step Lock" to better reflect what it does.
- **IIFE namespace** — all JS is now scoped in a single IIFE, nothing leaks to `window.*`.

---

## Features

### Sequencer Grid

- **Up to 16 rows × 16 steps** — each row is a pitched voice, C5 down to C2
- **Left-click / Tap** — toggle a step at 100% probability
- **Right-click / Long-press** — open Step Lock (per-step pitch, decay, waveform override)
- **Click-drag / Touch-drag** — paint or erase multiple cells at once
- **Probable steps** shown as dashed outlines; probability set via Step Lock

### Synthesis — 10 Voice Types

| Symbol | Type | Character |
|--------|------|-----------|
| `~` | Sine | Pure, clean tone |
| `^` | Triangle | Soft, hollow |
| `W` | Sawtooth | Bright, buzzy |
| `Π` | Square | Hollow, reedy |
| `*` | Noise | Filtered noise, percussive |
| `FM` | FM | Metallic, bell-like, complex |
| `Pu` | Pulse | Thin, nasal, hollow |
| `De` | Detune | Fat supersaw, wide stereo feel |
| `Ch` | Chord | Root + major 3rd + 5th, instant harmony |
| `Smp` | Sample | Load any audio file; pitch-shifted per row |

### Row Controls Popup (`≡`)

Every row has a `≡` button that opens a floating panel with all controls in one place. Nothing clutters the grid by default.

| Section | Controls |
|---------|----------|
| **Voice** | Waveform (10 types), Decay, Octave shift, Speed multiplier, Arpeggiator, Chord type |
| **Sequencer** | Row length (2–16), Euclidean beat count |
| **MIDI** | Per-row channel override |
| **FX** | Reverb send, Delay send, Filter cutoff, Filter resonance |
| **Utilities** | Mute, Solo, Probability lock |
| **Sample** | Load audio file, Clear sample, drag-and-drop onto color dot |

### Transport

- **Play / Stop** with clean state reset
- **Live Record** — tap cells to write notes at the current playhead position
- **Tap Tempo** — 4-tap rolling average
- **BPM** — 60 to 180
- **Swing** — 0 to 75%
- **Volume**
- **Humanize** — randomises timing (±30ms) and velocity (±20%) for a live feel
- **Rows / Steps sliders** — resize the grid from 4×4 up to 16×16 in real time

### Patterns

- **8 pattern slots** — switch instantly or queue during playback
- **Copy** — duplicate current pattern to any slot
- **Chain mode** — auto-advance through patterns 1→2→3→…→8→1
- **Song mode** — arrange patterns into a linear sequence (up to 16 steps, each repeating ×1–8)
- **Transpose** — per-pattern pitch shift of ±12 semitones

### Generative Tools

- **Random** — sparse probabilistic fill, respects locked rows
- **Mutate** — evolves the current pattern with 4 intensity levels (Low / Med / High / Chaos)
- **Auto-Mutate** — triggers mutation automatically every 2, 4, 8, or 16 bars
- **Roll** — one-shot random fill with immediate application
- **Euclidean Generator** — Bjorklund algorithm, distributes beats evenly across row length

### Scale Lock

Quantises all voices to a musical scale in real time. Root note selectable across all 12 pitches.

Free · Major · Minor · Dorian · Phrygian · Lydian · Mixolydian · Minor Pentatonic · Major Pentatonic · Chromatic

### Themes — 6 Colour Palettes

| Theme | Character |
|-------|-----------|
| **Neon** | Cyan / Magenta — the default dark neon look |
| **Inferno** | Orange / Yellow — warm, fiery |
| **Forest** | Green — deep and organic |
| **Void** | Violet / Blue — cold and spacious |
| **Rose** | Pink / Purple — soft and dreamy |
| **Ice** | Sky Blue — crisp and minimal |

Themes repaint the entire UI instantly — row colours, oscilloscope gradient, scrollbar, sliders, and all accent elements.

### Localisation — 8 Languages

Switch languages in real time from the selector in the header. Choice persists to `localStorage`.

🇬🇧 English · 🇪🇸 Spanish · 🇫🇷 French · 🇩🇪 German · 🇷🇺 Russian · 🇨🇳 Chinese · 🇯🇵 Japanese · 🇰🇷 Korean

### Piano Roll

- Toggle with the **Roll** button
- Shows all active rows and steps for the current pattern
- Probability shown as opacity
- Live playhead during playback

### Oscilloscope

- Live waveform display
- Gradient follows the active theme's colour range
- Flat line when idle

### MIDI

- **Web MIDI output** — select any connected MIDI device
- **Per-row channel routing** — each row defaults to its own channel (1–16), overridable per row
- **All Notes Off** sent on Stop
- **MIDI file export** — downloads a standard `.mid` file with correct tempo track, per-row tracks, swing as tick offsets, velocity from step probability. Export modes: Current / All patterns / Chain

### Sharing & Presets

- **Share button** — copies a URL with the full session state (patterns, samples, all settings) compressed via LZ-String
- **5 preset slots** — saved to `localStorage`, includes mute/solo state and loaded samples
- Backward compatible — presets from earlier versions load and pad correctly

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Space` | Play / Stop |
| `1`–`8` | Select pattern |
| `M` | Mutate |
| `R` | Random |
| `F` | Fullscreen |
| `H` | Help / Instructions |
| `Ctrl+Z` | Undo |
| `Shift+Backspace` | Clear |

---

## Architecture

Chromatrack is intentionally a single HTML file with no build step, no bundler, and no runtime dependencies beyond Tailwind CSS (loaded from CDN for utility classes only). All JavaScript runs inside a single IIFE — nothing leaks to the global scope.

### Audio Engine

- **Web Audio API** — all synthesis is built from raw oscillator, gain, biquad filter, and buffer source nodes
- **Web Worker scheduler** — a dedicated worker fires a 25ms tick, completely isolated from the main thread and immune to tab throttling
- **Lookahead buffering** — notes are scheduled 100ms ahead of the audio clock, eliminating jitter
- **Dynamics compressor** on the master bus
- **Sample playback** — `AudioBufferSourceNode` with per-note pitch shifting relative to row base frequency

### Timing

The scheduler uses the Web Audio clock (`audioCtx.currentTime`) as the source of truth. The worker tick wakes the scheduler, which schedules all notes within the lookahead window. Visual feedback is decoupled — a `visualQueue` holds scheduled events and `requestAnimationFrame` drains it in sync with the display.

### Polymetric Clock

Each row maintains its own step counter and fractional accumulator. The speed multiplier (½×, 1×, 2×, 4×) advances the accumulator by a different amount each global tick, so rows run at completely independent rates against the same master clock.

### State & Sharing

All session state is serialised to JSON and compressed with LZ-String for URL sharing. Samples are stored as base64 data URIs and round-trip through presets and shared URLs. Language preference persists in `localStorage`.

---

## Browser Support

| Browser | Support |
|---------|---------|
| Chrome / Edge | ✅ Full — recommended |
| Firefox | ✅ Full |
| Safari | ✅ Works — Web MIDI requires a plugin |
| Mobile Chrome | ✅ Full touch support |
| Mobile Safari | ⚠️ Works — Web MIDI not available |

Web MIDI requires a secure context (HTTPS or localhost).

---

## Usage Tips

- **Polymetric grooves** — set different step lengths per row (e.g. 3, 4, 5) and let them drift against each other
- **Euclidean + lock** — generate a euclidean pattern on a row, lock it, then mutate everything else around it
- **Song mode** — build 8 distinct patterns and arrange them into a full track structure with repeat counts
- **Sample + pitch** — load a one-shot drum hit onto a row; each step plays it at a different pitch based on the row's note
- **FM + long decay** — FM voice with ∞ decay makes evolving metallic pads
- **Chord voice + arp** — combine the Chord waveform with the Up-Down arpeggiator for cascading harmony
- **Auto-mutate + prob lock** — lock your kick and bassline rows, enable auto-mutate every 4 bars, let the upper voices evolve while the groove stays anchored
- **Humanize** — even 10–20% makes programmed patterns feel significantly more alive
- **Share early** — the Share URL encodes everything including samples; send it to collaborators or save it as a bookmark

---

## License

MIT — do whatever you want with it.

---

## Credits

Built with the Web Audio API, a Web Worker, LZ-String, and an unreasonable amount of attention to timing accuracy.
