 Week 2 - Advanced Synthesis and STA with Design Compiler - Introduction to Logic Synthesis


This document talks about introduction to synthesis and STA.

  <details>
  <Summary> Day1 - Lecture 1 - Introduction to the course </summary>
   
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
    - ![Alt Text](images/Day5_DCDay1_images/gtkwave1_Day1_vsd.jpg)
</details>


