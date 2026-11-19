# gisl

A new research project: WebGL2 visualization of GIS wind fields and wind-field particles.

This repository was started on 2026-11-20. It is an early-stage exploration, not a finished or production system.

## Goal

Render wind particles and wind barbs on the GPU in the browser, then improve texture sampling at tile edges and half-pixel boundaries.

Planned work:

- Pack wind `u/v` into a 2D texture and advect particles on the GPU
- Update particle state with a WebGL2 ping-pong framebuffer (WebGL2 has no compute shaders)
- Investigate bilinear / bicubic sampling, float precision, and boundary clamp
- Later, instance wind barbs from the same wind texture, on a pass separate from the particle buffer

## Status

The `index.html` page is a starting canvas only. Particle advection, sampling, and wind-barb instancing are not implemented yet.
