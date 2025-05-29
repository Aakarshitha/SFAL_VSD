Week4 - BabySOC Modelling

This week we are learning about modelling and simulating VSD's BabySOC, with the RVMYTH processor, PLL and DAC components. Modelling will help us learn, understand and simulate the microarchitecture of the SOC, and observe the simulated GTKWave.

<details>
  <Summary> Introduction to BabySOC Modelling</Summary>
  
  - Model and simulate the VSDBabySoC using iverilog, then we will show the results using gtkwave tool. 
  - VSDBabysoc module is initialised with values, resulting in PLL's clock generation, CLK for the circuit. 
  - The CLK signal instruction memory instructions of RVMYTH processor to be executed. 
  - Register r17 will be filled values per cycle. 
  - DAC core uses the values from register r17 to give an output called OUT signal.

  - **Modelling of RVMYTH**
    - The RVMYTH processor written in TL-Verilog, must be written in Verilog.
    - Therefore, it is translated to verilog using Sandpiper saas [Here](https://github.com/shivanishah269/risc-v-core)
  - **Modelling of PLL and DAC**
    - These two analog components cannot be synthesised, hence their behaviour has to be modelled in simulation.
    - Real datatype is used in simulation
    - [This](https://github.com/vsdip/rvmyth_avsdpll_interface) is the implementation of PLL old model. Now, with neccessary changes, [this](https://github.com/lakshmi-sathi/avsdpll_1v8) model is used.  
    - This [model](https://github.com/vsdip/rvmyth_avsdpll_interface) is used to model PLL and this [model](https://github.com/vsdip/rvmyth_avsddac_interface) is used to model DAC.
  
  </details>

  <details>
  <Summary>  BabySOC Modelling Process </Summary>

  - Digital output value fed into the DAC is increased/decreased to observe changes on the DAC output.
  - Code snippet is as follows:
```
   $ sudo apt install make python python3 python3-pip git iverilog gtkwave docker.io
   $ sudo chmod 666 /var/run/docker.sock
   $ cd ~
   $ pip3 install pyyaml click sandpiper-saas
```
  - Come out of the dircetory, clone the respitory and do it in an arbitary directory structure.
```
   $ cd ~
   $ git clone https://github.com/manili/VSDBabySoC.git
```

  - cd to the dircetory `$ cd VSDBabySoC`
  - To convert TLV RVMYTH processor into verilog, use sandpiper command `sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/`


   </details>
  
