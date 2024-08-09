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
  - [PERFORM PLACEMENT IN OPENLANE](#steps-to-perform-placement-in-openlane)
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
 
- [DAY 4: DELAY TABLES, CTS, TIMING ANALYSIS](#day-4-delay-tables-cts-timing-analysis)

- [THEORY + LAB 5: FINAL STEPS FOR RTL2GDS USING TRITONROUTE & OPENSTA](#theory--lab-5-final-steps-for-rtl2gds-using-tritonroute--opensta)
  - [Introduction to Routing Algorithm](#introduction-to-routing-algorithm)
  - [Steps to build Power Distribution Network](#steps-to-build-power-distribution-network)
  - [Steps for pin place by std cells](#steps-for-pin-place-by-std-cells)
  - [Steps for global and detailed routing and configure TritonRoute](#steps-for-global-and-detailed-routing-and-configure-tritonroute)
  - [Steps to configure synthesis settings to fix slack and include vdd/vss](#steps-to-configure-synthesis-settings-to-fix-slack-and-include-vddvss)
- [REFERENCES](#references)
- [AUTHOR](#author)
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
 | **Task**                    | **Steps**                                                                 |
|-----------------------------|---------------------------------------------------------------------------|
| **Centering the Design**     | 1. Press `S` to select the entire design.                                 |
|                             | 2. Press `V` to align the design vertically to the middle of the screen.   |
| **Zooming In on a Specific Area** | 1. Left-click and drag to highlight the desired region.             |
|                             | 2. Right-click to open the context menu.                                   |
|                             | 3. Press `Z` to zoom in on the selected area.                              |
| **Retrieving Cell Details**  | 1. Hover your cursor over the cell for which you want details.            |
|                             | 2. Press `S` to select the cell.                                           |
|                             | 3. In the `tkcon` window, type the command `what` to display the cell's details. |
 
### PERFORM PLACEMENT IN OPENLANE
After successfully completing the floorplanning, the design process advances to the placement stage, which consists of two primary phases:

Global Placement: In this phase, the tool determines the approximate locations for all the standard cells within the design.

Detailed Placement: This phase finalizes the exact positions of all the standard cells, ensuring that the placement is legal. Legalization involves verifying that no standard cells overlap and that each cell is correctly positioned within the designated site rows.

To begin the placement process, use the following command:
```bash
run_placement
```
After placement, use the below command to view results:
```bash
/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-07_16-44/results/placement
```
And then we can see 'picorv32a.placement.def' file. To open it using MAGIC use the follwoing command:
```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def
```
## THEORY 3: DESIGN LIBRARY CELL USING MAGIC LAYOUT AND NGSPICE CHARACTERIZATION

### SPICE DECK CREATION FOR CMOS INVERTER
-A SPICE deck is essentially a netlist that contains detailed connectivity information, including the input signals, output tap points, and various other essential details. Let’s explore this with an example:
![image](https://github.com/user-attachments/assets/703abbb2-864c-4bda-b3d6-a8f173f0279e)

- Nodes are required for defining the netlist:
```bash
  MOSFET (ORDER FOR NETLIST) : Drain Gate Substrate Source
Syntax for MOSFET In a Netlist:
e.g : M1 out in vdd vdd pmos W = 0.375u L = 0.25u
```
![image](https://github.com/user-attachments/assets/fd69b185-3587-4e54-a95c-ccd31fd0caea)

![image](https://github.com/user-attachments/assets/f5bdb2d3-7805-445a-8b00-140acad56bdd)

### INVERTER CHARACTERISTICS

| **Characteristic**             | **Description**                                                                 |
|--------------------------------|---------------------------------------------------------------------------------|
| **Static Characteristics**     |                                                                                 |
| - **Noise Margins**            | The tolerance of the inverter to noise, defined by the difference between logic levels. |
| - **Transfer Characteristics** | The relationship between input voltage and output voltage.                      |
| - **Power Dissipation**        | The amount of power consumed by the inverter when it is in a steady state.      |
| - **DC Gain**                  | The gain of the inverter in the transition region, determining the steepness of the transfer curve. |
| **Dynamic Characteristics**    |                                                                                 |
| - **Propagation Delay**        | The time taken for the output to change after a change in input.                |
| - **Rise Time (tr)**           | The time it takes for the output to transition from low to high.                |
| - **Fall Time (tf)**           | The time it takes for the output to transition from high to low.                |
| - **Power-Delay Product (PDP)**| The product of power dissipation and propagation delay, indicating the energy efficiency of the inverter. |
| - **Capacitive Load Effects**  | The impact of capacitive loading on the speed and power consumption of the inverter. |

### INCEPTION OF LAYOUT & CMOS FABRICATION PROCESS

#### CREATE ACTIVE REGIONS
- ![image](https://github.com/user-attachments/assets/3d8fb7eb-2a77-4775-9596-a7747c8ff8a7)


#### FORMATION OF WELLS
- ![image](https://github.com/user-attachments/assets/797f3eeb-31f0-470e-ab74-f815ba9e37f4)


#### FORMATION OF GATE TERMINALS
- ![image](https://github.com/user-attachments/assets/a05bc54a-273b-4b6f-8110-10cbec65dba8)

#### LIGHTLY DOPED DRAIN (LDD) FORMATION
- ![image](https://github.com/user-attachments/assets/cd4c8565-4e34-4af7-beed-040fe2a1a811)


#### SOURCE DRAIN FORMATION
- ![image](https://github.com/user-attachments/assets/853c79db-019a-4352-a7a0-20dc3be1dbb9)


#### LOCAL INTERCONNECT FORMATION
- ![image](https://github.com/user-attachments/assets/dc2254b2-38ff-45bf-b3aa-2d7ee17e5cff)

#### HIGHER LEVEL METAL FORMATION
- ![image](https://github.com/user-attachments/assets/5b3656b8-0196-4704-8f91-f69a54426d83)


## LAB 3: INTRODUCTION TO MAGIC AND SKY130A

### HOW TO MAKE CHANGES WHILE BEING IN THE FLOW?
- First, verify the current configuration of the pins. Navigate to the following directory
- Use command to open "def" file in magic:
```bash
 magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def
```
- As we can see, the pins are currently placed at random equidistant intervals. If you want to change this to a different IO strategy, the IO placer (an open-source EDA tool) supports four different strategies. To make this change, navigate to the following directory and open the floorplan.tcl file:
  ```bash
  /Desktop/work/tools/openlane_working_dir/openlane/configuration$
  ```
  ```bash
  set ::env(FP_IO_MODE) 1; # 0 matching mode - 1 random equidistant mode
  ```
  The above code shows that the pins are randomly equidistant, so now set it to 2 and check for the pins
  ```bash
  set ::env(FP_IO_MODE) 2
  run_floorplan
  ```
### HOW TO GIT CLONE THE "VSDSCREDITCELLIGEN" REPO?
-Go to Openlane directory and use the following command
```bash
git clone <url of the github repo you want to clone>
```
Copy the file to directory vsdstdcelldesign using following command:
```bash
cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
```
-After successfully copied, use below command to open it:
```bash
magic -T sky130A.tech sky130_inv.mag &
```
### INTRODUCTION TO SKY130A BASIC LAYERS AND LEF USING INVERTER

#### TO CREATE STANDARD CELL LAYOUT IN MAGIC
- Refer this repository: 

#### TO EXTRACT THE NETLIST IN MAGIC
- In the tckon window, use the following command:
```bash
  % extract all
% ext2spice cthresh 0 rthresh 0
```

#### CREATE SPICEDECK USING SKY130 TECH
- [Content here...]

#### CHARACTERIZE INVERTER USING SKY130 TECH FILES
-Pin Definitions: Adjust the pin definitions (A and Y) to match the actual physical layout of your inverter.
-Timing Information: Replace the timing information with actual data from your characterization.
-Cell Size and Floorplan: Modify the cell size and floorplan according to your design.
```bash
LEFDEF VERSION 5.8 ;
UNITS DISTANCE MICRONS ;
    
# Define the cell
MACRO INVX1
  CLASS CORE ;
  ORIGIN 0 0 ;
  SIZE 1.0 BY 1.0 ;  # Example size, adjust as needed

  # Define the pins
  PIN A
    DIRECTION INPUT ;
    PORT
      LAYER METAL1 ;
      RECT 0.0 0.0 0.2 0.2 ;  # Adjust dimensions
    END
  END

  PIN Y
    DIRECTION OUTPUT ;
    PORT
      LAYER METAL1 ;
      RECT 0.0 0.2 0.2 0.4 ;  # Adjust dimensions
    END
  END

  # Timing information
  TIMING
    CELL RISE
      ( 0.1 0.2 0.3 0.4 ) ;  # Example timing data, adjust as needed
    END

    CELL FALL
      ( 0.1 0.2 0.3 0.4 ) ;  # Example timing data, adjust as needed
    END

    PROPELLING DELAY
      (0.060) ;  # Propagation Delay
    END

    CELL RISE DELAY
      (0.0637) ;  # Rise Time
    END

    CELL FALL DELAY
      (0.0275) ;  # Cell Fall Delay
    END
  END

  # Additional cell properties
  DIEAREA ( 0.0 0.0 ) ( 1.0 1.0 ) ;
  FLOORPLAN
    ROW 0.0 0.0 ;
  END

END MACRO
```

## Introduction to Magic Tools and DRC
-Follow this Webpage :  http://opencircuitdesign.com/magic/Rules

## Introduction to SKY130 PDK
https://skywater-pdk.readthedocs.io/en/main/ 
Use below command to download the LAB files while being in the home directory:
```bash
sudo wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
```
To extract labs from a zip file using a command line, you can use the following commands depending on your operating system:
```bash
sudo tar xfz drc_tests.tgz
```
## Introduction to Magic & Steps to Load SKY130 Tech Rules

| Step                             | Instructions                                                                                         |
|----------------------------------|------------------------------------------------------------------------------------------------------|
| **Select an Area and Fill with Metal 3** | 1. Open the Magic GUI.                                                                            |
|                                  | 2. Select the desired area on your layout.                                                          |
|                                  | 3. Navigate to the metal 3 layer.                                                                    |
|                                  | 4. Press `P` to fill the selected region with metal 3.                                               |
| **Create the VIA2 Mask**          | 1. Open the `tkcon` terminal within Magic.                                                           |
|                                  | 2. Type the command: `cif see VIA2`.                                                                 |
|                                  | 3. The metal 3-filled area will now be associated with the VIA2 mask.                                |


## Lab exercise to Fix Poly.9 error in SKY130 Tech File
- [Content here...]

## Lab Challenge Exercise to Describe DRC Error as Geometrical Construct
- [Content here...]

## Lab Challenge to Find Missing or Incorrect Rules and Fix them
- [Content here...]

## DAY 4: DELAY TABLES, CTS, TIMING ANALYSIS

### Introduction to delay tables
![image](https://github.com/user-attachments/assets/51305ee8-9962-45f1-af0e-2802477bda3d)
![image](https://github.com/user-attachments/assets/7b16b4c1-f04f-46a7-897c-3304607f4c87)
At every level , each node is driving the same load, hence there is no skew, if there would be a case with different loads then there will be skew.

### Introduction to CTS
![image](https://github.com/user-attachments/assets/6ec6b85e-a4ac-4bd8-b008-04442a906c72)
![image](https://github.com/user-attachments/assets/28c5902f-748c-4334-a44e-2fa219e0d294)
![image](https://github.com/user-attachments/assets/1c66c1c2-9f6e-453b-b6c8-0cc80fcbb05e)


### TIMING ANALYSIS
![image](https://github.com/user-attachments/assets/78cad181-2b94-4d35-a6f0-3024b9b1b9ec)
![image](https://github.com/user-attachments/assets/e33c4ca4-176a-423b-8b71-80bb251e68c5)


## LAB 4: PRE-LAYOUT TIMING ANALYSIS & IMPORTANCE OF GOOD CLOCK TREE

### Timing Modelling Using Delay Tables

#### Converting the Grid Info to Track Info
Purpose:

In physical design, it is essential to convert grid information, such as rows and columns, into track information. Tracks are predefined horizontal and vertical paths on each metal layer.

Considerations:

When designing standard cells, consider the following:

Case 1: Input and output ports should align with the intersections of vertical and horizontal tracks. Case 2: The standard cell's width should be an odd multiple of the horizontal track pitch, and its height should be an odd multiple of the vertical track pitch.

LEF File Extraction:

To continue, we need the LEF (Library Exchange Format) file for the Inverter cell. Extract this file from the current Inverter cell to provide essential information for the place-and-route (PNR) process.

Understanding Tracks:

Open the tracks.info file to learn more about the horizontal and vertical tracks available on each metal layer. This file specifies pitch, spacing, and other relevant details necessary for efficient routing.

-Command to open the custom Inverter Layout in Magic, first go to the 'vsdstdcelldesign' dircetory and then use:
```bash
magic -T sky130A.tech sky130_inv.mag &
```
![image](https://github.com/user-attachments/assets/6e7f6a9c-a2b7-48a1-8f1c-2bc6c895d7f1)
-Open the tracks.info file to know more about tracks:
```bash
# Fisrt go to the following directory :
/home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd

# open the tracks.info file
less tracks.info
```
![image](https://github.com/user-attachments/assets/e3f4668f-ef40-460a-992e-6db19fa4d2ab)
-To set grids as tracks of locali layer, use the follwoing command:
```bash
grid 0.46um 0.34um 0.23um 0.17um
```
![image](https://github.com/user-attachments/assets/a06fa015-026f-49b3-aef4-a39c90d9bbd5)
Now, we can see in the below image , that the Case 1 consideration is met i.e. Input and output ports are aligned with the intersections of vertical and horizontal tracks.
![image](https://github.com/user-attachments/assets/bea9003f-25d1-482d-92af-5550cf810b3a)
Now, we can see in the below image , that the Case 2 consideration are also met as 3 boxes are covered between the boundariesi.e. The standard cell's width should be an odd multiple of the horizontal track pitch, and its height should be an odd multiple of the vertica track pitch.
![image](https://github.com/user-attachments/assets/8022e0a9-62b2-4a99-8488-22acb837ed76)
![image](https://github.com/user-attachments/assets/0c4964c6-90f9-40ef-b2c1-9618bb24281d)
-How to convert labels to ports [No need to do it here as it is already done]:
![image](https://github.com/user-attachments/assets/26ca8fd8-7be5-4c99-bfef-7ae1950fe16d)

#### Converting Magic Layout to Standard Cell LEF
![image](https://github.com/user-attachments/assets/83897712-5ced-48c6-87c0-a4ebf460f4c4)
![image](https://github.com/user-attachments/assets/bc460505-a8ee-4299-980c-07af6f2f13de)
![image](https://github.com/user-attachments/assets/b1dae180-2c3d-4994-bd67-fb386aa83ae5)
![image](https://github.com/user-attachments/assets/92c44e4a-c86d-4884-9149-95574defcd92)
Now we need to extract the LEF file. First save .mag file by using the command ``save sky130_vsdinv.mag``` in the tkcon terminal.
![image](https://github.com/user-attachments/assets/9bab5ec8-e08d-45de-826b-e583d0ba6f59)
Now, use the follwoing command to open the saved mag file:
```bash
magic -T sky130A.tch sky130_vsdinv.mag &
```
![image](https://github.com/user-attachments/assets/7c89de43-1d85-431c-8552-625b4f92ab76)
![image](https://github.com/user-attachments/assets/077365f5-c1b3-46db-96db-1f7a7b3d9e13)

### Timing analysis with ideal clocks using openSTA

#### Configure OpenSTA for post-synth timing analysis
Next stage is to perform STA on the design: First create 'pre_sta.conf' file in the openlane directory as shiown below:
![image](https://github.com/user-attachments/assets/11efd173-b87e-497f-bbdd-5c1e38c2485f)
```bash
set_cmd_units -time ns -capacitance pF -current mA -voltage V -resistance kOhm -distance um
read_liberty -max /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib
read_liberty -min /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib
read_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis.v
link_design picorv32a
read_sdc /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/my_base.sdc
report_checks -path_delay min_max -fields {slew trans net cap input_pins}
report_tns
report_wns
```
![image](https://github.com/user-attachments/assets/ee7a9db4-0d23-4c10-85d5-45f065c0798f)
```bash


set ::env(CLOCK_PORT) clk
set ::env(CLOCK_PERIOD) 24.73
set ::env(SYNTH_DRIVING_CELL) sky130_fd_sc_hd__inv_8
set ::env(SYNTH_DRIVING_CELL_PIN) Y
set ::env(SYNTH_CAP_LOAD) 17.653
set ::env(IO_PCT) 0.2
set ::env(SYNTH_MAX_FANOUT) 6

create_clock [get_ports $::env(CLOCK_PORT)]  -name $::env(CLOCK_PORT)  -period $::env(CLOCK_PERIOD)

set input_delay_value [expr $::env(CLOCK_PERIOD) * $::env(IO_PCT)]
set output_delay_value [expr $::env(CLOCK_PERIOD) * $::env(IO_PCT)]

puts "\[INFO\]: Setting output delay to: $output_delay_value"
puts "\[INFO\]: Setting input delay to: $input_delay_value"

set_max_fanout $::env(SYNTH_MAX_FANOUT) [current_design]

set clk_indx [lsearch [all_inputs] [get_port $::env(CLOCK_PORT)]]

set all_inputs_wo_clk [lreplace [all_inputs] $clk_indx $clk_indx]

set all_inputs_wo_clk_rst $all_inputs_wo_clk

set_input_delay $input_delay_value -clock [get_clocks $::env(CLOCK_PORT)] $all_inputs_wo_clk_rst

set_output_delay $output_delay_value -clock [get_clocks $::env(CLOCK_PORT)] [all_outputs]

set_driving_cell -lib_cell $::env(SYNTH_DRIVING_CELL) -pin $::env(SYNTH_DRIVING_CELL_PIN) [all_inputs]

set cap_load [expr $::env(SYNTH_CAP_LOAD) /1000.0]

puts "\[INFO\]: Setting load to: $cap_load"

set_load $cap_load [all_outputs]
```
and then create 'my_base.sdc' file in the /picorv32a/src directory as shown above.
#### Steps to run CTS using TritonCTS
To update the previous design with the improved version, use the command:
```bash
write_verilog //path of the previous design//
#In our case:
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-07_16-44/results/synthesis/picorv32a.synthesis.v
```
![image](https://github.com/user-attachments/assets/5a2ed7b4-d6a9-4917-9db6-cf58d164f676)
Once the update is complete, proceed with the Floorplan stage using the same commands as before.
```bash
init_floorplan
place_io
tap_decap_or
```
```bash
run_placement
```
Now after the placement has been completed, we go for CTS:
```bash
run_cts
```
### Timing analysis with real clocks using openSTA
```bash
openroad
```
Above command to enter into openroad.
In openroad, We will first create the database (creted from lef and def files) and in the timing analysis this db is used. Run the follwoing commands:
```bash
read_lef /openLANE_flow/designs/picorv32a/runs/20-07_16-44/tmp/merged.lef
```
```bash
read_def /openLANE_flow/designs/picorv32a/runs/20-07_16-44/results/cts/picorv32a.cts.def
```
```bash
write_db pico_cts.db
```
```bash
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/20-07_16-44/results/synthesis/picorv32a.synthesis_cts.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
set_propagated_clock [all_clocks]
report_checks -path_delay min_max -format full_clock_expanded -digits 4

```
#### Steps to execute OpenSTA with post-CTS timing libraries and CTS assignment
First use ```exit`` to exit from openroad, now you will come to openlane: Now follow these steps: To check the current value of CTS_CLK_BUFFER_LIST
```bash
echo $::env(CTS_CLK_BUFFER_LIST)
```
![image](https://github.com/user-attachments/assets/2003fe64-dded-4da8-8a0b-2f89d267b7ca)
To remove sky130_fd_sc_hd__clkbuf_1 from the list
```bash
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]
```
![image](https://github.com/user-attachments/assets/bdb74c91-cff7-4f78-9aed-7ac96899fc85)
To check the current value of CURRENT_DEF
```bash
To check the current value of CURRENT_DEF
```
```bash
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/12-07_11-26/results/placement/picorv32a.placement.def
```
```bash
echo $::env(CTS_CLK_BUFFER_LIST)
```
Now, We need to follow the similar steps that we have followed earlier in the openroad. go to openroad again and then:
```bash
read_lef /openLANE_flow/designs/picorv32a/runs/12-07_11-26/tmp/merged.lef

read_def /openLANE_flow/designs/picorv32a/runs/12-07_11-26/results/cts/picorv32a.cts.def

write_db pico_cts1.db

read_db pico_cts1.db

read_verilog /openLANE_flow/designs/picorv32a/runs/12-07_11-26/results/synthesis/picorv32a.synthesis_cts.v

read_liberty $::env(LIB_SYNTH_COMPLETE)

link_design picorv32a

read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

set_propagated_clock [all_clocks]

report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
```
![image](https://github.com/user-attachments/assets/28ce9eac-0eb1-42c2-b1d7-4e484ce9b2e9)
```bash
report_clock_skew -hold
```
![image](https://github.com/user-attachments/assets/c9d38e13-1874-47a9-8757-7cd56380f076)
```bash
report_clock_skew -setup
```
To insert sky130_fd_sc_hd__clkbuf_1 :
```bash
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]
```
![image](https://github.com/user-attachments/assets/1abf71b8-9597-4221-b890-d62b1e66703f)


## THEORY + LAB 5: FINAL STEPS FOR RTL2GDS USING TRITONROUTE & OPENSTA

### Introduction to Routing Algorithm
Introduction to maze routing(Lees algorithm)
Routing:It is finding the best shortest possible connection between two end points with one point being the source and other point being the target and with less number of twist and turns.
Maze-Routing(Lee's Algorithm): These should not be zig-zag lines of connections most of the connections should be in L shape or in Z shape. So according to algorithm first it create some grids and grids are routing at the backend. It's called as routing grid. There are some numbers of grids on this routig having some dimensions. SO here we are having two points one is 'Source' and the other is 'Target'. With the help of this routing grid algorithm has to find out the best possible way between them.

First step is algorithm tries to lable all of the grids surrounded. Only the adjacent horizontal and vertical grids are labeled not the digonal one as shown in the image below.Now we will lable the grids to the next integer untill we reach to the target. In the example we reached the target after integer 9.So now there are so many ways to reach to target from source but we have to choose the best shortest possible way to reach the target.And we need to avoid the zig-zag way better to cghoose 'L' shape routing'.
![image](https://github.com/user-attachments/assets/2bf73365-e013-418d-b580-ecf766922113)
![image](https://github.com/user-attachments/assets/2b7e3c37-2b10-4662-8243-de3a9899f667)
![image](https://github.com/user-attachments/assets/201582a6-ca73-42be-82a2-24f83615e69c)
![image](https://github.com/user-attachments/assets/6a02dc3e-8fb7-43bf-82ba-2015db9e15aa)
![image](https://github.com/user-attachments/assets/2f9bad5e-dd4d-4ea2-bec0-47183adf98d3)
![image](https://github.com/user-attachments/assets/c1fbb71d-c3ed-4aa4-8352-f54d6ec20a52)

### Steps to build Power Distribution Network

### Steps for pin place by std cells
![image](https://github.com/user-attachments/assets/e2a30f51-6ecb-4f09-8f21-a7367f3ab34d)

In the figure above, we can see how power is distributed to the standard cells. Surrounding the design are I/O pads, with the red and blue blocks representing power pads. The red pads supply power, while the blue ones provide the ground connection. These pads connect to power and ground rings that encircle the design, supplying power to straps. The vertical lines seen for the rings are known as power straps. Connections from the power straps and rings extend to the power rails, with standard cells positioned between these rails. The height of the standard cells must be multiples of the rail pitch to ensure proper power and ground supply.


Now the last stage in the design is Routing , us ethe following command:
```bash
run_routing
```
![image](https://github.com/user-attachments/assets/5aa69f48-5e09-4f73-9d4f-c0799e12d5d9)
The routing has been completed with zero violations, but there is a negative slack, we need to eleiminate the engaticve slack for successful completion of the Physical Design Flow.


### Steps for global and detailed routing and configure TritonRoute
-Commands to view and change parameters to improve timing and run synthesis:
| Step | Command                                          | Description                                                               |
|------|--------------------------------------------------|---------------------------------------------------------------------------|
| 1    | `prep -design picorv32a -tag 24-03_10-03 -overwrite` | Prepare the design for updating variables                                   |
| 2    | `set lefs [glob $::env(DESIGN_DIR)/src/*.lef]`       | Include newly added LEF files in the OpenLane flow                          |
| 3    | `add_lefs -src $lefs`                               | Merge the LEF files                                                        |
| 4    | `echo $::env(SYNTH_STRATEGY)`                       | Display the current value of the `SYNTH_STRATEGY` variable                   |
| 5    | `set ::env(SYNTH_STRATEGY) "DELAY 3"`               | Set a new value for the `SYNTH_STRATEGY` variable                            |
| 6    | `echo $::env(SYNTH_BUFFERING)`                     | Check if `SYNTH_BUFFERING` is enabled by displaying its current value       |
| 7    | `echo $::env(SYNTH_SIZING)`                        | Display the current value of the `SYNTH_SIZING` variable                    |
| 8    | `set ::env(SYNTH_SIZING) 1`                        | Set a new value for the `SYNTH_SIZING` variable                             |
| 9    | `echo $::env(SYNTH_DRIVING_CELL)`                  | Check the current value of `SYNTH_DRIVING_CELL` to ensure it's the correct cell |
| 10   | `run_synthesis`                                   | Run the synthesis process after the design is prepared                      |

![image](https://github.com/user-attachments/assets/3b07f6d2-f2f4-41e2-ba2a-24179dad8b90)
![image](https://github.com/user-attachments/assets/d6c62888-201c-491c-9aaf-646b5a6cf5cf)

To view the final layout, use the following command:
```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-07_15-00/tmp/merged.lef def read /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-07_15-00/results/routing/picorv32a.def &
```

![image](https://github.com/user-attachments/assets/b0c975cd-5bc7-45fb-84b8-6daaea4a7fcd)
![image](https://github.com/user-attachments/assets/71b0f5e4-636f-42cb-808d-47ac5aa8ac87)

### Triton route:

![image](https://github.com/user-attachments/assets/54050705-1318-4a3e-9643-3604d4b19eb2)
![image](https://github.com/user-attachments/assets/5c71bac9-3470-41a1-8aa3-f63dcad37cbb)

TritonRoute Features TritonRoute is a sophisticated detailed routing tool designed for the physical design of integrated circuits (ICs). It integrates several advanced features that enable efficient and accurate routing in complex designs, especially for advanced technology nodes.

Key Features of TritonRoute

Preprocessed Route Guides:
TritonRoute uses preprocessed route guides to enhance the efficiency of the routing process. These guides are generated during the global routing stage and provide the tool with initial routing paths, helping to streamline the detailed routing phase. By following these guides, TritonRoute can reduce the search space for routing paths, leading to faster and more efficient routing.

Inter-Guide Connectivity:
The tool effectively manages inter-guide connectivity, ensuring that the connections between different routing guides are optimized for both performance and manufacturability. This feature helps maintain continuity across different routing segments and ensures that all nets are properly connected according to the design specifications.

Intra- & Inter-Layer Routing:
TritonRoute handles both intra-layer and inter-layer routing with precision. Intra-layer routing deals with connections within the same metal layer, while inter-layer routing handles connections between different metal layers. The tool carefully manages the transitions between layers, using vias and other routing strategies to ensure that all connections are made efficiently and with minimal interference.

Intra-Layer Parallel and Inter-Layer Sequential Panel Routing:
TritonRoute employs an intra-layer parallel routing method, allowing it to handle multiple routing tasks simultaneously within the same layer. This parallelism increases the efficiency and speed of the routing process. For inter-layer routing, TritonRoute uses a sequential panel routing method. This approach ensures that connections between different layers are made in a controlled and orderly manner, reducing the risk of conflicts and ensuring that all design rules are adhered to.

Connectivity Access Point Handling:
TritonRoute includes advanced algorithms for managing connectivity access points, which are critical for ensuring that all nets are properly connected in the final design. The tool handles both access points and access point clusters, ensuring that even in dense or complex designs, all required connections are made reliably.

Access Point Cluster Management:
TritonRoute manages access point clusters, which are groups of potential connection points that can be used to connect different parts of the design. By efficiently managing these clusters, the tool can optimize routing paths and reduce congestion, leading to better overall design performance.

## REFERENCES
This project has utilized resources and materials from the following sources:
-[VSD STANDARD CELL DESIGN] (#https://github.com/nickson-jose/vsdstdcelldesign)
-[GOOGLE SKYWATER PDK](#https://github.com/google/skywater-pdk)
-Materials provided in the NASSCOM VSD SoC Design Program

### AUTHOR
Preethika-M
