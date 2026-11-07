# I²C device addresses

The I²C peripherals share the ESP32-S3 I²C bus: `I2C_SDA` (GPIO 47) and `I2C_SCL` (GPIO 48). Addresses below are shown in 7-bit format, as commonly used by firmware APIs.

| Device | I²C address | Source |
| --- | --- | --- |
| 0,96" OLED display [**(SSD1315)**](https://cursedhardware.github.io/epd-driver-ic/SSD1315.pdf) | `0x3C` | [HS HS96L01W4S03](https://www.lcsc.com/datasheet/C5139758.pdf) |
| **SGTL5000** audio codec | `0x0A` | [SGTL5000 data sheet](https://www.nxp.com/docs/en/data-sheet/SGTL5000.pdf) |
| **CY8CMBR3108** capacitive touch controller | `0x37` | [Touch control schematic](images/schematics/SCH_Little%20Squeaky%20Machine_7-Touch%20control_2026-09-18.svg) |
| **STK8321** three-axis accelerometer | `0x0F` | [Gyro control schematic](images/schematics/SCH_Little%20Squeaky%20Machine_8-Gyro%20Control_2026-09-18.svg) |
