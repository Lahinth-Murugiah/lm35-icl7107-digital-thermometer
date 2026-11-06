# LM35 and ICL7107 Digital Thermometer

This IE2044 System Modeling and Prototyping project uses an **LM35 temperature sensor** and an **ICL7107 integrating ADC with built-in seven-segment display drivers** to display temperature on two digits. The circuit was simulated in **Proteus**, tested on a breadboard, and laid out as a PCB in **EasyEDA**.

[Project report](docs/IE2044_Assignment_Group_06.pdf) · [Proteus simulation](simulation%20and%20PCB%20Design/proteus/evidenceproteus-30c.png) · [PCB routing](simulation%20and%20PCB%20Design/easyeda/pcb-2d-routing.png)

## Circuit design and project targets

[![Proteus circuit and two-digit display with the LM35 set to 30 degrees Celsius](simulation%20and%20PCB%20Design/proteus/evidenceproteus-30c.png)](simulation%20and%20PCB%20Design/proteus/evidenceproteus-30c.png)

| Signal stage | Project target | Circuit implementation |
| --- | --- | --- |
| 1. Temperature sensing | Convert temperature into an analog voltage | The LM35 produces an output proportional to temperature, with a nominal sensitivity of 10 mV/°C. |
| 2. Analog-to-digital conversion | Convert the sensor signal into a display reading | The ICL7107 uses a dual-slope integrating ADC. The reference adjustment sets the conversion scale. |
| 3. Temperature display | Two-digit indication over an intended 0–99°C range | Two seven-segment displays are driven by the ICL7107. |
| 4. Power supply | Provide the required positive and negative supply rails | The design uses +5 V and −5 V for the ICL7107, with an ICL7660 negative-supply circuit described in the report. |

The two-digit range is a **design target**. The published simulation captures show individual test points; they do not establish accuracy across the full range.

### Sensor output and calibration

| Temperature | Nominal LM35 output | Basis |
| --- | --- | --- |
| 0°C | 0 mV | 0 × 10 mV/°C |
| 30°C | 300 mV | 30 × 10 mV/°C |
| 99°C | 990 mV | 99 × 10 mV/°C |

These are nominal sensor-output calculations, not measured hardware results. The report describes a **100 mV reference target**. The final displayed scale also depends on the ADC input scaling and the display-digit connections; the reference value alone does not establish one displayed count per degree Celsius.

## PCB design

<table>
  <tr>
    <th width="50%">EasyEDA routing</th>
    <th width="50%">3D perspective</th>
  </tr>
  <tr>
    <td width="50%" align="center" valign="middle">
      <a href="simulation%20and%20PCB%20Design/easyeda/pcb-2d-routing.png"><img src="simulation%20and%20PCB%20Design/easyeda/pcb-2d-routing.png" alt="EasyEDA two-dimensional PCB routing layout" width="450"></a>
    </td>
    <td width="50%" align="center" valign="middle">
      <a href="simulation%20and%20PCB%20Design/easyeda/pcb-3d-perspective.png"><img src="simulation%20and%20PCB%20Design/easyeda/pcb-3d-perspective.png" alt="EasyEDA three-dimensional perspective render of the thermometer PCB" width="450"></a>
    </td>
  </tr>
</table>

[![Top view of the digital thermometer PCB in EasyEDA](simulation%20and%20PCB%20Design/easyeda/pcb-3d-top.png)](simulation%20and%20PCB%20Design/easyeda/pcb-3d-top.png)

The images document the **PCB layout and 3D design**. The board was not physically fabricated, so these renders do not represent an assembled or tested PCB.

## Simulation and bench results

| Proteus: 0°C test point | Proteus: 30°C test point |
| --- | --- |
| [![Proteus simulation with the LM35 set to 0 degrees Celsius](simulation%20and%20PCB%20Design/proteus/evidenceproteus-0c.png)](simulation%20and%20PCB%20Design/proteus/evidenceproteus-0c.png) | [![Proteus simulation with the LM35 set to 30 degrees Celsius](simulation%20and%20PCB%20Design/proteus/evidenceproteus-30c.png)](simulation%20and%20PCB%20Design/proteus/evidenceproteus-30c.png) |

The published Proteus screenshots document the **0°C and 30°C** test points. The [project report](docs/IE2044_Assignment_Group_06.pdf) discusses additional simulation testing and the practical breadboard attempt.

| Development stage | Reported outcome |
| --- | --- |
| Proteus simulation | Temperature-to-display operation demonstrated in simulation, with two separate captures published here. |
| Breadboard test | Fluctuating readings of approximately ±2 to ±5 counts, sensitivity to touch/interference, and difficulty calibrating the reference voltage. |
| EasyEDA PCB | Routing and 3D views completed; the board was not physically fabricated. |

The report discusses breadboard parasitics, ground noise, ICL7660 charge-pump ripple, long analog signal wires, and reference-adjustment sensitivity as possible contributors to unstable readings. These are proposed explanations rather than separately measured causes.

### Stage-by-stage verification

Further bench verification should record the LM35 output, the differential ADC input, the reference voltage, and both supply rails at known temperatures. Comparing the display against a reference thermometer at several stable temperatures would establish offset, scaling error, and repeatability.

A fabricated PCB would allow the proposed grounding, decoupling, and shorter analog connections to be evaluated. Native Proteus and EasyEDA design files, a bill of materials, and fabrication outputs are not currently included in this repository.

