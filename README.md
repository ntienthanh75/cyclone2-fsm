# Cyclone II FSM LED Repository

This repository contains one FSM-based LED controller design in the shared Cyclone II FPGA Board project.

## Target board

- FPGA: Altera/Intel Cyclone II `EP2C5T144C8`
- Package: `T144`
- I/O standard: `3.3-V LVTTL`
- Quartus II: 13.0 SP1
- Programming: USB-Blaster through JTAG

The related projects use the same target device and shared board connections. See the [shared board specification](https://github.com/ntienthanh75/fpga-cyclone2-5led/blob/main/docs/board-spec.md).

## Pin assignments

- Clock: pin `17`
- Reset: pin `88`
- Buzzer: pin `4`; it is active-low, so drive `1` to mute it
- LED outputs: pins `8`, `9`, `24`, and `25`

## Build

Open `fsm.qpf` in Quartus II 13.0 SP1 and compile the project. The generated programming file is `output_files\fsm.sof`.

## Download to the board

1. Power the board and connect the USB-Blaster.
2. Verify the JTAG chain:

   ```powershell
   & 'D:\Program\altera\13.0sp1\quartus\bin64\jtagconfig.exe'
   ```

3. Program the FPGA:

   ```powershell
   & 'D:\Program\altera\13.0sp1\quartus\bin64\quartus_pgm.exe' -c 'USB-Blaster [USB-0]' -m JTAG -o 'p;D:\fpga\fsm\output_files\fsm.sof'
   ```

The `.sof` configuration is temporary and is lost after power-off.

## Related projects

- [Cyclone II 5LED and joystick projects](https://github.com/ntienthanh75/fpga-cyclone2-5led)
- [Cyclone II LCD Nios II project](https://github.com/ntienthanh75/lcd_nios)
- [Cyclone II adder with timing constraints](https://github.com/ntienthanh75/adders_time_constrains)

This repository is also used to study FSM synthesis results and the impact of paths on timing constraints.
