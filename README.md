# Ember Drift

An interactive particle field built with **vanilla JavaScript and HTML Canvas**, featuring flowing noise-based motion, cursor interaction, color themes, bursts, shooting stars, cursor trails, and adaptive rendering quality.

**No frameworks. No dependencies. No build step.**

[Live Demo](https://hosseinb1111.github.io/ember-drift/)

---

## ✨ Overview

**Ember Drift** is a generative visual experiment built around a simple idea:

> particles should feel less like objects moving across a screen and more like a field of light flowing through an invisible current.

The particle movement is driven by a custom **Perlin-noise-based vector field**, while mouse and touch interaction locally disturb the flow.

The result is an interactive background that continuously changes without following a predefined animation path.

---

## 🌌 Features

* 🌊 **Noise-driven particle field**
* 🖱️ **Interactive cursor influence**
* 💥 **Click / tap particle bursts**
* ✨ **Shooting stars**
* 🎨 **Multi-color particle palettes**
* 🌓 **Multiple visual themes**
* 🔢 **Binary visual mode**
* 🧲 **Attract / repel interaction**
* 🌀 **Cursor trails**
* ⚙️ **Adjustable particle density**
* 🚀 **Automatic render-quality adjustment**
* ⏸️ **Pause / resume animation**
* 📱 **Touch support**
* ♿ **Reduced-motion support**
* 📐 **Responsive canvas rendering**
* 🖥️ **High-DPI / device-pixel-ratio handling**

---

## 🎨 Themes

Ember Drift currently includes two visual modes.

### Ember

The default experience uses a dark background with flowing colored particles and soft light trails.

Available palette colors include:

* Ember
* Spark
* Rose
* Glacier
* Aurora
* Violet

Multiple colors can be enabled at the same time to create different particle mixes.

### Binary

A completely different visual direction based around:

```text
01
```

Particles become falling binary glyphs and the interface switches to a monospace visual language.

The theme also changes:

* typography
* cursor shape
* particle rendering
* interface styling
* descriptive text

---

## 🖱️ Interaction

The particle field responds to the user's pointer.

### Move

Moving the cursor through the field changes the local particle flow.

### Click

Clicking creates a radial burst that pushes particles outward and produces a short chromatic flash.

### Attract / Repel

The interaction mode can be switched between attraction and repulsion.

### Touch

On touch devices, tapping and dragging can interact with the field without requiring a mouse.

---

## ⚙️ Controls

The dock at the bottom of the screen provides control over the simulation.

| Control       | Description                                 |
| ------------- | ------------------------------------------- |
| 🎨 Theme      | Switch between visual themes                |
| ● Palette     | Enable or disable particle colors           |
| Density       | Change particle count                       |
| ↕ Interaction | Toggle attract / repel behavior             |
| ✨ Stars       | Enable or disable shooting stars            |
| 🌀 Trail      | Enable or disable cursor trails             |
| ⚙ Quality     | Switch between automatic and manual quality |
| ⏸ Pause       | Pause or resume the animation               |

---

## 🧠 How It Works

The core of Ember Drift is a **2D vector field** generated from layered Perlin noise.

Each particle samples the field at its current position and converts the resulting angle into a velocity vector.

Conceptually:

```text
Position
   ↓
Perlin Noise
   ↓
Field Angle
   ↓
Particle Velocity
   ↓
Particle Position
   ↓
Render
```

The field changes over time, so particles continuously move through a changing flow rather than following fixed paths.

Pointer interaction is then applied locally around the cursor:

```text
Noise Field
     +
Pointer Influence
     +
Burst Forces
     ↓
Final Particle Velocity
```

Each particle also maintains a short trail to create the flowing light effect.

---

## 🧮 Rendering

The application uses multiple Canvas layers:

```text
┌───────────────────────────┐
│ Background Stars          │
├───────────────────────────┤
│ Main Particle Field       │
├───────────────────────────┤
│ Effects / Bursts / Trails │
├───────────────────────────┤
│ Flash Layer               │
├───────────────────────────┤
│ HTML Controls / UI        │
└───────────────────────────┘
```

Separate canvases are used for different visual layers so particle rendering and temporary effects can be handled independently.

The renderer also takes the device pixel ratio into account and caps it to avoid unnecessarily large canvas buffers.

---

## 🚀 Adaptive Quality

Ember Drift includes an automatic rendering-quality system.

The application monitors frame timing and can move between:

```text
HIGH
 ↓
MEDIUM
 ↓
LOW
```

when rendering becomes expensive.

Quality affects values such as:

* background star count
* shooting star count
* particle effect density
* cursor trail length
* visual effect counts

Quality can also be changed manually from the controls.

The goal is to keep the experience responsive without completely removing the visual character of the simulation.

---

## ♿ Accessibility & Device Support

The experiment includes several considerations for different devices and users.

### Reduced Motion

When:

```text
prefers-reduced-motion: reduce
```

is detected, the application automatically:

* reduces particle density
* disables shooting stars
* disables cursor trails

### Touch Devices

Mouse-specific cursor effects are disabled on touch devices, while touch interaction remains available for the particle field.

### Responsive Rendering

The canvases resize with the viewport and are rendered using the device pixel ratio, with a configurable cap.

---

## 🧰 Technology

This project intentionally uses browser-native technologies.

* **HTML5**
* **CSS3**
* **JavaScript**
* **Canvas API**
* **requestAnimationFrame**
* **Perlin noise**
* **CSS media queries**
* **Browser pointer / touch events**

No React, Vue, Tailwind, Three.js, or external runtime is required.

---

## 📁 Project Structure

The project is intentionally lightweight:

```text
ember-drift/
└── index.html
```

The application is contained in a single HTML file with:

* markup
* styling
* simulation logic
* rendering
* interaction handling
* theme configuration

This keeps the experiment easy to run, inspect, fork, and modify.

---

## ▶️ Run Locally

No installation is required.

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/ember-drift.git
cd ember-drift
```

Then open:

```text
index.html
```

in a modern browser.

For a local development server, you can also use any static HTTP server of your choice.

---

## 🎛️ Customization

Most of the simulation can be adjusted from the `CONFIG` object near the beginning of the script.

For example:

```js
const CONFIG = {
  quality: 'auto',
  dprCap: 2,
  densityLevels: [900, 1500, 2200, 450],
  pointerRadius: 260,
  pointerForce: 2.4,
};
```

You can experiment with:

* particle density
* pointer radius
* pointer force
* device-pixel-ratio limits
* trail lengths
* shooting star counts
* background star counts
* particle effect counts
* noise scaling

The `THEMES` object controls:

* colors
* fonts
* interface copy
* cursor shape
* rendering mode

This makes adding another visual theme relatively straightforward.

---

## 🔬 What I Wanted to Explore

This project started as a visual experiment rather than a traditional application.

The interesting part for me was exploring how relatively simple browser primitives can produce complex motion:

```text
Noise
+
Particles
+
Vectors
+
Interaction
+
Time
=
Emergent Motion
```

Instead of creating a fixed animation, the goal was to create a system that continuously generates movement.

---

## 🧪 Project Type

**Generative visual experiment / interactive Canvas project**

This project is primarily focused on:

* creative coding
* browser rendering
* particle simulation
* interaction design
* procedural motion
* performance experimentation

It is intentionally small and self-contained.

---

## 📸 Preview

Add a screenshot or short GIF here:
(./assets/preview.png)
A short screen recording of the interaction would also work particularly well for this project.

---

## 📄 License

Add your preferred license here, for example:

```text
MIT License
```

or replace this section with the license you choose.
