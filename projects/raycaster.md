---
title: Raycasting Engine
layout: default
---
<img src='images/raycast.gif' style='width: 75%;'/>

## Summary
This is a basic raycasting engine implemented in C++/SDL2. Currently, It's very barebones - it only supports orthgonal (textured) walls and static world entities. Due to rendering issues, I stopped the project after adding basic world entities.

## Compiling & Running
- Install libraries:
  - [SDL2](https://www.libsdl.org/download-2.0.php)
  - [SDL2_image](https://www.libsdl.org/projects/SDL_image/)
  - [Armadillo](http://arma.sourceforge.net/)
- Use the included makefile (Linux) or build the source files in an empty C++ project within Visual Studio ([Windows](https://lazyfoo.net/tutorials/SDL/01_hello_SDL/windows/msvsnet2010u/index.php)).

## Controls
- **WASD:** move/strafe
- **Left/right arrows:** turning

## Remarks
As you may have already noticed, the wall textures in the test map were lifted from [Wolfenstein 3D](https://en.wikipedia.org/wiki/Wolfenstein_3D). This 1992 FPS was one of the earliest of its kind which makes it a great reference for this kind of pseudo-3D rendering technique.

## References
- [Lode Vandevenne](https://lodev.org/cgtutor/raycasting.html)
- [Permadi](https://permadi.com/1996/05/ray-casting-tutorial-table-of-contents/)
- [Hunter Loftis](https://www.playfuljs.com/a-first-person-engine-in-265-lines/)