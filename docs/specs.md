```
 ⡇ ⡇⢹⠁⢹⠁⡇ ⣏⡉ ⢎⡑⡎⢱⡇⢸⣏⡉⣎⣱⣇⠜⢇⢸ ⡷⢾⣎⣱⡎⠑⣇⣸⡇⡷⣸⣏⡉
 ⠧⠤⠇⠸ ⠸ ⠧⠤⠧⠤ ⠢⠜⠣⠪⠣⠜⠧⠤⠇⠸⠇⠱ ⠇ ⠇⠸⠇⠸⠣⠔⠇⠸⠇⠇⠹⠧⠤
```

The Little Squeaky Machine is a hardware reference platform for the [Little Weirdo software synthesizer](https://github.com/hi-squeaky-things/little-weirdo).

## Little Squeaky Machine Hardware

### Specifications and capabilities

| Subsystem | Component | Description |
| --- | --- | --- |
| Microcontroller | [ESP32-S3-WROOM-1](https://documentation.espressif.com/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf) | Runs the Little Weirdo firmware and manages the device's sound generation and controls. |
| Audio codec | [SGTL5000](https://www.nxp.com/docs/en/data-sheet/SGTL5000.pdf) | Provides stereo line input and output, microphone input with bias, and a capless stereo headphone amplifier with mixing and filtering. |
| Capacitive touch | [CY8CMBR3108](https://www.infineon.com/assets/row/public/documents/30/49/infineon-cy8cmbr3002-cy8cmbr3102-cy8cmbr3106s-cy8cmbr3108-cy8cmbr3110-cy8cmbr3116-datasheet-en.pdf) | Provides eight capacitive touch inputs over I²C, available through an edge connector. |
| TRS MIDI | [ESP32-S3-WROOM-1](https://documentation.espressif.com/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf) | Supports MIDI communication through TRS-A connections. |
| USB MIDI | [ESP32-S3-WROOM-1](https://documentation.espressif.com/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf) | Supports MIDI communication over USB-C. |
| Potentiometers and encoders | [ESP32-S3-WROOM-1](https://documentation.espressif.com/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf) | Provides hands-on controls, including four rotary encoders. |
| Motion sensor | [STK8321](https://uploadcdn.oneyac.com/attachments/files/brand_pdf/sensortek/STK8321.pdf) | Measures acceleration along three axes and communicates over I²C. |
| Keys | [CPG151101S11](https://www.lcsc.com/datasheet/C41430893.pdf) | Provides 25 hot-swappable tactile switches. |
| Display | [HS HS96L01W4S03](https://www.lcsc.com/datasheet/C5139758.pdf) | 0,96" OLED Display, I²C, SSD1315 |

## Schematics

### Processing

This schematic covers the ESP32-S3 and its supporting circuitry, including a USB-C-compliant interface, electrostatic discharge (ESD) and electromagnetic compatibility (EMC) protection, boot and reset buttons, and an OLED display. A resettable fuse provides additional protection for the 5 V rail supplying the full-color LEDs.

![Processing schematic](images/schematics/SCH_Little%20Squeaky%20Machine_1-Processing_2026-09-18.svg)

### Audio codec

This schematic shows the SGTL5000 audio codec and its supporting circuitry, including connectors, internal and external microphones, and a low-power, low-noise power supply.

![Audio codec schematic](images/schematics/SCH_Little%20Squeaky%20Machine_2-Audio%20Codec_2026-09-18.svg)

### LED controls

This schematic covers the circuitry for controlling the machine's full-color LEDs.

![LED controls schematic](images/schematics/SCH_Little%20Squeaky%20Machine_3-Led%20Controls_2026-09-18.svg)

### Key matrix controls

This schematic shows the key matrix and its connections for the 25 hot-swappable tactile switches.

![Key matrix controls schematic](images/schematics/SCH_Little%20Squeaky%20Machine_4-Key%20Matrix%20Controls_2026-09-18.svg)

### Potentiometer and encoder controls

This schematic shows the connections for the four rotary encoders.

![Potentiometer and encoder controls schematic](images/schematics/SCH_Little%20Squeaky%20Machine_5-Pot%20and%20Encoder%20Controls_2026-09-18.svg)

### MIDI input and output

This schematic covers the TRS-A MIDI input and output connections.

![MIDI input and output schematic](images/schematics/SCH_Little%20Squeaky%20Machine_6-Midi%20In-Out_2026-09-18.svg)

### Touch controls

This schematic shows the capacitive touch controller and its connections, including the touch inputs available through the edge connector.

![Touch controls schematic](images/schematics/SCH_Little%20Squeaky%20Machine_7-Touch%20control_2026-09-18.svg)

### Motion sensing

This schematic shows the STK8321 three-axis accelerometer and its I²C connection.

![Motion sensing schematic](images/schematics/SCH_Little%20Squeaky%20Machine_8-Gyro%20Control_2026-09-18.svg)
