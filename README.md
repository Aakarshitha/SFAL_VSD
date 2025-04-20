# SFAL_VSD
<details>
  <Summary> SFAL_VSD SOC</summary>

  This project is to create an SOC from specifications to netlist.

<details>
  <Summary> Day 0: Tools Installation</summary>

  All the instructions for installation of required tools can be found here:

  **System Check**
    -6GB RAM, 50 GB HDD
    -Ubuntu 20.04+
    -4vCPU
    
  **TOOL CHECK**
  **Yosys**
    -$ sudo apt-get update
    -$ git clone https://github.com/YosysHQ/yosys.git
    -$ cd yosys
    -$ sudo apt install make (If make is not installed please install it) 
    -$ sudo apt-get install build-essential clang bison flex \
        libreadline-dev gawk tcl-dev libffi-dev git \
        graphviz xdot pkg-config python3 libboost-system-dev \
        libboost-python-dev libboost-filesystem-dev zlib1g-dev
    -$ make config-gcc
    -$ make 
    -$ sudo make install
    
  **Iverilog** - Steps to install iverilog
    -sudo apt-get update
    -sudo apt-get install iverilog
    
  **GTKWAVE** - Steps to install gtkwave
    -sudo apt-get update
    -sudo apt install gtkwave


