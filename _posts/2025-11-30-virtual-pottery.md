---
layout: post
title: "VR Pottery Simulation System"
author: "Huiling Huang"
categories: project
tags: [project]
image: Pottery.png
---

This project is an **interactive virtual pottery simulation system** built in Unity 2021, combining real-time mesh deformation with Ultraleap hand tracking to create an immersive, gesture-based pottery-making experience.

The system allows users to shape virtual clay through mouse input or hand gestures, watch their creation rotate in real-time, and save their designs for later refinement.  
It demonstrates how procedural mesh generation, dynamic vertex manipulation, and natural interaction can come together to simulate a tactile craft in a digital environment.

---

## 🌟 Project Overview

Traditional pottery requires physical materials, space, and time. This VR simulation aims to capture the **creative and meditative aspects** of pottery-making while removing those constraints.

The core challenge was translating the **continuous, organic shaping** of real clay into a responsive digital interaction.  
Users should feel like they are genuinely molding material, not just moving vertices on a screen.

The project focuses on:

- **Procedural mesh generation** that creates pottery geometry from scratch  
- **Real-time deformation** that responds immediately to user input  
- **Natural gesture control** through Ultraleap hand tracking  
- **Persistent design storage** so users can iterate on their creations

---

## 🧭 Core Interaction Flow

The user starts with a **procedurally generated base shape**—a simple cylinder that can be configured with different layer counts and subdivision levels.

From there, they enter one of three interaction modes:

- **Camera Mode**: Rotate and zoom around the pottery to inspect it from all angles  
- **Shaping Mode**: Click and drag (or use hand gestures) to deform the pottery horizontally  
- **Smoothing Mode**: Hold and move to smooth out rough surfaces

The system also supports **material modes** that change both the visual appearance and the interaction behavior:

- **Wet Clay Mode**: Fast rotation, full shaping enabled—the active creation phase  
- **Baked Mode**: Slow rotation, viewing only—the finished piece

This dual-mode approach helps users understand when they are in "creation" versus "presentation" states, similar to real pottery workflows.

---

## 🛠️ System Architecture

### Procedural Mesh Generation

The pottery geometry is built in **five distinct sections**:

1. **Bottom**: A flat circular base  
2. **Outer Wall**: The main cylindrical body, parameterized by layer count and per-layer radius  
3. **Top**: The rim of the pottery  
4. **Inner Wall**: The interior surface (for hollow forms)  
5. **Inner Bottom**: The interior base

Each section is generated programmatically using configurable parameters:

- **Layer count**: Default 30 layers, determining vertical resolution  
- **Subdivision level**: Default 60 subdivisions, controlling horizontal detail  
- **Radius array**: Per-layer radius values that define the pottery's profile

The generation algorithm uses **cosine-weighted influence** to ensure smooth transitions between layers, preventing sharp edges that would break the illusion of continuous material.

### Real-time Deformation System

When the user interacts with the pottery, the system performs **real-time vertex manipulation**:

1. **Input Detection**: The system captures mouse/touch delta or hand gesture position  
2. **Influence Calculation**: A cosine falloff function determines how strongly each vertex is affected based on its distance from the interaction point  
3. **Radius Modification**: The affected layer's radius is adjusted proportionally  
4. **Mesh Update**: Vertices are recalculated and normals are smoothed for visual quality

The deformation happens at **60 FPS**, ensuring the interaction feels immediate and responsive.

The system supports both **horizontal shaping** (expanding or contracting the pottery's width) and **smoothing** (reducing surface irregularities), giving users fine control over the final form.

### Hand Tracking Integration

For users with Ultraleap devices, the system translates hand gestures into pottery controls:

- **KongZhiMoNi.cs** acts as a bridge between Ultraleap's hand tracking data and the pottery deformation system  
- **DetectionManager** processes raw hand tracking input  
- The distance between the user's index fingers controls the **deformation intensity**

This gesture-based control makes the experience more intuitive and immersive, as users can shape the pottery with natural hand movements rather than mouse clicks.

### Data Persistence

The system includes a **JSON-serializable data model** (`PotteryData`) that captures:

- Layer count and subdivision level  
- Per-layer radius values  
- Material mode  
- Rotation state

Users can **save their designs** at any point and **load them later** for further refinement.  
This persistence layer also tracks unsaved changes, prompting users before they lose work.

---

## 🎨 Design Decisions

### Why Procedural Generation?

Rather than using pre-made 3D models, the system generates pottery geometry from scratch.  
This approach:

- Allows **infinite variation** without storing large mesh files  
- Makes it easy to **parameterize and modify** the base shape  
- Enables **real-time deformation** because the mesh structure is known at runtime

### Why Layer-Based Deformation?

The deformation system modifies **layer radii** rather than individual vertices.  
This design:

- Maintains **geometric consistency** (the pottery stays rotationally symmetric)  
- Simplifies **undo/redo logic** (only radius arrays need to be stored)  
- Provides **intuitive control** (users think in terms of "making it wider" or "narrower")

### Why Dual Material Modes?

The wet clay / baked material modes serve both **visual and functional purposes**:

- **Visual**: Helps users understand the state of their creation  
- **Functional**: Different rotation speeds and interaction rules create a clear mental model of the workflow

---

## 💻 Technical Implementation

### Tech Stack

- Unity 2021.3.45f1 (LTS)  
- Ultraleap Tracking 7.2.0  
- Newtonsoft.Json for serialization  
- Unity Standard Rendering Pipeline

### Key Components

- **Pottery.cs**: Core mesh generation and deformation logic  
- **PotteryTest.cs**: UI controller managing mode switches and user input  
- **SelfRoute.cs**: Automatic rotation system for presentation mode  
- **KongZhiMoNi.cs**: Hand tracking bridge translating gestures to pottery controls  
- **MessageBox**: UI system for user prompts and notifications

### Project Structure

```plaintext
Assets/
├── TaoChi/                      # Core project code
│   ├── Pottery/
│   │   ├── Scripts/
│   │   │   ├── Pottery.cs      # Main pottery system
│   │   │   ├── PotteryTest.cs  # UI controller
│   │   │   └── SelfRoute.cs    # Auto-rotation
│   │   ├── KongZhiMoNi.cs      # Hand tracking bridge
│   │   └── Materials/          # Pottery materials
│   ├── MessageBox/             # UI message system
│   └── Scenes/                 # Unity scenes
├── LeapMotionGestureDetection/ # Hand tracking system
└── Samples/                    # Ultraleap examples
```

---

## 📄 Reflection

This project strengthened my understanding of:

- **Procedural mesh generation** and how to build geometry programmatically  
- **Real-time vertex manipulation** and maintaining mesh quality during deformation  
- **Natural interaction design** and translating physical gestures into digital controls  
- **State management** in interactive systems (saving/loading, mode switching, unsaved changes)

It also demonstrated how **minimal code structures** can create rich, responsive experiences when paired with thoughtful interaction design and real-time feedback.

The system successfully bridges the gap between **technical mesh manipulation** and **intuitive user experience**, making complex 3D geometry feel as natural to shape as real clay.

---

You can find the source code in [the repository](https://github.com/vvhuiling/virtual_pottery).
