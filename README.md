# Perceptual Frequency Trainer (PFT-1)

A single-file, browser-based brainwave entrainment and intuition training application built with vanilla HTML, CSS, and JavaScript. No dependencies. No build step. Open and run.

---

## Overview

PFT-1 combines isochronic/binaural audio entrainment, synchronized visual stimulation, and a suite of psi training exercises into one self-contained tool. It is designed for researchers, meditators, musicians, and curious experimenters who want to explore the relationship between brainwave frequency states and cognitive/perceptual performance.

---

## Features

### Audio Engine
- **Isochronic Tones** — Precisely scheduled sawtooth pulse beats using the Web Audio API lookahead scheduler for tight timing accuracy
- **Binaural Beats** — Stereo sine waves with a per-ear frequency offset equal to the target frequency; left/right panning handled via `StereoPannerNode`
- **Frequency Range** — 1 Hz to 50 Hz (0.5 Hz steps), spanning all five classical brainwave bands
- **Pink Noise (Ganzfeld)** — Optional broadband noise layer for sensory reduction protocols
- **Volume Control** — Independent master gain slider

### Brainwave Bands

| Band   | Range      | State              |
|--------|------------|--------------------|
| Delta  | < 4 Hz     | Deep Sleep         |
| Theta  | 4–8 Hz     | Meditative Drift   |
| Alpha  | 8–13 Hz    | Relaxed Focus      |
| Beta   | 13–31 Hz   | Active Cognition   |
| Gamma  | > 31 Hz    | High-Speed Binding |

### Visual Entrainment Engine
- **Strobe Sync** — Flash overlay pulses in phase with each isochronic beat
- **Focus Modalities**
  - *Point Focus* — Animated reticle with counter-rotating rings and crosshair
  - *Sensory Viz* — Multi-layer sine wave interference patterns synced to frequency
  - *Aura Field* — Multi-band interference waveform overlay
- **Ganzfeld Deprivation** — Full-screen red overlay to reduce visual input and promote perceptual noise

### Psi Training Suite (5 Modes)

All five modes log results to `localStorage` and feed the shared analytics engine.

| Mode | Description |
|------|-------------|
| **Zener Cards** | Classic 5-symbol forced-choice card guessing (circle, cross, wave, square, star) |
| **Remote Viewing** | Timed focus/sketch/reveal protocol — 8s focus, sketch impressions, compare to hidden shape |
| **Precognition** | Select a symbol *before* a random outcome is generated |
| **Signal Detection** | Click anomalies on a noise field; scored by hits, false alarms, and d-prime (d′) |
| **Symbol Drift** | Observe morphing polygonal shapes; open-ended pattern observation |

### Analytics Engine
- Tracks total guesses, correct guesses, and per-band accuracy across all psi modes
- Rolling average (last 20 trials)
- Z-score significance test (threshold: |z| > 2.0 flagged as notable)
- Per-band breakdown cards (Delta through Gamma)
- All data persisted to `localStorage`; clearable from the UI

### Grounding Protocol
- Triggered manually (button or `G` key) or as a safety reset
- Resets frequency to 8 Hz (Alpha low-end)
- Displays a 5-step somatic grounding sequence
- Full-screen modal blocks session interaction until dismissed

### Session Metrics Dashboard
- Elapsed session timer (MM:SS)
- Active frequency and band label
- Processing tier (T-1 through T-5)
- Beat interval in milliseconds
- Live bar visualizer and entrainment protocol description
- Waveform preview canvas

---

## Safety

A safety acknowledgment screen appears on first load. The app produces flickering visual stimuli.

> **Do not use if you have photosensitive epilepsy or a history of seizures.**  
> Do not use while driving or operating machinery.  
> Take a 5-minute break every 25 minutes.  
> Discontinue use if you experience discomfort, headache, or visual disturbance.

---

## Keyboard Shortcuts

| Key       | Action                          |
|-----------|---------------------------------|
| `Space`   | Play / Pause                    |
| `G`       | Activate Grounding Protocol     |
| `P`       | Open / Close Psi Training panel |
| `Esc`     | Close active overlay            |

---

## Usage

1. Open `perceptual-frequency-trainer.html` in any modern browser (Chrome, Firefox, Edge, Safari)
2. Read and acknowledge the safety notice
3. Adjust the **Target Frequency** slider to your desired Hz
4. Press **Play** (or `Space`) to begin audio entrainment
5. Optionally enable **Visual Sync** to add strobe pulsing
6. Switch focus modality tabs (Point / Sensory / Aura) in the visual panel
7. Enable **Binaural Mode** toggle to switch from isochronic to binaural beats
8. Press **P** or the Psi Training button to open the intuition trainer
9. Press **G** at any time to pause and run the grounding protocol

---

## State Persistence

Session preferences (frequency, volume, binaural mode, sync state, focus modality) are saved to `localStorage` under the key `pftstate` and restored on next load. Psi statistics are stored separately under `pftpsistats` and `pftanalyticsengine`.

---

## Technical Notes

- **No dependencies** — pure HTML5, CSS custom properties, and vanilla JavaScript
- **Web Audio API** — lookahead scheduling (`LOOKAHEAD_MS = 25ms`, `SCHEDULE_AHEAD = 0.1s`) prevents click artifacts
- **Responsive layout** — CSS Grid with breakpoints at 900px and 540px
- **Accessibility** — ARIA roles, labels, and `aria-selected` on all interactive controls; `prefers-reduced-motion` respected
- **Performance** — Animation frames are throttled (`FRAME_MIN_MS = 33ms`) and cancelled on pause/close to prevent runaway RAF loops
- **HiDPI** — All canvas elements scale by `devicePixelRatio`

---

## File Structure

```
perceptual-frequency-trainer.html   ← entire application (single file)
```

---

## License

© Ego Sum Media. All rights reserved.
