# Arduino OLED Watch

A fully custom smartwatch interface built on Arduino, featuring a real-time clock, multi-mode torch, alarm system, stopwatch, Flappy-style game, and a multi-screen menu — all rendered on a 128×64 OLED display.

![Language](https://img.shields.io/badge/language-C++-00599C?style=flat-square&logo=c%2B%2B)
![Platform](https://img.shields.io/badge/platform-Arduino-00979D?style=flat-square&logo=arduino)
![Display](https://img.shields.io/badge/display-SH1106_OLED-555?style=flat-square)

---

## Overview

This project turns an Arduino Nano/Uno into a wearable watch interface. All interaction happens through three hardware buttons, navigating a menu system across 10+ distinct screens. The firmware is written in C++ and runs entirely on the Arduino without any wireless or app dependency.

## Features

| Screen | Description |
|--------|-------------|
| **Clock** | Live time, date, weekday, and seconds via DS3231 RTC |
| **Alarm** | Set and trigger alarms with buzzer output |
| **Stopwatch** | Run / pause / reset with millisecond display |
| **Torch** | White LED and red LED, each with 3 brightness levels |
| **Laser** | Dedicated laser module control |
| **Display settings** | Brightness icons and screen rotation |
| **Volume** | Separate alarm and general audio levels |
| **Flappy game** | A simple "Flappy Man" arcade game |
| **Sleep mode** | Low-power idle screen |

## Hardware

| Component | Details |
|-----------|---------|
| Microcontroller | Arduino Nano / Uno |
| Display | SH1106 1.3" OLED (I2C, address `0x3C`) |
| RTC Module | DS3231 (I2C) |
| LEDs | White + red on pins 3 and 4 |
| Laser module | Pin 5 |
| Buzzer / speaker | Pins 9 and 10 |
| Navigation buttons | Pins 14, 16, 17 (INPUT_PULLUP) |

## Wiring

| Arduino | → | SH1106 OLED |
|---------|---|-------------|
| A4 (SDA) | → | SDA |
| A5 (SCL) | → | SCL |
| 5V | → | VCC |
| GND | → | GND |

| Arduino | → | DS3231 RTC |
|---------|---|------------|
| A4 (SDA) | → | SDA |
| A5 (SCL) | → | SCL |
| 5V | → | VCC |
| GND | → | GND |
## Getting started

**1. Install libraries** in Arduino IDE (Sketch → Include Library → Manage Libraries):
- `Adafruit GFX Library`
- `Adafruit SH1106` (or `Adafruit SH110x`)
- `RTClib` by Adafruit

**2. Wire the hardware** as shown above. Both the OLED and RTC share the I2C bus.

**3. Upload** `Smart_Watch_15Nov.ino` to your board.

**4. Navigate** using the three buttons:
- **Button A (pin 14)** — scroll up / increment
- **Button B (pin 16)** — select / confirm
- **Button C (pin 17)** — scroll down / back

> First upload: the RTC will be set to the compile timestamp automatically.
> Re-upload if the time drifts.

## Project structure

arduino-oled-watch/
└── Smart_Watch_15Nov.ino   # Full firmware — clock, menus, games, I/O

## Why I built this

I wanted to explore low-level embedded UI design — specifically how to build a
multi-screen menu system with minimal memory on a microcontroller that has no OS,
no heap allocator, and 2 KB of SRAM. The constraint of fitting an alarm, stopwatch,
torch controller, and a game into one `.ino` file forced careful state management
and taught me a lot about C++ on constrained hardware.

## Potential improvements

- [ ] Add BLE module for time sync via phone
- [ ] Replace fixed pin assignments with a config header
- [ ] Persist alarm settings to EEPROM across power cycles
- [ ] Add a step counter via MPU-6050 accelerometer

## License

MIT — feel free to fork and modify.
