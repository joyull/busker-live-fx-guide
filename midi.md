# MIDI Foot Controller Mapping

Remote-control presets, effect bypass, looper commands, and tap tempo from an external MIDI controller.

## Supported Connections

- **USB MIDI** (Lightning-to-USB camera adapter, USB-C hub)
- **Bluetooth MIDI** (pair via iOS Settings → Bluetooth MIDI scan)
- **Network MIDI** (another device on the same Wi-Fi network)

## Screen Layout

Tap **🎛 MIDI** in the title bar → MIDI Controller screen.

![MIDI Controller screen](screenshots/midi-main.png)

```
┌─────────────────────────────────────────┐
│  ← MIDI Controller            Done     │
├─────────────────────────────────────────┤
│  MIDI DEVICE                            │
│  ✓  MeloAudio MIDI Commander            │
│                                         │
│  MAPPINGS                            +  │
│  Tap Tempo                              │
│    CC #64 ch 1  →  Tap Tempo   [Learn] │
│  Preset Next                            │
│    CC #65 ch 1  →  Preset Next [Learn] │
│  Looper REC A                           │
│    Note 60 ch 1 →  Looper REC A[Learn] │
└─────────────────────────────────────────┘
```

### Top: MIDI Device
Connected MIDI devices. The checkmark shows the active one. A single device is auto-selected; tap to switch when multiple are connected.

### Bottom: Mappings
Registered mappings, one per row:
- Auto-generated name
- Trigger (what MIDI message comes in) → Action (what happens)
- **Learn** button to relearn the trigger

Use **+** in the header to add a new mapping.

## Adding a Mapping

Tap **+** → the Add Mapping sheet appears.

![Add MIDI mapping](screenshots/midi-add.png)

```
┌─────────────────────────────────────────┐
│  Cancel   Add Mapping          Add     │
├─────────────────────────────────────────┤
│  MIDI TRIGGER                  [Learn] │  ← pinned
│  [ CC  NOTE  NOTE_OFF  PC ]            │
│  Ch 1          # 64                    │
├─────────────────────────────────────────┤
│  SELECTED ACTION                        │
│  (Tap a section below, then pick)      │
│                                         │
│  ▸ Global    (9)                       │  ← scrolls
│  ▸ Effect   (10)                       │
│  ▸ Looper   (12)                       │
└─────────────────────────────────────────┘
```

### 1. Set the trigger (top, pinned)
- **Message Type**: CC / NOTE (On) / NOTE_OFF / PC (Program Change)
- **Channel**: 1–16
- **Number**: CC / Note / PC number (0–127)

**Learn is easiest**: tap Learn, press the footswitch you want, and the channel/type/number fill in automatically.

### 2. Pick an action (bottom, scrollable)
Actions are grouped into 3 sections. Expand a section and tap to select.

#### Global (app-wide)
| Action | Effect |
|--------|--------|
| Preset Next / Prev | Cycle saved presets |
| Channel Next / Prev | Move to next/previous channel |
| Channel Select 1–4 | Jump to a specific channel |
| Tap Tempo | Sets the Delay Time parameter by tap rhythm |

#### Effect (bypass toggles)
On/off for each of the channel's 10 effects:
- Tuner / Compressor / EQ / AMP / Boost / IR Loader / Doubler / Chorus / Delay / Reverb

#### Looper (12 commands)
For both Loop A and Loop B:
- Record / Play / Stop / Overdub / Undo / Clear

### 3. Tap Add

## Examples

### Boss FS-7 2-button switch → Tuner + Boost bypass
1. Plug in the USB MIDI adapter — the device auto-appears.
2. + → Learn → step on FS1 → CC 82 captured.
3. Effect section → **Tuner Bypass** → Add.
4. + → Learn → step on FS2 → CC 83 captured.
5. Effect section → **Boost Bypass** → Add.
6. FS1 now toggles the tuner, FS2 toggles solo boost.

### Tap tempo from a MIDI controller
1. + → Learn → press the button you want for tap.
2. Global section → **Tap Tempo** → Add.
3. Tap that button in the tempo you want — the Delay Time updates automatically.

### 3-button looper control (REC / OVR / STOP)
1. FS1 → Learn → Looper → **Looper Record (Loop A)** → Add.
2. FS2 → Learn → **Looper Overdub (Loop A)** → Add.
3. FS3 → Learn → **Looper Stop (Loop A)** → Add.
4. Full hands-free looping.

## Editing & Deleting

- **Delete**: swipe left on a row in the Mappings list.
- **Change trigger only**: tap **Learn** on that row → send the new MIDI message. The action is preserved.
- **Change the action**: delete the mapping and re-add.

## Notes

- Mappings are **saved separately from presets** — switching presets doesn't change your MIDI setup.
- If two mappings share the same trigger, both fire. Usually you want to avoid that.
- **Continuous CC control (moving knobs with a CC) is not exposed in the UI** — only click-style toggles for effects and the looper.
- Disconnecting a MIDI device keeps mappings saved; reconnect to use them again.
