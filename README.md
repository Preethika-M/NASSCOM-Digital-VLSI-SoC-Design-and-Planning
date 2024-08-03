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
  - [STEPS TO RUN FLOORPLAN USING OPENLANE](#steps-to-run-floorplan-using-openlane)
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
RTL (Register Transfer Level) Design:

High-level description of the circuit using Verilog or VHDL.

Synthesis:
Converts RTL code into a gate-level netlist (network of logic gates).
Floor Planning and Power Planning (FP+PP):

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
![Screenshot 2024-08-03 083432](https://github.com/user-attachments/assets/afb357e5-eba4-4d7b-902b-46ab1b3e141e)![Screenshot 2024-08-03 083413](https://github.com/user-attachments/assets/d5675408-c927-4838-b290-f2424823eb7f)



### SOC DESIGN USING OPENLANE
- [Content here...]

## LAB 1: GETTING FAMILIAR WITH OPEN SOURCE EDA TOOLS

### Understanding OPENLANE Directory Structure
- [Content here...]

### Design Preparation Step
- [Content here...]

### Review files after design prep and run synthesis
- [Content here...]

### Characterization of Synthesized Results
- [Content here...]

## THEORY 2: GOOD FLOORPLAN VS BAD FLOORPLAN & INTRODUCTION TO LIBRARY CELLS

### CHIP FLOORPLANNING CONSIDERATIONS
- [Content here...]

### LIBRARY BINDING AND PLACEMENTS
- [Content here...]

### CELL DESIGN AND CHARACTERISATION FLOWS
- [Content here...]

### GENERAL TIMING CHARACTERISATION PARAMETERS
- [Content here...]

## LAB 2: FLOORPLANNING & PLACEMENT

### STEPS TO RUN FLOORPLAN USING OPENLANE
- [Content here...]

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
