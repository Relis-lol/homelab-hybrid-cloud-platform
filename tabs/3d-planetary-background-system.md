## 3D Planetary Background System

Lightweight cinematic WebGL background system created for the EVE-inspired homepage environment.
Built as a fully browser-rendered real-time scene focused on visual immersion, efficient rendering, and low memory usage while maintaining a high-end sci-fi aesthetic.

## Features

* Real-time 3D planetary rendering
* Dynamic atmospheric glow layers
* Procedural city-light system
* Animated volumetric cloud layer
* Orbital satellite traffic system
* Cinematic directional lighting
* Large-scale nebula panorama background
* Responsive fullscreen rendering
* Browser-only architecture
* No backend dependencies

## Optimization Work

The scene was heavily optimized to reduce browser memory usage while preserving visual quality and realism.

Implemented optimizations included:

* Geometry complexity reduction
* Shared satellite geometries
* Reduced texture overhead
* Smart mipmap management
* Canvas texture downscaling
* Selective anisotropic filtering
* Reduced starfield density
* Optimized shader texture sampling
* Controlled texture filtering to prevent flickering artifacts
* Improved cloud rendering stability during movement

## Result

Memory usage was reduced from roughly:

```text
~460 MB → ~186 MB
```

while maintaining:

* cinematic atmosphere
* smooth motion
* stable lighting
* high visual fidelity
* low artifacting during animation

## Tech Stack

* HTML5
* CSS3
* Three.js
* GLSL Shaders
* Vanilla JavaScript
* WebGL

## Goal

The project was designed as a lightweight cinematic homepage background system combining:

* real-time rendering
* shader-based visual effects
* frontend optimization
* browser performance engineering
* immersive sci-fi presentation

The focus was not only visual quality, but also practical optimization for long-running browser sessions and low-overhead rendering on consumer hardware.
