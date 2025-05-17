
<details>
  <Summary> SFAL_VSD SOC</summary>

  This project is to create an SOC from specifications to netlist.
</details>
<details>
  <Summary> Week 0 - Day 0 - Tools Installation</summary>

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
  <Summary> Week 1 - Day 1 - Introduction to Verilog RTL Design and Synthesis</summary>
  
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
  <Summary> Week 1 - Day 2 - Timing Libs, Hierarchical versus flat synthesis, and efficient flop coding styles</summary>

  - **Introduction to Timing Libs**
  - **Hierarchical Versus Flat Synthesis**
  - **Various Flop Coding Styles and Optimisations**
  - **Images for this lab**
    - ![Alt Text](images/Day2images/why_flops_Day2_VSD.jpg)
    - ![Alt Text](images/Day2images/why_flops2_Day2_VSD.jpg)
    - ![Alt Text](images/Day2images/why_flops1_Day2_VSD.jpg)
    - ![Alt Text](images/Day2images/libcell_day2_vsd.jpg)
    - ![Alt Text](images/Day2images/libcell1_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/libcell2_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/libcell3_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/hier_synth_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/hier_synth1_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/hier_synth2_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/hier_synth3_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/hier_synth4_flat_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/and2_0_lib_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/and2_2_lib_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/and2_4_lib_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/mul2_synth_1_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/mul2_synth_2_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/mul2_synth_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/mult8_synth1_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/mult8_synth_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/async_set_synth1_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/async_set_synth_2_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/async_set_synth_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/async_sync_rst_codingstyles1_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/async_sync_rst_codingstyles_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/asyncres_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/asyncres_synth_day2_vsd.jpg)
    - ![Alt Text](images/Day2images/asyncset_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/dff_asyncres_synth_show_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/pvt_concept_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/stackedpmosbad_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/submod1_1_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/submod1_2_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/submod1_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/syncres_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/syncres_synth1_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/syncres_synth2_Day2_vsd.jpg)
    - ![Alt Text](images/Day2images/synth_asyncres_day2_vsd.jpg) 
    
</details>  

<details>
  <Summary> Week 1 - Day 3 - Combinational and Sequential Optimisations</summary>

  - **Introduction to Optimisations**
  - **Combinational Logic Optimisations**
  - **Sequential Logic Optimisations**
  - **Sequential Logic Optimisations for unused outputs**
  - **Images for this lab**
    - ![Alt Text](images/Day3images/absorptionlaw_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/ddfconst12_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst12_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst1_sim_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst1_synth_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst2_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst2_sim_Day3_vsd.jpg)
    - ![Alt Text](images/Day3imagesdffconst3_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst3_sim_day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst3_synth_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst4_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst4_sim_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst4_synth_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst5_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst5_sim_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/dffconst5_synth_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/multiplemodule_opt2_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/multiplemodule_opt2_synth_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/multiplemodule_opt_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/multiplemodule_opt_synth_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/optchk4_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/optimisa_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/seq_optimisa_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/synth_optchk2_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/synth_optchk2_show_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/synth_optchk3_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/synth_optchk4_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/synth_optchk_Day3_vsd.jpg)
    - ![Alt Text](images/Day3images/synth_optchk_show_Day3_vsd.jpg)

</details> 

<details>
  <Summary> Week 1 - Day 4 - GLS, Blocking vs Non-Blocking, simulation-synthesis mismatch</summary>

  - **GLS, Synthesis-Simulation Mismatch, and Blocking vs Non-Blocking Statements**
    - Missing Sensitivity List
      - GLS introduction and flow with iverilog
      - ![Alt Text](images/Day4images/GLSiverilog_flow_Day4_vsd.jpg)
      - ![Alt Text](images/Day4images/GLSintro_Day4_vsd.jpg)
      - Simulator works mainly on activity - changes in signal values whereas synthesiser only sees functionality
      - therefore having a correct and complete sensitivity list for always blocks is necessary to avoid synthesis simulation mismatch
      - Eg of a mux, difference between always@(sel) and always@(*) is highlighted
      - ![Alt Text](images/Day4images/misssensitvity_synthsimmismatch_Day4_vsd.jpg)
    - Blocking and Non-Blocking statements
      - Caveat with blocking nonblocking statements are discussed
      - Example of aiming for a shift register is used
      - if blocking assignment is used it is seen as a single flop instead of two flops, this is wrong, as all statements are evaluated in order and assignment of rhs to lhs happens before moving on to next statement, giving wrong behaviour
      - ![Alt Text](images/Day4images/blockingstatementcaveat1_synthsimmismatch_Day4_vsd.jpg)
      - ![Alt Text](images/Day4images/blockingstatementcaveat2_synthsimmismatch_Day4_vsd.jpg)
      - So always use non blocking statement for sequential logic generation, as in non-blocking order of statements do not matter and all rhs is evaluated before all lhs.
      - ![Alt Text](images/Day4images/blockingstatementcaveat_synthsimmismatch_Day4_vsd.jpg)
  - **Labs on GLS and Synthesis-Simulation Mismatch**
    - Example of ternary operator based mux used
    - simulated, synthesised and got netlist, these are the results I got
    - ![Alt Text](images/Day4images/ternaryop_gls_lab_day4_vsd.jpg)
    - ![Alt Text](images/Day4images/ternaryop_gls_lab_realnetlist_day4_vsd.jpg)
    - but this was the expected netlist output
    - ![Alt Text](images/Day4images/ternaryop_gls_lab_expectednetlist_day4_vsd.jpg)
    - Ran to get GLS netlist next to get smae simulation result
    - ![Alt Text](images/Day4images/ternaryop_gls_lab_postglssim_day4_vsd.jpg)
    - Second example showed synthesis and simulation mismatch for bad mux
    - ![Alt Text](images/Day4images/badmuxsynthsim_mismatch_Day4_vsd.jpg)
    - **Commands used to get GLS**
      - iverilog my_lib/verilog_model/primitives.v my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_netlist.v verilog_files/tb_ternary_operator_mux.v
      - ./a.out
      - gtkwave tb_ternary_operator_mux.vcd

  - **Labs on Synthesis-Simulation Mismatch for Blocking Statements**
    - exmaples of synthesis simulation mismatch for blocking statements here
    - ![Alt Text](images/Day4images/blockingcaveat_Day4_vsd.jpg)
    - ![Alt Text](images/Day4images/blcokingcaveatsynthsimmismatch_Day4_vsd.jpg)

</details> 

<details>
  <Summary> Week 2 - Advanced Synthesis and STA with Design Compiler - Introduction to Logic Synthesis </summary>

  - **Day1 - Lecture 1 - Introduction to the course**
    - **Common terminology used are**
    - Synopsys Design Constraints or SDC is commonly used in industry. It is based on tool command language or tcl.
    - We do a lab of using an imaginary library to invoke DC and see what happens - it is not able to read the yourlibrary.lib file.
    - So, we see that if we write the netlist, it is written in the form of gtech cells. Gtech in DC is the virtual library in DC's memory to understand the design.
    - Even after giving the sky130 library file, it gives same wrong output
    - So, what is missing is the two environment variables to be set to the target sky130 library ie the link_library and the target_library.
    - After that we need to set link library, here * represents all libraries loaded previously in DC's memory.
    - This, inclusing * is so that we don't override the existing loaded libraries in DC's memory, just append my new library to be considered into the DC's memory.
    - Now, it clearly shows linking and loading the design into DC's memory.
  - **Lecture 2 - Introduction to DC and tool**
    - **Lab 1 - Invoking DC Basic Setup**
      - DC tool basic setup was dicussed how to setup link library, target library, how the library file highlights different characteristics of the standard cell and technology.
    - **Lab 2 - Introduction to DDC GUI with Design Vision**
    - **Lab3 - DC Synopsys DC Setup**
      - ![Alt Text](images/Day5_DCDay1_images/yosys_lab3_1_day1_vsd.jpg)
      - ![Alt Text](images/Day5_DCDay1_images/yosys_lab3_2_day1_vsd.jpg)
      - ![Alt Text](images/Day5_DCDay1_images/yosys_lab3_3_day1_vsd.jpg)
      - ![Alt Text](images/Day5_DCDay1_images/yosys_lab3_4_day1_vsd.jpg)
      - ![Alt Text](images/Day5_DCDay1_images/yosys_lab3_5_day1_show_vsd.jpg)
      - ![Alt Text](images/Day5_DCDay1_images/yosys_lab3_6_day1_show_vsd.jpg)
      - ![Alt Text](images/Day5_DCDay1_images/yosys_lab3_7_day1_netlist_vsd.jpg)
      - ![Alt Text](images/Day5_DCDay1_images/yosys_lab3_day1_vsd.jpg)
  - **Lecture 3- TCL Quick Refresher**
    - Basic concepts of tcl, code basics etc were discussed.
    - **Lab4 - TCL Commands**
  - **Images for the above labs**
    - ![Alt Text](images/Day5_DCDay1_images/cell_selection_day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/faster_slowercells_day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/gate_flavor1_day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/gate_flavor2_day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/good,uxdesign_Day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/goodmuxtb_Day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/gtkwave1_Day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/installations_Day1_VSD.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/iverilog1_Day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/libcells_day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/rtldesign_day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/simulator_flow_Day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/synthesis_day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/synthesis_illustration_day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/testbench_Day1_VSD.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/yosys_setupflow_day1_vsd.jpg)
    - ![Alt Text](images/Day5_DCDay1_images/yosys_verificationflow_day1_vsd.jpg)

  - **Day 2 - Basics of STA**
    - **Lecture 4 - Intro to STA**
      - Basics of STA concepts were described and learnt in great detail, with examples and diagrams.
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec4_img1.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec4_img2.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec4_img3.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec4_img4.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec4_img5.jpg)
    - **Lecture 5 - What are Constraints**
      - Constraints are dicussed and transition time and output loads dicussed. Their impact on STA discussed.
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec5_img1.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec5_img2.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec5_img3.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec5_img4.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec5_img5.jpg)
    - **Lecture 6 - Input Trans and Output Load**
      - Basics were discussed how this affects setup and hold, operating frequency etc.
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec6_img1.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec6_img2.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec6_img3.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lec6_img4.jpg)
    - **Lab 5 - Timing dot libs**
      - Library files discussed.
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab5_img1.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab5_img2.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab5_img3.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab5_img4.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab5_img5.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab5_img6.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab5_img7.jpg)
    - **Lab 6 - Exploring dotlib P1**
      - dot lib P1
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab6_img1.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab6_img2.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab6_img3.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab6_img4.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab6_img5.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab6_img6.jpg)
    - **Lab 7 - Exploring dotlib P2**
      - dot lib P2
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab7_img1.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab7_img2.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab7_img3.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab7_img4.jpg)
      - ![Alt Text](images/Day6_DCDay2_images/vsd_DC_Day2_STA_lab7_img5.jpg)

  - **Day 3 - Advanced STA**
    - **Lecture 7 - SDC P1 Clock and Clock Tree Modelling - Uncertainity**
      - Basics of clock uncertainity like jitter and skew, and how it impacts clock integrity and timing closure.
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec7_img1.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec7_img2.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec7_img3.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec7_img4.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec7_img5.jpg)
    - **Lecture 8 - SDC P2 IO Delays**
      - Discussion of input and output delay constraints
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img1.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img10.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img11.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img2.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img3.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img4.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img5.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img6.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img7.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img8.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img9.jpg)
    - **Lab 8 - Loading design- get_ports, get_nets, get_cells**
      - source the .synopsys_dc.setup file from home = > make sure link library and target_libarry are set properly
      - pwd is ../DC_WORKSHOP/verilog_files/
      - read_verilog lab8_circuit.v
      - check if it completed successfully
      - link
      - compile_ultra
      - design load, use of get_ports, get_nets, get_cells, hier or not, small tcl commands and scripts.
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img1.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img2.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img3.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img4.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img5.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img6.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img7.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img8.jpg)
    - **Lab 9 - get_pins, get_clocks, querying clocks**
      - learnt about get_pins, get_clocks, and querying if a pin is a clock or not
      - get diection and other get_attribute for pins and nets
      - learnt about get_attribute using clock versus clocks the difference between them
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab9_img1.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab9_img2.jpg)
    - **Lab 10 - create_clock_waveform**
      - learnt about creating clocks and learning the impact of various constraints
      - ![Alt Text](images/Day7_DCDay3_images/
    - **Lab 11 - Clock Network Modelling - Uncertainty, report_timing**
      - Modelling various factors of the network, like uncertainity
      - setting source and network latency
      - min and max delays translating into setup and hold times
      - ![Alt Text](images/Day7_DCDay3_images/
    - **Lab 12 - IO Delays**
      - Modelling for input output delays, min and max
      - transition delays being added to the constraints
      - All the commands below are the constraints used:
        - create_clock -name MYCLK -per 10 [get_ports clk];
        - set_clock_latency -source 2 [get_clocks MYCLK];
        - set_clock_latency 1 [get_clocks MYCLK];
        - set_clock_uncertainty -setup 0.5 [get_clocks MYCLK];
        - set_clock_uncertainty -hold 0.1 [get_clocks MYCLK];
        - set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_A];
        - set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_B];
        - set_input_delay -min 1 -clock [get_clocks MYCLK] [get_ports IN_A];
        - set_input_delay -min 1 -clock [get_clocks MYCLK] [get_ports IN_B];
        - set_input_transition -max 0.4 [get_ports IN_A];
        - set_input_transition -max 0.4 [get_ports IN_B];
        - set_input_transition -min 0.1 [get_ports IN_A];
        - set_input_transition -min 0.1 [get_ports IN_B];
        - create_generated_clock -name MYGEN_CLK -master MYCLK -source [get_ports clk] -div 1 [get_ports out_clk];
        - create_generated_clock -name MYGEN_DIV_CLK -master MYCLK -source [get_ports clk] -div 2 [get_ports out_div_clk]; 
        - set_output_delay -max 5 -clock [get_clocks MYGEN_CLK] [get_ports OUT_Y];
        - set_output_delay -min 1 -clock [get_clocks MYGEN_CLK] [get_ports OUT_Y];
        - set_load -max 0.4 [get_ports OUT_Y];
        - set_load -min 0.1 [get_ports OUT_Y];
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab12_img10.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab12_img11.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab12_img12.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab12_img13.jpg)
       
    - **Lec9 - Generated clocks***
      - learnt about how generated clocks workout in designs
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec9_img1.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec9_img2.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec9_img3.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec9_img4.jpg)
     
    - **Lab13 - Lab for generated clocks**
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab13_img1.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab13_img2.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab13_img3.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab13_img4.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab13_img5.jpg)
     
    - **Lec10 - virtual clock, max latency and rise/fall IO delays**
      - Learnt about virtual clocks max latency and rise and fall how they affect final reporting of timing, slack paths etc
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec10_img1.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec10_img2.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec10_img3.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec10_img4.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec10_img5.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec10_img6.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec10_img7.jpg)
     
    - **Lab15 - Set max latency Part 1**
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img.JPG)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img1.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img2.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img3.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img4.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img5.JPG)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img8.JPG)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img9.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img10.JPG)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img11.jpg)


    - **Lab15 - virtual clk Part 2**
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img12.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img13.jpg)
      - ![Alt Text](images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img14.jpg)
  - **Day4 - Optimizations**
    - **Lec11 - Combinational Optimizations**
      - optimizations like constant
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec11_img1.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec11_img3.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec11_img4.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec11_img5.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec11_img6.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec11_img7.jpg)
    - **Lec12 - Sequential Optimizations**
      - optimizations involing sequential elements
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec12_img1.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec12_img2.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec12_img3.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec12_img4.jpg)
    - **Lab16 - Combinational Optimizations Part 1**
      - ![Alt Text](images/Day7_DCDay3_images/
    - **Lab16 - Resource Sharing Optimizations Part2**
      - ![Alt Text](images/Day7_DCDay3_images/
      - ![Alt Text](images/Day7_DCDay3_images/
    - **Lab17 - Sequential Optimizations**
      - ![Alt Text](images/Day7_DCDay3_images/
      - ![Alt Text](images/Day7_DCDay3_images/
    - **Lec13 - Special optimizations**
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img1.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img2.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img3.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img4.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img5.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img6.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img7.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img8.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img9.JPG)
    - **Lec14 - How Paths are timed MCP**
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img1.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img2.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img3.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img4.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img5.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img6.JPG)
    - **Lab18 - Boundary Optimmizations**
      - ![Alt Text](images/Day7_DCDay3_images/
      - ![Alt Text](images/Day7_DCDay3_images/
    - **Lab19 - Register Retiming**
      - ![Alt Text](images/Day7_DCDay3_images/
      - ![Alt Text](images/Day7_DCDay3_images/
    - **Lab20 - Isolating Output Ports**
      - ![Alt Text](images/Day7_DCDay3_images/
      - ![Alt Text](images/Day7_DCDay3_images/
    - **Lab21 - Multicycle Path**
      - ![Alt Text](images/Day7_DCDay3_images/
      - ![Alt Text](images/Day7_DCDay3_images/
  - **Day5 - Quality Checks**
    - **Lecture Report Timing**
      - Learnt about report_timing commands and -max_paths2 and nworst
      - difference between them
      - ![Alt Text](images/Day9_DCDay5_images/vsd_DC_Day3_SDC_lec15_img1.JPG)
      - ![Alt Text](images/Day9_DCDay5_images/vsd_DC_Day3_SDC_lec15_img2.JPG)

    - **Lab - Report Timing**
      - ![Alt Text](images/Day7_DCDay3_images/
      - ![Alt Text](images/Day7_DCDay3_images/
      - ![Alt Text](images/Day7_DCDay3_images/
    - **Lab - Check Timing, check design and max_capacitance**
      - ![Alt Text](images/Day7_DCDay3_images/
      - ![Alt Text](images/Day7_DCDay3_images/
      - ![Alt Text](images/Day7_DCDay3_images/





  
</details>

