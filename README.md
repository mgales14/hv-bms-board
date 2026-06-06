# HV BMS Board — High-Voltage Battery Monitoring IC Board

> Ford Motor Company · Electrification Platform  
> Status: **VERIFIED** · ISO 26262 ASIL-B

---

## Overview

Sensing and protection daughterboard for a 400V lithium-ion battery pack BMS, designed in KiCAD 7. Interfaces with the main BMS controller via isolated CAN-FD and reports per-cell voltage, temperature, and over-condition fault flags.

## Design Highlights

- **Stackup**: 4-layer with creepage/clearance managed for 400V isolation
- **Isolation boundary**: 4kV reinforced (per IEC 62368)
- **Cell monitoring**: 16S configuration, ±1mV measurement accuracy
- **Protocols**: Isolated CAN-FD @ 2 Mbps, SPI to host MCU
- **Protection features**: Over-voltage, under-voltage, over-temperature, cell-balancing FETs

## Simulation

AC sweep (frequency domain) analysis performed on the analog front-end feedback loop:

- Phase margin confirmed > 45° across process corners
- Input filter −3dB frequency placed at 10 kHz for ADC anti-aliasing
- Common-mode rejection of differential inputs validated at 60 Hz and 150 kHz

## Compliance

- ISO 26262 ASIL-B functional safety documentation
- Creepage and clearance per IEC 62368-1 for 400V working voltage
- Component derating: all caps derated to 50% of rated voltage

## Files

```
hv-bms-board/
├── kicad/
│   ├── hv_bms.kicad_sch
│   ├── hv_bms.kicad_pcb
│   └── hv_bms.kicad_pro
├── simulation/
│   └── spice/
│       ├── ac_sweep_afend.asc    # AC loop analysis
│       └── input_filter.asc      # ADC anti-alias filter
├── fabrication/
│   ├── gerbers/
│   └── bom.csv
└── docs/
    ├── design_notes.md
    └── isolation_calc.md         # Creepage / clearance calcs
```

## Tools Used

`KiCAD 7` `LTspice` `ISO 26262` `CAN-FD` `400V Isolation` `IEC 62368`
