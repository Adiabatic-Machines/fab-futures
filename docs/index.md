# Fab Futures

These materials guide you from a working Verilog example to verified layout
artifacts. Start with the introduction if chip design is new to you; use the
later lectures as references while you build and debug your project.

## Lectures

1. [Introduction & Pipeline](notebooks/01_introduction_pipeline.ipynb) - Overview of the chip design flow
2. [Analog Basics](notebooks/02_analog_basics.ipynb) - Fundamentals of analog circuit design
3. [Schematic & Simulation](notebooks/03_schematic_simulation.ipynb) - Circuit capture and simulation
4. [Layout & Fabrication](notebooks/04_layout_fabrication.ipynb) - Physical design and manufacturing
5. [RTL Design & Verification](notebooks/05_rtl_design_verification.ipynb) - Digital design with HDLs
6. [Synthesis & Physical Design](notebooks/06_synthesis_physical_design.ipynb) - From RTL to layout
7. [Packaging & Board Design](notebooks/07_packaging_board_design.ipynb) - Chip packaging and PCB integration

## Getting Started

To serve the same rendered course locally, clone the repository and install the
documentation dependencies:

```bash
git clone https://github.com/Adiabatic-Machines/fab-futures.git
cd fab-futures
python -m pip install -r requirements-docs.txt
python -m mkdocs serve
```

Open the URL printed by MkDocs, normally `http://127.0.0.1:8000`. This command
renders the notebooks but does not execute their code cells. For the Docker EDA
environment and the first verified simulation, follow the
[repository quick start](https://github.com/Adiabatic-Machines/fab-futures#quick-start).
