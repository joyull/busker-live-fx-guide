# Delay

Repeats the input signal at a set time interval. Two modes: **Digital** (clean, precise) and **Tape** (warm, organic). On acoustic guitar it's used for fingerstyle space, ambient layering, slapback echo, and more.

![Delay screen](../screenshots/effect-delay.png)
<!-- SCREENSHOT: Delay — top row Mod Rate + Mode picker + TAP, Normal/Fast appears in Tape mode -->

## Layout

```
┌───────────────────────────────────────────────────┐
│  Delay                                [ ON ]      │
├───────────────────────────────────────────────────┤
│  🎛 Mod Rate    [ Digital | Tape ]    [ TAP ]     │  ← Row 1
│                 [ Normal  | Fast ]                │     (Tape only)
│                                                    │
│  🎛 Time  🎛 Feedback  🎛 Mix   🎛 Filter/Age     │  ← Row 2
│                                                    │
│  🎛 LF Cut  🎛 Grit/Bias  🎛 Mod   🎛 Smear/LoC   │  ← Row 3
└───────────────────────────────────────────────────┘
```

> ⚠️ **Several labels change with Mode.** Switching between Digital and Tape renames Filter/Age, Grit/Bias, Mod/Wow·Flut, Smear/Lo Contour, and Mod Rate/Crinkle on the same knob positions.

## Modes

### Digital
Clean, precise repeats. Best for fingerstyle / ambient. 60–2500 ms range.

### Tape (dTape)
Emulates a tape machine's natural degradation:
- **wow / flutter / crinkle** add subtle pitch drift
- Tape saturation warms and darkens each repeat
- Adds a **Speed (Normal/Fast)** picker
  - **Normal**: standard (60–2500 ms)
  - **Fast**: hi-fi (30–1250 ms, wider bandwidth)

## Parameters

| Param | Range | Description |
|-------|-------|-------------|
| **Time** | 60–2500 ms | Delay time |
| **Feedback** | 0–100 % | Repeats (100 % = infinite). Tape auto-limits via saturation |
| **Mix** | 0–100 % | Dry/wet ratio. Auto-ducks while you play |
| **Filter** (Digital) / **Age** (Tape) | 1k–20k Hz | Digital: HF cut / Tape: tape aging amount |
| **LF Cut** | 20–500 Hz | Low-cut inside the feedback loop |
| **Grit** (Digital) / **Bias** (Tape) | 0–100 % | Digital: repeat distortion / Tape: tape bias |
| **Mod** (Digital) / **Wow/Flut** (Tape) | 0–100 % | Digital: modulation amount / Tape: wow+flutter depth |
| **Mod Rate** (Digital) / **Crinkle** (Tape) | 0.1–5 Hz | Digital: LFO rate / Tape: crinkle frequency |
| **Smear** (Digital only) | 0–100 % | Softens the attack of repeats |
| **Lo Contour** (Tape only) | 0–100 % | Low-end shape on repeats |

## TAP Tempo

Tap the round **TAP** button at the top-right at your target tempo — Time is set automatically. A MIDI footswitch can do the same via [MIDI guide](../midi.md) → Global → Tap Tempo.

## Auto-Duck

While you're playing, the wet signal is **auto-attenuated to 40 %**, then swells back up during pauses. If that's too much, raise Mix to compensate.

## Recommended Settings

| Use | Time | Feedback | Mix | Filter/Age | Mode | Mod |
|-----|------|----------|-----|------------|------|-----|
| Subtle ambience | 120 ms | 20 % | 15 % | 3.5 kHz | Digital | 0 % |
| Slapback | 100 ms | 5 % | 20 % | 5 kHz | Tape Normal | 0 % |
| Fingerstyle | 350 ms | 35 % | 20 % | 4 kHz | Digital | 0 % |
| Ambient / worship | 700 ms | 50 % | 30 % | 3 kHz | Digital | 15 % |
| Warm echo | 400 ms | 40 % | 25 % | 2.5 kHz (Age) | Tape Normal | 0 % |
| Long soundscape | 1200 ms | 60 % | 40 % | 2 kHz | Digital | 10 % |

## Feedback Guide

- **0–10 %**: single echo (slapback)
- **20–40 %**: natural repeats
- **50–70 %**: long tails (ambient)
- **80 %+**: approaching self-oscillation — watch out!  
  Tape auto-limits via saturation.

## Time Ranges

- **80–150 ms**: Slapback / short ambience
- **250–400 ms**: Fingerstyle default
- **500–1000 ms**: Ambient / worship
- **1000 ms+**: Soundscapes, pads

## Digital vs Tape

| Aspect | Digital | Tape |
|--------|---------|------|
| Accuracy | High (precise) | Lower (intentional drift) |
| Highs | Preserved | Darken each repeat |
| Feel | Clean | Warm, organic |
| Best for | Fingerstyle, ambient, precision | Strumming, soloing, vintage |
