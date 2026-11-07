# HOLO Client (Fabric, Minecraft Java 1.21.11)

Spatial 3D interface prototype. Open with **Right Shift** in-game.

## Set up
1. Generate a blank 1.21.11 project at https://fabricmc.net/develop/template (ships the Gradle wrapper).
2. Replace its `src/`, `build.gradle`, `gradle.properties`, `settings.gradle` with the ones here
   (or keep yours and just copy `src/`). Bump Loader / Fabric API to whatever the template suggests.
3. `./gradlew runClient`

Mojang mappings are used (1.21.11 is the last obfuscated release and Yarn ends there).

## How the 3D works
- `gfx/Gfx` : own perspective camera. Vertices are transformed, near-clipped and divided on the CPU.
- `gfx/GpuBatch` + `HoloPipelines` : three custom RenderPipelines (solid / glass / additive glow) with a
  pass-through shader (`shaders/core/scene.*`). Drawn straight into the main render target with a depth clear.
- `ui/HoloScreen` : hub -> category ring -> module arena, ray picking, camera fly-throughs, 3D sliders/orbs/toggles.
  Text is 2D overlay at projected anchor points.

## Milestones
- [x] 3D hub, camera, picking, category ring, module settings arena, config persistence
- [ ] Per-module live previews (CustomSky, Hand Aura, HitFX, Player Trail)
- [ ] HUD editor (drag/resize in a 3D screen preview)
- [ ] In-world effect implementations
