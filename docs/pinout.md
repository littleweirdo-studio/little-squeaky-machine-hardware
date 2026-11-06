```
 ⡇ ⡇⢹⠁⢹⠁⡇ ⣏⡉ ⢎⡑⡎⢱⡇⢸⣏⡉⣎⣱⣇⠜⢇⢸ ⡷⢾⣎⣱⡎⠑⣇⣸⡇⡷⣸⣏⡉
 ⠧⠤⠇⠸ ⠸ ⠧⠤⠧⠤ ⠢⠜⠣⠪⠣⠜⠧⠤⠇⠸⠇⠱ ⠇ ⠇⠸⠇⠸⠣⠔⠇⠸⠇⠇⠹⠧⠤
```

# Pinout

This page summarizes the ESP32-S3 connections shown in the board schematics. Use the [processing schematic](images/schematics/SCH_Little%20Squeaky%20Machine_1-Processing_2026-09-18.svg) as the source of truth when checking a connection.

For the peripherals' I²C addresses, see [I²C device addresses](address.md).

## ESP32-S3 connections

The tables below list the module signal or GPIO identifier, its board net name, and its function. GPIO identifiers are not physical header-pin numbers.

### Power, reset, and boot

| Module signal / GPIO | Net name | Function |
| --- | --- | --- |
| `EN` | `EN` | Enables or resets the ESP32-S3 module. |
| GPIO 0 | `CHIP_BOOT` | Boot-strapping signal and reused for KEY_25 |
| GPIO 1 | `RESET` | Board reset |
| GPIO 45 | — | Not connected in the current schematic. |
| GPIO 46 | — | Not connected in the current schematic. |

### USB and MIDI

| GPIO | Net name | Function |
| --- | --- | --- |
| 19 | `USB_D-` | USB-C data minus. |
| 20 | `USB_D+` | USB-C data plus. |
| 17 | `MIDI_OUT` | TRS-A MIDI output. |
| 18 | `MIDI_IN` | TRS-A MIDI input. |

### I²C and OLED

| GPIO | Net name | Function |
| --- | --- | --- |
| 47 | `I2C_SDA` | I²C data. |
| 48 | `I2C_SCL` | I²C clock. |

### Audio codec I²S bus

| GPIO | Net name | Function |
| --- | --- | --- |
| 42 | `I2S_MLCK` | Audio codec master clock. |
| 41 | `I2S_WS` | Word-select (WS/LRCLK) clock. |
| 40 | `I2S_BCLK` | Audio bit clock. |
| 39 | `I2S_DOUT` | Audio data output. |
| 38 | `I2S_DIN` | Audio data input. |

### Touch, key matrix, and controls

| GPIO | Net name | Function |
| --- | --- | --- |
| 4, 5, 6, 7, 15 | `TOUCH_ROW_1`–`TOUCH_ROW_5` | Key-matrix row lines. |
| 14, 13, 12, 10| `TOUCH_COL_1`–`TOUCH_COL_5` | Key-matrix column lines. |
| 0 | `KEY_SW_25` | Boot key |
| 21 | `LED_CTRL` | LED control signal. |
| 16, 8 | `ENCO0_A/B` | Encoder 0 A/B channels. |
| 3, 9 | `ENCO1_A/B` | Encoder 1 A/B channels. |
| 1, 2 | `ENCO2_A/B` | Encoder 2 A/B channels. |
| 43, 44 | `ENCO3_A/B` | Encoder 3 A/B channels. |
| 21 | `H_OLED` | OLED header net. |

### Notes

- Net names in backticks match the labels used in the schematic.
- The ESP32-S3's native USB data lines are used for USB-C connectivity.
