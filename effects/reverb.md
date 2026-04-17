# Reverb

Adds spatial ambience. Based on a Dattorro Plate algorithm with 5 room presets, 5 main knobs, and an optional Shimmer layer — tuned for natural-sounding acoustic-guitar spaces.

![Reverb screen](../screenshots/effect-reverb.png)

## Layout

```
┌───────────────────────────────────────────────────┐
│  Reverb                              [ ON ]       │
├───────────────────────────────────────────────────┤
│  [Booth][Studio][Plate][Hall][Cathedral]          │  ← preset strip
│                                                    │
│    🎛 Mix      🎛 Decay     🎛 Tone               │  ← Row 1
│    🎛 Pre-Dly  🎛 Size     🎛 Shimmer             │  ← Row 2
│                                                    │
│           ⌄ Engineer View                         │  ← (Debug build)
└───────────────────────────────────────────────────┘
```

## Room Presets

The horizontal strip at the top snaps Mix / Decay / Tone / Pre-Dly / Size to preset values in one tap.

| Preset | Feel | RT60 | Size |
|--------|------|------|------|
| **Booth** | Small, dry (vocal booth) | ~0.4 s | Small |
| **Studio** | Medium studio room | ~1.0 s | Medium |
| **Plate** | Studio plate | ~1.8 s | Medium–large |
| **Hall** | Concert hall | ~3.5 s | Large |
| **Cathedral** | Cathedral | ~7.5 s | Huge |

You can tweak individual knobs after selecting a preset (the preset stays highlighted only while all 5 values match).

## Main Parameters

| Param | Range | Label shows | Description |
|-------|-------|-------------|-------------|
| **Mix** | 0–100 % | % | Dry/wet ratio |
| **Decay** | 0–100 % | RT60 (s) | Tail length. Live RT60 reflects Size coupling |
| **Tone** | 0–100 % | Hz/kHz | Tail brightness (damping LPF freq) |
| **Pre-Dly** | 0–100 % | ms | Pre-delay — gap between dry and wet |
| **Size** | 0–100 % | × (scale) | Room-size scale affecting decay and diffusion |

> 💡 **Knobs display real physical values** — e.g. Decay "1.8s", Tone "4.2k", Pre-Dly "35ms". You tune in real units, not abstract 0–100 %.

## Shimmer (optional)

Active when `shimmer > 1 %`. Feeds a pitch-shifted copy (one octave up) into the reverb tail for a heavenly texture. Popular for acoustic fingerstyle / ambient.

- **0 %**: off
- **20–40 %**: subtle sparkle
- **50–80 %**: clearly audible shimmer layer
- **100 %**: full-on dreamy (can muddle pitch if overused)

> ⚠️ The Shimmer knob is **hidden on Vocal channels** (not suitable for vocals).

## Recommended Settings (acoustic fingerstyle)

| Use | Preset start | Mix | Decay | Tone | Pre-Dly | Size | Shimmer |
|-----|-------------|-----|-------|------|---------|------|---------|
| Studio recording | Studio | 25 % | 35 % | 55 % | 15 % | 30 % | 0 |
| Folk live | Booth | 18 % | 25 % | 65 % | 5 % | 10 % | 0 |
| Worship backing | Hall | 28 % | 60 % | 45 % | 35 % | 65 % | 15 % |
| Ambient layer | Cathedral | 35 % | 80 % | 40 % | 45 % | 85 % | 40 % |
| Fingerstyle live | Plate | 22 % | 45 % | 55 % | 20 % | 40 % | 0 |
| Dreamy intro | Cathedral | 40 % | 85 % | 35 % | 50 % | 90 % | 70 % |

## Parameter Deep Dive

### Mix
Too high and the tail drowns the original. **20–30 %** is usually ideal.

### Decay
Longer = bigger-sounding space. Acoustic fingerstyle sits around **1.0–2.5 s (Decay 35–55 %)**. Song backing can go 2 s+.

### Tone
- **40–50 %**: darker hall (classical)
- **55–65 %**: natural (recommended default)
- **70–85 %**: bright and spacious (great for live monitors)

### Pre-Dly
- **0–10 ms**: tail tight to the dry (small space)
- **20–40 ms**: natural sense of distance (default)
- **50–80 ms**: slapback-like rhythmic feel

### Size
Separate from Decay. Same RT60 with larger Size produces **more diffuse reflection patterns**. Note the computed RT60 label — it grows slightly when Size goes up, even if Decay is constant.

## Engineer View (Debug build only)

Developer tuning panel. Hidden entirely in Release builds — regular users won't see it.

## Signal Chain Tip

Reverb lives at the **end of the chain**, after Delay. This means the delay repeats also feed into the reverb, producing a coherent final spatial image.

When using Shimmer, lower the Delay Feedback a bit — both effects lengthen tails and the combination can get muddy.
