# Pinout

This page summarizes the ESP32-S3 connections shown in the board schematics. Use the [processing schematic](images/schematics/SCH_Little%20Squeaky%20Machine_1-Processing_2026-09-18.svg) as the source of truth when checking a connection.

For the peripherals' I²C addresses, see [I²C device addresses](address.md).

## ESP32-S3 connections

The tables below are organized by function and show all the GPIO identifiers of the ESP32-S3 and their functions. GPIO identifiers are not physical header-pin numbers but indicate how they are internally connected to the ESP32-S3.

### Reset and boot

| GPIO | Net name | Function |
| --- | --- | --- |
| 0 | `CHIP_BOOT` | Boot-strapping signal and reused for a key switch |
| 1 | `RESET` | Board reset / Reset switch |

### USB and MIDI

```ruby
  rear view                              ▼                         ▼ 
╭━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╮
│ ╭─╮     ┎─MIC-IN  ┎─LINE-OUT           ┎─MIDI-IN               ╭───╮ ╭─╮   │
│ ╰┳╯     ◉    ◉    ◉     ◉              ◉     ◉                 ╰─┳─╯ ╰┳╯   │
│ MIC EX/IN    ┖─LINE-IN  ┖─HEADPHONE          ┖─MIDI-OUT         USB RESET  │
╰━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╯
                                               ▲
```   

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

All pins are connected to the corresponding pins on the SGTL5000 audio codec.

| GPIO | Net name | Function |
| --- | --- | --- |
| 42 | `I2S_MLCK` | Audio codec master clock connected |
| 41 | `I2S_WS` | Word-select (WS/LRCLK) clock. |
| 40 | `I2S_BCLK` | Audio bit clock. |
| 39 | `I2S_DOUT` | Audio data output. |
| 38 | `I2S_DIN` | Audio data input. |

The SGTL5000's analog inputs and outputs are connected to the rear-view connectors.

```ruby
  rear view                              
╭━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╮
│ ╭─╮     ┎─MIC-IN  ┎─LINE-OUT           ┎─MIDI-IN               ╭───╮ ╭─╮   │
│ ╰┳╯     ◉    ◉    ◉     ◉              ◉     ◉                 ╰─┳─╯ ╰┳╯   │
│ MIC EX/IN    ┖─LINE-IN  ┖─HEADPHONE          ┖─MIDI-OUT         USB RESET  │
╰━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╯
   ▲      ▲    ▲    ▲     ▲                           
```   

| Interface | Description|
|--         |--|
|MIC EX/IN  | Selection between the internal microphone and the external microphone (condenser). |
|MIC-IN     | Connect an external condenser microphone to the machine. |
|LINE-IN    | Connect an external line source, e.g., another machine, instrument, or phone. |
|LINE-OUT   | Line-out for the great sounds you produce with the machine. |
|HEADPHONE  | Headphone connector with a capless audio design. |

### Touch, key matrix, and controls

!!! info "The keyboard matrix has inline diode to prevent ghosting."

| GPIO | Net name | Function |
| --- | --- | --- |
| 4, 5, 6, 7, 15 | `TOUCH_ROW_1`–`TOUCH_ROW_5` | Key-matrix row lines. |
| 14, 13, 12, 10| `TOUCH_COL_1`–`TOUCH_COL_5` | Key-matrix column lines. |
| 0 | `KEY_SW_25` | Boot key |
| 21 | `LED_CTRL` | RMT (Remote Control Transceiver) LED control signal. |
| 16, 8 | `ENCO0_A/B` | Encoder 0 A/B channels. |
| 3, 9 | `ENCO1_A/B` | Encoder 1 A/B channels. |
| 1, 2 | `ENCO2_A/B` | Encoder 2 A/B channels. |
| 43, 44 | `ENCO3_A/B` | Encoder 3 A/B channels. |
| 21 | `H_OLED` | I²C for the OLED display. |

### Notes

- Net names in backticks match the labels used in the schematic.
- The ESP32-S3's native USB data lines are used for USB-C connectivity.
