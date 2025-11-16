# Arduino OLED Watch UI

This project is an Arduino-based mini watch interface built around an SH1106 OLED display and a DS3231 RTC.

## Features

- Clock screen with date, weekday and seconds  
- Alarm set menu + alarm ringing screen  
- Stopwatch (run, pause, reset)  
- Torch modes:
  - White LED (3 brightness levels)
  - Red LED (3 brightness levels)
  - Laser control
- Display settings:
  - Brightness icons
  - Screen rotation
- Volume settings for alarm and general sounds  
- Simple Flappy-style game (“Flappy man”)  
- Sleep mode and main menu navigation

## Hardware Used

- Arduino (e.g., Nano/Uno)  
- SH1106 OLED display (I2C)  
- DS3231 RTC module  
- LEDs / laser on pins 3, 4, 5  
- Buzzer / speaker on pins 9 and 10  
- Buttons on pins 14, 16, 17 (with INPUT_PULLUP)

## Libraries

- `Adafruit_GFX`
- `Adafruit_SH1106`
- `RTClib`
- `SPI`
- `Wire`

## How to Use

1. Install the required libraries in the Arduino IDE.  
2. Wire the OLED and RTC as I2C (address 0x3C for the display).  
3. Upload the sketch.  
4. Use the buttons to:
   - Navigate menus
