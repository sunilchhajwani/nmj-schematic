# Neuromuscular Junction — 3D Schematic

Interactive 3D cross-section of a skeletal muscle fibre showing the full process of neuromuscular transmission at the motor end-plate. Built with Three.js (r128), single self-contained HTML file, no build step, no dependencies beyond the CDN script.

## What It Shows

The simulation walks through all 10 phases of neuromuscular transmission in sequence, matching the textbook anatomy where a **single myelinated motor axon branches into several terminal boutons** that synapse onto the motor end plate:

| # | Phase | What Happens |
|---|-------|-------------|
| 1 | **Resting** | Membrane potential at −90 mV. Vesicles docked at each bouton. |
| 2 | **AP Propagation** | Action potential runs down the myelinated axon and into the branches. |
| 3 | **Ca²⁺ Influx** | Voltage-gated Ca²⁺ channels open in **all terminal boutons**. |
| 4 | **Exocytosis** | [Ca²⁺] rise triggers SNARE-mediated vesicle fusion in every bouton → ACh released. |
| 5 | **Diffusion** | ACh molecules cross each 50 nm synaptic cleft. |
| 6 | **Receptor Binding** | ACh binds nicotinic receptors (nAChR) concentrated on junctional folds. |
| 7 | **EPP Generation** | Na⁺ influx creates the end-plate potential (EPP) — summed over all boutons. |
| 8 | **Muscle AP** | EPP reaches threshold (−55 mV) → voltage-gated Na⁺ channels fire → muscle AP. |
| 9 | **Degradation** | AChE in the basal lamina hydrolyses ACh → choline + acetate. |
| 10 | **Relaxation** | nAChR channels close, membrane potential resets, vesicles recycled. |

## Structures Rendered

The 3D layout now mirrors textbook NMJ diagrams: a **single myelinated axon trunk branches into four terminal boutons** sitting on the folded motor end plate.

- **Motor axon trunk** (myelinated, purple) with myelin sheath segments
- **Axon branches** (purple tubes) splitting from one trunk into four terminal boutons
- **Terminal boutons** (spherical presynaptic swellings) — 4 boutons, each with its own active zone
- **Synaptic vesicles** (ACh-containing, yellow) — 10 vesicles per bouton that fuse during exocytosis
- **Voltage-gated Ca²⁺ channels** (blue) — 4 per bouton at each active zone
- **Synaptic clefts** (~50 nm, translucent blue slabs) — one under each bouton with basal lamina
- **Motor end plate** (muscle fibre membrane with junctional folds)
- **Junctional folds** (5 invaginations increasing receptor surface area)
- **Nicotinic ACh receptors** (green) — 6 per bouton, turn bright when activated
- **Acetylcholinesterase** (red enzymes) — distributed in each cleft/basal lamina

## Features

- **Branching anatomy matching the textbook image** — single axon → branches → multiple boutons → motor end plate
- **AP propagation animation** — yellow pulse travels down the myelinated axon, splits into branches, and invades each bouton
- **Real-time 3D rendering** — orbit camera (drag to rotate, scroll to zoom)
- **Animated particle systems** — Ca²⁺ ions, ACh molecules, degradation products
- **Live readouts** — [Ca²⁺], vesicles released, [ACh], receptors activated, EPP (mV), membrane potential, AChE activity, AP count
- **Membrane potential trace** — scrolling canvas graph with threshold line at −55 mV
- **Phase-change tip bar** — contextual teaching tips on each phase transition
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
- Single HTML file (~53 KB), no external assets
- Catmull-Rom tube geometry for organic axon branches
- Branching physiology: AP pulse propagates from trunk → branches → all 4 boutons
- Per-bouton components: vesicles, Ca²⁺ channels, ACh molecules, receptors, AChE
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

- The **branching motor neuron** anatomy typical of textbook NMJ diagrams
- The **safety factor** of neuromuscular transmission (EPP normally exceeds threshold with large margin)
- The role of **AChE** in terminating synaptic action (relevant to anticholinesterase drugs like neostigmine)
- The **Ca²⁺-dependent** nature of vesicle fusion in every bouton (relevant to Lambert-Eaton myasthenic syndrome)
- The **nicotinic receptor** as a ligand-gated Na⁺ channel (relevant to myasthenia gravis, where autoantibodies block nAChR)

## License

MIT