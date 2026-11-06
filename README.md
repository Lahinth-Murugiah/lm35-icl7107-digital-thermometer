# LM35 + ICL7107 Digital Thermometer

A two-digit digital thermometer design using an **LM35 temperature sensor** and an **ICL7107 integrating ADC with built-in 7-segment display drivers**. Developed for the IE2044 – System Modeling and Prototyping module at the Sri Lanka Institute of Information Technology (Group 06).

> **Project status:** The supplied materials document Proteus simulation and an EasyEDA PCB layout. The report records unstable breadboard readings, and the PCB was not physically fabricated. This repository does not claim a completed PCB-mounted prototype.

## Project overview

The LM35 produces an output of approximately 10 mV/°C. The design targets a 100 mV reference so the display scaling corresponds to one count per degree Celsius, with a two-digit intended range of 0°C–99°C.

| Item | Design |
|---|---|
| Temperature sensor | LM35 |
| ADC / display driver | ICL7107, DIP-40 |
| Display | Two 7-segment displays |
| Intended range | 0°C–99°C |
| Sensor sensitivity | 10 mV/°C |
| Reference target | 100 mV |
| Supply | +5 V and −5 V for ICL7107 |
| PCB design tool | EasyEDA |
| Circuit simulation | Proteus |

## How it works

1. The LM35 senses temperature and generates a proportional analog voltage.
2. The ICL7107 converts the analog input using its dual-slope integrating ADC architecture.
3. The ICL7107 drives the 7-segment displays.
4. The reference potentiometer is adjusted to the 100 mV target described in the report.

## Repository structure

```text
.
├── README.md
├── docs/
│   ├── assignment-brief.pdf
│   └── project-report.pdf
├── hardware/
│   ├── proteus/
│   │   └── evidence/
│   │       ├── proteus-0c.png
│   │       └── proteus-30c.png
│   └── easyeda/
│       └── renders/
│           ├── pcb-2d-routing.png
│           ├── pcb-3d-perspective.png
│           └── pcb-3d-top.png
└── images/
    └── pcb-preview.png
```

**Repository publication note:** This initial GitHub update publishes the project README and supporting folder documentation. The binary PDFs and PNG renders from the supplied materials still need to be uploaded; the paths above describe the intended final layout and are not links to files already present on GitHub.

## Simulation and design evidence

The supplied Proteus screenshots show the LM35 set to 0°C and 30°C, with corresponding two-digit display readings. The report also describes additional simulation test points; separate screenshots for all those points were not supplied.

The EasyEDA images show the PCB routing and 3D board views. These are visual design evidence, not fabrication or assembly evidence.

## Testing and limitations

- **Proteus:** The report describes successful simulation verification of the LM35-to-display scaling.
- **Breadboard:** The report records fluctuating readings (approximately ±2 to ±5 counts), sensitivity to touch/interference and difficulty calibrating the reference voltage.
- **PCB:** The board was designed in EasyEDA but was not physically fabricated. No Gerber package, NC drill files, BOM export or assembled-PCB test evidence is currently published.

The report discusses possible practical contributors including breadboard parasitics, ground noise, charge-pump ripple from the ICL7660 negative supply, long analog signal wires and reference-adjustment sensitivity. Proposed improvements include a fabricated PCB, improved grounding and decoupling, input filtering and a more stable reference source.

## Tools and components

- Proteus – circuit simulation
- EasyEDA – PCB design
- LM35 – analog temperature sensor
- ICL7107 – integrating ADC and LED display driver
- ICL7660 – negative voltage generation as described in the report

## Contributors

- **Lahinth M.** – IT24103482
- **Viyashan K.** – IT24103620

**Module:** IE2044 – System Modeling and Prototyping  
**Group:** 06  
**Institution:** Sri Lanka Institute of Information Technology  
**Report submission date:** 1 May 2026

## Recommended files to add next

To make the project reproducible, add the original editable source files when available:

- Proteus native project and any required linked libraries/models.
- EasyEDA schematic and PCB source/export.
- Gerber files, NC drill file, board outline and fabrication notes after design-rule checks.
- Bill of Materials with part numbers, footprints and quantities.
- Physical assembly photographs and measured hardware results after fabrication.

Run a fresh ERC/DRC and verify all outputs before manufacturing.

## License

No open-source license has been specified. Unless the authors add a license, reuse and redistribution permissions are not granted by this repository by default. Assignment and institutional materials remain subject to their respective rights.
