Week 1 - RTL Design and Synthesis

This document gives details and learning from the Week 1 module of RTL Design and Synthesis and concepts related to it.

<details>
  <Summary> Day 1 - Introduction to Verilog</summary>
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
  <Summary> Day 2 - Timing Libs, Hierarchical versus flat synthesis, and efficient flop coding styles </summary>

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
  <Summary> Day 3 - Combinational and Sequential Optimisations </summary>

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
  <Summary> Day 4 - GLS, Blocking vs Non-Blocking, simulation-synthesis mismatch </summary>

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
