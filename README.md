# NASSCOM_SoC_design_VSD

This repo documents my very first shot at Physical Design by OpenLane 

Follow this Official documentation [OpenLane Documentation](https://openlane.readthedocs.io/en/latest/) 

The official OpenLane flow is give as follows in the given flow diagram 

![image](https://github.com/user-attachments/assets/7a5a6643-13c3-4857-8455-b2395261e79d)

follow the [source](https://openlane.readthedocs.io/en/latest/flow_overview.html) for further information 

Starting the OpenLane Environment and Running the flow

![image](https://github.com/user-attachments/assets/06542fa1-b2f2-4221-a1ce-7cf5e80c5f01)


this is the link for the OPENLANE openroad a project by effables (a step taken towards making backend vlsi deign opensource)
[Links and resources in Youtube](https://www.youtube.com/playlist?list=PLUg3wIOWD8yoZCg9XpFSgEgljx6MSdm9L)


## Lets explore the file systems before starting 

<br>

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20145459.png)

<br>
<br>
A process design kit (PDK) is a set of files used within the semiconductor industry to model a fabrication process for the design tools used to design an integrated circuit.

![image](https://github.com/user-attachments/assets/665287f1-e09f-49f7-834a-999dfe181a35)

<br>
<br>
Google SkyWater 130 PDK is an open-source toolkit for designing computer chips at the 130nm scale. Developed by Google and SkyWater Technology, it makes chip design accessible to everyone, from students to researchers, and supports innovation by providing essential design resources and compatibility with various design tools.
<br>
<br>

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20145638.png)

<br>

the libs.tech has technology specific tools that are used in substages lets take a look at what the OpenLane flow has to offer 

## Synthesis

- **yosys/abc**: Perform RTL synthesis and technology mapping.
- **OpenSTA**: Performs static timing analysis on the resulting netlist to generate timing reports.

## Floorplanning

- **init_fp**: Defines the core area for the macro as well as the rows (used for placement) and the tracks (used for routing).
- **ioplacer**: Places the macro input and output ports.
- **pdngen**: Generates the power distribution network.
- **tapcell**: Inserts welltap and decap cells in the floorplan.

## Placement

- **RePLace**: Performs global placement.
- **Resizer**: Performs optional optimizations on the design.
- **OpenDP**: Performs detailed placement to legalize the globally placed components.

## CTS (Clock Tree Synthesis)

- **TritonCTS**: Synthesizes the clock distribution network (the clock tree).

## Routing

- **FastRoute**: Performs global routing to generate a guide file for the detailed router.
- **TritonRoute**: Performs detailed routing.
- **OpenRCX**: Performs SPEF extraction.

## Tapeout

- **Magic**: Streams out the final GDSII layout file from the routed def.
- **KLayout**: Streams out the final GDSII layout file from the routed def as a back-up.

## Signoff

- **Magic**: Performs DRC Checks & Antenna Checks.
- **KLayout**: Performs DRC Checks.
- **Netgen**: Performs LVS Checks.
- **CVC**: Performs Circuit Validity Checks.

<br>

<body>
    <div class="image-row" style="display: flex; justify-content: flex-end; gap: 20px;">
        <img src="https://github.com/user-attachments/assets/1a92e3cc-7875-4a6a-b566-fa12b3a2bb9c" alt="Image 3" style="max-width: 100px; height: auto;">
        <img src="https://github.com/user-attachments/assets/d7338541-787e-413b-95ea-6308cd3a6939" alt="Image 2" style="max-width: 100px; height: auto;">
        <img src="https://github.com/user-attachments/assets/4df76b9c-b2ab-4d8d-b187-9358402e1ecd" alt="Image 1" style="max-width: 100px; height: auto;">
    </div>
</body>
</html>

<br>
<br>
Go to this path everytime when you want to invoke openalane 

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20152931.png)

use the ``docker`` command and use the ``./flow.tcl -interactive`` so that you can so throught the flow 
manually 

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20161323.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20161717.png)

If its a success then you will see this in your terminal

then invoke openlane package 0.9 using the following command ``package require openlane 0.9``

to prep your design and make a LEF file 
(What is a LEF file ? (.tlef) and (.lef) 
The technology LEF contains layer information (such as metal layers), while the cell LEF contains cell informations) Silicon  specific files that contribute to our final GDSII (Graphic Design System II file formating)

run the following command ``prep -design picorv32a``

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20162810.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20162850.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20164440.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20173539.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20173808.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20174305.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20175222.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20175528.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20181118.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20181651.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20181741.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20181937.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20182707.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-13%20182732.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20121926.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20140807.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20140944.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20141425.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20141746.png)

![](https://github.com/ARX-0/NASSCOM_SoC_design_VSD/blob/main/images/Screenshot%202024-07-14%20142658.png)

use the command ``run_synthesis`` to run your synthesizer and generate a netlist 

![image](https://github.com/user-attachments/assets/64e8fdbc-33e1-4538-90f9-77a8bcfd7896)

at this step your synthesis is complete 

![image](https://github.com/user-attachments/assets/50d937a3-95e1-4d55-9059-f20b6e0fc757)

the synthesised netlist can be viewed as such refering the above part automated by yosys 
