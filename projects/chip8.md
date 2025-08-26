---
title: CHIP-8 Emulator
layout: default
---

## Background
I took on this project as an introduction to emulation. [CHIP-8](https://en.wikipedia.org/wiki/CHIP-8) is the de-facto "baby's first emulator" project since its design is so simple, but it can still teach you a lot of low-level computer
architecture fundamentals. 

![CHIP-8 Demo GIF]({% link /projects/images/chip8.gif %})

## Summary

### CHIP-8 Hardware Details
CHIP-8 is an interpreted programming language and subsequently never really had dedicated hardware designed for it. It was made with the following specs:
- 35 opcodes
- 4KB of memory
- 16 registers plus one dedicated addressing register
- 2 60Hz timers
- 16-button keypad
- 64x32 pixel monochrome display
- Sound beeper

### The Emulator
#### Features
The emulator was written in C# using WinForms for the UI. Since I wrote this as a learning aid, it has several debug-oriented features that allow you to inspect the contents of the virtual machine as it runs:
- A debug window which displays:
  - Program counter, stack pointer, address register (I), and opcode
  - Register contents
  - Stack contents and current stack frame/depth
  - Timer states
- A window which displays the currently executing instruction and its address.
- A button which allows the user to view an arbitary byte of memory at a given address.
- Variable clock speed

Since the CHIP-8 just has basic monochrome graphics, I added some pre-built color themes that can be selected via a drop-down menu. 

#### Controls
The leftmost 16 keys of the keyboard (1 to 4, Q to R, A to F, and Z to V) act as the keypad of the CHIP-8. Each game seems to use different keybinds and they pretty much never use all 16 of them.

#### Compiling & Running
- Create a C# WinForms project in Visual Studio.
- Add the source code from the [repository](https://github.com/JOBBIN9422/ChocolateCHIP) to your project.
- Build the project and load a [ROM](https://github.com/JOBBIN9422/ChocolateCHIP/tree/master/emuDebug/games/roms).



## Remarks
CHIP-8 never had native hardware designed for it - it was developed as an interpreted language to be executed in a simple virtual machine. This allowed it to be run on early 8-bit computers which didn't have many games written for them at the time, and it offered
a noticeable performance gain over BASIC interpreters of the time.

The CHIP-8 interpreter standards are kind of loose which leads to some minor differences and quirks between different implentations. For example, many different games expect wildly different clock speeds for the virtual CPU. 
I assume this is due to the many decades worth of interpreters written for all sorts of different hardware (everything from 8-bit computers to calculators). This made having an adjustable clock speed a necessity for testing different games on the emulator.

Secondly, different interpreters handle the CHIP-8's draw code differently for pixels which are outside of the screen bounds. Some interpreters treat out-of-bounds pixels as no-ops. Other interpreters (mine included) perform modulo operations on out-of-bounds pixels
(this wraps them around to the other side of the screen). Either setting can break some games depending on which behavior they expect. For example, graphics wrapping in the BLITZ ROM causes an unintended game over due to the columns of pixels wrapping from the bottom edge to the top of the screen.

![CHIP-8 Demo GIF 2]({% link /projects/images/chip8-2.gif %})

## References
- [Laurence Muller](http://www.multigesture.net/articles/how-to-write-an-emulator-chip-8-interpreter/)
- [Cowgod](http://devernay.free.fr/hacks/chip8/C8TECH10.HTM)
- [Matthew Mikolay](http://mattmik.com/files/chip8/mastering/chip8.html)