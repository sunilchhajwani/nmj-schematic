# Neuromuscular Junction — 3D Schematic

Interactive 3D cross-section of a skeletal muscle fibre showing the full process of neuromuscular transmission at the motor end-plate. Built with Three.js (r128), single self-contained HTML file, no build step, no dependencies beyond the CDN script.

## What It Shows

The simulation walks through all 10 phases of neuromuscular transmission in sequence:

| # | Phase | What Happens |
|---|-------|-------------|
| 1 | **Resting** | Membrane potential at −90 mV. Vesicles docked at active zone. |
| 2 | **AP Arrival** | Action potential depolarises the axon terminal bouton. |
| 3 | **Ca²⁺ Influx** | Voltage-gated Ca²⁺ channels open → Ca²⁺ flows into presynaptic terminal. |
| 4 | **Exocytosis** | [Ca²⁺] rise triggers SNARE-mediated vesicle fusion → ACh released into cleft. |
| 5 | **Diffusion** | ACh molecules cross the 50 nm synaptic cleft. |
| 6 | **Receptor Binding** | ACh binds nicotinic receptors (nAChR) on the motor end plate. |
| 7 | **EPP Generation** | Na⁺ influx through nAChR creates the end-plate potential (local depolarisation). |
| 8 | **Muscle AP** | EPP reaches threshold (−55 mV) → voltage-gated Na⁺ channels fire → muscle action potential. |
| 9 | **Degradation** | AChE in the basal lamina hydrolyses ACh → choline + acetate. |
| 10 | **Relaxation** | nAChR channels close, membrane potential resets, vesicles recycled. |

## Structures Rendered

- **Motor axon** (myelinated, with myelin sheath segments)
- **Axon terminal / bouton** (presynaptic swelling)
- **Synaptic vesicles** (ACh-containing, 24 vesicles that fuse during exocytosis)
- **Voltage-gated Ca²⁺ channels** (6 channels at the active zone)
- **Synaptic cleft** (~50 nm, translucent blue region with basal lamina)
- **Motor end plate** (sarcolemma with junctional folds)
- **Junctional folds** (5 invaginations increasing receptor surface area)
- **Nicotinic ACh receptors** (12 nAChR, turn green when activated)
- **Acetylcholinesterase** (8 AChE enzymes in the cleft, degrade ACh)

## Features

- **Real-time 3D rendering** — orbit camera (drag to rotate, scroll to zoom)
- **Animated particle systems** — Ca²⁺ ions, ACh molecules, degradation products
- **Live readouts** — [Ca²⁺], vesicles released, [ACh], receptors activated, EPP (mV), membrane potential, AChE activity, AP count
- **Membrane potential trace** — scrolling canvas graph with threshold line at −55 mV
- **Phase-change tip bar** — contextual teaching tips appear on each phase transition
- **Stimulation controls** — single AP trigger or continuous stimulation (0–100 Hz)
- **Animation speed control** — 0.2× to 3.0×
- **Toggle labels & legend** — anatomical labels and colour-coded legend

## Running

### macOS / Linux / Windows

1. **Open directly in a browser:**
   ```
   open index.html          # macOS
   xdg-open index.html      # Linux
   start index.html         # Windows
   ```

2. **Or serve locally (recommended for best CDN loading):**
   ```
   cd nmj-schematic
   python3 -m http.server 8765
   ```
   Then open `http://localhost:8765` in your browser.

### Requirements

- Modern browser with WebGL support (Chrome, Firefox, Safari, Edge)
- Internet connection (Three.js loaded from CDN)
- No installation, no build step

## Controls

| Control | Action |
|---------|--------|
| **Drag** | Rotate camera around the scene |
| **Scroll / Pinch** | Zoom in / out |
| **🔥 Fire AP** | Trigger a single action potential |
| **Stimulation slider** | Continuous stimulation at 0–100 Hz |
| **Speed slider** | Animation speed 0.2× – 3.0× |
| **🏷️ Labels** | Toggle anatomical labels |
| **📖 Legend** | Toggle structure legend |

## Technical Details

- **Three.js r128** (stable CDN version)
- Single HTML file (~50 KB), no external assets
- All physiology driven by a 10-state state machine
- Particle systems for Ca²⁺ ions, ACh molecules, and degradation products
- Membrane potential trace rendered on Canvas 2D
- Camera uses smooth lerp orbit controls (mouse + touch)

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Blank page / no 3D | Check WebGL is enabled in your browser settings |
| CDN script blocked | Use the local server method instead of opening the file directly |
| Labels not showing | Click the "🏷️ Labels" button to toggle |
| Simulation not progressing | Click "Enter Simulation" on the start screen first, then "🔥 Fire AP" |

## Educational Context

This schematic is designed for PG residents and intensivists studying neuromuscular physiology. It visualises:

- The **safety factor** of neuromuscular transmission (EPP normally exceeds threshold with large margin)
- The role of **AChE** in terminating synaptic action (relevant to anticholinesterase drugs like neostigmine)
- The **Ca²⁺-dependent** nature of vesicle fusion (relevant to Lambert-Eaton myasthenic syndrome)
- The **nicotinic receptor** as a ligand-gated Na⁺ channel (relevant to myasthenia gravis, where autoantibodies block nAChR)

## License

MIT