# 🎤 AI Karaoke Mode & CDJ Stem Deck Guide

PulseMusic integrates state-of-the-art neural audio source separation and professional DJ performance tooling directly into the playback client.

---

## 1. AI Karaoke Mode

### Real-Time Vocal Separation (HTDemucs)
PulseMusic utilizes the Hybrid Transformer Demucs (HTDemucs) neural network to isolate vocal signals from accompanying instrumental tracks in real time:
- **0% (Pure Instrumental):** Complete lead vocal removal for studio-quality karaoke accompaniment.
- **15% (Subtle Guide Vocals):** Gentle backing track preservation mimicking professional karaoke systems (e.g., Singa guide vocal mode).
- **100% (Original Master):** Natural unattenuated mix.

### Word-by-Word Synchronized Lyrics
- **Syllable-Level Timing Interpolation:** Parses high-precision extended LRC time stamps (`<00:12.40>`) and dynamically calculates phonetic weights for smooth, continuous lyric illumination.
- **Lead-In Visual Countdown:** Automatically detects pauses exceeding 4.5 seconds and renders 3 progressive countdown indicators before the singer's next vocal entry.
- **Dual-Screen TV Stage Mode:** Press `F11` or click the TV icon to launch the distraction-free fullscreen stage view designed for external monitors, living room televisions, or event projectors.

---

## 2. CDJ Pro Stem Deck

Inspired by industry-standard DJ hardware (Pioneer CDJ-3000 / DDJ-FLX10), the Stem Deck provides tactile multitrack mixing:

### Multitrack Stem Channels
- **🎤 Vocals Channel:** Volume slider, instant Mute, and Solo toggle.
- **🥁 Drums Channel:** Frequency-accurate percussion isolation.
- **🎸 Bass & Instruments Channel:** Harmonically isolated chord progressions and sub-bass lines.

### DJ Performance Controls
- **Interactive Vinyl Jog Wheel:** Touch-sensitive scratch response with rotational inertia and visual platter positioning.
- **Performance Quick-Pads:**
  - `Acapella Solo`: Instantly isolates vocals while muting all instruments.
  - `Instrumental (Karaoke)`: Instantly strips vocals for live singing or crowd sing-alongs.
  - `Drum Break`: Drops all melodic elements, leaving only the driving beat.
  - `Normal`: Restores the complete mix immediately.
- **Camelot Harmonic Key Matching:** Identifies the musical key (e.g., `8A`, `11B`) and alerts DJs to harmonically compatible tracks on the Camelot wheel.
- **Pitch Bend & Tempo Slider:** Smooth $\pm 16\%$ BPM tempo adjustment with quantized snap-to-zero detent.
- **Quantized Beat Loops & Hot Cues:** Instant cue points (1–4) and loop brackets (1/2, 1, 2, 4, 8, 16 beats).
