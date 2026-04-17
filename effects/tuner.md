# Tuner

Analyzes the input signal and displays pitch (note / octave / cents). It sits at the head of the chain and is unaffected by downstream effects.

![Tuner screen](../screenshots/effect-tuner.png)

## Layout

```
┌──────────────────────────────────────────┐
│  Tuner                        [ ON ]     │
├──────────────────────────────────────────┤
│                                          │
│              A                           │  ← detected note
│           2  -3¢                         │  ← octave + cents
│       ●──────────○──────────●           │  ← cents gauge
│                                          │
│        440.0 Hz       conf 96%           │  ← frequency / confidence
│                                          │
│           [ 🔇  Mute ]                   │
└──────────────────────────────────────────┘
```

## Readouts

- **Note (large)**: nearest of the 12 semitones (A–G♯)
- **Octave**: 2–6 range (covers standard acoustic tuning E2–E4 area)
- **Cents**: ±100 from the target note. `0¢` means in tune.
- **Cents gauge**: center ● = in tune, left = flat, right = sharp
- **Frequency**: detected frequency in Hz
- **Confidence**: 0–100%. Drops on noise or silence

## Controls

### ON/OFF (header capsule)
- **ON**: tuner tap is active. Unless Mute is also on, audio still passes through the chain.
- **OFF**: the tuner UI stops; input passes through normally.

### Mute
- Blocks the output while tuning so the audience doesn't hear it.
- Turn Mute off to resume playing.

## Tips

- **Live tuning routine**:
  1. Select the Tuner → enable Mute.
  2. Tune your strings.
  3. Disable Mute → back to playing.
- **Low confidence (< 60%)** usually means the level is too low or you're playing chords. Pluck a single note.
- **Drop / down tunings** are supported — the octave display follows along.

## Standard Acoustic Tuning Reference

| String | Note | Frequency |
|--------|------|-----------|
| 1 (high) | E4 | 329.63 Hz |
| 2 | B3 | 246.94 Hz |
| 3 | G3 | 196.00 Hz |
| 4 | D3 | 146.83 Hz |
| 5 | A2 | 110.00 Hz |
| 6 (low) | E2 | 82.41 Hz |
