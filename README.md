# VSD OpenlANE Physical Design Workshop May-2023
Hands-on experience with the labs throughout the VSD 5-day Openlane Physical Design Workshop - May 2023

## Day 1 – OpenLANE and Sky130PDK

Theory

1. OpenLANE:
OpenLANE is an open-source digital RTL-to-GDSII (Register Transfer Level to Graphic Data System version II) flow that aims to automate the entire digital IC design process. It provides a complete, end-to-end flow for designing and manufacturing digital chips. OpenLANE integrates various open-source tools and methodologies to enable efficient chip design.

OpenLANE incorporates several key components and features, including:
- RTL synthesis: Converting Register Transfer Level (RTL) code written in hardware description languages (HDL) like Verilog or VHDL into a gate-level netlist.
- Floorplanning: Determining the placement of different blocks within the chip's layout.
- Placement: Placing the logical gates and components in their designated positions on the chip.
- Clock tree synthesis: Constructing the clock distribution network to deliver clock signals to different parts of the chip.
- Routing: Establishing the connections between different components and nets on the chip.
- Timing analysis: Verifying that the design meets the required timing constraints.
- Physical verification: Checking the layout for various manufacturing and design rule violations.

OpenLANE incorporates multiple open-source tools like Yosys, ABC, OpenROAD, and Magic, and aims to provide a comprehensive and automated RTL-to-GDSII flow that can be used by both academia and industry.

2. Sky130PDK:
Sky130PDK (Process Design Kit) is a technology-specific process design kit developed by Google and SkyWater Technology Foundry. It is an open-source PDK that provides a set of files and libraries required to design integrated circuits using the SkyWater 130 nm process.

The Sky130PDK includes essential components such as:
- Digital standard cells: A library of pre-designed, characterized digital logic gates and components.
- Analog cells: A collection of analog building blocks like amplifiers, comparators, and voltage references.
- I/O libraries: A set of input/output cells for interfacing the chip with the external world.
- Memory compilers: Tools for generating memory instances of different sizes and configurations.
- Device models: Models that describe the electrical characteristics of different transistors and components.

The Sky130PDK is optimized for the SkyWater 130 nm technology node, which offers a low-cost and accessible option for small-scale chip manufacturing. It allows designers to create their own custom digital or analog chips using the provided building blocks and design rules.

Both OpenLANE and Sky130PDK are part of the larger open-source hardware movement, aiming to democratize IC design by providing free and open tools, libraries, and processes to the community. They enable individuals and organizations to design and manufacture their own chips without the need for expensive proprietary tools and processes.

## How to talk to Computers

Introduction to QFN-48 Package, chips, pads, core, die, and Ips (Level 4)

1. QFN-48 Package:
The QFN-48 (Quad Flat No-leads 48) package is a type of surface-mount integrated circuit (IC) package commonly used for housing and interconnecting integrated circuits. It is characterized by its flat and thin profile, with no leads extending from the package. The package has a total of 48 pins that are arranged in a grid-like pattern on the bottom surface, allowing for direct soldering onto the printed circuit board (PCB).

2. Chips:
In the context of integrated circuits, a chip refers to a small piece of semiconductor material, typically made of silicon, on which electronic circuits are fabricated. These circuits can include transistors, resistors, capacitors, and other components. The chip is the actual device that performs the desired functions, such as processing data or controlling a specific application.

3. Pads:
Pads, also known as bond pads or contact pads, are the metalized areas on the surface of an integrated circuit where electrical connections are made between the chip and the package. These pads provide contact points for wire bonding or soldering to establish electrical connectivity between the chip and external components or the PCB.

4. Core:
The core of an integrated circuit refers to the central processing unit (CPU) or the main computational unit of the chip. It contains the logic circuits responsible for executing instructions and performing calculations. The core is often the most critical and complex part of the chip, and it determines the chip's primary functionality.

5. Die:
The term "die" refers to the small, square or rectangular piece of semiconductor material (such as silicon) on which the integrated circuits are fabricated. The die contains the active components, transistors, and interconnects that form the electronic circuits. It is usually separated from the wafer during the manufacturing process and then packaged to protect it and provide electrical connections.

6. IPs (Intellectual Properties):
In the context of integrated circuits, IPs (Intellectual Properties) are pre-designed and pre-verified functional blocks or modules that can be integrated into larger chip designs. IPs are often developed by third-party companies and are licensed to chip designers for use in their designs. Examples of IPs include processors, memory controllers, communication interfaces, and specialized functional units. By using pre-designed IPs, chip designers can save time and effort in developing complex circuits and focus on their specific design requirements.

Level 4 refers to the depth of knowledge required for this explanation, indicating a more detailed and technical understanding of the subject matter.

### Introduction to RISC-V

RISC-V is an open-source instruction set architecture (ISA) that defines the set of instructions and their behavior for a computer processor. It is designed to be simple, modular, and extensible, allowing for flexibility in implementing the architecture. RISC-V stands for "Reduced Instruction Set Computing - Five."

Here are some key points about RISC-V:

1. Open-Source: RISC-V is an open standard, meaning that the instruction set architecture specifications are freely available to the public. This openness encourages collaboration, innovation, and customization by enabling anyone to design, manufacture, and sell RISC-V-based chips without needing to pay license fees or royalties.

2. Simplicity: RISC-V follows a clean and minimalist design philosophy. It provides a small set of instructions that are simple, regular, and orthogonal. The instruction set focuses on essential operations, avoiding unnecessary complexity and providing a solid foundation for building efficient processors.

3. Modularity and Extensibility: RISC-V offers a modular design, allowing implementers to choose the subset of instructions that best suits their needs. Additionally, RISC-V supports optional instruction extensions, enabling customization for specific applications or target markets. This flexibility enables a wide range of implementations, from small embedded devices to high-performance processors.

4. Standardization and Compatibility: RISC-V has a well-defined and stable instruction set architecture, ensuring compatibility across different implementations. This compatibility allows software developers to write code that can run on various RISC-V processors without modification, fostering a healthy software ecosystem.

5. Versatility: RISC-V is designed to support a broad range of applications and use cases. It can be found in embedded systems, mobile devices, Internet of Things (IoT) devices, data centers, high-performance computing, and even supercomputers. Its flexibility and openness make it suitable for diverse industries and research environments.

6. Education and Research: RISC-V's open nature and simplicity make it an excellent platform for education and research in computer architecture. Its availability as an open-source ISA allows academic institutions, students, and researchers to explore and experiment with processor design, instruction set extensions, and optimization techniques.

Overall, RISC-V represents a disruptive approach to computer architecture, providing an open and flexible alternative to proprietary instruction set architectures. Its simplicity, modularity, and extensibility have gained significant traction in the industry and academia, making RISC-V a compelling choice for designing and implementing processors.

From Software Applications to Hardware

## SoC Design and OpenLANE

### Introduction to all components of Open-Source Digital ASIC Design

Open-source digital ASIC (Application-Specific Integrated Circuit) design encompasses several components and tools that enable the development and manufacturing of custom digital chips. Here's an introduction to the main components of open-source digital ASIC design:

1. Open-Source EDA Tools:
EDA (Electronic Design Automation) tools are software tools used for designing and analyzing integrated circuits. In the context of open-source digital ASIC design, several open-source EDA tools are commonly used. Some examples include:

- Yosys: A framework for RTL synthesis and formal verification.
- OpenROAD: A complete RTL-to-GDSII flow that includes tools for floorplanning, placement, clock tree synthesis, and routing.
- Magic: A layout tool for designing integrated circuits.
- OpenSTA: A static timing analysis tool.
- qflow: A toolset for digital synthesis, placement, routing, and physical verification.

These open-source EDA tools provide the necessary functionality to design and analyze digital ASICs.

2. Open-Source IP Cores:
IP (Intellectual Property) cores are pre-designed and pre-verified functional blocks that can be integrated into larger chip designs. Open-source IP cores are available for various functionalities, such as processors, memory controllers, interfaces, and specialized components. These open-source IP cores can be leveraged in open-source digital ASIC designs to reduce development time and effort.

Examples of open-source IP cores include the RISC-V processors (like the Rocket, BOOM, or PicoRV32 cores), memory controllers like SDRAM or DDR controllers, UART (Universal Asynchronous Receiver-Transmitter) interfaces, and more.

3. Open-Source PDKs:
A PDK (Process Design Kit) provides the necessary information and files required to design integrated circuits using a specific fabrication process. Open-source PDKs, like the Skywater PDK (based on the Sky130 process), offer the essential components for designing chips using the specified process.

The PDK typically includes technology files, device models, standard cell libraries, analog building blocks, I/O libraries, and other resources needed to design and simulate chips. Open-source PDKs enable designers to access the required information and resources without relying on proprietary and expensive PDKs.

4. Open-Source Hardware Description Languages:
Hardware Description Languages (HDLs) are used to describe the behavior and structure of digital circuits. Open-source HDLs, such as Verilog and VHDL, are commonly used in open-source digital ASIC design. These languages allow designers to write the code that describes the functionality and interconnections of the digital circuits they are designing.

The availability of open-source HDLs ensures that designers have access to the necessary tools and languages to describe their digital ASIC designs accurately.

5. Design Methodologies and Flows:
Open-source digital ASIC design methodologies and flows provide a structured approach for designing and verifying digital chips. These methodologies outline the steps and best practices for tasks like RTL design, synthesis, floorplanning, placement, routing, timing analysis, and physical verification.

Open-source digital ASIC design flows, such as OpenLANE, provide an end-to-end flow that integrates multiple tools and steps into a cohesive design process.

Overall, open-source digital ASIC design encompasses a collection of open-source EDA tools, IP cores, PDKs, HDLs, and design methodologies that enable designers to create custom digital chips using an open and collaborative approach. These components provide the necessary resources, tools, and guidelines for designing, verifying, and manufacturing digital ASICs.

### Simplified RTL2GDS flow

The RTL-to-GDS (Register Transfer Level to Graphic Data System) flow is the process of transforming a digital design described at the RTL level into a physical layout ready for fabrication. Here is a simplified overview of the RTL-to-GDS flow:

1. RTL Design:
The flow begins with the creation of the RTL design using a hardware description language (HDL) like Verilog or VHDL. The RTL design describes the behavior and interconnections of the digital circuit.

2. RTL Synthesis:
The RTL design is synthesized using an RTL synthesis tool, such as Yosys. RTL synthesis transforms the high-level RTL description into a gate-level netlist, which represents the design in terms of logic gates and flip-flops.

3. Technology Mapping:
The gate-level netlist is then mapped to a target technology library. During this step, the logic gates in the netlist are replaced with specific cells from the library that match the desired functionality. The technology library contains standard cells that are optimized for the target process technology.

4. Floorplanning:
Floorplanning involves determining the placement of different functional blocks within the chip's layout. It considers factors such as block sizes, power and clock distribution, and I/O placement. Floorplanning helps create an initial estimate of the chip's area and determines the overall chip dimensions.

5. Placement:
Placement refers to the process of determining the specific locations of individual gates and components on the chip. It aims to minimize the chip's area and optimize the interconnect lengths for better performance. Placement tools, like OpenROAD, are used to achieve an efficient and optimized placement.

6. Clock Tree Synthesis:
Clock tree synthesis (CTS) is the construction of a clock distribution network that delivers clock signals to different parts of the chip. The goal is to ensure balanced and low-skew clock distribution, minimizing clock delay and skew among flip-flops. CTS tools generate the clock tree structure and insert buffer and repeater cells to achieve proper clock distribution.

7. Routing:
Routing involves establishing the physical connections between the components and interconnecting the nets based on the placement results. The router takes into account the design rules and constraints to create a routing solution that satisfies timing and electrical requirements. The routing process may involve multiple layers of metal interconnects.

8. Design Rule Checking:
After routing, the layout is checked against the design rules provided by the foundry. Design Rule Checking (DRC) ensures that the layout adheres to specific constraints related to minimum spacing, width, and other manufacturing requirements. DRC tools identify and report violations that need to be fixed.

9. Layout vs. Schematic (LVS) Checking:
Layout vs. Schematic (LVS) verification compares the connectivity and functionality of the layout with the original schematic representation. It ensures that the physical layout matches the intended design and that there are no errors or discrepancies.

10. Timing Analysis:
Timing analysis is performed to ensure that the design meets the required timing constraints. Tools like OpenSTA are used to analyze the timing paths and identify any violations such as setup time, hold time, or maximum delay violations.

11. GDS Generation:
Once the design has passed all verification steps, the final step is to generate the GDSII (Graphic Data System version II) file. The GDSII file contains the layout information in a standardized format that can be used for mask generation and fabrication.

It's important to note that the actual RTL-to-GDS flow can be more complex, involving additional steps and optimizations. The above overview provides a simplified understanding of the key stages involved in transforming an RTL design into a physical layout ready for manufacturing.

Introduction to OpenLANE and Strive chipsets

Introduction to OpenLANE detailed ASIC design flow

## Starting the Labs

### Get familiar to open-source EDA tools

Getting familiar with open-source EDA (Electronic Design Automation) tools is a valuable step for designers interested in open-source digital ASIC design. Here are some popular open-source EDA tools along with a brief description of each:

1. Yosys:
Yosys is a widely used open-source synthesis tool. It takes RTL (Register Transfer Level) designs described in hardware description languages (HDLs) like Verilog or VHDL and synthesizes them into a gate-level netlist. Yosys supports a range of synthesis optimizations and is highly configurable, making it a versatile tool for RTL synthesis.

2. OpenROAD:
OpenROAD is an open-source RTL-to-GDSII (Register Transfer Level to Graphic Data System version II) flow that encompasses various stages of the ASIC design process, including floorplanning, placement, clock tree synthesis, and routing. OpenROAD integrates several open-source tools and aims to provide an end-to-end flow for digital chip design.

3. Magic:
Magic is an open-source layout tool used for designing integrated circuits. It allows designers to create and modify layout geometries, perform design rule checks (DRC), and view the layout in a graphical interface. Magic supports a wide range of layout formats and is commonly used in the layout stage of ASIC design.

4. Qflow:
Qflow is an open-source digital synthesis and place-and-route flow. It provides a set of tools that enable digital synthesis, placement, and routing for ASIC designs. Qflow integrates several open-source tools such as Yosys, Graywolf, and Qrouter to offer a complete flow from RTL to GDSII.

5. OpenSTA:
OpenSTA is an open-source static timing analysis tool. It analyzes the timing paths in a digital design to ensure that the design meets the required timing constraints. OpenSTA provides detailed timing reports, including setup time, hold time, and maximum delay violations, helping designers optimize their designs for timing performance.

6. Icarus Verilog:
Icarus Verilog is an open-source Verilog simulator and compiler. It allows designers to compile and simulate Verilog designs, providing a way to verify the functionality of digital circuits at the RTL level. Icarus Verilog supports a range of simulation features and is widely used for testbench development and functional verification.

These are just a few examples of popular open-source EDA tools. Exploring and utilizing these tools will provide hands-on experience in various stages of the ASIC design flow. Additionally, many open-source EDA tools have active communities, forums, and documentation available, making it easier to find resources and support as you familiarize yourself with these tools.
### What is OpenLANE and why should we use OpenLANE?

OpenLANE is an open-source RTL-to-GDSII (Register Transfer Level to Graphic Data System version II) flow for digital ASIC design. It provides a complete, automated, and community-driven platform for implementing digital designs from RTL to physical layout. OpenLANE incorporates several open-source tools and methodologies to enable efficient and customizable chip design.

Here are some key reasons why you should consider using OpenLANE:

1. Open-Source and Community-Driven:
OpenLANE is an open-source project, which means that the design files, scripts, and tools are freely available to the public. This openness fosters collaboration and innovation within the ASIC design community. By using OpenLANE, you can tap into a vibrant community of designers, contribute to the project, and benefit from the collective expertise of the community.

2. Complete RTL-to-GDSII Flow:
OpenLANE offers an end-to-end flow for digital ASIC design. It integrates various stages of the design process, including synthesis, floorplanning, placement, clock tree synthesis, and routing. Having a complete flow in a single platform simplifies the design process and reduces the need to manually stitch together different tools.

3. Automation and Efficiency:
OpenLANE emphasizes automation to streamline the design process and improve productivity. It provides predefined design methodologies, guidelines, and optimizations that enable designers to quickly iterate on their designs. Automation helps reduce human errors and accelerates the turnaround time for chip designs.

4. Configurability and Customization:
OpenLANE is highly configurable, allowing designers to tailor the flow and optimizations to their specific design requirements. It provides a range of options for technology nodes, design rules, and synthesis parameters. This flexibility enables designers to optimize their designs for area, power, performance, or other desired metrics.

5. Pre-validated IP Integration:
OpenLANE supports the integration of pre-validated intellectual property (IP) cores. These IP cores can be open-source or proprietary, enabling designers to leverage existing designs and reduce development time. OpenLANE provides a framework for integrating IP cores into the overall chip design seamlessly.

6. Educational and Research Purposes:
OpenLANE serves as an excellent platform for education and research in digital ASIC design. Its open-source nature allows academic institutions, students, and researchers to experiment, learn, and explore various aspects of chip design. The availability of the source code and documentation facilitates learning and encourages contributions to the field.

By utilizing OpenLANE, designers can benefit from a collaborative ecosystem, automated design flow, configurability, and customization options. Whether you are a professional designer, a student, or a researcher, OpenLANE offers a powerful and accessible platform for digital ASIC design.

### Tool Interface

VM Virtual Box:VirtualBox is a powerful virtualization software that allows you to run multiple operating systems on a single physical machine. It enables you to create and manage virtual machines (VMs), which act as self-contained systems within your computer.

Here are some key features and benefits of VirtualBox:

1. Cross-Platform Compatibility: VirtualBox is available for Windows, macOS, Linux, and Solaris, making it a versatile virtualization solution that can be used on various operating systems.

2. Hardware Virtualization: VirtualBox supports hardware virtualization technologies like Intel VT-x and AMD-V, which enhance the performance and compatibility of virtual machines.

3. VM Creation and Management: VirtualBox provides an intuitive interface for creating and managing VMs. You can create VMs with different operating systems, allocate resources such as CPU cores, memory, and storage, and customize settings according to your requirements.

4. Snapshot and Restore: VirtualBox allows you to take snapshots of VMs at specific points in time. This feature is useful for creating backups or capturing a VM's state before making changes. You can also restore a VM to a previous snapshot if needed.

5. Virtual Networking: VirtualBox provides various networking options to connect VMs to the host machine or to each other. You can configure network adapters, set up virtual networks, and enable features like NAT (Network Address Translation) or bridged networking for communication between VMs and the external network.

6. Guest Additions: VirtualBox includes guest additions, which are software packages installed on guest operating systems to enhance performance and provide additional functionalities. Guest additions enable features like seamless mouse integration, shared folders, clipboard sharing, and improved graphics.

7. USB Device Support: VirtualBox allows you to connect USB devices to VMs, enabling you to use USB peripherals within the virtual environment. This feature is useful for testing USB devices, accessing external storage, or using USB-based hardware.

8. Extensibility and Customization: VirtualBox is open-source and extensible. It provides an API and software development kit (SDK) for extending its functionality and integrating with other tools or systems.

VirtualBox is widely used for various purposes, including software development, testing, running legacy applications, creating sandbox environments, and exploring different operating systems. Its versatility, ease of use, and extensive feature set make it a popular choice for virtualization needs.

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

#### To determine if the I/O ports are located at an intersection, follow these steps on the TKCON window:

Activate the grid by pressing 'G' on the magic console.

Set the grid size to the desired dimensions, such as 0.46um, 0.34um, 0.23um, or 0.17um.

Locate the I/O ports in the LI1 layer.

Check if the I/O ports align at the intersection points on the grid.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/03c64363-5bde-4773-bf1c-7c0fe9c79c89)

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/22147e4c-b89d-4587-8ba7-a230e2ce8f99)

#### Lab steps to convert magic layout to std cell layout

### Create Port Definition

Open the Magic Layout window and source the .mag file for the design, such as the inverter.

Navigate to the "Edit" menu and select "Text." This action will open a dialogue box for entering text.

Double press the 'S' key while the cursor is positioned at the I/O labels. This action automatically populates the text with the string name and size information of the port.

> In the figure below, the number specified in the text area adjacent to the enable checkbox determines the sequencing of the ports when they are written in the LEF file. The number assigned to each port represents its order, starting from 0 as the first port in the list.

By following these steps, you can define ports for the macro cell in the Magic console and proceed with the LEF extraction process.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/f4a81348-8772-4e77-8055-0404b27d6034)

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/0397f74b-1377-4813-8028-67ae2efdded0)

> To determine the connectivity of the ground and power layers from the metal1 layer, follow these steps:

In the Magic window, create a box or rectangle over the areas designated as VPWR (power) and VGND (ground).

Switch to the TKCON window.

Use the appropriate command in the TKCON window to check the connectivity of the ground and power layers from the metal1 layer.

By performing these steps, you can verify the connectivity of the ground and power layers and ensure that they are either the same or different from the signal layer.

![Screenshot 2023-06-05 124428](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/ae6db668-025b-4a34-9196-89dc327981bb)

![Screenshot 2023-06-05 124512](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/368e5423-d256-4829-9ba6-6e5dd6169d2d)

> After this we need to save the layout as "save sky130_vsdinv.mag" in tkcon console. When you type ls-ltr inside the vsdstdcelldesign directory , we can see the saved mag file.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/9b8ea5b7-cb79-4f22-bc87-3f756079ce47)

After doing this we need to create a lef file for this layout , for this open layout "sky130_vsdinv.mag" and type "lef write" in tkcon window. 

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/225eaf4c-0eaa-4ea8-8228-ad57f2890a1b)

when we open it we can see what all changes we did during port definition. This is how lef file is written.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/92cfc8e5-07a6-450b-ba5c-c03b1c52d415)

> Next step is to plug this lef file into picorv32. Before we do this we need to move the files into "src" folder to present all our design files in one location.

> We have to include our custom cell into the openlane flow. The first step is "Synthesis". For this we need to have a library that has our "cell definition".

For STA analysis we require three libraries where pmos and nmos work in different corners depending on the tepmperature. There are slow(SS), fast(FF) and typical corners(TT). The tool should map the vsd cell during  the synthesis.

> Now we should copy these libs into the src folder under picorv32a design
 
 ![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/0102b41c-7492-4c83-9ac7-5cc79a0e8f50)
 
 > We need to modify config.tcl file before performing synthesis.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/29e85476-f029-448a-9521-4e269ab044ea)

> Invoke the docker and run the design in interactive mode by giving "prep -design picorv32a -tag 31-05_18-34 -overwrite"

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/e3993b48-1484-42ba-94a0-99360f65d726)

> Next invoke the lefs in the openlane by giving the following commands

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/41cbc969-a49f-4db9-b9d6-e97ba1e25ffb)
`
> Running synthesis - After running synthesis the slack obtained is -23.89ns.

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/bbdecf9c-9aab-4597-8223-1611840c39d7)

#### Synthesis settings to fix slack

> Copy the chip area into a notepad and now we will balance between area and delay by changing the strategy in the README.md file under configuration directory.
 
  To check the strategy "echo $::env (SYNTH_STRATEGY)
  
  To set the strategy "set ::env (SYNTH_STRATEGY) 1" to 1 will increase the area a little but the timing should improve
  
  ![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/ceacc4ac-b51a-4495-a113-2811f20bcdd3)

> ![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/0f760869-1db0-45d9-82f4-a90ff6d16d7f)

> Now let us see what the driving cell is in the configuration directory "README.md" file. 

> Run synthesis again to check if the slack gets reduced or not.

> After the slack gets reduced, run floorplan by typing "run_floorplan"

> After running all these commands
Floor plan stage:

   init_floorplan
   
   place_io
   
   global_placement_or
   
   tap_decap_or
   
   we get

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/15bdc6a5-1d3a-43e7-ab95-1deb9980df7c)

For Placement: Command to run is "detailed_placement"

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/88fb3ff1-7ad9-4472-b70c-ee281b5580db)

PD network generation :

   gen_pdn
   
   ![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/415aadc8-ea59-42fd-a0a2-378cb00aeef4)

Routing :

   run_routing

![image](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/b2d68932-8b44-41c8-8772-ae065edc142f)


### Post-synthesis timing analysis Using OpenSTA

Timing analysis using the OpenSTA tool is typically performed outside the openLANE flow. To initiate the STA analysis, you would invoke OpenSTA with the pre_sta.conf configuration file, 

sta pre_sta.conf

During the placement stage of the design flow, the clock is assumed to be ideal, as it is propagated only once Clock Tree Synthesis (CTS) is performed. Therefore, before CTS, only setup slack is considered in the analysis.

Setup time refers to the minimum time required for the data to stabilize before the active edge of the clock so that it can be correctly captured.

Setup slack is calculated as the data required time minus the data arrival time. It represents the available timing margin for the setup time.

The clock is generated from a Phase-Locked Loop (PLL), which consists of built-in circuit elements and logic. Variations can occur in the clock generation process depending on the specific circuit. These variations collectively contribute to clock uncertainty. One such parameter is clock jitter, which refers to the deviation of the clock edge from its original position.

Clock uncertainty encompasses various factors such as skew, jitter, and margin. Skew refers to the variation in arrival times of the clock signal at different points in the circuit. Jitter represents the uncertainty in the arrival time of the clock due to deviations from its expected position. Margin indicates the amount of tolerance or safety margin available in the timing analysis to account for various uncertainties and process variations.

By analyzing the timing report, you can identify areas where slack can be improved. One approach to improving slack is upsizing the cells, which involves replacing them with higher drive strength cells. This modification can lead to significant changes in the slack, ultimately improving the timing performance of the design.

Certainly! Here's a rewritten version of the information you provided:

During the Clock Tree Synthesis (CTS) stage, the goal is to ensure that the clock reaches each clock pin from the clock source with minimum skew and insertion delay. This is achieved by implementing an H-tree structure using a midpoint strategy. Clock inverters or buffers are inserted in the clock path to balance skews.

Before running the CTS in the TritonCTS tool, it's important to check if the slack was attempted to be reduced in a previous run. If so, the netlist may have been modified through cell replacement techniques. Therefore, the Verilog file needs to be updated using the "write_verilog" command. Following that, the synthesis, floorplan, and placement stages are rerun.

### To execute the CTS, the following command is used:

run_cts

![Screenshot 2023-06-06 102915](https://github.com/nikhithatb/vsdiatworkshop/assets/135085619/253e6b9f-8dab-4028-bfa8-ffa6d68f9f03)


After the CTS run, the slack values are obtained. For example:

Setup slack: 4.33
Hold slack: 0.25

Once the clock is propagated through the CTS stage, the subsequent timing analysis is performed with real clocks. This is done within the openlane flow using the OpenROAD tool.

The following commands are used:

openroad

write_db pico_cts.db

read_db pico_cts.db

read_verilog /openLANE_flow/designs/picorv32a/runs/03-07_11-25/results/synthesis/picorv32a.synthesis_cts.v

read_liberty $::env(LIB_SYNTH_COMPLETE)

link_design picorv32a

read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

set_propagated_clock (all_clocks)

report_checks -path_delay min_max -format full_clock_expanded -digits 4


After performing the post-CTS timing analysis, the resulting slack values are obtained. For example:

Setup slack: 4.0565
Hold slack: -0.1673

These slack values provide information about the timing margins in the design, where positive values indicate sufficient margin and negative values indicate violations.
































 
 
  
  




























 


   
  
  









































