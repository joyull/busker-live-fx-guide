# EQ — Parametric Equalizer

6-band EQ plus a high-pass filter, a narrow notch, and a phase-invert switch. Designed around the acoustic guitar's typical **feedback frequencies** and **box-tone resonance**.

![EQ screen](../screenshots/effect-eq.png)

## Layout

```
┌─────────────────────────────────────────────────┐
│  Parametric EQ                       [ ON ]     │
├─────────────────────────────────────────────────┤
│     [ Normal | Invert ]   Phase                 │
│                                                  │
│   🎛 HPF   🎛 85Hz   🎛 350Hz  🎛 700Hz         │  ← Row 1
│   🎛 1.6k  🎛 4.8k   🎛 10k    🎛 Notch         │  ← Row 2
└─────────────────────────────────────────────────┘
```

## Parameters

| Param | Range | Purpose |
|-------|-------|---------|
| **Phase** | Normal / Invert | 180° phase flip — feedback control, mix-phase alignment |
| **HPF** (High Pass) | Off, 20–120 Hz | Low-end cut. Kills stage rumble and thumps |
| **85 Hz** | −9 to +9 dB | Low body (boomy range) |
| **350 Hz** | −9 to +9 dB | Box tone (acoustic resonance center) |
| **700 Hz** | −9 to +9 dB | Low-mid (wood) |
| **1.6 kHz** | −9 to +9 dB | Mid (finger attack) |
| **4.8 kHz** | −9 to +9 dB | High presence (pick noise) |
| **10 kHz** | −9 to +9 dB | Air |
| **Notch** | Off, 20–300 Hz | Narrow single-band cut — kills a specific feedback frequency |

## Acoustic Guitar EQ Starter Recipes

### Clean-up (starting point)
- **HPF 80 Hz**: remove rumble
- **350 Hz: −3 dB**: reduce box tone (works on almost every acoustic)
- **4.8 kHz: +2 dB**: add presence
- **10 kHz: +1 dB**: subtle air

### Fighting feedback
1. Roll **HPF** up to 80–100 Hz for low-end feedback
2. If feedback occurs, identify the frequency and **Notch** it out
   - Dreadnought-class feedback: 100–220 Hz
   - OM/parlor models: 200–350 Hz

### When to Phase Invert
- **Stage monitor interaction** thinning the low end → try flipping
- **Two mics on one guitar** → align phase
- If flipping makes the sound thicker, you had a phase problem

### Genre starting points

| Genre | 85 Hz | 350 Hz | 700 Hz | 1.6k | 4.8k | 10k |
|-------|-------|--------|--------|------|------|-----|
| Fingerstyle | 0 | −2 | −1 | 0 | +2 | +1 |
| Strumming (pop) | +1 | −3 | 0 | 0 | +3 | +1 |
| Bluegrass / flatpicking | 0 | −4 | −1 | +1 | +4 | +2 |
| Ambient / layered | +1 | −2 | 0 | −1 | +1 | +2 |

## Signal Chain Note

EQ sits **after Compressor, before the AMP** in the chain. Because the AMP has its own tone stack, use the EQ mainly for **feedback control, resonance cleanup, and overall brightness** — not for the core tone shaping.
