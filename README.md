# gisl

A new research project: WebGL2 visualization of GIS wind fields and wind-field particles.

This repository was started on 2026-11-20. It is an early-stage exploration, not a finished or production system.

## Current demo

Open [index.html](./index.html) in a browser with WebGL2 (or use GitHub Pages once enabled). You should see a procedural wind field and about 65,536 particles advected on the GPU.

Implemented so far:

- Wind `u/v` packed into a 2D `RGBA16F` texture: `RG` is one time snapshot, `BA` is the next, blended by `timeFrac`
- Particle state in a pair of ping-pong framebuffers (WebGL2 has no compute shaders)
- Wind sampling: bilinear (`texture`) or Catmull-Rom bicubic, both clamped to the half-texel interior so edge taps are not lost
- Integration: Euler or RK4, selectable in the on-page controls
- Particles respawn when they leave the domain or their lifetime ends

The wind field is procedural, not yet loaded from real GIS tiles. Wind-barb instancing is not implemented yet.

## Goal

Render wind particles (and later wind barbs) on the GPU in the browser, and keep studying texture sampling at tile edges, half-pixel boundaries, and float precision.
