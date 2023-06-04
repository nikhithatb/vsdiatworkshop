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
 
 > When we open magic layout window and observe, and are not equidistant anymore, they are stacked upon one another.
 
 ![Screenshot 2023-06-02 103446](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/5420112f-eb56-4045-9df4-a4b3f95b5494)
 
 ![Screenshot 2023-06-02 103551](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/17026dfa-2957-497a-8ec3-8ff6a1b8e7b0)
 
 #### Git steps to clone the inverter design from the git repo link https://github.com/nickson-jose/vsdstdcelldesign which has pmos, nmos and inverter sky130 spice models, custom made by Nickson Jose.
 
 > step1: Go to the git repo link and click the top right "code" menu
 
 > step2: Copy the https:// url 
 
 > step3: Paste it in the ubuntu terminal window under openlane directory with the below command
 
   git clone https://github.com/nickson-jose/vsdstdcelldesign.git
  
 > Once you clone it should appear as below
 
 ![Screenshot 2023-06-02 111016](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/cc01c1d1-1c6f-46ad-a1f3-0e98c8150339)
 
 > Once you open the vsdstdceldesign folder you can all the files which are cloned from the git repo shown above
 
 ![Screenshot 2023-06-02 111320](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/ed8d92cc-b24f-489f-9172-4169f505413a)
 
 #### Lb introduction to sky130 basic layers layout and LEF using inverter.
 
 > The next thing we should do is open the .mag folder and see how many layers are there for building an inverter , we will be performing spice extraction as well as the post-layout spice simulations.

> Before we open the mag file, we need the magic tech file to open this. For that we can copy the magic tech file in the "vsdstdcelldesign" folder. To do this, we should first copy the magic tech file from magic directory

![Screenshot 2023-06-02 112314](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/e2d2d594-9c47-4216-8734-90511443109b)

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/29bd90f2-1fda-4198-8193-b039bd97cc7a)

 As you can see it is copied inside vsdstdcelldesign directory.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/6ea9f03a-2370-4fe8-a047-7716ba307adb)

> And the we open the magic window by typing this command 

![Screenshot 2023-06-02 113411](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/0374fa15-7a79-499a-8061-ce6a1fc5e956)

> The layout of the inverter opens here

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/e8ad5154-139e-40e1-a9fc-c775c6a9a51d)

> Inside the magic layout window , if we want to see how the layers are connected to the gate(polysilicon) with the pmos and nmos diffusion layer , we can select the portion on the layout by clicking 's' on the invereter cell and type 'what' in the tcl window.

![Screenshot 2023-06-02 114653](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/f8af7bb2-772a-4522-9c6d-4fb15acf6fca)

> On the right corner we can see different color palattes where there are different colors for different layers of the layout design.

> Next we will check whether the drain of pmos and drain of nmos are connected or not.

> To check if the output 'y' is connected to the drain of pmos and the drain of nmos.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/791911c1-52f0-44b5-a51b-a9b69a482c2f)

> To check if the source of the pmos is connected to vdd we select the contact of the source and then check.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/2bd29811-30be-4d82-8726-bbd8f1ee547f)

> To check if the nmos is connected to ground , we do the same by selecting the contact of the source of nmos. 

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/7624499f-0e3d-46db-b0b0-eacf6b1adb8e)

#### Lab steps to create standard cell layout and extract spice netlist

#### Creation of a standard cell in magic layout

To create a bounding box in Magic with the specified dimensions, you can follow these steps:

1. Open the Magic tool and invoke the sky130 technology file by running the command:

   magic -T sky130A.tech
 

2. In the Magic tkcon window, type the following command to create the bounding box:
  
   property FIXED_BBOX {0 0 138 272}

   This command sets the fixed bounding box with the given dimensions. The values {0 0} represent the bottom-left coordinates of the bounding box, and the values {138 272} represent the top-right coordinates. The width of the bounding box is set to 138, which is 3 times the width of the standard cell (0.46 * 3 = 1.38). The height is set to the height of the standard cell, which is 272.

3. After entering the command, press Enter. The bounding box will be created with the specified dimensions.

Now you have successfully created a bounding box in Magic with a width of 1.38 (3 times the width of the standard cell) and a height of 2.72 (height of the standard cell). You can proceed with your layout design within this bounding box.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/965a173c-ab8e-482f-97bd-08e41bef1453)

To proceed with defining the ground and power segments, contacts, and the layout of the logic part in the standard cell layout design using Magic, you can follow these steps:

1. Define Ground and Power Segments:

   - In the Magic tkcon window, select the metal layer 1 (M1) for defining the ground and power segments. Use the command:
     
     layer M1
     

   - To define the ground segment, draw a rectangle by specifying its coordinates using the `box` command. For example:
     
     box 0 0 138 20
     
     This command creates a rectangle from coordinates (0, 0) to (138, 20) on the M1 layer, representing the ground segment.

   - Similarly, define the power segment using the `box` command. For example:
     
     box 0 252 138 272
     
     This command creates a rectangle from coordinates (0, 252) to (138, 272) on the M1 layer, representing the power segment.

2. Define Contacts:

   - Switch to the contact layer (typically via M1 stack) using the command:
    
     layer contact
    
   - To define a contact for the ground segment, use the `box` command to draw a rectangle at the appropriate location. For example:
    
     box 130 0 138 8
    
     This command creates a contact rectangle from coordinates (130, 0) to (138, 8) on the contact layer, representing the contact for the ground segment.

   - Similarly, define a contact for the power segment using the `box` command. For example:
     
     box 130 264 138 272
     
     This command creates a contact rectangle from coordinates (130, 264) to (138, 272) on the contact layer, representing the contact for the power segment.

3. Layout of the Logic Part:

   - Switch to the desired layer for drawing the logic part layout (typically M1) using the command:
   
     layer <desired_layer>

   - Now, you can draw the layout of the logic part of the standard cell using various commands, such as `rect`, `poly`, and `wire`. These commands allow you to define shapes, polygons, and wires respectively, based on the desired circuit design.

   - Specify the coordinates and dimensions of the logic part components using the appropriate commands. For example:

     rect 20 30 40 60
 
     This command creates a rectangle at coordinates (20, 30) with a width of 40 and height of 60 on the specified layer.

   - Continue defining the layout of the logic part as per your circuit design requirements, using the relevant commands to create shapes, polygons, and wires.

By following these steps, you can define the ground and power segments, contacts, and layout of the logic part for any standard cell layout in Magic. Remember to switch between the appropriate layers using the `layer` command based on the element you want to define or draw.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/ca25aad5-82c5-411b-82a2-db3efbe10d00)

> We can check and modify the drc errors in the magic window by clicking on 'DRC' menu and select 'DRC find next error'

#### How to extract the inverter layout in ngspice

> Step 1: To create ngspice file

To extract the inverter in ngspice, all we need to do is write the 'extract all' in tkcon.tcl window and we can see the ext file and check in the 'vsdstdcelldesign' directory.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/e92f60dc-2ff5-4a1e-9666-ac5176f46f46)

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/f78cf8cc-9801-4b93-bcff-4053d887e265)

> Step 2: To extract spice file inside the vsdstdcelldesign directory we should give the following command

![Screenshot 2023-06-02 144947](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/f0d1b5b1-f7ec-4432-b572-0f1456a3343c)

 When we open the spice file it has as shown below

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/c771adf7-ac1e-4419-8ee5-d28c2c49922f)

#### Lab steps to create final SPICE deck using SKY130 tech

 When you open the spice file which is extracted and modify the file by giving inputs as pshort , nshort library model files , source, ground and setting the grid values with trainsient analysis we have seen in the magic window before running it in the ngspice file. The modified file is shown below.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/d518fbf4-9b92-4de5-81f4-5ccb6f1bb0d6)

> The model file looks like this. The below shown is the 'pshort.lib' model file

![Screenshot 2023-06-03 105635](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/380d6a91-6ff6-4cf0-a7a0-7e409dbd3fc7)

> After running the ngspice with the spice file, we get the output like this

![Screenshot 2023-06-03 105518](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/023f36d1-b8af-4c74-b111-60a264dc0dd6)

#### Lab steps to chracterize inverter using SKY130 model files

> To check the plot we need to type "plot y vs time a". Here y is the output, time is the time period and a is the input.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/3ffd5f75-ffaa-4e1f-8e50-ba4b80956c80)

Here the spikes are showing on the plotted pulse, to overcome that we need to change the Cload in the "sky130_inv.spice"as higher value than the previos one, I changed to 2fF. Now the plot like below, some what better compared to the previous one.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/eb625570-bdb0-4784-a6e4-fd6aedb036e1)

Next step is to charcetize the cell that means to find the value of four parameters 1. Rise Transition (output rise 20%-80%) 2. Fall Transition(output fall 80%-20%) 3.Fall cell delay 4.Rise cell delay also called the propogation delay. 

> For Rise Transition, the 20% of 3.3V is 0.64

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/cabbc52e-8163-4316-8148-441e07a26674)

![Screenshot 2023-06-03 112037](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/f18639fe-36cc-4b2e-9947-878be2d4f717)


> For Rise Transition, the 80% of 3.3V is 2.64

![Screenshot 2023-06-03 112351](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/fea67921-7c89-49e2-ab9e-1a5d3b695815)

![Screenshot 2023-06-03 112330](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/dc2f1d06-7071-4c29-8152-8585b2dadb8a)

Therefore the Rise transition for the above plot is 2.245-2.181 = 0.064ns

> Similarly for fall transition , from 80%-20%

For 80%, the fall transition is

![Screenshot 2023-06-03 113523](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/77d90d33-60cd-4b4c-b151-7129d1bba9d2)

For 20%, the fall transition is

![Screenshot 2023-06-03 113626](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/bf1b71a3-be68-4863-b7d0-7c21964ec9b8)

Therefore the Fall transition for the above plot is 0.04ns

> Cell rise delay at 50% of 3.3V is 1.64V , therefore the output and input at 50% is shown below

![Screenshot 2023-06-03 114304](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/4ef01af6-1694-4f27-9f0b-0c569dbdf11a)

Therefore 2.2132-2.1498 = 0.0634ns is the cell rise delay.

> Cell fall delay at 50% of 3.3V is 1.64V , therefore the output and input at 50% is shown below

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/aa779c09-83aa-4c93-a0c1-021d9bd2e339)

Therefore 4.09-4.07 = 0.02ns is the cell fall delay.

> Next objective is to use the inverter layout to create a  LEF file and this LEF file will be used in the openlane and plug-in this cell by making a custom cell uing a custom link. We will plug this cell in picorv32 core and see the openlane takes this input or not.

#### Lab introduction to Magic tool options and DRC rules.

### Intrdocution to Magic 
* In-depth knowledge of Magic's DRC engine
* Introduction to Google Skywater DRC rules
* Lab: warm-up exercise : Fix a simple rule error
* Lab: Main exercise : Fix or create a complex error

* The documentation URL for Magic DRC is http://opencircuitdesign.com/magic
  > Two main guides for magic is "using magic"  and technology files

* To read the skywater pdk documentation and understand the design rules we can follow this link https://skywater-pdk.readthedocs.io/en/main/ and    https://github.com/google/skywater-pdk.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/65a15860-0b76-4856-a3fb-8462921e9e85)

> We can click on the rules specified in this docs and can be used for the layouts that are used in the labs

When we see inside the open_pdk drc files after the extraction using "tar xfz drc_tests.tgz" we can see the complete information about the magic layout for this lab.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/52769c34-2663-45a7-a1d8-51f4a93ada52)

> To look into the magicrc file you can open and see what is inside of it

#### Starting the Magic

> magic -d XR  It is the command to start the magic for better graphics 

First we can check the simple example failing set of rules of metal 3 layer by either typing the command 

magic -d XR metal3.mag

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/ec920ae6-35a1-4d34-b625-095f95c803b7)

or from the magic window "menu - file - open -load file9here, metal3.mag".

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/50feb95c-eb8c-4021-87cc-72e57eea0d9b)

We can look for the rules from https://skywater-pdk.readthedocs.io/en/main/ for each of them. Here for metal 3 the rules can be seen as below from the link.

> Under the 'Design rules' content go to 'periphery rules', from there we can click on metal 3 rule button and you can see like this below

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/2ec55e57-62ba-4066-b421-9fb03b3e6a43)

> To look on the area of the metal 3 opened in the magic window , click 'left mouse button' and then 'right mouse button' drag the box by clicking right mouse button and then click 'column (: or ;)' and type 'drc why'.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/8900b3c1-27d5-4ad5-b2d3-64e50c10d46f)

1. Start by hovering your mouse pointer over the M3 contact icon on the side toolbar. This will allow you to draw a large area of M3 contact on the layout.

2. Once you have drawn the M3 contact area, a cursor box will appear around it.

3. Now, type the command "cif see VIA2" to create contact cuts represented as black square shapes. These contact cuts don't physically exist on the drawn layout but are used as a mask layer called VIA2, which will be included in the GDS (Graphic Data System) file.

4. Additional details about these contact cuts can be found in the CIF output section of the tech file.

5. The current view is the feedback entry. You can dismiss it by using the command "feed clear".

6. To ensure accurate placement, use the internal snap command "snap int" for the cursor to move along the edge of the grid.

7. There are specific spacing rules to follow. For example, the spacing between VIA2 and Metal 3 should be 0.065u.

8. To measure the distance, position the cursor between the contact cut and the drawn via edge, then click the box in the "tkcon" command. This will provide the distance between them.

9. The tool will automatically handle the placement and spacing of the contact cuts, ensuring there are no Design Rule Check (DRC) errors, and the distance will not be smaller than the specified value.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/ab03a3ea-c5f9-4dff-a1f1-2d7ca2acb1b7)

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/52c4ff26-9a68-4547-9e7e-4bf57fc86bb1)

### Lab : To fix poly.9 error in sky130 tech-file

Steps to fil poly.9 error in sky130 tech-file

1. Start by loading the "poly.mag" file in the tkcon window. You can do this using the command "load poly.mag".

2. Use the mouse cursor to locate the area where the error is occurring. In this case, it is the violation of "Poly.9" due to spacing between "polyres" and "poly" layers.

3. Open the technology file, "sky130A.tech", and search for any existing design rule check (DRC) rules related to "Poly.9". Determine if a rule for the spacing between "polyres" and "poly" layers already exists.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/e12e6fff-209a-4d98-9275-bea2dfe66e76)

4. If there is no existing rule for the spacing between "polyres" and "poly", create a new rule in the technology file. Define the required spacing between these layers. This rule will ensure proper spacing for all instances of "polyres" and "poly".

5. Once you have modified the technology file to include the new rule, load the updated file in the tkcon window using the command "tech load sky130A.tech".

6. The design tool might not automatically perform a DRC check after loading the technology file. Therefore, manually initiate a DRC check to verify if the modifications have resolved the spacing violation. Use the command "drc check" to run the DRC check.

7. After the DRC check, you might find that the spacing violation between "polyres" and "poly" has been resolved. However, it is possible that the spacing between "poly" and "tap/diff" layers is now violated.

8. To address this new violation, modify the technology file to include the necessary spacing rule between "poly" and "tap/diff" layers.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/6f8e41b7-ade2-4ab0-b7a2-4c9d9326c01c)

9. Load the updated technology file again in the tkcon window using the command "tech load sky130A.tech".

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/246e3e57-5911-407b-9ba7-0c7f4bcc320a)

10. Perform another DRC check to ensure that all spacing violations, including the ones between "polyres" and "poly" as well as "poly" and "tap/diff", have been resolved.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/78ad9691-b01f-426e-94b7-778ae9e9ab0a)

By following these steps, you should be able to resolve the spacing violations and ensure that the design meets the required design rules for the "polyres," "poly," and "tap/diff" layers.

### Lab4 Pre-Layout Timing analysis and importance of good clock tree

#### Timing modelling using delay tables

##### Lab steps to convert grid info to track info

> Next objective is to use the inverter layout to create a  LEF file and this LEF file will be used in the openlane and plug-in this cell by making a custom cell uing a custom link. We will plug this cell in picorv32 core and see the openlane takes this input or not.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/82b46fc7-39de-4ee2-9fcc-d76db3afb3ce)

#### Tracks

The width and height of a standard cell should be odd multiples of the horizontal track pitch and vertical track pitch. This information is specified using the following syntax in the "tracks.info" file:

metallayer direction offset spacing
li1 X 0.23 0.46
li1 Y 0.17 0.34

In the above syntax, "li1" represents the metal layer. The "X" and "Y" denote the direction of the tracks, where "X" refers to the horizontal direction and "Y" refers to the vertical direction.

The "offset" value indicates the starting position of the first track, and the "spacing" value represents the distance between adjacent tracks.

For example, in the "li1 X 0.23 0.46" line, it means that for the metal layer "li1" in the horizontal direction, the offset of the first track is 0.23 units, and the spacing between tracks is 0.46 units.

Similarly, in the "li1 Y 0.17 0.34" line, it means that for the metal layer "li1" in the vertical direction, the offset of the first track is 0.17 units, and the spacing between tracks is 0.34 units.

By adhering to these specifications, the standard cell's width and height will be ensured to be odd multiples of the horizontal and vertical track pitches, respectively.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/032c63e9-b0ea-4d39-bfcc-ac6b5986afe7)


















 
 
  
  




























 


   
  
  









































