Week 2 - Advanced Synthesis and STA with Design Compiler - Introduction to Logic Synthesis


This document talks about advanced STA, timing constraints and running DC to understand them.

<details>
  <Summary>Day 3 - Advanced STA</summary>
  
  - **Lecture 7 - SDC P1 Clock and Clock Tree Modelling - Uncertainity**
    - Basics of clock uncertainity like jitter and skew, and how it impacts clock integrity and timing closure.
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec7_img1.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec7_img2.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec7_img3.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec7_img4.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec7_img5.jpg)
  - **Lecture 8 - SDC P2 IO Delays**
    - Discussion of input and output delay constraints
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img3.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img4.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img5.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img6.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img7.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img8.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec8_img9.jpg)
  - **Lab 8 - Loading design- get_ports, get_nets, get_cells**
    - source the .synopsys_dc.setup file from home = > make sure link library and target_libarry are set properly
    - pwd is ../DC_WORKSHOP/verilog_files/
    - read_verilog lab8_circuit.v
    - check if it completed successfully
    - link
    - compile_ultra
    - design load, use of get_ports, get_nets, get_cells, hier or not, small tcl commands and scripts.
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img2.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img3.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img5.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img6.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab8_img8.jpg)
  - **Lab 9 - get_pins, get_clocks, querying clocks**
    - learnt about get_pins, get_clocks, and querying if a pin is a clock or not
    - get diection and other get_attribute for pins and nets
    - learnt about get_attribute using clock versus clocks the difference between them
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab9_img1.jpg)
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
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab12_img10.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab12_img11.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab12_img12.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab12_img13.jpg)
     
  - **Lec9 - Generated clocks**
    - learnt about how generated clocks workout in designs
   
  - **Lab13 - Lab for generated clocks**
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab13_img3.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab13_img4.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab13_img5.jpg)
   
  - **Lec10 - virtual clock, max latency and rise/fall IO delays**
    - Learnt about virtual clocks max latency and rise and fall how they affect final reporting of timing, slack paths etc
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lec10_img7.jpg)
   
  - **Lab15 - Set max latency Part 1**
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img.JPG)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img1.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img2.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img3.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img4.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img5.JPG)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img8.JPG)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img9.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img10.JPG)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img11.jpg)
  - **Lab15 - virtual clk Part 2**
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img12.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img13.jpg)
    - ![Alt Text](../images/Day7_DCDay3_images/vsd_DC_Day3_SDC_lab15_img14.jpg)

</details>
