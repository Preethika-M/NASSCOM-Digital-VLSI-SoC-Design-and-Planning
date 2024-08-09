NASSCOM - DIGITAL - SOC - DESIGN - AND - PLANNING:

# Table of Contents

- [THEORY 1: OPEN-SOURCE EDA, OPENLANE & SKY130 PDK](#theory-1-open-source-eda-openlane--sky130-pdk)
  - [What is an RTL to GDSII flow?](#what-is-an-rtl-to-gdsii-flow)
  - [Insight into the QFN-48 Chip: Pads, Core, Die, and IP Components](#insight-into-the-qfn-48-chip-pads-core-die-and-ip-components)
  - [SOC DESIGN USING OPENLANE](#soc-design-using-openlane)
- [LAB 1: GETTING FAMILIAR WITH OPEN SOURCE EDA TOOLS](#lab-1-getting-familiar-with-open-source-eda-tools)
  - [Understanding OPENLANE Directory Structure](#understanding-openlane-directory-structure)
  - [Design Preparation Step](#design-preparation-step)
  - [Review files after design prep and run synthesis](#review-files-after-design-prep-and-run-synthesis)
  - [Characterization of Synthesized Results](#characterization-of-synthesized-results)
- [THEORY 2: GOOD FLOORPLAN VS BAD FLOORPLAN & INTRODUCTION TO LIBRARY CELLS](#theory-2-good-floorplan-vs-bad-floorplan--introduction-to-library-cells)
  - [CHIP FLOORPLANNING CONSIDERATIONS](#chip-floorplanning-considerations)
  - [LIBRARY BINDING AND PLACEMENTS](#library-binding-and-placements)
  - [CELL DESIGN AND CHARACTERISATION FLOWS](#cell-design-and-characterisation-flows)
  - [GENERAL TIMING CHARACTERISATION PARAMETERS](#general-timing-characterisation-parameters)
- [LAB 2: FLOORPLANNING & PLACEMENT](#lab-2-floorplanning--placement)
  - [RUN FLOORPLAN USING OPENLANE](#steps-to-run-floorplan-using-openlane)
  - [STEPS TO PERFORM PLACEMENT IN OPENLANE](#steps-to-perform-placement-in-openlane)
- [THEORY 3: DESIGN LIBRARY CELL USING MAGIC LAYOUT AND NGSPICE CHARACTERIZATION](#theory-3-design-library-cell-using-magic-layout-and-ngspice-characterization)
  - [SPICE DECK CREATION FOR CMOS INVERTER](#spice-deck-creation-for-cmos-inverter)
  - [INCEPTION OF LAYOUT & CMOS FABRICATION PROCESS](#inception-of-layout--cmos-fabrication-process)
    - [CREATE ACTIVE REGIONS](#create-active-regions)
    - [FORMATION OF WELLS](#formation-of-wells)
    - [FORMATION OF GATE TERMINALS](#formation-of-gate-terminals)
    - [LIGHTLY DOPED DRAIN (LDD) FORMATION](#lightly-doped-drain-ldd-formation)
    - [SOURCE DRAIN FORMATION](#source-drain-formation)
    - [LOCAL INTERCONNECT FORMATION](#local-interconnect-formation)
    - [HIGHER LEVEL METAL FORMATION](#higher-level-metal-formation)
- [LAB 3: INTRODUCTION TO MAGIC AND SKY130A](#lab-3-introduction-to-magic-and-sky130a)
  - [HOW TO MAKE CHANGES WHILE BEING IN THE FLOW?](#how-to-make-changes-while-being-in-the-flow)
  - [HOW TO GIT CLONE THE "VSDSCREDITCELLIGEN" REPO?](#how-to-git-clone-the-vsdsccreditcelligen-repo)
  - [INTRODUCTION TO SKY130A BASIC LAYERS AND LEF USING INVERTER](#introduction-to-sky130a-basic-layers-and-lef-using-inverter)
    - [TO CREATE STANDARD CELL LAYOUT IN MAGIC](#to-create-standard-cell-layout-in-magic)
    - [TO EXTRACT THE NETLIST IN MAGIC](#to-extract-the-netlist-in-magic)
  - [SKY130 TECH FILE LABS](#sky130-tech-file-labs)
    - [CREATE SPICEDECK USING SKY130 TECH](#create-spicedeck-using-sky130-tech)
    - [CHARACTERIZE INVERTER USING SKY130 TECH FILES](#characterize-inverter-using-sky130-tech-files)
- [Introduction to Magic Tools and DRC Rules](#introduction-to-magic-tools-and-drc-rules)
- [Introduction to SKY130 PDK](#introduction-to-sky130-pdk)
- [Introduction to Magic & Steps to Load SKY130 Tech Rules](#introduction-to-magic--steps-to-load-sky130-tech-rules)
- [Lab exercise to Fix Poly.9 error in SKY130 Tech File](#lab-exercise-to-fix-poly9-error-in-sky130-tech-file)
- [Lab Challenge Exercise to Describe DRC Error as Geometrical Construct](#lab-challenge-exercise-to-describe-drc-error-as-geometrical-construct)
- [Lab Challenge to Find Missing or Incorrect Rules and Fix them](#lab-challenge-to-find-missing-or-incorrect-rules-and-fix-them)
- [THEORY 4: DELAY TABLES, CTS, TIMING ANALYSIS](#theory-4-delay-tables-cts-timing-analysis)
  - [Introduction to delay tables](#introduction-to-delay-tables)
  - [Introduction to CTS](#introduction-to-cts)
  - [TIMING ANALYSIS](#timing-analysis)
- [LAB 4: PRE-LAYOUT TIMING ANALYSIS & IMPORTANCE OF GOOD CLOCK TREE](#lab-4-pre-layout-timing-analysis--importance-of-good-clock-tree)
  - [Timing Modelling Using Delay Tables](#timing-modelling-using-delay-tables)
    - [Converting the Grid Info to Track Info](#converting-the-grid-info-to-track-info)
    - [Converting Magic Layout to Standard Cell LEF](#converting-magic-layout-to-standard-cell-lef)
    - [Introduction to Timing Libs and Steps to Include New Cell in Synthesis](#introduction-to-timing-libs-and-steps-to-include-new-cell-in-synthesis)
    - [Steps to configure synthesis settings to fix slack and include vdd/vss](#steps-to-configure-synthesis-settings-to-fix-slack-and-include-vddvss)
  - [Timing analysis with ideal clocks using openSTA](#timing-analysis-with-ideal-clocks-using-opensta)
    - [Configure OpenSTA for post-synth timing analysis](#configure-opensta-for-post-synth-timing-analysis)
    - [Steps to run CTS using TritonCTS](#steps-to-run-cts-using-tritoncts)
  - [Timing analysis with real clocks using openSTA](#timing-analysis-with-real-clocks-using-opensta)
    - [Steps to execute OpenSTA with post-CTS timing libraries and CTS assignment](#steps-to-execute-opensta-with-post-cts-timing-libraries-and-cts-assignment)
  - [How to set wire to include but 1 segments?](#how-to-set-wire-to-include-but-1-segments)
- [THEORY + LAB 5: FINAL STEPS FOR RTL2GDS USING TRITONROUTE & OPENSTA](#theory--lab-5-final-steps-for-rtl2gds-using-tritonroute--opensta)
  - [Introduction to Routing Algorithm](#introduction-to-routing-algorithm)
  - [Steps to build Power Distribution Network](#steps-to-build-power-distribution-network)
  - [Steps for pin place by std cells](#steps-for-pin-place-by-std-cells)
  - [Steps for global and detailed routing and configure TritonRoute](#steps-for-global-and-detailed-routing-and-configure-tritonroute)
  - [Steps to configure synthesis settings to fix slack and include vdd/vss](#steps-to-configure-synthesis-settings-to-fix-slack-and-include-vddvss)
- [REFERENCES](#references)

## THEORY 1: OPEN-SOURCE EDA, OPENLANE & SKY130 PDK

### What is an RTL to GDSII flow?
 ![image](https://github.com/user-attachments/assets/857b8aa4-a80b-4b6e-9f3a-79bba78e6527)
RTL (Register Transfer Level)

Design:
High-level description of the circuit using Verilog or VHDL.

Synthesis:
Converts RTL code into a gate-level netlist (network of logic gates).


Floor Planning: Defines the overall architecture and placement of functional blocks.

Power Planning: Designs the power distribution network.

Placement:
Positions standard cells within the floorplan to optimize performance and routability.

Clock Tree Synthesis (CTS):
Creates a clock distribution network to ensure minimal skew and latency.

Routing:
Connects placed cells with wires according to the netlist, optimizing for signal integrity and performance.

Sign-Off:
Verifies that the design meets functional, timing, power, and signal integrity requirements.

GDSII (Graphic Data System II):
Generates the final file containing the complete physical layout of the chip for manufacturing.



 


### Insight into the QFN-48 Chip: Pads, Core, Die, and IP Components
![image](https://github.com/user-attachments/assets/53b64855-6f93-45b1-9c5e-4b1997905e7e)

![Screenshot 2024-08-03 083432](https://github.com/user-attachments/assets/afb357e5-eba4-4d7b-902b-46ab1b3e141e)![Screenshot 2024-08-03 083413](https://github.com/user-attachments/assets/d5675408-c927-4838-b290-f2424823eb7f)

Arduino Microcontroller Board Analysis

The image provided shows an Arduino Microcontroller Board. The primary focus is on the encircled area, which contains the 'Microprocessor.' We will be designing this microprocessor from an abstract level to the fabrication level using the RTL to GDS flow. To understand this process better, let's review some essential IC design components and terminologies:

IC Design Components and Terminologies
Core:
The core is the section of the chip where the fundamental logic of the design is implemented. This includes the microprocessor, memory blocks, and other critical functional blocks that define the chip's primary operations.

IO Pads:
IO pads serve as the communication channels between the core and the external environment. They are essential for transmitting and receiving signals, providing the necessary interface between the internal circuitry of the chip and external devices or systems.

Die:
The die is the part of the chip that includes both the core and IO pads. It represents the actual area implemented on the silicon wafer. The die is cut from the wafer and packaged to form the final integrated circuit (IC) that is used in electronic devices.

IPs (Intellectual Properties):
Foundry IPs are specialized components that often require manual design or human intervention to create. Examples include Analog-to-Digital Converters (ADC), Digital-to-Analog Converters (DAC), Phase-Locked Loops (PLLs), and many more. These components are crucial for the chip's functionality and are typically provided by third-party vendors or designed in-house.

### SOC DESIGN USING OPENLANE
![image](https://github.com/user-attachments/assets/ad27ee67-bf09-46be-a94b-bd50f6241198)


## LAB 1: GETTING FAMILIAR WITH OPEN SOURCE EDA TOOLS

### Understanding OPENLANE Directory, Structure Design Preparation Step
![image](https://github.com/user-attachments/assets/e8edf63a-136e-431a-afb5-8edf868217e1)

![Screenshot from 2024-08-03 17-39-28](https://github.com/user-attachments/assets/927570ef-b1bc-4702-bc65-fae51ba7c266)


### Review files after design prep and run synthesis
![Screenshot from 2024-08-06 08-51-45](https://github.com/user-attachments/assets/3f96e823-262d-42f2-9dc7-96b93d6c33ce)



## THEORY 2: GOOD FLOORPLAN VS BAD FLOORPLAN & INTRODUCTION TO LIBRARY CELLS

### CHIP FLOORPLANNING CONSIDERATIONS
![image](https://github.com/user-attachments/assets/0455a9f2-b58d-47d7-9cda-ec4b953c13db)
![image](https://github.com/user-attachments/assets/72be02cc-ad6e-4962-a261-040d70ab07e1)
![image](https://github.com/user-attachments/assets/c6c0bc03-f4fc-4de1-a2a0-c287c79e924b)
![image](https://github.com/user-attachments/assets/7e53b5aa-5b3f-48a1-a5f1-bb153fde7308)
![image](https://github.com/user-attachments/assets/ea862a9b-a520-4f9e-90a5-d8f614b122c2)
### Utilization Factor and Aspect Ratio
To calculate the Utilization Factor and Aspect Ratio, we must first determine the height and width of the core and die. These dimensions are directly influenced by the design's netlist, which specifies the number of components required to implement the logic. Consequently, the height and width of the die area are derived from the dimensions of the core area.

Example Calculation
Consider a netlist that includes two logic gates and two flip-flops. If we assume that each element occupies an area of 1 square unit, the netlist would contain four elements, resulting in a minimum total area requirement of 4 square units for the core area.

Utilization Factor
The Utilization Factor is the ratio of the area occupied by the netlist within the core to the total core area. An effective floorplan typically has a Utilization Factor less than 1. If the Utilization Factor equals 1, it indicates that the core area is fully occupied with no available space for additional logic, leading to an inefficient and potentially problematic floorplan.

Aspect Ratio
The Aspect Ratio is the ratio of the height of the core to its width. When the Aspect Ratio is 1, the core is square-shaped. An Aspect Ratio different from 1 indicates a rectangular shape for the core. Proper consideration of the Aspect Ratio is crucial in achieving a balanced and effective design layout.

### CONCEPT OF PREPLACED CELLS

![image](https://github.com/user-attachments/assets/eff0c46d-b9a2-4a2e-8de8-63b91b6c7703)

The concept of preplaced cells involves strategically organizing a complex combinational logic circuit, which may include thousands of gates, into predetermined locations within the layout. This process begins by identifying and positioning critical components or blocks, such as memory modules, clock gating cells, comparators, and multiplexers, at specific locations within the design.

These preplaced cells are treated as distinct entities or "black boxes," simplifying the overall integration and management of the design. The process of arranging these preplaced cells, along with other intellectual property (IP) blocks, within the layout is known as floorplanning.

During floorplanning, these IP blocks or critical components are assigned specific, user-defined locations on the chip before the automated placement-and-routing (P&R) process begins. Because their positions are predefined, they are referred to as preplaced cells. After the floorplanning stage, automated placement and routing tools are used to place the remaining logical cells in the design onto the chip, ensuring optimal connectivity and performance.

### CONCEPT OF DECOUPLING CAPACITOR

![image](https://github.com/user-attachments/assets/292d65d2-2cc9-4bea-9a71-422ee9f59f32)

In circuits, certain high-power components may experience insufficient power due to voltage drops in the connecting wires, leading to operation outside their required voltage range for reliable switching. To mitigate this issue, decoupling capacitors (De-cap cells) are strategically placed near these power-demanding components. These capacitors are connected to the power supply and charge up during periods of low switching activity.

When switching occurs, the decoupling capacitors rapidly discharge, providing the necessary power directly to these components. This quick response helps to stabilize the voltage and ensures reliable operation. After the switching event, the capacitors recharge, ready to supply power again when needed. This mechanism is crucial in circuit design to maintain stable operation and prevent performance issues caused by fluctuating power supply conditions.


### POWER PLANNING CONCEPT 

![image](https://github.com/user-attachments/assets/f521da2e-dfb8-4d26-aae4-34ca1cfb0493)
Power Planning: Addressing Voltage Drop and Ground Bounce
In the previous section, we discussed the role of decoupling capacitors (De-cap cells) in managing power distribution across various circuit blocks. However, De-cap cells have their limitations, including leakage power and increased chip area. To address these challenges, we employ a technique known as power planning. This approach is particularly important in areas of the chip with significant switching activity, where two critical issues can arise: voltage drop and ground bounce.

Voltage Drop
Voltage drop occurs when a large number of cells simultaneously switch from 0 to 1, creating a sudden surge in power demand. If the power supply is insufficient, the input voltage at that location can drop below the required level. This drop becomes a significant problem when the voltage level falls below the noise margin, leading to unreliable circuit operation and potential signal integrity issues.

Ground Bounce
Ground bounce is a phenomenon that happens when a group of cells simultaneously switch from 1 to 0, causing a large amount of current to flow to the ground pin at once. This sudden influx of current can temporarily elevate the ground voltage above 0, creating what is known as ground bounce. The problem arises when this temporary rise exceeds the noise margin, potentially causing logic errors and instability in the circuit.

Power Planning: Ensuring Stable Power Distribution
To address issues like voltage drop and ground bounce, an effective technique called power planning is employed. This involves creating two distinct power grids: one dedicated to Vdd (positive voltage) and another for ground. These power grids are usually implemented using the uppermost metal layers of the chip to minimize resistance and reduce voltage drops.

The power grids are carefully distributed across the entire design and connected to multiple Vdd and ground sources. This configuration allows cells to draw power directly from the nearest Vdd grid when switching from 0 to 1. Similarly, when a cell needs to release power, it discharges to the closest ground grid. By distributing power through these well-structured grids, power planning ensures that voltage levels remain stable and consistent, providing efficient power delivery to all parts of the chip and preventing performance issues.

### LIBRARY BINDING AND PLACEMENTS
![image](https://github.com/user-attachments/assets/1c08faeb-a974-4deb-a7af-459833d3a291)
![image](https://github.com/user-attachments/assets/cde58852-40b1-493c-8aea-179f71c20d29)
Netlist Binding and Initial Placement Design
In a netlist, each component is represented with its unique functionality—such as an AND gate having one configuration and an OR gate another. However, in the design library, all components are standardized with uniform square or rectangular shapes. This library includes a variety of pre-designed elements, each defined by specific properties like area, delay, and power consumption. Additionally, the library often contains multiple versions of the same component, each with different trade-offs in performance and size.

For example, larger versions of a component may offer faster performance but consume more area, while smaller versions conserve space at the expense of speed. The selection of these components during the initial placement stage is crucial for optimizing the overall design.

Optimizing Placement with Estimated Wire Length and Capacitance
During the placement phase, it is essential to consider the estimated wire length and associated capacitance when positioning cells. Wire length estimation involves calculating the distance between input sources and the output sinks they drive. Proper estimation helps minimize signal delays and optimize the overall performance of the circuit. By carefully considering wire length and capacitance, the placement process can achieve a balance between performance and area efficiency, leading to a more reliable and effective design.

### CELL DESIGN AND CHARACTERISATION FLOWS
![image](https://github.com/user-attachments/assets/abf517e6-a5a7-43dd-868e-4b4975eb6e05)
![image](https://github.com/user-attachments/assets/ad8bbfe3-61af-402b-af52-75191006b857)
Standard Cells
Standard cells are fundamental building blocks used in IC design, ranging from basic logic gates (like NAND, NOR, XOR) to more complex functional units (such as flip-flops and adders). These cells are designed to be reusable across different integrated circuit (IC) designs. Each standard cell is characterized by its functionality, area, power consumption, and timing characteristics, making them essential for efficient and scalable design processes.

Library
In IC design, a library (or cell library) is a collection of standard cells. Each cell within the library is optimized for specific parameters, including speed (delay), power consumption, area (size), and drive strength. The library serves as a repository of pre-designed components that can be used to create various digital circuits, ensuring consistency and efficiency across multiple designs.

Typical Cell Design Flow
The typical cell design flow involves several key steps, which are outlined below:
![image](https://github.com/user-attachments/assets/a5795dcb-4a9f-4c41-ac3f-30308a127862)


### GENERAL TIMING CHARACTERISATION PARAMETERS
![image](https://github.com/user-attachments/assets/f65d7a20-b4a1-4bd4-85e8-b221c3f88516)
![image](https://github.com/user-attachments/assets/94cd643c-8dde-47dd-9072-8763454f406a)
![image](https://github.com/user-attachments/assets/3deb8924-3691-4f70-a4eb-39e5450d2374)
![image](https://github.com/user-attachments/assets/0a971c67-ad7f-4dfc-88f8-c9ac1485b5d8)


## LAB 2: FLOORPLANNING & PLACEMENT

### RUN FLOORPLAN USING OPENLANE
To ensure a successful floorplanning process, designers must carefully consider specific parameters, often referred to as "switches," that can significantly influence the outcome. Key switches include the utilization factor and aspect ratio, which play a critical role in shaping the floorplan. It is essential for designers to confirm that these parameters meet the project specifications before starting the floorplanning phase. The accompanying image highlights the different types of switches that are pivotal during the floorplanning stage.
- After synthesis, use below command to run floorplan:
  ```bash
    run_floorplan
    ```
- Now to open the def file in magic, use below command:
  ```bash
   magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def

  ```
  
### STEPS TO PERFORM PLACEMENT IN OPENLANE
- [Content here...]

## THEORY 3: DESIGN LIBRARY CELL USING MAGIC LAYOUT AND NGSPICE CHARACTERIZATION

### SPICE DECK CREATION FOR CMOS INVERTER
- [Content here...]

### INCEPTION OF LAYOUT & CMOS FABRICATION PROCESS

#### CREATE ACTIVE REGIONS
- [Content here...]

#### FORMATION OF WELLS
- [Content here...]

#### FORMATION OF GATE TERMINALS
- [Content here...]

#### LIGHTLY DOPED DRAIN (LDD) FORMATION
- [Content here...]

#### SOURCE DRAIN FORMATION
- [Content here...]

#### LOCAL INTERCONNECT FORMATION
- [Content here...]

#### HIGHER LEVEL METAL FORMATION
- [Content here...]

## LAB 3: INTRODUCTION TO MAGIC AND SKY130A

### HOW TO MAKE CHANGES WHILE BEING IN THE FLOW?
- [Content here...]

### HOW TO GIT CLONE THE "VSDSCREDITCELLIGEN" REPO?
- [Content here...]

### INTRODUCTION TO SKY130A BASIC LAYERS AND LEF USING INVERTER

#### TO CREATE STANDARD CELL LAYOUT IN MAGIC
- [Content here...]

#### TO EXTRACT THE NETLIST IN MAGIC
- [Content here...]

### SKY130 TECH FILE LABS

#### CREATE SPICEDECK USING SKY130 TECH
- [Content here...]

#### CHARACTERIZE INVERTER USING SKY130 TECH FILES
- [Content here...]

## Introduction to Magic Tools and DRC Rules
- [Content here...]

## Introduction to SKY130 PDK
- [Content here...]

## Introduction to Magic & Steps to Load SKY130 Tech Rules
- [Content here...]

## Lab exercise to Fix Poly.9 error in SKY130 Tech File
- [Content here...]

## Lab Challenge Exercise to Describe DRC Error as Geometrical Construct
- [Content here...]

## Lab Challenge to Find Missing or Incorrect Rules and Fix them
- [Content here...]

## THEORY 4: DELAY TABLES, CTS, TIMING ANALYSIS

### Introduction to delay tables
- [Content here...]

### Introduction to CTS
- [Content here...]

### TIMING ANALYSIS
- [Content here...]

## LAB 4: PRE-LAYOUT TIMING ANALYSIS & IMPORTANCE OF GOOD CLOCK TREE

### Timing Modelling Using Delay Tables

#### Converting the Grid Info to Track Info
- [Content here...]

#### Converting Magic Layout to Standard Cell LEF
- [Content here...]

#### Introduction to Timing Libs and Steps to Include New Cell in Synthesis
- [Content here...]

#### Steps to configure synthesis settings to fix slack and include vdd/vss
- [Content here...]

### Timing analysis with ideal clocks using openSTA

#### Configure OpenSTA for post-synth timing analysis
- [Content here...]

#### Steps to run CTS using TritonCTS
- [Content here...]

### Timing analysis with real clocks using openSTA

#### Steps to execute OpenSTA with post-CTS timing libraries and CTS assignment
- [Content here...]

### How to set wire to include but 1 segments?
- [Content here...]

## THEORY + LAB 5: FINAL STEPS FOR RTL2GDS USING TRITONROUTE & OPENSTA

### Introduction to Routing Algorithm
- [Content here...]

### Steps to build Power Distribution Network
- [Content here...]

### Steps for pin place by std cells
- [Content here...]

### Steps for global and detailed routing and configure TritonRoute
- [Content here...]

### Steps to configure synthesis settings to fix slack and include vdd/vss
- [Content here...]

## REFERENCES
