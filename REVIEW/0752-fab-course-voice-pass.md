# Fab Course Voice + Fact Pass

Review branch: `0752.1-fab-course-voice`

This packet is the shortest path through the judgment calls. The executable
course content is unchanged: all notebook code cells and stored outputs match
the branch baseline exactly.

## Recommended Review Order (25 minutes)

1. Open the [one-page overview](0752-fab-course-voice-overview.svg) (2 min).
2. Check the learner entry path in `README.md`, `docs/index.md`, Lecture 1's
   Environment Setup, and `examples/QUICKSTART.md` (6 min).
3. Review the seven lecture samples below, focusing on teaching register and
   factual containment rather than line-by-line copy (12 min).
4. Scan the technical-token ledger and gate results (3 min).
5. Record approve / changes requested in the checklist (2 min).

## Red-Tier Corrections

| Surface | Before | After |
|---|---|---|
| Hosted course access | A placeholder `your-class-url.example.com` looked actionable. | Hosted access is described only when an instructor has supplied a real URL; the repository makes no public-host promise. |
| Local VNC credential | `abc123` appeared as an ordinary password. | Every visible occurrence identifies it as an upstream, loopback-only default and says not to expose/forward the service or reuse the credential. |
| Documentation setup | The docs home installed nonexistent `requirements.txt` and launched Jupyter. | It installs checked-in `requirements-docs.txt`, runs `python -m mkdocs serve`, and explains that rendering does not execute cells. |
| First simulation | The root README copied from `/path/to/examples` and compiled against paths that do not exist from the stated directory. | The normal path runs the checked-in `make sim-fortune` target from `/foss/examples`; the editable-copy path uses the verified absolute library paths already established in the quick start. |
| Course completion | Several surfaces treated course GDS or P&R completion as tapeout-ready silicon. | The course deliverable is reproducible RTL, verification evidence, and flow artifacts; shuttle harness, PDK, signoff, acceptance, fabrication, packaging, and test remain explicit separate milestones. |

## One Sample per Lecture

| Lecture | Before | After / review question |
|---|---|---|
| 1. Introduction | “Use our hosted environment,” an example URL, an uncontained default password, then “That’s it!” | A real instructor-provided path or a contained local path, with a known-good `Test complete` checkpoint and an exact editable-copy command. Does this feel calm without feeling bureaucratic? |
| 2. Analog basics | “Digital logic is like Morse code — just ON and OFF” and “Every computer is built from these!” | The analogy is bounded by thresholds/timing; larger functions are described as logic, storage, and interconnect. Is this still accessible to a beginner? |
| 3. Schematic simulation | “Let’s walk through a complete simulation”; sample propagation delays looked observed. | The lab names its ngspice/model prerequisite, and the displayed numbers are explicitly illustrative rather than measurements from the learner’s run. |
| 4. Layout + fabrication | The journey ended with “the fab builds it” and “you get a chip.” | The learner produces and reviews course artifacts; an accepted shuttle submission and fabrication are future, conditional stages. |
| 5. RTL + verification | “Flip-Flop (Good)” and “Latch (Usually Bad)” flattened a real design distinction. | The terms are edge-triggered flip-flop and level-sensitive latch; unintended inference is separated from intentional latch-based design. |
| 6. Synthesis + physical design | A small Tcl fragment was called a “minimal OpenROAD flow,” inviting copy/paste use. | It is labeled a conceptual skeleton, while repository targets and the selected shuttle’s current flow remain authoritative. |
| 7. Packaging + board design | “When things don’t work,” high current led directly to checks. | Bring-up now has an explicit power-off stop condition and current-limit recovery path. Is the safety note prominent enough? |

## Scope Disposition

| Family | Disposition |
|---|---|
| Root README | Revised: course boundary, credential containment, verified first run. |
| Course overview | Revised: definition of done and shuttle boundary. |
| Published docs home | Revised: canonical repository and real documentation setup. |
| Lectures 1–7 | Revised: learner orientation in every lecture plus targeted fact/teaching corrections. |
| Examples README | Revised: baseline-first workflow and evidence-based next steps. |
| Examples quick start | Revised: credential containment, pass checkpoint, useful escalation bundle. |
| Examples troubleshooting | Revised: diagnostic register and hardware stop conditions. |
| Visible launcher copy | Revised: the script reports the default as local-only and warns against exposure. Runtime behavior is unchanged. |
| MkDocs repository link | Corrected from the former personal organization to `Adiabatic-Machines`. |
| Verilog, testbenches, notebook code cells, notebook outputs, PDK/flow scripts | Retained unchanged; outside the prose pass unless a demonstrated instruction defect required otherwise. |

## Technical-Token Ledger

- Repository URLs: `AlexWynn-AM/fab-futures` →
  `Adiabatic-Machines/fab-futures` in MkDocs and five learner links.
- Documentation command: nonexistent `requirements.txt` / `jupyter lab` →
  checked-in `requirements-docs.txt` / `python -m mkdocs serve`.
- Baseline run: broken copy/manual compile sequence → `cd /foss/examples` and
  `make sim-fortune`.
- Editable-copy compile: names `-I/foss/examples/lib`, `debounce.v`, and
  `uart_tx.v`, matching the existing checked-in quick-start command.
- `abc123` remains because it is the upstream image default; its security
  context changed, not the runtime credential.
- No module names, PDK names, design constraints, voltages, clock rates,
  expected testbench outputs, or notebook code/output payloads changed.
- The dead third-party PDF for *Practical Electronics for Inventors* was
  replaced with the publisher page; both authors are now credited.

## Gates

- `python3 -m mkdocs build --strict --site-dir /private/tmp/fab-course-site-0752` — pass; seven notebooks rendered.
- `make -C examples sim-all` — pass; all four testbenches ended successfully.
- `make -C examples synth-fortune synth-synth synth-dice synth-led` — pass with Yosys 0.64; each synthesis `CHECK` reported zero problems.
- Notebook integrity audit — pass; seven notebooks parse, and every code-cell source and stored output matches `HEAD` exactly.
- External-link audit — 32/33 returned HTTP 2xx. The remaining official Analog Devices LTspice URL rejects/times out for `curl` but was verified in browser/search on 2026-08-15. One genuinely dead PDF link was replaced.
- Optional gates unavailable on host: Verilator, OpenROAD, Magic, and a configured Sky130 `PDK_ROOT`; no full ASIC-flow claim is made.

## Reviewer Checklist

- [ ] The instructor voice is direct and natural across all seven samples.
- [ ] The local credential warning is proportionate and actionable.
- [ ] The course/shuttle boundary is accurate without deflating the project.
- [ ] The latch correction and illustrative-output labels are technically sound.
- [ ] The hardware stop condition is sufficient for this course.
- [ ] Approve for merge, or list requested changes with the file/lecture name.
