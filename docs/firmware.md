# Firmware upload for the machine

The machine uses the standard way to upload firmware to an ESP32-S3: flashing the program over the board's USB serial interface using the ESP32-S3 bootloader.

This is the usual method for ESP32-S3 development boards and is the same approach used by ESP-IDF, esptool, espflash, and other standard flashing tools.

!!! info "The machine comes with a preloaded, battle-tested firmware, and it is not locked"

## How it works

The internal ESP32-S3 MCU of the machine exposes a serial download bootloader that accepts firmware data through the USB-C connection. To upload firmware:

1. Connect the machine to the computer with a USB cable `#!ruby [1]`
2. Put the board into flashing mode by holding the RESET `#!ruby [2]` button while resetting or powering the board.
```ruby
                                                        [1] ⇉ PLUG IT IN!!!
  rear view                                                       ↓↓↓   
╭━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╮
│ ╭─╮     ┎─MIC-IN  ┎─LINE-OUT           ┎─MIDI-IN               ╭───╮ ╭─╮   │
│ ╰┳╯     ◉    ◉    ◉     ◉              ◉     ◉                 ╰─┳─╯ ╰┳╯   │
│ MIC EX/IN    ┖─LINE-IN  ┖─HEADPHONE          ┖─MIDI-OUT         USB RESET ⇇ [2] hold it
╰━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╯
```    
3. Release BOOT `#!ruby [1]` once the board is in download mode.
```ruby
 top view      ╭━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╮
╭━━━━━━━━━━━━━━╯    ╭MIC╮                                                                   │
│                   │ ♫ │                 ╭────────────╮                              [1] HOLD IT 
│                   ╰───╯                 │ LttL       │                              ↓↓↓   │
│           ╡    ╭0╮               ╭1╮    │ Squeaky    │   ╭2╮               ╭3╮     ╭═M═╮  │
│           ╡    │◉│               │◉│    │ Machine ♫  │   │◉│               │◉│     │░░░│  │
│           ╡    ╰─╯               ╰─╯    ╰────────────╯   ╰─╯               ╰─╯     ╰▀▀▀╯  │
│ external ─╡   ╭─0─╮ ╭─C─╮ ╭─D─╮ ╭─1─╮ ╭─F─╮ ╭─G─╮ ╭─A─╮ ╭─2─╮ ╭─C─╮ ╭─D─╮ ╭─3─╮ ╭─F─╮     │
│ interface ╡   │░░░│ │ # │ │ # │ │░░░│ │ # │ │ # │ │ # │ │░░░│ │ # │ │ # │ │░░░│ │ # │     │
│           ╡   ╰───╯ ╰▀▀▀╯ ╰▀▀▀╯ ╰───╯ ╰▀▀▀╯ ╰▀▀▀╯ ╰▀▀▀╯ ╰───╯ ╰▀▀▀╯ ╰▀▀▀╯ ╰───╯ ╰▀▀▀╯     │
│           ╡      ╭─C─╮ ╭─D─╮ ╭─E─╮ ╭─F─╮ ╭─G─╮ ╭─A─╮ ╭─B─╮ ╭─C─╮ ╭─D─╮ ╭─E─╮ ╭─F─╮ ╭─G─╮  │
│           C      │   │ │   │ │   │ │   │ │   │ │   │ │   │ │   │ │   │ │   │ │   │ │   │  │
│                  ╰───╯ ╰───╯ ╰───╯ ╰───╯ ╰───╯ ╰───╯ ╰───╯ ╰───╯ ╰───╯ ╰───╯ ╰───╯ ╰───╯  │
╰━━━━━━━━━━━━━━╮                                                                            │
               ╰━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╯
```

4. Send the firmware image using a standard flashing tool and select the correct serial port.
5. Reset the board after the upload completes so the new firmware starts running.

## Typical command

Using esptool, the upload is normally done like this:

```bash
esptool.py --chip esp32s3 --port /dev/ttyUSB0 --baud 460800 write_flash -z 0x0 little_squeaky_machine.bin
```

For typical Rust based firmware:

```bash
espflash flash --monitor  firmware/target/xtensa-esp32s3-none-elf/release/little_squeaky_machine
```

## Notes

- This is the standard ESP32-S3 firmware upload method.
- The board must be in BOOT mode for the serial bootloader to accept programming.
- If the upload fails, check the USB cable, serial port selection, and whether the board is in flashing mode.
- Tools such as `idf.py flash` or `cargo espflash` use the same underlying ESP32-S3 bootloader mechanism.

In short, the machine is using the normal ESP32-S3 firmware programming flow: upload through the USB serial bootloader, not a custom or proprietary flashing method.
