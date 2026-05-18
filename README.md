This repository contains a memory layout dump of Hex.dll – the core game assembly of Heroes of Might and Magic: Olden Era.
The file (Hex.dll_ptch6.h) was generated using Il2CppDumper and manual analysis.

Its purpose is simple: give you the class structures, field offsets, and method addresses needed to build ESP cheats (Extra Sensory Perception – e.g., wallhacks, player boxes, health bars, etc.).

What’s Inside?
Class definitions (e.g., Unit, Hero, CameraShake, BhWorldCamera).

Field offsets (where to find positions, health, team ID, name, etc.).

Method RVA (relative virtual addresses) – can be used to hook or call functions externally.

The dump is not a full source code – it’s a memory map for an Il2Cpp game. Perfect for building an external overlay that reads game memory.

How This Helps You Make ESP
With this dump, you can:

Locate entity lists – find the classes that store all units/heroes.

Read positions – look for Vector3 fields like position, transform, worldPosition.

Get health/mana – find float health, int32_t mana fields inside player/unit classes.

Identify teams – find int32_t side, uint8_t team etc.

Build a memory reader – use ReadProcessMemory or a driver to read those offsets.

You locate the base address of the Unit array, loop through, read each unit’s position/health/team, and draw boxes or health bars on an overlay.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2604c7c1-7f3d-47d9-a3a9-ae50259d6dd0" />

The image demonstrates what can be built using this dump

Important Notes
Offsets can change after game updates. The dump is a snapshot. You may need to re‑dump after patches.

Use at your own risk. Online games may ban for memory reading/modification.

This file is for educational / research purposes only. Don’t be a jerk – don’t use cheats in competitive multiplayer.

🛠️ How to Use (Quick Start)
Find the base address of Hex.dll in the game process.

Add the base to each RVA from the dump to get absolute addresses.

Read process memory (e.g., ReadProcessMemory on Windows) using the offsets from the classes you need.

Render an overlay (DirectX, OpenGL, or ImGui) to draw ESP information.

Need help? There are plenty of open‑source ESP frameworks that work with Il2Cpp dumps – this file provides the game‑specific offsets.

Contributing
If you have corrected field offsets or found new useful classes for ESP, open a pull request. Please include proof (e.g., memory dump screenshots).

License
This dump is provided “as is” for educational purposes. All game code belongs to the original developers.

Happy hacking – and may your ESP be flawless. 🧙‍♂️
