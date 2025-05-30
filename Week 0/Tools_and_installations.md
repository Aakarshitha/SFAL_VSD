
 Week 0 - Tools Installation

This module for Week 0 talks about tools and isntallations required to get started.

<details>
   <Summary> Day 0 </summary>
  - All the instructions for installation of required tools can be found here:
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
