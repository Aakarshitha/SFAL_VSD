Week 3 - BabySoC Introduction

This week we understand system on chip, thier significance, different components and their application using BabySOC @ https://github.com/manili/VSDBabySoC?tab=readme-ov-file#openlane-details-and-flow 
  
  <details>
  <Summary>  Introduction to SOC </summary>
    
     An SOC or System on Chip is essentially a system consisting of different IPs and components that are integrated together on a single chip to form a working, fuly functional device working at a specific operating frequency. The various components on it generally includes a microprocessor, like a RISC-V CPU like RVMYTH, some memory IPs, ADCs, DACs, to convert from analog to digital and viceversa, some serial interfaces to have I/O, like LEDs, SPI, I2C, UART some high frequency operating IPs lie Ethernet or PCIE and perhaps a NOC or network on chip/bridge that interacts with all these togehter to get work done. This systems has a lot of complexity usually, due to the various different components involved and the transactions between them, which makes it an ideal option for complex tasks.
     ![Alt Text](images/Week3_BabySOC_Modelling/SOCimg1.jpeg)

  - **Common Components of an SOC**
    - **Central Processor Unit(CPU)** - There is the central processing unit that executes instructions and manages program flow.
    - **Memory (SRAM/DRAM/ROM)** - Stores data and instructions; includes on-chip (SRAM) and off-chip (DRAM) memory.
    - **Interconnect (e.g., AMBA AXI, NoC)** - Facilitates cohenerent secure communication between cores, peripherals, and memory.
    - **Peripherals (UART, I2C, SPI, GPIO)** - SOC can have multiple different peripheral IPs with respective interfaces for external devices and sensors.
    - **DMA (Direct Memory Access)** - DMA transfers data between memory and peripherals without CPU involvement. Manages many transfers, reducing CPU work overload.
    - **Clock Management (PLL, Clock Gating)** - Generates and distributes clocks; enables dynamic frequency scaling, clock division and maintainence etc
    - **Power Management Unit (PMU)** - It controls voltage and power states to optimize energy efficiency.
    - **Interrupt Controller** - This manages interrupt requests and prioritizes them for the CPU.
    - **Debug Interface (e.g., JTAG)** - Debug feature to allow external debugging, control and programming of the chip, with observation of functionality.
    - **Fabric/Bus Matrix** - This connects all internal blocks with appropriate arbitration and routing, resolution and coherency maintainence.
    - **Timers and Counters, Security Engine-firewalls etc** - IPs present to provide timing functions for scheduling and delays. Some IP/firewall IP to handle encryption, decryption, and secure boot processes.
  
  - **What is BabySOC?**
    BabySOC is a simple SOC, with 3 main components- a RISC-V MYTH Processor, an 8x-PLL or Phase Locked Loop and a 10-bit DAC or Digital to Analog Convertor IP. It is a fully open-source, powerful SOC, fabricated under Sky130 technology, that can perform functions and interact with the outer world, giving analog output to devices like televisions or audio devices, to give music pieces or video frames. 
  - **Components of BabySOC**
    - **Phase Locked Loops(PLLs)**
      - A Phase Locked Loop is a a fundamental circuit that acts like a feedback control system that synchronizes the phase of an output signal with that of an input signal. It's a fundamental building block in many electronic systems, particularly for frequency synthesis, clock recovery, and signal processing and in this case, generating a stable clock for the entire BabySOC. PLLs consist of a voltage-controlled oscillator (VCO), a phase detector, and a loop filter. 
      - ![Alt Text](images/Week3_BabySOC_Modelling/PLLs.jpg)
    - **Digital to Analog Convertor(DAC)**
      - A Digital to Analog Convertor or DAc is a fundamental electrical component that can convert digital signals into its analog form, and can do it in many ways forming different types of DACs. Their functionality is measued by metrics called Integral Non-Linearity/INL and Differential Non-Linearity/DNL. An example below is the R/2R DAC. DACs and ADCs have several applications in SOCs, in various applications that have the conversion of communication/transactions between the digital and analo world.
      - ![Alt Text](images/Week3_BabySOC_Modelling/dACimg.png)
    - **RVMYTH**
      - RVMYTH is an RISC-V Processor IP Core that is designed by students in the VSD and Redwood EDA in TL Verilog. It is open-source and free to be used by students and professors/mentors.
      - ![Alt Text](images/Week3_BabySOC_Modelling/vsdbabysoc_block_diagram.jpg)
        
  - **Advantages and Key challenges with SOCs**
     - High integration reduces board size and cost and the lower power consumption due to fewer external components.
     - They can have better performance from on-chip communication. They have increased reliability and compact form factor.
     - However, they are complex to design and verify and to meet the required operating frequency.
     - It gets difficult and costly to fix post-silicon bugs, and hence, sometimes, we lead to silcion respins.
     - Less flexible for upgrades. Thermal and Power management is harder in dense chips.

  - **Key Applications of SOCs**
    - **Smartphones/Wearables** – Compact, low power, fast performance (e.g., Snapdragon, Apple A-series).
    - **Automotive** – Real-time processing for safety and infotainment.
    - **IoT Devices** – Low-cost, low-power with integrated radios (e.g., ESP32).
    - **AI Edge Devices** – Local inference with NPUs or GPUs (e.g., Google Edge TPU).
    - **Industrial/Networking** – High-speed data handling and control.
   
  - **Types of SoCs**
    - **Microprocessor-based** – General-purpose, OS-capable (e.g., ARM Cortex-A).
    - **Microcontroller-based** – Embedded, low-power systems (e.g., STM32).
    - **Application-specific (ASIC)** – Optimized for specific tasks like AI or modems.
    - **FPGA-based** – Reconfigurable logic with CPUs (e.g., Xilinx Zynq).
    - **Heterogeneous** – Mix of CPUs, GPUs, NPUs for diverse tasks (e.g., Apple M-series).

</details>
