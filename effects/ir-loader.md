# IR Loader

Loads a WAV/AIFF file and applies it via convolution, reproducing the captured response of a **guitar body, mic, room, or speaker cab**. For acoustic guitar the most common use is a **body IR** — a studio-mic recording of a specific instrument's resonance.

<img src="../screenshots/effect-ir.png" alt="IR Loader screen" width="320">

## Parameters

| Param | Range | Description |
|-------|-------|-------------|
| **Load IR** | Button | Pick a WAV/AIFF file (iOS Files picker) |
| **Mix** | 0–100 % | Dry ↔ Wet balance |
| **Gain** | −12 to +12 dB | Level trim after IR processing |

## What's an IR?

An Impulse Response is a file that captures the **frequency and time response of a specific space, mic, or speaker**. Convolving your signal with an IR makes it sound like it was recorded through that system.

Common acoustic IR types:
- **Body IR**: captures a guitar body's resonance (e.g. Martin D-28) — cheap pickup → expensive-mic tone
- **Room IR**: studio / church / chamber
- **Mic IR**: a specific microphone's response (e.g. Neumann U87)
- **Speaker IR**: electric amp cab — not recommended for acoustic

### 1. Prepare your IR
- WAV or AIFF format
- 48 kHz recommended (matches the app default)
- Under 200 ms (typical for acoustic)

Popular sources:
- **3 Sigma Audio** — Martin, Taylor, Gibson body IRs
- **ML Sound Lab** — studio / room IRs
- **DIY** — record your own guitar through a good mic

### 2. Get it on your iOS device
- Copy to Files via iCloud Drive, Dropbox, AirDrop.
- Or sync through iTunes/Finder to the app's container.

### 3. Load it
1. Select the IR Loader → confirm the header **ON**.
2. Tap **Load IR** → pick your WAV/AIFF.
3. The filename appears when loaded.

### 4. Blend
- **Mix**: start at 70–100 % to hear the full IR effect.
- **Gain**: compensate if the level jumps after loading.

### Body IR (pickup → mic tone)
- Mix **80–100 %**, Gain 0 dB
- AMP Speaker Sim **OFF** (the body IR already provides the finished tone)

### Room IR (space only)
- Mix **30–50 %**, Gain −3 dB
- Keep the existing tone and add spatial feel

### Layering
Only one IR slot is supported. For stacked effect, combine **AMP Speaker Sim + IR Loader** (cab + body), or use Reverb's Room settings alongside an IR.

## IR Loader + AMP Speaker Combinations

| Source | Recommended |
|--------|-------------|
| Pickup DI + body IR loaded | AMP Speaker **OFF**, IR Mix 100 % |
| Pickup DI + no IR | AMP Speaker **ON** |
| Microphone + no IR | AMP Speaker **OFF** (already has mic tone) |
| Microphone + room IR | AMP Speaker **OFF**, IR Mix 30–40 % |
