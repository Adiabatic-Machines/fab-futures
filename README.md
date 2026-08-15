# Fab Futures: Microelectronics

A four-week, hands-on introduction to the RTL-to-GDS flow. You will modify a
working design, verify it in simulation, and produce layout artifacts with
open-source tools. A completed course project is a strong starting point for a
shuttle submission; it is not automatically fabrication-ready until it meets
that shuttle's harness, signoff, and submission requirements.

## What You'll Build

Pick a project and take it from Verilog to GDS:

| Project | Description |
|---------|-------------|
| **Fortune Teller** | Magic 8-ball — press a button, get a fortune |
| **Pocket Synth** | 4-button musical instrument |
| **Dice Roller** | Hardware random dice with 7-segment display |
| **Morse Beacon** | Flash messages in Morse code on LEDs |

All projects use the same RTL-to-GDS flow. You'll learn digital design, synthesis, place & route, and verification — with a chip you actually want to demo.

## Repository Structure

```
fab-futures/
├── examples/           # Starter projects with full source & testbenches
│   ├── fortune_teller/
│   ├── pocket_synth/
│   ├── dice_roller/
│   ├── morse_beacon/
│   └── lib/            # Shared modules (UART, debounce)
├── designs/            # Your work goes here
├── class-overview.md   # Full 4-week curriculum
└── IIC-OSIC-TOOLS/     # Docker-based EDA toolchain
```

## Quick Start

### 1. Install Docker

- [Get Docker](https://docs.docker.com/get-docker/)
- Make sure Docker Desktop is **running**

### 2. Start the Environment

```bash
./run-iic-osic-tools.sh
```

### 3. Open in Browser

Open [http://localhost:8080](http://localhost:8080). The upstream image uses
`abc123` as its local VNC default. Treat that credential as suitable only for a
loopback-only classroom session: do not expose or forward port 8080. Configure
proper authentication before using the environment on a shared or remote host.

You'll get a full Linux desktop with all the EDA tools pre-installed:
- **Xschem** — schematic capture
- **ngspice** — SPICE simulation
- **Yosys** — synthesis
- **OpenROAD** — place & route
- **Magic / KLayout** — layout viewing
- **Icarus Verilog** — simulation
- **GTKWave** — waveform viewer

### 4. Run Your First Simulation

Inside the container, run the checked-in example target:

```bash
cd /foss/examples
make sim-fortune
```

The run is successful when the output ends with `Test complete`. To make a
copy you can edit without changing the examples, continue with the
[step-by-step quick start](examples/QUICKSTART.md#step-7-make-it-yours).

## Course Overview

| Week | Topics |
|------|--------|
| **1** | Foundations — semiconductors, dev pipeline, PDK setup, analog basics |
| **2** | Schematic & Fabrication — SPICE, layout, DRC/LVS |
| **3** | Digital Design — RTL, synthesis, place & route, timing |
| **4** | Testing & Integration — packaging, verification, presentations |

See [`class-overview.md`](class-overview.md) for the full curriculum with homework assignments.

## Example Projects

Each example includes:
- Heavily commented Verilog (designed for beginners)
- Working testbench with simulation instructions
- Concepts explained inline (state machines, timing, protocols)

See [`examples/README.md`](examples/README.md) for project details,
customization ideas, and the distinction between a successful course flow and
a shuttle-approved submission.

## Tools & PDKs

This course uses [IIC-OSIC-TOOLS](https://github.com/iic-jku/IIC-OSIC-TOOLS), an all-in-one Docker container with open-source EDA tools.

Supported PDKs:
- **SkyWater 130nm** (sky130A) — primary
- **GlobalFoundries 180nm** (gf180mcuD)
- **IHP 130nm** (ihp-sg13g2)

## Alternative Modes

From the `IIC-OSIC-TOOLS/` directory:

```bash
./start_shell.sh    # Terminal only (no GUI)
./start_jupyter.sh  # Jupyter notebooks
./start_x.sh        # Local X11 (XQuartz on Mac)
```

## Resources

- [Fab Futures Program](https://futures.academany.org/classes/microelectronics/) — official Academany microelectronics course
- [IIC-OSIC-TOOLS Documentation](https://github.com/iic-jku/IIC-OSIC-TOOLS)
- [SkyWater PDK Documentation](https://skywater-pdk.readthedocs.io/)
- [OpenROAD Documentation](https://openroad.readthedocs.io/)
- [Zero to ASIC Course](https://zerotoasiccourse.com/) — Matt Venn's course on chip design
