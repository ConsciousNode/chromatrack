# Chromatrack

A fully self-contained generative step sequencer built entirely with the Web Audio API. No install. No server. No dependencies. Just one HTML file.

> Open `Chromatrack.html` in any modern browser and make music.

---

## Quick Start

1. Download `Chromatrack_Final.html`
2. Open it in Chrome, Edge, or Firefox
3. Click **Play**

That's it.

---

## Features

### Sequencer Grid

* **16 rows × 16 steps** — each row is a pitched voice, C5 down to C2
* **Left-click / Tap** — toggle a step at 100% probability
* **Right-click / Long-press (empty cell)** — set a probable step (plays sometimes, shown as dashed outline with percentage)
* **Right-click / Long-press (active cell)** — open **Step Lock**: override pitch, decay, and waveform for that step individually
* **Click-drag / Touch-drag** — paint or erase multiple cells at once

### Synthesis — 10 Voice Types

| Symbol | Type | Character |
| --- | --- | --- |
| `~` | Sine | Pure, clean tone |
| `^` | Triangle | Soft, hollow |
| `W` | Sawtooth | Bright, buzzy |
| `Π` | Square | Hollow, reedy |
| `*` | Noise | Filtered noise, percussive |
| `FM` | FM | Metallic, bell-like, complex |
| `Pu` | Pulse | Thin, nasal, hollow |
| `De` | Detune | Fat supersaw, wide stereo feel |
| `Ch` | Chord | Root + major 3rd + 5th, instant harmony |
| `Sa` | Sample | Load any audio file — playback pitched to each step |

### Per-Row Controls

Every row has independent controls accessible via the row control panel:

| Control | Function |
| --- | --- |
| **Color dot** | Click to set a custom row color; right-click to reset to theme default |
| **~ ^ W Π * FM Pu De Ch Sa** | Cycle through 10 voice types |
| **P / S / M / L / ∞** | Decay time — Pluck / Short / Medium / Long / Pad |
| **«2 «1 ·· »1 »2** | Octave shift (−2 to +2) |
| **4–16** | Step length — polymetric, independent per row |
| **Euclidean (1–8)** | Distribute beats evenly using the Bjorklund algorithm |
| **M / channel#** | MIDI channel override (1–16 or Auto) |
| **· / M / S** | Mute (click) / Solo (double-click) |
| **½ · 2 4** | Speed multiplier per row |
| **↑ ↓ ↕ ?** | Arpeggiator — Off / Up / Down / Up-Down / Random |
| **Chord type** | Per-row voicing: Off, Major, Minor, Dom7, Maj7, Min7, Dim, Aug, Sus4, Add9 |
| **🔓 / 🔒** | Lock row from Mutate and Random |
| **R·** | Reverb send level (0 / 25 / 50 / 75 / 100%) |
| **D·** | Delay send level |
| **Filter** | Per-row lowpass filter cutoff and resonance |

### Step Lock

Right-click (or long-press) any **active** cell to override that individual step:

* **Pitch** — detune ±12 semitones from the row's base note
* **Decay** — independent decay length for just this step
* **Waveform** — different voice type for just this step

Step Lock lets a single row behave like multiple instruments across its sequence.

### Transport

* **Play / Stop** with clean state reset
* **Live Record** — tap cells to write notes at the current playhead position in real time
* **Tap Tempo** — 4-tap rolling average
* **BPM** — 60 to 180
* **Swing** — 0 to 75%
* **Volume**
* **Humanize** — randomises timing (±30ms) and velocity (±20%) for a live feel

### Groove Templates

8 preset timing grids beyond simple swing:

| Groove | Character |
| --- | --- |
| **Straight** | No offset — clean grid |
| **Shuffle** | Heavy triplet swing |
| **Swing 54** | Lighter swing feel |
| **Laid Back** | Everything pushed slightly behind the beat |
| **Pushed** | Everything slightly ahead of the beat |
| **Humanoid** | Irregular human-style offsets per step |
| **MPC** | Classic MPC swing pattern |
| **Trap** | Triplet-influenced trap feel |

Groove templates combine with the Swing slider for additional shaping.

### Patterns

* **8 pattern slots** — switch instantly or queue during playback (switches happen at the next bar)
* **Copy** — duplicate any pattern to any other slot, with live diff overlay on hover
* **Chain mode** — automatically advances through patterns 1→2→3…→8→1…
* **Song mode** — arrange patterns into a linear sequence (up to 16 steps, each repeating ×1–8)
* **Transpose** — per-pattern pitch shift of ±12 semitones

### Generative Tools

* **Random** — sparse probabilistic fill respecting locked rows
* **Mutate** — evolves the current pattern with 4 intensity levels (Low / Med / High / Chaos)
* **Auto-Mutate** — triggers mutation automatically every 2, 4, 8, or 16 bars
* **Euclidean Generator** — distributes beats as evenly as possible across a row's step length (Bjorklund algorithm)

### Scale Lock

Quantises all voices to a musical scale in real time:

| Scale |
| --- |
| Free (no quantisation) |
| Major |
| Minor |
| Dorian |
| Phrygian |
| Lydian |
| Mixolydian |
| Minor Pentatonic |
| Major Pentatonic |
| Chromatic |

Root note selectable across all 12 chromatic pitches.

### Themes — 6 Colour Palettes

| Theme | Character |
| --- | --- |
| **Neon** | Cyan / Magenta — the default dark neon look |
| **Inferno** | Orange / Yellow — warm, fiery |
| **Forest** | Green — deep and organic |
| **Void** | Violet / Blue — cold and spacious |
| **Rose** | Pink / Purple — soft and dreamy |
| **Ice** | Sky Blue — crisp and minimal |

Themes repaint the entire UI instantly. Per-row custom colors override the theme on individual rows.

### Sample Pad Bank

16 velocity-sensitive sample pads for one-shot playback — drums, hits, stabs, anything.

* **Load** — right-click any pad to load an audio file onto it
* **Trigger** — click, or use keyboard shortcuts: `Q W E R` (top row), `A S D F` (middle), `Z X C V` (bottom), `1 2 3 4` (number row)
* **Clear** — right-click a loaded pad and select clear
* **Volume** — per-pad level control
* Pads fire through the master bus with reverb and delay available

Combine with the sequencer for hybrid pitched-melody + drum-hit arrangements.

### Collapsible Control Panel

Click the chevron button (or press `C`) to collapse the transport and control section, giving the sequencer grid and pad bank the full screen. State persists across sessions.

### Piano Roll

* Toggle with the **Roll** button
* Shows all 16 rows and 16 steps for the active pattern
* Probability shown as opacity
* Live playhead during playback
* Zoom levels: 1× / 2× / 3× / 4×

### Oscilloscope

* Live waveform display
* Gradient follows the active theme's colour range
* Flat line when idle

### MIDI

* **Web MIDI output** — select any connected MIDI device
* **Per-row channel routing** — each row defaults to its own channel (1–16), overridable
* **All Notes Off** sent on Stop
* **MIDI file export** — downloads a standard `.mid` file with:
  + Correct tempo track
  + Per-row tracks
  + Swing encoded as tick offsets
  + Velocity mapped from step probability
  + Export modes: Current pattern / All patterns / Chain

### Sharing & Presets

* **Share** — copies a URL with your full session LZ-compressed into the query string. Anyone with the link opens exactly your session.
* **Presets (1–5)** — save/load sessions to `localStorage`. Saves everything: patterns, all row settings, BPM, swing, scale, transpose, song arrangement, theme.

### Localisation

Full UI translation in 8 languages — English, Spanish, French, German, Russian, Chinese, Japanese, Korean — including all controls, labels, and help text. Select from the language dropdown in the top bar.

---

## Architecture

Chromatrack is intentionally a single HTML file with no build step, no bundler, and no runtime dependencies beyond Tailwind CSS (loaded from CDN for utility classes only).

### Audio Engine

* **Web Audio API** — all synthesis is built from raw oscillator, gain, biquad filter, and buffer source nodes
* **Web Worker scheduler** — a dedicated worker fires a 25ms tick, isolated from the main thread and immune to tab throttling
* **Lookahead buffering** — notes are scheduled 100ms ahead of the audio clock, eliminating jitter
* **Dynamics compressor** on the master bus
* **Convolution reverb** — procedurally generated impulse response, no external files required

### Timing

The scheduler uses the Web Audio clock (`audioCtx.currentTime`) as the source of truth. The worker tick wakes the scheduler, which schedules all notes within the lookahead window. Visual feedback is decoupled — a `visualQueue` holds scheduled events and `requestAnimationFrame` drains it in sync with the display.

### Synthesis

Every note creates a fresh node graph: oscillator(s) → gain envelope → per-row filter → reverb send → delay send → master gain → analyser → compressor → destination. Nodes are created and destroyed per-note. Sample playback uses AudioBufferSourceNode with pitch mapping.

### Polymetric Clock

Each row maintains its own step counter and a fractional accumulator. The speed multiplier (½×, 1×, 2×, 4×) advances the accumulator by a different amount each global tick, allowing rows to run at completely independent rates against the same master clock.

---

## Keyboard Shortcuts

| Key | Action |
| --- | --- |
| `Space` | Play / Stop |
| `R` | Toggle Record |
| `T` | Tap Tempo |
| `M` | Mutate |
| `F` | Fullscreen |
| `C` | Collapse / expand control panel |
| `1–8` | Switch pattern slots |
| `Q W E R` `A S D F` `Z X C V` `1 2 3 4` | Trigger sample pads |

---

## Browser Support

| Browser | Support |
| --- | --- |
| Chrome / Edge | ✅ Full — recommended |
| Firefox | ✅ Full |
| Safari | ✅ Works — Web MIDI requires a plugin |
| Mobile Chrome | ✅ Full touch support |
| Mobile Safari | ⚠️ Works — Web MIDI not available |

Web MIDI requires a secure context (HTTPS or localhost).

---

## Usage Tips

* **Polymetric grooves** — set different step lengths per row (3, 4, 5) and let them drift against each other
* **Step Lock for accents** — right-click the downbeat cell to give it a longer decay and a different waveform while keeping the row consistent elsewhere
* **Euclidean + lock** — generate a Euclidean pattern on a row, lock it, then mutate everything else around it
* **Sample + chord voicing** — load a short sample and set a chord type to voice it harmonically across steps
* **Song mode** — build 4–8 distinct patterns and arrange them into a full track with repeat counts
* **FM + long decay** — FM voice with the ∞ decay setting makes evolving metallic pads
* **Auto-mutate + prob lock** — lock your kick and bassline rows, enable auto-mutate every 4 bars, let the upper voices evolve while the groove stays anchored
* **Humanize** — even 10–20% makes programmed patterns feel significantly more alive
* **Share mid-session** — hit Share any time to get a URL that restores your exact session state

---

## Changelog

### v3.0.0
- **8 pattern slots** (up from 4)
- **Sample voice** — load any audio file as a pitched instrument per row
- **Step Lock** — per-step pitch, decay, and waveform overrides via right-click on active cells
- **Per-row chord voicings** — 9 types (Major, Minor, Dom7, Maj7, Min7, Dim, Aug, Sus4, Add9)
- **Per-row custom color picker** — click color dot to set any color, right-click to reset
- **8 groove templates** — Straight, Shuffle, Swing 54, Laid Back, Pushed, Humanoid, MPC, Trap
- **Share via URL** — full session LZ-compressed into a shareable link
- **8 localisations** — EN, ES, FR, DE, RU, ZH, JA, KO
- **Per-row reverb send** — 5 levels via row control panel
- **16-pad sample bank** — load audio onto pads, trigger via keyboard or click
- **Collapsible control panel** — hide transport to maximise grid view, persists in localStorage

### v2.0.0
- Song mode
- Chain mode
- Per-row arpeggiator
- Per-row filter (cutoff + resonance)
- Per-row delay send
- Probability steps
- Auto-mutate
- Piano roll

### v1.0.0
- Initial release

---

## License

MIT — do whatever you want with it.

---

## Credits

Built with the Web Audio API, a Web Worker, and an unreasonable amount of attention to timing accuracy.

**ConsciousNode SoftWorks**
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
