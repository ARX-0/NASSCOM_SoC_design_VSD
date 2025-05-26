# NASSCOM_SoC_design_VSD

This repo documents my very first shot at Physical Design using OpenLane.

## Official Documentation

Follow the official [OpenLane Documentation](https://openlane.readthedocs.io/en/latest/).


the priority of tcl files 

**your_design inside the design folder** 
1). sky130A....tcl
2). config.tcl
3). config.tcl {in the configuration folder i.e default} 

one over rides the other


go with the flow of

run_synthesis
run_floorplan
run_placement
.....


The official OpenLane flow is shown in the flow diagram below:

![OpenLane Flow](https://github.com/user-attachments/assets/7a5a6643-13c3-4857-8455-b2395261e79d)

For further information, refer to the [source](https://openlane.readthedocs.io/en/latest/flow_overview.html).

## Starting the OpenLane Environment and Running the Flow

![Starting OpenLane](https://github.com/user-attachments/assets/06542fa1-b2f2-4221-a1ce-7cf5e80c5f01)

This is the link for the OPENLANE openroad, a project by efabless (a step towards making backend VLSI design open source):
[Links and resources on YouTube](https://www.youtube.com/playlist?list=PLUg3wIOWD8yoZCg9XpFSgEgljx6MSdm9L)

## File Systems Exploration

Before starting, let's explore the file systems.

![File Systems](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20145459.png)

A Process Design Kit (PDK) is a set of files used within the semiconductor industry to model a fabrication process for the design tools used to design an integrated circuit.

![PDK](https://github.com/user-attachments/assets/665287f1-e09f-49f7-834a-999dfe181a35)

The Google SkyWater 130 PDK is an open-source toolkit for designing computer chips at the 130nm scale. Developed by Google and SkyWater Technology, it makes chip design accessible to everyone, from students to researchers, and supports innovation by providing essential design resources and compatibility with various design tools.

![SkyWater 130 PDK](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20145638.png)

The `libs.tech` directory contains technology-specific tools that are used in various stages. Let's take a look at what the OpenLane flow has to offer.

## OpenLane Flow Steps

### Synthesis

- **yosys/abc**: Perform RTL synthesis and technology mapping.
- **OpenSTA**: Performs static timing analysis on the resulting netlist to generate timing reports.

### Floorplanning

- **init_fp**: Defines the core area for the macro, as well as the rows (used for placement) and the tracks (used for routing).
- **ioplacer**: Places the macro input and output ports.
- **pdngen**: Generates the power distribution network.
- **tapcell**: Inserts welltap and decap cells in the floorplan.

### Placement

- **RePLace**: Performs global placement.
- **Resizer**: Performs optional optimizations on the design.
- **OpenDP**: Performs detailed placement to legalize the globally placed components.

### CTS (Clock Tree Synthesis)

- **TritonCTS**: Synthesizes the clock distribution network (the clock tree).

### Routing

- **FastRoute**: Performs global routing to generate a guide file for the detailed router.
- **TritonRoute**: Performs detailed routing.
- **OpenRCX**: Performs SPEF extraction.

### Tapeout

- **Magic**: Streams out the final GDSII layout file from the routed def.
- **KLayout**: Streams out the final GDSII layout file from the routed def as a back-up.

### Signoff

- **Magic**: Performs DRC Checks & Antenna Checks.
- **KLayout**: Performs DRC Checks.
- **Netgen**: Performs LVS Checks.
- **CVC**: Performs Circuit Validity Checks.

## Invoking OpenLane

Go to this path every time you want to invoke OpenLane:

![Invoke OpenLane](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20152931.png)

Use the `docker` command and then use `./flow.tcl -interactive` to go through the flow manually.

![Docker Command](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20161323.png)

![Interactive Flow](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20161717.png)

If successful, you will see this in your terminal:

Invoke the OpenLane package 0.9 using the following command: `package require openlane 0.9`.

### Preparing Your Design and Making a LEF File

A LEF file contains information about the layers and cells used in the design. Run the following command to prepare your design and make a LEF file: `prep -design picorv32a`.

## Running Designs in OpenLane Flow

![Running Designs](https://github.com/user-attachments/assets/bd882e30-ee73-4c50-9f5f-64539c162dee)

![Design Screenshot 1](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20162810.png)
![Design Screenshot 2](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20162850.png)
![Design Screenshot 3](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20164440.png)
![Design Screenshot 4](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20173539.png)
![Design Screenshot 5](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20173808.png)
![Design Screenshot 6](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20174305.png)
![Design Screenshot 7](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20181118.png)
![Design Screenshot 8](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20181651.png)
![Design Screenshot 9](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20181741.png)
![Design Screenshot 10](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20181937.png)
![Design Screenshot 11](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20182707.png)

### I did calculate the T flip flop ratios for the AES for fun :) 

![image](https://github.com/user-attachments/assets/b9c56c71-e01f-4be0-ae73-5a52ffcec09e)


![Design Screenshot 12](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20182732.png)
![Design Screenshot 13](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20121926.png)
![Design Screenshot 14](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20140807.png)
![Design Screenshot 15](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20140944.png)
![Design Screenshot 16](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20141425.png)
![Design Screenshot 17](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20141746.png)
![Design Screenshot 18](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20142658.png)

Use the command `run_synthesis` to run your synthesizer and generate a netlist.

![Run Synthesis](https://github.com/user-attachments/assets/64e8fdbc-33e1-4538-90f9-77a8bcfd7896)

### Completed Synthesis

At this step, your synthesis is complete.

![Completed Synthesis](https://github.com/user-attachments/assets/50d937a3-95e1-4d55-9059-f20b6e0fc757)

The synthesized netlist can be viewed as shown above, automated by Yosys.

### Finding the Flop Ratio

![Flop Ratio](https://github.com/user-attachments/assets/e8561937-7313-430b-ae02-4a9caf43716d)

The general rule of thumb is: `dff_count / total_number_of_cells`.

By dividing: `1613 / 14876 = 0.108429`.


## Viewing the floorplan 

![image](https://github.com/user-attachments/assets/cd63a45a-ea51-4fd0-b4a0-591a66d024e4)

    magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def & 


You can view the floorplan in magic the following is the console log 

![image](https://github.com/user-attachments/assets/82f784c7-a243-4bd8-8893-f8eb5bb90dd2)

![image](https://github.com/user-attachments/assets/4c0da5a7-16b2-4cd7-a8b4-2174d803b0e5)

### Zooming in the magic tool to view our floorplan

![image](https://github.com/user-attachments/assets/3ad2ebc1-48a6-4cf2-97dd-276973b1ce0e)

![image](https://github.com/user-attachments/assets/09d568d4-4fbd-4f65-a673-71d1a01d1211)

![image](https://github.com/user-attachments/assets/322c92b3-4997-4b56-8fd5-87d1e6ee9615)

![image](https://github.com/user-attachments/assets/91cfc739-1e60-45af-9dfd-42d011a0e88d)

![image](https://github.com/user-attachments/assets/56c0b0f4-5e05-4579-b5ea-0de958bbe02f)

![image](https://github.com/user-attachments/assets/9635b322-89c8-4725-baa2-f06005cfa9df)

the extreme left end

![Screenshot 2024-07-21 155700](https://github.com/user-attachments/assets/d7fa5c65-b5c2-4e14-a51e-99324c306784)

![Screenshot 2024-07-21 155632](https://github.com/user-attachments/assets/4d3a3e70-5a99-4671-8549-1db869f715df)

![Screenshot 2024-07-21 155608](https://github.com/user-attachments/assets/7c8cdc7d-1bc0-4cc1-8d67-a199f1fc37a6)

## Beyond this I came to understand what is being done and I started to experiment with a different design because picorv32a stopped working for some reason, I took up the aes core.
