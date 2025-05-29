Week 2 - Advanced Synthesis and STA with Design Compiler - Introduction to Logic Synthesis


This document talks about optimizations in synthesis and using advanced STA to do it.  

<details>
  <Summary>Day4 - Optimizations</summary>
  
  - **Lec11 - Combinational Optimizations**
      - optimizations like constant
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec11_img5.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec11_img6.jpg)
    - **Lec12 - Sequential Optimizations**
      - optimizations involing sequential elements
    - **Lab16 - Combinational Optimizations Part 1**
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img1.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img2.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img3.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img4.jpg)
    - **Lab16 - Resource Sharing Optimizations Part2**
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img7.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img8.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img9.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img10.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img11.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img12.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab16_img13.jpg)
    - **Lab17 - Sequential Optimizations**
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab17_img10.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab17_img2.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab17_img4.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab17_img6.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab17_img7.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab17_img8.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab17_img9.jpg)
    - **Lec13 - Special optimizations**
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img3.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img4.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img5.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img6.JPG)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img7.JPG)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img8.JPG)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec13_img9.JPG)
    - **Lec14 - How Paths are timed MCP**
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img1.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img2.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img3.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img4.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img5.JPG)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day3_SDC_lec14_img6.JPG)
    - **Lab18 - Boundary Optimmizations**
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab18_img1.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab18_img2.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab18_img3.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab18_img4.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab18_img5.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab18_img6.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab18_img7.jpg)
    - **Lab19 - Register Retiming**
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab19_img3.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab19_img4.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab19_img5.jpg)
      - ![Alt Text](images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab19_img6.jpg)
    - **Lab20 - Isolating Output Ports**
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab20_img1.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab20_img2.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab20_img3.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab20_img4.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab20_img5.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab20_img6.jpg)
    - **Lab21 - Multicycle Path**
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img1.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img10.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img11.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img12.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img13.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img2.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img3.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img4.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img5.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img6.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img7.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img8.jpg)
      - ![Alt Text](../images/Day8_DCDay4_images/vsd_DC_Day4_SDC_lab21_img9.jpg)
</details>
