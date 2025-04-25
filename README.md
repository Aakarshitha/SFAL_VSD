
<details>
  <Summary> SFAL_VSD SOC</summary>

  This project is to create an SOC from specifications to netlist.
</details>
<details>
  <Summary> Day 0 - Tools Installation</summary>

  All the instructions for installation of required tools can be found here:
  - **SYSTEM CHECK**
    - 6GB RAM, 50 GB HDD
    - Ubuntu 20.04+
    - 4vCPU
    
  - **TOOL CHECK**
    - **Yosys**
      - $ sudo apt-get update
      - $ git clone https://github.com/YosysHQ/yosys.git
      - $ cd yosys
      - $ sudo apt install make (If make is not installed please install it) 
      - $ sudo apt-get install build-essential clang bison flex \
            libreadline-dev gawk tcl-dev libffi-dev git \
            graphviz xdot pkg-config python3 libboost-system-dev \
            libboost-python-dev libboost-filesystem-dev zlib1g-dev
      - $ make config-gcc
      - $ make 
      - $ sudo make install
      - ![Alt Text](images/yosys.jpg) 
    - **Iverilog** - Steps to install iverilog
      - sudo apt-get update
      - sudo apt-get install iverilog
      - ![Alt Text](images/iverilog.jpg)
    - **GTKWAVE** - Steps to install gtkwave
      - sudo apt-get update
      - sudo apt install gtkwave
      - ![Alt Text](images/gtkwave.jpg)

    - **ngspice** - After downloading the tarball from https://sourceforge.net/projects/ngspice/files/ to a local directory, unpack it using:
      - $ tar -zxvf ngspice-37.tar.gz
      - $ cd ngspice-37
      - $ mkdir release
      - $ cd release
      - $ ../configure  --with-x --with-readline=yes --disable-debug
      - $ make
      - $ sudo make install
    - **magic**
      - $ sudo apt-get install m4
      - $ sudo apt-get install tcsh
      - $ sudo apt-get install csh
      - $ sudo apt-get install libx11-dev
      - $ sudo apt-get install tcl-dev tk-dev
      - $ sudo apt-get install libcairo2-dev
      - $ sudo apt-get install mesa-common-dev libglu1-mesa-dev
      - $ sudo apt-get install libncurses-dev
      - git clone https://github.com/RTimothyEdwards/magic
      - cd magic
      - ./configure
      - make
      - make install

</details>

<details>
  <Summary> Day 1 - Introduction to Verilog RTL Design and Synthesis</summary>
  
  - **Introduction to iverilog testbench**
    - RTL Design adherence to the initial architecture specifications is checked by simulation of the design using a simulator tool. That simulator tool we are using here is iverilog.
    - Design is actual verilog/system verilog code with intended functionality. Has primary inputs and outputs in form of wires or logic/registers/memory elements.
    - Testbench is a set of stimulus applied with delays and initialisation to ensure that design meets functionality. Does not have any primary inputs or outputs.
    - Simulator looks for changes in the input signals, based on this, checks its influence on output signals.

  - **Labs using iverilog and gtkwave**
    - used iverilog to simulate design and testbench of good mux
    - used gtkwave to view the dumped "value change dump" or vcd file
    - learnt to use iverilog and gtkwave commands
    - saw the design and tb files
   
  - **Introduction to Yosys and Logic Synthesis**
    - used Yosys as the synthesizer tool, learnt what synthesis meant
    - learnt about yosys setup and verification flow, tb for netlist is same as that of rtl design
    - Learnt about rtl design, synthesis and its illustration, library cells, flavours of library cells
    - Also learnt about usage of faster versus slower cells, need wider transistors and why we need them

  - **Labs using Yosys and Sky103PDKs**
    - Synthesised good mux using yosys
    - OBSERVATION made: I saw only one type of library cell (constrasting to the video) and therefore my good mux design was synthesised using only that library cell
    - the library cell was sky130_fd_sc_hd__tt_025C_1v80.lib
    - good mux finally synthesised and the cells it inferred was just 1 2_1 mux cell since only one lib file was there.
    - **Commands used:**
      - read_liberty -lib lib/sky130_fd_sc_hd__tt_025C_1v80.lib
      - read_verilog verilog_files/good_mux.v
      - hierarchy -top good_mux
      - synth -top good_mux
      - abc -liberty lib/sky130_fd_sc_hd__tt_025C_1v80.lib
      - show
      - write_verilog -noattr synth_out.v
    - **Images for this lab**
      - ![Alt Text](images/Day1images/cell_selection_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/faster_slowercells_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/gate_flavor1_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/gate_flavor2_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/good,uxdesign_Day1_vsd.jpg)
      - ![Alt Text](images/Day1images/goodmuxtb_Day1_vsd.jpg)
      - ![Alt Text](images/Day1images/gtkwave1_Day1_vsd.jpg)
      - ![Alt Text](images/Day1images/installations_Day1_VSD.jpg)
      - ![Alt Text](images/Day1images/yosys_setupflow_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/yosys_verificationflow_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/iverilog1_Day1_vsd.jpg)
      - ![Alt Text](images/Day1images/libcells_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/rtldesign_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/simulator_flow_Day1_vsd.jpg)
      - ![Alt Text](images/Day1images/synthesis_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/synthesis_illustration_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/testbench_Day1_VSD.jpg)
      - ![Alt Text](images/Day1images/yosys_lab3_1_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/yosys_lab3_2_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/yosys_lab3_3_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/yosys_lab3_4_day1_vsd.jpg)
      - ![Alt Text](images/Day1images/yosys_lab3_5_day1_show_vsd.jpg)
      - ![Alt Text](images/Day1images/yosys_lab3_6_day1_show_vsd.jpg)
      - ![Alt Text](images/Day1images/yosys_lab3_7_day1_netlist_vsd.jpg)
      - ![Alt Text](images/Day1images/yosys_lab3_day1_vsd.jpg)

</details>

<details>
  <Summary> Day 2 - Timing Libs, Hierarchical versus flat synthesis, and efficient flop coding styles</summary>

  - **Introduction to Timing Libs**
  - **Hierarchical Versus Flat Synthesis**
  - **Various Flop Coding Styles and Optimisations**
  - **Images for this lab**
    - ![Alt Text](images/Day2images/why_flops_Day2_VSD.jpg)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    - ![Alt Text](images/Day2images/)
    
    

    
</details>  

<details>
  <Summary> Day 3 - Combinational and Sequential Optimisations</summary>

  - **Introduction to Optimisations**
  - **Combinational Logic Optimisations**
  - **Sequential Logic Optimisations**
  - **Sequential Logic Optimisations for unused outputs**
  - **Images for this lab**
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    - ![Alt Text](images/Day3images/)
    
</details> 

<details>
  <Summary> Day 4 - GLS, Blocking vs Non-Blocking, simulation-synthesis mismatch</summary>

  - **GLS, Synthesis-Simulation Mismatch, and Blocking vs Non-Blocking Statements**
  - **Labs on GLS and Synthesis-Simulation Mismatch**
  - **Labs on Synthesis-Simulation Mismatch for Blocking Statements**
  - **Images for this lab**
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)
    - ![Alt Text](images/Day4images/)

</details> 



