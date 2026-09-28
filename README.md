
**Module 6: In-Vehicle Infotainment (IVI) Systems — Option 1**

> Design a conceptual architecture diagram of an IVI system integrating media,
> navigation, and projection features. Annotate component interfaces and data flow.

## Contents

| File | Description |
|---|---|
| `Project1_IVI_Architecture_Diagram.ipynb` | Colab notebook that builds and renders the architecture diagram with Graphviz. |
| `IVI_Project1_Report.docx` | Full written report: objectives, system overview, interface/data-flow table, use-case walkthrough, and conclusion. |
| `ivi_architecture.png` | Pre-rendered copy of the diagram (also embedded in the report). |
| `README.md` | This file. |

## What the project does

The notebook builds a four-layer conceptual architecture for an IVI system
entirely in code (no hand-drawn diagram):

1. **Application layer** — Media Player App, Navigation App, Projection Client
2. **IVI framework / system services** — Media Service, Navigation Service,
   Projection Service, Telephony Service, Display Compositor
3. **Hardware Abstraction Layer (HAL)** — Audio HAL, GNSS/Sensor HAL, Display
   HAL, Vehicle HAL
4. **Hardware** — Speakers, GPS/GNSS receiver, center display, vehicle CAN bus

Every connection between components is labeled with the concrete interface or
protocol carrying data across it (AIDL calls, PCM audio, NMEA fixes,
composited surfaces, CAN signals, etc.), which is what the assignment asks
for under "annotate component interfaces and data flow."

## How to run

1. Open `Project1_IVI_Architecture_Diagram.ipynb` in [Google Colab](https://colab.research.google.com).
2. Run all cells top to bottom. The first cell installs the Graphviz system
   binary (`apt-get install graphviz`) and the Python bindings — Colab does
   not ship these by default.
3. The final diagram renders inline and is also saved as `ivi_architecture.png`
   in the Colab runtime's working directory.

No Android SDK, emulator, or MATLAB is required for this project — it only
needs Python 3 and Graphviz.

## Report

`IVI_Project1_Report.docx` is the write-up to accompany the notebook. It
covers:

- Assignment restatement and objectives
- A layer-by-layer system overview
- The rendered architecture diagram (Figure 1)
- A full interface/data-flow table (Table 1) — every edge in the diagram,
  its protocol, and the data it carries
- A cross-cutting use case (an incoming call interrupting media playback)
  showing the architecture supports realistic runtime behavior, not just a
  static component list
- Methodology notes on why the diagram was generated programmatically
- References

## Extending this project

- Add a Bluetooth HAL + hands-free profile box feeding the Telephony Service.
- Split "Projection Client" into separate Android Auto and CarPlay boxes if
  the target platform must support both simultaneously.
- Cross-reference with **Project 2** (Android Automotive app simulation) and
  **Project 4** (MATLAB service-interaction state machine) from the same
  Module 6 submission — both implement the call-interrupts-media behavior
  described in Section 6 of the report at a finer level of detail.
