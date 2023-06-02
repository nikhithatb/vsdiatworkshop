# VSD OpenlANE Physical Design Workshop May-2023
Hands-on experience with the labs throughout the VSD 5-day Openlane Physical Design Workshop - May 2023

## Day 1 – OpenLANE and Sky130PDK

Theory

## How to talk to Computers

Introduction to QFN-48 Package, chips, pads, core, die, and Ips (Level 4)

Introduction to RISC-V

From Software Applications to Hardware

## SoC Design and OpenLANE

Introduction to all components of Open-Source Digital ASIC Design

Simplified RTL2GDS flow

Introduction to OpenLANE and Strive chipsets

Introduction to OpenLANE detailed ASIC design flow

## Starting the Labs

## Get familiar to open-source EDA tools
### What is OpenLANE and why should we use OpenLANE?

### Tool Interface
VM Virtual Box

### Part1: Sky_Lab1 - OpenLANE Directory Structure 

#### Files to run the workshop are all present in the tools directory under the Desktop folder

![Screenshot 2023-05-31 080438](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/17619bd5-3fc2-4f12-be22-193b4ed7bd2a)

#### Under the openlane_working_dir folder there are two subdirectories 1. openlane 2. pdks

In this workshop we will be using Skywater 130 pdk.

### The pdk subdirectory has sky130A where we will be working on. It also has open_pdks and skywater-pdk subdirectories

under sky130A, there are two files called "libs.ref" and "lib.tech" , each of the files indicates different functionality

> libs.ref file contains process specific files like timing, lef, cell lef. 

> libs.tech file contains specific to the tool.

Here we will be using "sky130_fd_sc_hd" pdk varaiant.

![Screenshot 2023-05-31 082233](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/ee6b21f0-fad7-4b7b-b2a8-b2ef25474ce0)

Under lib folder in the sky130_fd_sc_hd pdk variant, there are different process and PVT corners library files shown below

![Screenshot 2023-05-31 092919](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/108c050b-4fb9-4b28-99d5-188a287e4418)

Under lef and techlef folder in the sky130_fd_sc_hd pdk variant, there are technology lef files named as "tlef" shown below

![Screenshot 2023-05-31 100821](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/916758b8-a099-4410-a527-baba36198de8)

#### Under the openlane_working_dir folder the tool where we will be working on is "openlane"

> #### To invoke the "openlane" tool, we type the command called "docker" in the present working directory which is "/Desktop/work.tools/openlane/-working_dir/openlane" 

 The terminal appears as shown below 
 
 ![Screenshot 2023-05-31 102802](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/732ef461-0321-425b-81ac-4e21e5beec00)
 
 As we invoke the docker, we can check by tpying our present working directory (pwd) is "/openLANE_flow". 
 
>  The openLANE_flow has the scripts and design folders which we can work on. Using the script is how the flow has to go, here we have the "flow.tcl" and we     use "interactive" mode.

> We use interactive mode that makes the flow from "RTL to GDSII" in step by step manner which is automated by openLANE tool rather than runnng the flow at once.   It helps us understand what is going in each step , which step is doing what and comparing the results.

![Screenshot 2023-05-31 104540](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/5b8566c2-73e7-4186-be08-0b291a0560cb)

To run the flow , we require some of the packages. To import the packages we do as shown below

![Screenshot 2023-05-31 104831](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/dc81078d-f5ee-448e-a993-77d462b9da9f)

Now we head back to the design folder which we are going to run. There are multiple designs under the design folder that are already builtin in the openlane. In this workshop we are going to run the design name called "picorv32a" which is run by the openlane tool.

Under the "picorv32a" design folder we can see the "src" , "sky130A_sky130_fd_sc_hd_config.tcl" and "config.tcl" files.
> src file is where the RTL and sdc are present.
> config.tcl bypasses any configurations that has been done in openlane.

![Screenshot 2023-05-31 113229](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/41e82b3b-a41e-418e-bc99-dc495749190f)


Inside the config.tcl file we can see as below. In the design environment there are design required SDC, RTL files and clock period is given as 20ns which is specific to the design and clock nets and setting of the file name which means if the file exisits, source that particular file.

![Screenshot 2023-05-31 111141](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/d72a94fa-9a99-4515-ba3a-e27f990750d5)

When we open "sky130A_sky130_fd_sc_hd_config.tcl" file , we can see the clock period is set as 12ns which overrides the clock period in the "config.tcl" file since sky130A_sky130_fd_sc_hd_config.tcl has highest priority here.
 
#### We have to perform the first step synthesis now , before doing that we need to prepare the file system i.e., to set up the design.

### Design Setup Stage

We need to setup the file system specific to the flow , each and every step of the flow will be fetching files from particular location. Thst location needs to be created. For that we type the below command.

![Screenshot 2023-05-31 113554](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/8d19abee-fe5c-46e1-a819-5e7462c895b7)

> After creating the location for the design, we can see a new directory called "runs" is created under picorv32a design folder.

![Screenshot 2023-05-31 114430](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/b35cc51a-678b-496e-9c2c-09b28b169c6d)

In the run diectory , under the date folder, "tmp" directory is present which is a temporary directory that stores temporary files inside it. The "merged.lef" file is under "tmp" directory.  

![Screenshot 2023-05-31 115212](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/06e911c3-a239-410e-b731-bbbbd51d8ea1)

The merged.lef directory contains cell and tech lef files inside it as shown below.

> technology lef file 

![Screenshot 2023-05-31 114818](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/20fbf88b-4733-42c2-a2f4-7c1697b73bfa)

> cell lef file

![Screenshot 2023-05-31 115056](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/11282acd-2fd8-4c18-b39e-64f9bb2c4f07)

> The results and reports are under the date directory which contains the folders for each step of the design.

![Screenshot 2023-05-31 120221](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/b7633202-7c1a-42d1-99f9-3aa9078291b0)

> The config.tcl files are under the "picorv32a" directory and "runs" directory are shown below.

![Screenshot 2023-05-31 121336](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/3f41b55b-04f4-4f51-ae22-5eff9dc5a4a3)

### Run Synthesis
> The command to run in the openlane prompt is "run_synthesis". This will run the yosys and abc synthesis 

After we ran the synthesis, it appears as shown below

![Screenshot 2023-05-31 125112](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/4fdb14e9-a1c8-4aff-bec1-50fed0251c34)

> When we look at the sysnthesis flow, we can see the statistics of the design 

![Screenshot 2023-05-31 125002](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/0b5b92f1-6537-455d-a621-53e6d623b11e)

![Screenshot 2023-05-31 125407](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/a3240a64-9aa1-40eb-b4b4-340d9a1f3898)

#### Checking the Synthesised Netlist

> We can check the synthesised netlist "picor32a.synthesis.v" in the results folder where the mapping is done. The abc has done all the mapping.

![Screenshot 2023-05-31 125632](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/1c7c6f61-6d00-4a2f-aa7e-63989d50c933)

#### Checking the Timing Reports

##### The timing reports generated after running the synthesis are shown below

![Screenshot 2023-05-31 131004](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/ff28bc84-1fd0-4262-b893-566a6aef67ca)

Some of the reports are shown below

> Checking the "yosys_4.stat.rpt"

![Screenshot 2023-05-31 131236](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/1f356d26-0996-4fd6-9206-b3bffe3d8183)


> checking the "opensta.rpt"

 ![Screenshot 2023-05-31 130554](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/49004100-657a-4020-a8fa-f97bad102b7e)
 
 > Violated slack
 
 ![Screenshot 2023-05-31 130727](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/485c7504-8cc1-4ecf-abd0-55c61e51cb92)
 
 ## Day 2 – OpenLANE and Sky130PDK - Good Floorplan vs Bad Floorplan
 
  Theory
 
 ###  Foorplaning  considerations



### Part 2: Lab2 -Steps to run floorplan using OpenLANE
> openlane directory , we can go to configuration folder where we can see for the .tcl files for floorplan, placement and cts stages as well as README.md file where we can check for the variables of all these stages that are required.

![Screenshot 2023-06-01 092904](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/4a3860b5-be37-493f-b498-1b03d693db8f)

![Screenshot 2023-06-01 094005](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/1dd285c2-9176-4fde-8048-ed3667c2b7cb)

![Screenshot 2023-06-01 094111](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/d5e89a43-1a9c-4609-aa33-e313644a94b7)

#### Where are the switches set?

> The "set" values for the variables in each stages are the system default values in the specific .tcl file. Below shown is the floorplan.tcl file.

![Screenshot 2023-06-01 095358](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/a3dea347-7eeb-4c58-a1a7-5f91209643ec)

#### Precedence of .tcl files

> Here the lowest prioroty is the system default i.e., the "floorplan.tcl" file settings , after that "config.tcl" and the next is "sky130A_sky130_fd_sc_hd_config.tcl"

### Running the floorplan with the system default values

> After running the "run_floorplan" folder in the openlane prompt window , we can check the reports, results and log files under "runs" folder as shown below.

run_floorplan

> 4-ioplacer.log file

![Screenshot 2023-06-01 100620](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/409c6b90-471a-4ea3-867a-1b67d8dc97f3)

> pdn.log file

![Screenshot 2023-06-01 100703](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/00a5cb24-2cfc-4fcd-af0f-a32d05ac4c8c)

>  picorv32a.floorplan.def file - using the die area x and y coordinates we can calculate teh die area.

![Screenshot 2023-06-01 100912](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/ac21f3f4-9d1a-49c4-bffc-3eaa84f4abfa)

The below snapshot shows the the statement I mentioned above as the  "sky130A_sky130_fd_sc_hd_config.tcl" overrides the core utilization of config.tcl file.

![Screenshot 2023-06-01 115348](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/517ace40-f0e6-4b15-9ebf-8d3c096a98d7)

![Screenshot 2023-06-01 114717](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/ab05686f-0534-40bb-ac65-b51765bae009)

### Opening Magic
 The command to open Magic is shown below
 
 ![Screenshot 2023-06-01 120852](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/2a62836d-1eb6-4e82-82b3-87a0cf7698ab)
 
 > Magic is opened for floorplan
 
 ![Screenshot 2023-06-01 203406](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/c7f29904-feb7-4a47-b2af-c6cf2ad707fc)

 > When we zoom in and see , we can see the decap cells ,IO pins and standard cells.
  
  ![Screenshot 2023-06-01 203224](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/5c9ef3d5-7fc6-4a3f-8d7f-ea8b03eeed56)

  ![Screenshot 2023-06-01 124612](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/f62ac50c-ddf8-44b9-be30-7092bb132269)
  
  
  ### Placement Stages
   > Global Placment    - Coarse placement without legalization and in openlane the main criteria for global placement stage is reducing the wirelength also called as half paramenter wire length (HPWL).
   
   > Detailed Placement - legalization happens in the detailed placement i.e., standard cells are placed in  standard cell rows , without overlapping with each   other.
   
   > Here I am doing the condition related placement not concentrating on the timing , to ensure the congestion is less.

   #### Placement is completed by running the command "run_placement" in the openlane prompt terminal
   
    run_placement
   
   ![Screenshot 2023-06-01 194501](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/22bbb723-f0ad-42b3-97aa-41ede139bab2)
   
   #### Opening Magic
   
     The command to open Magic after placement step is shown below
    
    ![Screenshot 2023-06-01 194841](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/57621be9-82a9-4a5f-90a9-86742bbf687b)
    
     > Magic is opened for placement
     
     ![Screenshot 2023-06-01 214443](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/494f4cf5-3b43-4912-bb85-3261492baceb)

      > When we zoom in and see , we can see the standard cells are placed in rows and there are no DRCs.
     
     ![Screenshot 2023-06-01 214942](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/61f6c3aa-303e-4fbe-ad81-c32650ccac2b)


 ### Day3  – OpenLANE and Sky130PDK - Design Library Cell Uisng Magic Layout and ngspice Characterization
 
 #### IO placer revision
 
 > The IO pins are placed at the equidistant places in the floorplan , if we want to change the distance , we need to change the value in the floorplan.tcl file  under configuration folder for the IO mode.
 
 > To do that we can do as shown below by setting as 2 and the run the floorplan again.
 
 ![Screenshot 2023-06-01 220858](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/6acae1c9-f54e-4f28-9bf0-eb73a1ddf96c)

 


   
  
  









































