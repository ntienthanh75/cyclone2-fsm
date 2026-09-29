# FSM synthesis experiment

Target: Waveshare/CoreEP2C5, Cyclone II `EP2C5T144C8`.

The 50 MHz constrained compile completed successfully with 0 errors.

| Result | Value |
|---|---:|
| Logic elements | 60 / 4,608 (1%) |
| Pins | 7 / 89 (8%) |
| Slow setup slack | +10.964 ns |
| Slow hold slack | +0.499 ns |
| Fast setup slack | +17.193 ns |
| Fast hold slack | +0.215 ns |

The experiment uses [`fsm.sdc`](fsm.sdc), with a 20 ns clock on `clk`. Reports and the SOF are under [`experiments/50MHz`](experiments/50MHz). Quartus also identifies the internally divided `clk1` and `clk2`; those generated clocks should be constrained separately if this design is taken beyond the basic experiment.

## Clock sweep

| Constraint | Slow setup | Slow hold | Fit |
|---:|---:|---:|:---:|
| 40 MHz | +16.041 ns | +0.499 ns | Pass |
| 50 MHz | +10.964 ns | +0.499 ns | Pass |
| 60 MHz | +7.909 ns | +0.499 ns | Pass |
| 75 MHz | +3.694 ns | +0.499 ns | Pass |
| 100 MHz | +2.716 ns | +0.499 ns | Pass |

All tested constraints fit. The experiments are in `experiments/clk_*MHz`.
