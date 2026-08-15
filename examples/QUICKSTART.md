# Quick Start Guide

New to chip design? Start here.

---

## Getting Access

You have two options:

### Option A: Instructor-Provided Environment
1. Open the link your instructor shared with you
2. Log in with your credentials
3. When the Linux desktop appears, continue to Step 1 below

### Option B: Run Locally
1. Install [Docker Desktop](https://www.docker.com/products/docker-desktop/)
2. Run `./run-iic-osic-tools.sh` from the course folder
3. Open [localhost:8080](http://localhost:8080) in your browser

The upstream image uses `abc123` as its local VNC default. Do not expose or
forward port 8080, and do not reuse that credential anywhere else. Before a
shared or remote deployment, follow the upstream environment's authentication
guidance and replace the default.

---

## Step 1: Open the Terminal

Inside the Linux desktop (in your browser window), you'll see a taskbar at the bottom.

**Open a terminal:**
- Click the terminal icon in the taskbar, OR
- Right-click the desktop → "Open Terminal Here"

---

## Step 2: Go to the Examples Folder

Type this command and press Enter:

```bash
cd /foss/examples
```

You're now in the folder with all the example projects.

---

## Step 3: Run Your First Simulation

Let's simulate the **Fortune Teller** project. Type:

```bash
make sim-fortune
```

**What you'll see:**

```
iverilog -Wall -g2012 -Ilib -o fortune_teller/fortune_teller.vvp ...
vvp fortune_teller/fortune_teller.vvp
VCD info: dumpfile fortune_teller_tb.vcd opened for output.
Pressing button...
Cannot predict.

Pressing button again...
Yes definitely!

Test complete
```

The final `Test complete` line is the important checkpoint: the compile and
self-checking testbench both finished. If it is missing, stop here and use the
[troubleshooting guide](TROUBLESHOOTING.md) before modifying the design.

---

## Step 4: View the Waveforms

Waveforms show you exactly what happened inside your chip, signal by signal.

```bash
gtkwave fortune_teller/fortune_teller_tb.vcd
```

A window opens showing signals over time. Try:
1. Click the `+` next to `fortune_teller_tb` in the left panel
2. Select a signal (like `clk` or `btn`)
3. Click "Append" to add it to the view
4. Use the zoom buttons to see the waveform

---

## Step 5: Try All the Examples

| Command | Project | What it does |
|---------|---------|--------------|
| `make sim-fortune` | Fortune Teller | Magic 8-ball over serial |
| `make sim-synth` | Pocket Synth | 4-button musical instrument |
| `make sim-dice` | Dice Roller | Roll dice on 7-segment display |
| `make sim-led` | Morse Beacon | Flash messages in Morse code |
| `make sim-all` | All projects | Run everything |

---

## Step 6: Look at the Code

The Verilog code is in each project folder:

```bash
# Look at Fortune Teller's main code
cat fortune_teller/fortune_teller.v | less
```

Press `q` to exit the viewer.

Or open it in a text editor:
```bash
gedit fortune_teller/fortune_teller.v &
```

---

## Step 7: Make It Yours

1. **Copy an example to your designs folder:**
   ```bash
   cp -r fortune_teller /foss/designs/my_fortune_teller
   cd /foss/designs/my_fortune_teller
   ```

2. **Edit the code:**
   ```bash
   gedit fortune_teller.v &
   ```

3. **Change the fortunes** (look for the ROM section around line 50)

4. **Test your changes:**
   ```bash
   iverilog -Wall -g2012 -I/foss/examples/lib -o test.vvp \
       fortune_teller.v fortune_teller_tb.v \
       /foss/examples/lib/debounce.v /foss/examples/lib/uart_tx.v
   vvp test.vvp
   ```

---

## Common Commands Reference

| What you want to do | Command |
|---------------------|---------|
| Go to examples | `cd /foss/examples` |
| Go to your designs | `cd /foss/designs` |
| List files | `ls` |
| List files with details | `ls -la` |
| View a file | `cat filename.v` or `less filename.v` |
| Edit a file | `gedit filename.v &` |
| Run simulation | `make sim-fortune` (or other project) |
| View waveforms | `gtkwave filename.vcd` |
| Check for errors | `verilator --lint-only -Wall yourfile.v` |

---

## What Do These Files Mean?

```
fortune_teller/
├── fortune_teller.v      # The actual chip design (Verilog)
└── fortune_teller_tb.v   # Test code that simulates pressing buttons
```

- **`.v` files** = Verilog source code (what becomes your chip)
- **`_tb.v` files** = Testbench (simulates the outside world)
- **`.vcd` files** = Waveform data (created when you simulate)
- **`.vvp` files** = Compiled simulation (temporary, can delete)

---

## If a Step Fails

1. Copy the exact command and the first error message.
2. Check [TROUBLESHOOTING.md](TROUBLESHOOTING.md) for that symptom.
3. Confirm that you are in the directory shown in the step.
4. If the problem remains, ask for help and include the command, error, and the
   last step that worked.

---

## Next Steps

Once you're comfortable running simulations:

1. **Modify an example** - change the fortunes, notes, or message
2. **Read the notebooks** - understand how the code works
3. **Design your own** - pick a project that excites you
4. **Synthesize it** - turn your Verilog into actual gates
5. **Check a target shuttle** — compare your artifacts with its current harness and signoff requirements before treating the design as submission-ready.
