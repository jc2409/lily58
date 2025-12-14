# Lily58 Custom Keymap - jc2409

Custom QMK firmware configuration for Lily58 keyboard with RP2040 microcontroller.

## Hardware Specifications

- **Keyboard:** Lily58 (MechBoards variant)
- **Microcontroller:** RP2040 (using `rp2040_ce` converter)
- **RGB Lighting:** 74 LEDs total
  - 58 per-key RGB LEDs (SK6812MINI-E)
  - 16 underglow RGB LEDs (WS2812B-5050)
- **Display:** Dual OLED screens with Bongo Cat animation

## Features

### RGB Matrix
- **Total LEDs:** 74 (split 37/37 per half)
- **Maximum Brightness:** 120
- **Enabled Effects:**
  - Gradient Up/Down
  - Gradient Left/Right
  - Alphas/Mods highlighting
  - Breathing
  - Hue Wave
  - Rainbow Moving Chevron
  - Rainbow Beacon
  - Solid Reactive Simple
  - Solid Reactive
  - Solid Multi-Splash

### OLED Display
- **Left Half:** WPM counter with Bongo Cat animation
- **Right Half:** Layer status and Caps Lock indicator
- **Animation:** Bongo Cat with typing-reactive frames
- **Timeout:** 10 minutes of inactivity

### Split Keyboard Sync
Full state synchronization between keyboard halves for reactive RGB effects:
- Transport mirroring enabled
- Layer state sync
- LED state sync
- Modifier state sync

## Keymap Layers

### Layer 0: QWERTY
```
,-----------------------------------------.                    ,-----------------------------------------.
| ESC  |   1  |   2  |   3  |   4  |   5  |                    |   6  |   7  |   8  |   9  |   0  |  `   |
|------+------+------+------+------+------|                    |------+------+------+------+------+------|
| Tab  |   Q  |   W  |   E  |   R  |   T  |                    |   Y  |   U  |   I  |   O  |   P  |  -   |
|------+------+------+------+------+------|                    |------+------+------+------+------+------|
|LShift|   A  |   S  |   D  |   F  |   G  |-------.    ,-------|   H  |   J  |   K  |   L  |   ;  |  '   |
|------+------+------+------+------+------|   [   |    |    ]  |------+------+------+------+------+------|
|LCTRL |   Z  |   X  |   C  |   V  |   B  |-------|    |-------|   N  |   M  |   ,  |   .  |   /  |RShift|
`-----------------------------------------/       /     \      \-----------------------------------------'
                  | LAlt | LGUI |LOWER | /Space  /       \Enter \  |RAISE |BackSP| RGUI |
                  |      |      |      |/       /         \      \ |      |      |      |
                  `----------------------------'           '------''--------------------'
```

### Layer 1: LOWER
Function keys and symbols layer.
```
,-----------------------------------------.                    ,-----------------------------------------.
|      |      |      |      |      |      |                    |      |      |      |      |      |      |
|------+------+------+------+------+------|                    |------+------+------+------+------+------|
|  F1  |  F2  |  F3  |  F4  |  F5  |  F6  |                    |  F7  |  F8  |  F9  | F10  | F11  | F12  |
|------+------+------+------+------+------|                    |------+------+------+------+------+------|
|   `  |   !  |   @  |   #  |   $  |   %  |-------.    ,-------|   ^  |   &  |   *  |   (  |   )  |   ~  |
|------+------+------+------+------+------|   [   |    |    ]  |------+------+------+------+------+------|
|      |      |      |      |      |      |-------|    |-------|      |   _  |   +  |   {  |   }  |   |  |
`-----------------------------------------/       /     \      \-----------------------------------------'
                  | LAlt | LGUI |LOWER | /Space  /       \Enter \  |RAISE |BackSP| RGUI |
                  |      |      |      |/       /         \      \ |      |      |      |
                  `----------------------------'           '------''--------------------'
```

### Layer 2: RAISE
Navigation and number pad layer.
```
,-----------------------------------------.                    ,-----------------------------------------.
|      |      |      |      |      |      |                    |      |      |      |      |      |  DEL |
|------+------+------+------+------+------|                    |------+------+------+------+------+------|
|   `  |   1  |   2  |   3  |   4  |   5  |                    |      | HOME | PGDN | PGUP | END  |  INS |
|------+------+------+------+------+------|                    |------+------+------+------+------+------|
|  F1  |  F2  |  F3  |  F4  |  F5  |  F6  |-------.    ,-------| Left | Down |  Up  | Right|      |      |
|------+------+------+------+------+------|   [   |    |    ]  |------+------+------+------+------+------|
|  F7  |  F8  |  F9  | F10  | F11  | F12  |-------|    |-------|   +  |   -  |   =  |   [  |   ]  |   \  |
`-----------------------------------------/       /     \      \-----------------------------------------'
                  | LAlt | LGUI |LOWER | /Space  /       \Enter \  |RAISE |BackSP| RGUI |
                  |      |      |      |/       /         \      \ |      |      |      |
                  `----------------------------'           '------''--------------------'
```

### Layer 3: ADJUST (LOWER + RAISE)
System controls and RGB Matrix settings.
```
,-----------------------------------------.                    ,-----------------------------------------.
|QKBOOT|      |      |      |      |      |                    |      |      |      |      |      |      |
|------+------+------+------+------+------|                    |------+------+------+------+------+------|
|      |      |      |      |      |      |                    |      |      |      |      |      |      |
|------+------+------+------+------+------|                    |------+------+------+------+------+------|
|      |      |      |      |      |      |-------.    ,-------|      |SPD-  |TOGGLE| HUE+ | SAT+ | VAL+ |
|------+------+------+------+------+------|       |    |       |------+------+------+------+------+------|
|      |      |      |      |      |      |-------|    |-------|      |SPD+  | MODE | HUE- | SAT- | VAL- |
`-----------------------------------------/       /     \      \-----------------------------------------'
                  | LAlt | LGUI |LOWER | /Space  /       \Enter \  |RAISE |BackSP| RGUI |
                  |      |      |      |/       /         \      \ |      |      |      |
                  `----------------------------'           '------''--------------------'
```

## RGB Matrix Controls

Access RGB controls by holding both LOWER and RAISE to enter the ADJUST layer:

| Key | Function |
|-----|----------|
| `RM_TOGG` | Toggle RGB Matrix on/off |
| `RM_NEXT` | Cycle through animation modes |
| `RM_HUEU` / `RM_HUED` | Increase/decrease hue |
| `RM_SATU` / `RM_SATD` | Increase/decrease saturation |
| `RM_VALU` / `RM_VALD` | Increase/decrease brightness |
| `RM_SPDU` / `RM_SPDD` | Increase/decrease animation speed |

## Building Firmware

### Prerequisites
- QMK firmware repository
- QMK toolchain installed

### Compile
```bash
qmk compile -kb lily58/rev1 -km jc2409
```

### Output
The compiled firmware will be located at:
```
.build/lily58_rev1_jc2409.uf2
```

## Flashing Instructions

1. Put keyboard into bootloader mode:
   - Press the RESET button on the microcontroller, OR
   - Press `QK_BOOT` key (on ADJUST layer, top-left position)

2. The keyboard will appear as a USB mass storage device

3. Copy the `.uf2` file to the mounted drive:
   ```bash
   cp .build/lily58_rev1_jc2409.uf2 /Volumes/RPI-RP2/
   ```

4. The keyboard will automatically reboot with the new firmware

5. Repeat for the other half of the split keyboard

## Configuration Files

- `keymap.c` - Main keymap definition and OLED code
- `config.h` - Hardware configuration and feature settings
- `rules.mk` - Build options and enabled features
- `keymap.json` - Converter configuration for RP2040

## Customization

### Modify Tapping Term
In `config.h`, adjust the tapping behavior:
```c
#define TAPPING_TERM 100  // milliseconds
```

### Change RGB Brightness
In `config.h`:
```c
#define RGB_MATRIX_MAXIMUM_BRIGHTNESS 120  // 0-255
```

### Enable/Disable RGB Effects
In `config.h`, comment out effects you don't want:
```c
// #define ENABLE_RGB_MATRIX_GRADIENT_UP_DOWN
```

### Modify OLED Timeout
In `keymap.c`:
```c
static long int oled_timeout = 600000;  // milliseconds (10 minutes)
```

## Tips

### Special Characters on macOS
- `<` - Shift + comma (`,`)
- `>` - Shift + period (`.`)

### Language Switching (macOS)
Default shortcut is usually Ctrl + Space or Cmd + Space (set in System Preferences)

### Caps Lock
Currently not mapped. Can be added to any layer as `KC_CAPS`

## Troubleshooting

### Splash effects only work in one direction
Ensure split transport sync is enabled in `config.h`:
```c
#define SPLIT_TRANSPORT_MIRROR
#define SPLIT_LAYER_STATE_ENABLE
#define SPLIT_LED_STATE_ENABLE
#define SPLIT_MODS_ENABLE
```

### RGB Matrix not working
1. Verify `RGB_MATRIX_ENABLE = yes` in `rules.mk`
2. Check LED count matches hardware (74 LEDs)
3. Confirm `RGB_MATRIX_DRIVER = ws2812` is set

### OLED not displaying
1. Ensure `OLED_ENABLE = yes` in `rules.mk`
2. Check I2C connections on hardware
3. Verify OLED rotation in code matches physical orientation

## License

This keymap is released under the GPL v2 License, consistent with QMK firmware.

## Credits

- QMK Firmware: https://qmk.fm/
- Lily58 keyboard design
- Bongo Cat animation sprites
