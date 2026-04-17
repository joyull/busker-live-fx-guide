# Full App Guide

Overall feature guide for the acoustic-guitar multi-effector. For per-effect details, see [Per-Effect Manuals](effects/).

## 1. App Layout at a Glance

<img src="screenshots/home.png" alt="Home screen" width="320">

### 1-1. Title bar (top)

- **☰ Presets** — load saved presets or save the current state
- **🎛 MIDI** — MIDI foot-controller mapping screen ([MIDI guide](midi.md))
- **⚙ Settings** — audio interface, buffer size, background audio, etc.

### 1-2. Channel header

Defaults to a single collapsed row. Tap to expand and reveal the channel type toggle (Guitar/Vocal) and gain/pan sliders.

<img src="screenshots/channel-expanded.png" alt="Channel header expanded" width="320">

**Channel model**
- Up to **4 simultaneous channels** (CH1–CH4). The app matches the physical input count of your audio interface.
- Each channel is either **Guitar** or **Vocal**, each with its own signal chain:
  - Guitar: Tuner → Comp → EQ → AMP → Boost → IR → Doubler → Chorus → Delay → Reverb
  - Vocal: Comp → EQ → Reverb
- **Swipe** left/right on the header (or tap page dots) to switch channels. No swipe when only 1 channel is active.

**Controls in the header**
- **CH number + 🎸/🎤 icon** — current channel type
- **+3dB · C** — gain and pan summary (C = center, L/R50 = left/right 50%)
- **⏻ power** — turn the channel on/off (off channels don't process audio)
- **⌄ / ⌃ chevron** — toggle expanded view
- When expanded, use the **Guitar | Vocal** capsule to change channel type

### 1-3. Signal chain bar

The effect sequence for the current channel. **Tap** an effect box to switch the editor to it. **Long press** to toggle on/off. Green border = active, gray = bypassed.

- The small bar above each box is a **peak level meter** after that effect.
- The selected effect is highlighted in blue.

### 1-4. Effect editor

Shows the parameters for the selected effect. The **ON/OFF capsule** on the top-right bypasses that effect. Knobs respond to **vertical drag**; double-tap to restore the default value.

### 1-5. Looper bar (bottom)

Always visible. See the [Looper guide](looper.md) for full details.

- Tap the **Looper title** to expand/collapse the detail panel.
- The **toggle on the right** enables/disables the looper as a whole (disabled = excluded from the DSP chain, saves CPU).

### 1-6. Status bar (bottom)

- **Input level** (dB + meter)
- **Sample rate / buffer size / round-trip latency**
- **Glitch counter** (✓ at 0, ⚠ at 1+)

### Guitar + vocal (2 channels)

1. Plug in a 2-input interface (Focusrite 2i2, Audient iD4, etc.).
2. Tap **CH1** header → expand → pick **Guitar**.
3. Swipe to **CH2** → expand → pick **Vocal**.
4. Long-press effects in the chain bar to enable/disable them per channel.
5. Sing and play — both channels process independently and mix to the output.

### Multi-guitar setup

- With a 4-input interface, set CH1–CH4 all to **Guitar** and run each with its own AMP, EQ, delay, etc.

## 3. Presets

**Save**
1. Dial in your sound (effect params + channel settings for all active channels).
2. ☰ in the title bar → **Save Current as Preset**.
3. Enter a name → Save.

**Load**
1. Tap ☰ → select a preset from the list.
2. The entire state loads immediately.

**Delete**
- Swipe left on a preset in the list.

**Note**: presets save the **entire 4-channel state**, not just the current channel.

## 4. Audio Interface

- **Required**: the app is designed around an external USB audio interface. The built-in mic works but with high latency and poor fidelity.
- Target latency: **< 5 ms round trip @ 48 kHz**, 64–128 sample buffer.
- Recommended devices: Focusrite Scarlett, Audient iD series, IK Multimedia iRig Pro Duo, Apogee Duet, SSL 2/2+, and similar.

**Physical vs loopback channels**
Some interfaces (Audient iD4, SSL 2+, MOTU M2, etc.) **report loopback channels on top of their physical inputs**. The app uses a known-device table to expose only real inputs, and for unrecognized devices you can manually set the channel count in ⚙ Settings.

## 5. Settings (⚙)

<img src="screenshots/settings.png" alt="Settings sheet" width="320">

- **Sample Rate**: 44.1 kHz / 48 kHz (default 48)
- **Buffer Size**: 32 / 64 / 128 / 256 samples (smaller = lower latency, higher glitch risk)
- **Background Audio**: keep audio running while the screen is locked
- **Physical Input Channels** (for supported devices): actual input count excluding loopback

## 6. Troubleshooting

| Symptom | Fix |
|---------|-----|
| Glitches or dropouts | Bump buffer size 64 → 128 or 128 → 256 |
| No input signal | Check interface connection; iOS **Settings → Privacy → Microphone** permission |
| Wrong channel count | Override it manually in ⚙ Settings |
| Sound wrong after loading a preset | Toggle the offending effect OFF → ON to reset its buffers |
| Latency too high | Verify 48 kHz + 64-sample buffer; check your interface's own latency spec |

If issues persist, include the interface model and Xcode console logs in a GitHub issue.
