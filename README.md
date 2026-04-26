# rgb_mayak

RGB beacon on an ATtiny — small AVR firmware that smoothly cycles an RGB LED through the colour wheel.

(Original Russian description: "Маячок на тиньке и RGB" — "Beacon on a Tiny and RGB".)

## What it does
Drives a common-anode RGB LED on `PB0` (green), `PB1` (red), `PB2` (blue) of an ATtiny13. The main loop walks through six colour-transition states (Red→Yellow→Green→Cyan→Blue→Magenta→Red), and the Timer/Counter0 overflow ISR generates software PWM so the colours fade smoothly. The "orange" portion of the cycle is intentionally extended.

Source header credits PaulBo (2010) under Creative Commons 3.0 Attribution-ShareAlike.

## Stack
- Language: C/C++ (`avr-libc`: `<avr/io.h>`, `<avr/interrupt.h>`, `<util/delay.h>`)
- Target: Atmel ATtiny13, `F_CPU = 8 MHz`
- IDE / toolchain: Atmel Studio (AVR Studio) project — `RGBJUK.atsln`, `RGBJUK.cppproj`, toolchain `com.Atmel.AVRGCC8`
- Programmer (per project file): AVRISP mkII via ISP

## Build / Run
Open `RGBJUK/RGBJUK.atsln` in Atmel/Microchip Studio and Build, then program the ATtiny13 over ISP. Alternatively compile manually with `avr-gcc -mmcu=attiny13` and flash with `avrdude`.

## Layout
- `RGBJUK/RGBJUK.cpp` — firmware source (state machine + Timer0 software PWM ISR)
- `RGBJUK/RGBJUK.atsln`, `RGBJUK.cppproj` — Atmel Studio solution / project

## Status
Archived in spirit (last touched 2012). License (per source header): Creative Commons BY-SA 3.0.
