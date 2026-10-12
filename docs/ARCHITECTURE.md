# 🏛️ PulseMusic Architecture & Engineering Specification

## 1. System Overview

PulseMusic is designed with a decentralized, serverless architecture that prioritizes audiophile audio fidelity, local data autonomy, and private peer-to-peer connectivity.

```mermaid
graph TD
    subgraph UI_Layer [User Interface Layer]
        Compose[Android: Jetpack Compose]
        QtShell[Desktop: PySide6 / Qt6 Frameless Shell]
        KaraokeUI[Dual-Screen Karaoke Stage]
        StemUI[CDJ Pro Stem Deck]
    end

    subgraph Audio_Engine [Audiophile Audio & DSP Engine]
        FLAC_Stream[Bit-Perfect FLAC 24-bit / 96kHz Stream]
        CPPDSP[Native C++ DSP Core: pulse_audio_dsp]
        EQ10[10-Band Parametric Biquad IIR Equalizer]
        DSEE[DSEE Extreme™ AI Harmonic Reconstruction]
        StemEngine[Demucs HT Real-Time 4-Stem Separator]
        Visualizer[64-Band Real-Time FFT Spectrum Analyzer]
    end

    subgraph Network_P2P [Decentralized P2P & Transport]
        TorMesh[Tor Onion Services P2P Mesh]
        LAN_Connect[LAN TCP 8974 / mDNS Zero-Conf]
        LiveSync[Pulse Live-Sync v1.2 Protocol]
        Scraper[Metadata Engine: MusicBrainz / Deezer / LRCLIB]
    end

    subgraph Storage [Local Autonomous Persistence]
        SQLite[Desktop: SQLite WAL Mode]
        Room[Android: Room SQLite]
        Cache[Multi-Bitrate Offline Audio Cache]
    end

    UI_Layer --> Audio_Engine
    UI_Layer --> Network_P2P
    Audio_Engine --> Storage
    Network_P2P --> Storage
```

---

## 2. Audio Processing Pipeline

The audio engine processes incoming streams without destructive intermediate resampling:

```mermaid
flowchart LR
    Source[Lossless FLAC Stream] --> Decoder[PCM 32-bit Float Decoder]
    Decoder --> RingBuffer[Zero-Copy Lockless Ringbuffer]
    RingBuffer --> EQ[10-Band Biquad IIR EQ]
    EQ --> DSEE[DSEE Extreme AI Overtone Synthesizer]
    DSEE --> Stems[4-Channel Stem / Vocal Isolator]
    Stems --> Limiter[True-Peak Brickwall Limiter]
    Limiter --> Output[Hardware Output: WASAPI / PipeWire / CoreAudio]
    Limiter -.-> FFT[64-Band FFT Spectrum Analyzer]
```

### Digital Signal Processing (DSP) Chain
1. **Decoded Floating-Point Stream:** 32-bit floating-point audio data normalized to `[-1.0, +1.0]`.
2. **10-Band Parametric Biquad IIR Filter:** Frequency bands at 31Hz, 62Hz, 125Hz, 250Hz, 500Hz, 1kHz, 2kHz, 4kHz, 8kHz, 16kHz with adjustable Q-factor and preamp headroom control.
3. **DSEE Extreme™ AI Reconstruction:** High-frequency spectral extrapolation identifying compressed cutoffs (e.g., 16–20 kHz) and synthesizing natural acoustic overtones up to 24+ kHz.
4. **Demucs HT AI Source Separation:** Real-time deep neural network separating audio into **Vocals**, **Drums**, **Bass**, and **Instruments**.
5. **Phase-Accurate 64-Band Spectrum Analysis:** Hardware-accelerated Fast Fourier Transform computed at 60 FPS with ballistic peak decay.
