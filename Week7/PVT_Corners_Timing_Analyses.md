Week 7 - Process, Voltage and Temperature Corners with Timing Analysis and Impact on BabySOC

This task involved synthesis, timing analysis and reporting of post synthesis simulations for the multiple corners of Process, Voltage and Temperatures, on VSD BabySOC, using SDC(Synopsys Design Constraints) file, and other stimulus. This is usually done in industry with various PVT corners to ensure best operation for the required PPA specifications. 

<details>
  <Summary> Post Synthesis and SImulation in BabySOC Modelling</Summary>
  
  - **What is PVT, SDC and Timing Analysis?**
    - 
  - **Reading SDC constraints and synthesising the design**
    - Commands used are:
      - dc_shell
      - set target_library /home/aakarshitha/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.db
      - set link_library {* /home/aakarshitha/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.db /home/aakarshitha/VSDBabySoC/src/lib/avsdpll.db /home/aakarshitha/VSDBabySoC/src/lib/avsddac.db}
      - set search_path {/home/aakarshitha/VSDBabySoC/src/include /home/aakarshitha/VSDBabySoC/src/module}
      - read_file {sandpiper_gen.vh sandpiper.vh sp_default.vh sp_verilog.vh clk_gate.v rvmyth.v rvmyth_gen.v vsdbabysoc.v} -autoread -top vsdbabysoc
      - 
      
  - **S**
    - adfds
    - Images for this work
      - avsddac images

      - sky130 images
        - ![Alt Text](../images/Week5-6_BabySOC_PostSynthesis_Simulation/dc_shell_launch_targetlib_set.jpg)

          
  - **Post Synthesis GLS Simulation**
    - Use these commands below:
      - cd 
    - Images for this step:
      - ![Alt Text](../images/Week5-6_BabySOC_PostSynthesis_Simulation/gls1.jpg)

        
  - **Bugs faced during the process and their fixes**
    - Errors during 
    - Errors during 
      - ![Alt Text](../images/Week5-6_BabySOC_PostSynthesis_Simulation/elab_errors.jpg)
      

  
  
  
  </details>
