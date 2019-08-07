# VHDL-Timing
Timing simulation example using VHDL

## Install

These examples use [ModelSim and Quartus from Intel FPGA](http://fpgasoftware.intel.com/?edition=lite), [GIT](https://git-scm.com/download/win), [Visual Studio Code](https://code.visualstudio.com/download), make sure they are installed locally on your computer before proceeding.

## Usage

1. Grab a copy of this repository to your computer's local folder (i.e. C:\projects):

    ```sh
    $ cd projects
    $ git clone https://github.com/ihabadly/vhdl-timing.git
    ```
2. Use Visual Studio Code (VSC) to edit and view the design files:

    ```sh
    $ cd vhdl-timing
    $ code .
    ```
    Click on the count_bin.vhd file in the left pane to view its contents.
    
3. From the VSC View menu, choose Terminal, in the VCS Terminal, create a "work" library:

    ```sh
    $ vlib work
    ```
    
4. Compile any of the design units, For example, to compile the binary counter design and its testbench:

    ```sh
    $ vcom count_bin.vhd
    $ vcom count_bin_tb.vhd
    ```
    
5. Simulate your design. For example, to simulate the binary counter testbench:

    ```sh
    $ vsim work.count_bin_tb
    ```
    
6. Synthesis your design. For example, to synthesis the binary counter, first create a working folder for the Quartus Prime Tool:

    ```sh
    $ mkdir quartus/count_bin
    ```

7.  Run the Quartus Prime Tool to synthesis the binary counter design, then:
    - From Menu, choose File -> New Project Wizard
    - Click: Next
    - For the working directory, fill with: "path to your projects folder"/vhdl-timing/quartus/count_bin
    - For the project name, fill with: count_bin
    - Click: Next
    - Click: Next
    - In File name, fill with: ../../count_bin.vhd
    - Click: Add
    - Click: Next
    - From Device family, choose: Cyclone IV E
    - From Available devices, choose: EP4CE22F17C6
    - Click: Next
    - From Simulation, choose Tool Name: ModelSim-Intel and Format: VHDL
    - Click: Next
    - Click: Finish
    - From Menu, choose Processing -> Start Compilation
    - Wait until compilation completes

8. Run timing simulation for your design. For example, to simulate the binary counter testbench after synthesizing the binary counter component:

    ```sh
    $ vcom ./quartus/count_bin/simulation/modelsim/count_bin.vho
    $ vsim work.count_bin_tb -sdftyp /dut=./quartus/count_bin/simulation/modelsim/count_bin_vhd.sdo
    ```
