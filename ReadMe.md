# Project Title: 
# Biometric Recognition Processor - Optimized 1 Dimensional Discrete Wavelet Transform Chip - RTL to GDS

## Overview
This repository contains the implementation of a Biometric Recognition Processor, focusing on the optimization of the 1 Dimensional Discrete Wavelet Transform (1D-DWT) component.
## Technologies Used - Synopsys SAED 32nm Technology node
## Project Details
- **University:** University of Minnesota, Twin Cities
- **Course:** EE5327 Master’s Project
- **Degree:** Master’s Degree in Electrical and Computer Engineering
- **Submitted By:** Kunal Kokate
- **Email ID:** kokat006@umn.edu
- **Supervisor:** Prof. Gerald Sobelman
- **College:** College of Science and Engineering (CSE)
- **Department:** Electrical and Computer Engineering
- **Submission Date:** December, 2023

## Abstract:
The project delves into the heart of biometric recognition with a focus on fingerprint recognition using VLSI architecture. At its core, the project centers around an Optimized 1D Discrete Wavelet Transform (O1D-DWT) component. This architecture integrates several crucial elements such as adders, D-flip-flops, shifters, buffers, clock divider, multiplexers, counters and 2’s complement blocks to create an efficient system for biometric recognition. The wavelet filter of type CDF-5/3 is used in this project which employs shifters, adders and several other blocks mentioned above to create a low pass filter with five taps and a high pass filter with three taps. The primary goal of this work is to process and analyze fingerprints in the form of binary image data, then decompose and compress the fingerprint image to reduce the memory size and decrease the computation time to optimize the 1D Discrete Wavelet Transform for high speed and more accurate results by passing through the high pass filter (HPF) and low pass filter (LPF) generating four sub-bands.

## Table of Contents
1. [Design Description of O1D-DWT Component](#design-description-of-o1d-dwt-component)
   1. [Function and Brief Description of Blocks Used in the Architecture (in Fig1.1)](#function-and-brief-description-of-blocks-used-in-the-architecture-in-fig11)
   2. [Interface Between Chip and External System](#interface-between-chip-and-external-system)
   3. [Table of I/O Ports, Bit-Widths, and Their Directions](#table-of-io-ports-bit-widths-and-their-directions)
2. [Design Synthesis, Fault Coverage, Physical Layout, and Sign-off Analysis](#design-synthesis-fault-coverage-physical-layout-and-sign-off-analysis)
   1. [Design Synthesis of O1D-DWT Chip](#design-synthesis-of-o1d-dwt-chip)
      1. [Table of Synthesis Report Based on Optimization Directives and Timing Driven Compile Pass for O1D-DWT Component](#table-of-synthesis-report-based-on-optimization-directives-and-timing-driven-compile-pass-for-o1d-dwt-component) 9
      2. [Table of Synthesis Report for FSM Based Implementation for O1D-DWT Component](#table-of-synthesis-report-for-fsm-based-implementation-for-o1d-dwt-component)
      3. [Table of Final Synthesis Report at 4 ns Clock Period](#table-of-final-synthesis-report-at-4-ns-clock-period
      4. [Analysis and Observation](#analysis-and-observation)
   2. [Fault Coverage & DFT Testing](#fault-coverage--dft-testing)
      1. [ATPG Results Summary](#atpg-results-summary)
      2. [Pre-DFT with Full Sequential Scan Chain Insertion](#pre-dft-with-full-sequential-scan-chain-insertion)
      3. [Post-DFT with Full Sequential Scan Chain Insertion](#post-dft-with-full-sequential-scan-chain-insertion)
      4. [Fault Simulation Results Summary](#fault-simulation-results-summary)
      5. [Pre-DFT Fault Simulation Report for O1D-DWT Chip](#pre-dft-fault-simulation-report-for-o1d-dwt-chip)
      6. [Post-DFT Fault Simulation Report for O1D-DWT Chip](#post-dft-fault-simulation-report-for-o1d-dwt-chip)
      7. [Analysis and Observation](#analysis-and-observation-1)
   3. [Physical Layout of O1D-DWT Chip](#physical-layout-of-o1d-dwt-chip)
      2.3.1 [Floor Planning](#floor-planning)
      2.3.2 [Placement and Legalization of Standard Cells](#placement-and-legalization-of-standard-cells)
   4. [Sign-off Analysis for O1D-DWT Chip](#sign-off-analysis-for-o1d-dwt-chip)
      2.4.1 [Post-SignOff Timing Analysis for O1D-DWT Design](#post-signoff-timing-analysis-for-o1d-dwt-design)
      2.4.2 [Post-SignOff Power Analysis for O1D-DWT Design](#post-signoff-power-analysis-for-o1d-dwt-design) 
      2.4.3 [Post-SignOff Power Threshold Voltage (Vth) Report for Standard Cells with HVT and SVT](#post-signoff-power-threshold-voltage-vth-report-for-standard-cells-with-hvt-and-svt)
      2.4.4 [Post-SignOff Leakage Power Report with Threshold Voltage (Vth)](#post-signoff-leakage-power-report-with-threshold-voltage-vth)
      2.4.5 [Post-SignOff Power Distribution Graph](#post-signoff-power-distribution-graph)
      2.4.6 [Noise Analysis for O1D-DWT Design](#noise-analysis-for-o1d-dwt-design)
      2.4.7 [Noise Analysis Report](#noise-analysis-report)
      2.4.8 [Post-SignOff Signal Integrity Analysis Report for O1D-DWT Design](#post-signoff-signal-integrity-analysis-report-for-o1d-dwt-design)
3. [Design Verification and Simulation Results](#design-verification-and-simulation-results)
   1. [Checks for Design Rule Violations](#checks-for-design-rule-violations)
   2. [Identify Coding Style Issues](#identify-coding-style-issues)
   3. [Performed Formal Verification to Ensure the Design Adheres to Specifications](#performed-formal-verification-to-ensure-the-design-adheres-to-specifications)
   4. [Analyze the Timing Characteristics of the Design](#analyze-the-timing-characteristics-of-the-design)
   5. [Analyze and Optimize Power Consumption in the Design](#analyze-and-optimize-power-consumption-in-the-design)
   6. [Timing SignOff](#timing-signoff)
   7. [Gate-Level Simulation](#gate-level-simulation)
4. [Conclusion](#conclusion)
5. [References](#references)
6. [Appendix A - Verilog/SystemVerilog Code](#appendix-a---verilogsystemverilog-code)
7. [Appendix B - Schematics](#appendix-b---schematics)


## Design Synthesis, Fault Coverage, Physical Layout, and Sign-off Analysis

## 1. Design Description of O1D-DWT Component
The project centers on the development of an Optimized 1D Discrete Wavelet Transform (O1D-DWT) component tailored for processing fingerprint data with binary input images. The objective is to efficiently decompose and compress the data, thereby reducing memory requirements and minimizing computation time. The optimization focuses on enhancing the speed and accuracy of the results through the application of low-pass filter (LPF) and high-pass filter (HPF) operations, ultimately yielding low-pass frequency bands and high-pass frequency bands at the output. 
<p align="center">
  <img src="https://github.com/KunalKokate/RTL2GDS_BiometricRecognitionProcessor_O1D-DWTChip/assets/42606968/93be5601-69f7-4e9e-a6b9-52f472280ccc" width="700" alt="image35">
</p>

<p align="center">
  <img src="https://github.com/KunalKokate/RTL2GDS_BiometricRecognitionProcessor_O1D-DWTChip/assets/42606968/d37a0ab9-8d84-40f8-9f8e-4d592b86c7b4" width="700" alt="image35">
</p>

   - ## 1.1 Function and Brief Description of Blocks Used in the Architecture (in Fig1.1)
A. D-Flip Flop: The architecture makes use of a series of four rising edge D-flip flops with synchronous reset and a clock signal. They help synchronize and control the flow of data within the circuit by capturing input data at specific moments in time, typically aligned with the clock signal. This synchronization ensures that data is processed in a consistent and predictable manner. And it stores the binary information from the input data for one clock cycle, likewise it stores the data at every intermediate stage for sequential processing of discrete wavelet transform.

B. Adders: There are in total 6 full adders used in the above architecture. The significance of using adders is to perform arithmetic operations on the binary input data. This addition operation is a fundamental step in many signal processing algorithms, including discrete wavelet transform. It allows us to perform data aggregation and prepare data for further transformations like FFT (Fast Fourier Transform).

C. 1-bit/2-bit left shifter: The 1-bit left shifter shifts the 16-bit input data by one bit to the left. Left shifting by one bit effectively divides the value by 2, which is a fundamental operation in wavelet transforms, especially for down-sampling or reducing the scale of data. The 2-bit left shifter shifts the 16-bit input data by two bits to the left. Similar to the 1-bit left shifter, the 2-bit left shifter further scales the data down by a factor of 4. This kind of scaling is useful for multi-resolution analysis, which is a key feature of wavelet transforms.

D. 3-bit right shifter: The 3-bit right shifter is used to perform a bitwise right shift operation on the input data. In a 16-bit system, shifting right by 3 bits results in a loss of the three least significant bits to reduce the precision and achieve the desired level of data decomposition.

E. 2’s complement and Buffer: The 2's complement block computes the two's complement of the input data. It is used for signed number representation. In the current design of discrete wavelet transform, it is used to represent the negative part of the signal, especially for filtering and feature extraction from the image. A buffer is used to maintain a copy of the original data for further processing.

F. Clock Divider: The clock divider generates an output clock signal that is a fraction of the input clock signal. In my project, the frequency of the input signal is 200MHz, the clock divider will divide the clock by 2 resulting in a 100 MHz signal. It is critical for controlling and synchronizing the processing stages within the design. 

G. Low Pass Filter Output and High Pass Filter Outputs: With these blocks working together, the processing of the input binary image data to yield two outputs (HPF and LPF with 4 sub-bands) is summarized as: The original image data is modified and analyzed using full adders and shifters to create high-frequency components. These high-frequency components are then combined and used to calculate the 2's complement. The 2's complement, along with original data preserved by the buffer, helps generate the low-frequency components. By employing clock synchronization and controlled data flow, the system separates and organizes high-frequency and low-frequency components into different sub-bands, resulting in the desired outputs: the High Pass Filter (HPF) for high-frequency components with detailed coefficients and the Low Pass Filter (LPF) for low-frequency components with approximate coefficients. 

   - ## 1.2 Interface Between Chip and External System
<p align="center">
  <img src="https://github.com/KunalKokate/RTL2GDS_BiometricRecognitionProcessor_O1D-DWTChip/assets/42606968/c7af1b50-6213-40b1-9332-bb2cfd44e411" alt="image35">
</p>
From the entire design perspective, the main architecture proposed[1] has an existing database of the fingerprints of human beings and it takes an input fingerprint on the other hand. 
Both the data is sent to the O1DDWT architecture as an input binary image data with any size. 
In my project, I have taken the input binary image to be 8x8 size with bit depth of 8. 
So the converted input image in binary would be 16x1 in one dimension, which can be processed by the O1D-DWT component with the expectation of performing signal processing methods on the image including discrete wavelet transform. 
The following figure (Fig 2) shows the interface between the O1D-DWT component and the external system of Biometric Recognition Processor. 
By performing decomposition, compression, down sampling, arithmetic operations, preserving or storing the input signal and processing it further to give our low and high frequencies at low pass and high pass filter output. 
These output signals are further given to the external blocks like demultiplexer[1] and LPF and HPF memory for performing FFT and feature extraction leading to comparison of the existing fingerprint and current image of fingerprint and finally it declares the results of the fingerprint is matched or unmatched.

   - ## 1.3 Table of I/O Ports, Bit-Widths, and Their Directions
| I/O Pins/Ports                    | Bit Width | Direction |
| ----------------------------------|-----------|------------|
| Clock (clk)                       | 1-bit     | Input      |
| Reset                             | 1-bit     | Input      |
| Input Binary Image Data (x_in)    | 16-bit    | Input      |
| Scan Chain Inputs (test_si, test_se)| 1-bit    | Input     |
| I/O ports of DFF’s (1 to 4)        | 16-bit    | Wire       |
| I/O ports of Full Adders (1 to 5)  | 16-bit    | Wire       |
| I/O ports of 2’s complement and Buffers | 16-bit | Wire       |
| I/O ports of 1 bit/2-bit/3-bit shifter | 16-bit | Wire       |
| Scan Chain Output (test_so)        | 1-bit     | Output     |
| Output of Low Pass Filter         | 16-bit    | Output     |
| Output of High Pass Filter        | 16-bit    | Output     |
| Clock Divider                     | 1-bit     | Output     |


## 2. Design Synthesis, Fault Coverage, Physical Layout, and Sign-off Analysis
  ## 2.1 Design Synthesis of O1D-DWT Chip
Following the development of a Verilog code for a 1-dimensional discrete wavelet transform chip, a .synopsys file was defined, encompassing the target library, symbol library, and link library. 
The designated target library for the chip is ss0p95v125c, featuring standard cells with distinct threshold voltages - High-Voltage Threshold (HVT), Low-Voltage Threshold (LVT), and Regular-Voltage Threshold (RVT). 
The design is based on Synopsys 32nm technology node, specifically SAED 32nm. 
Command used for executing the design by running the Tcl script is: 
> dc_shell -64 -f ./scripts/dc_flow.tcl

  ### 2.1.1 Table of Synthesis Report Based on Optimization Directives and Timing Driven Compile Pass for O1D-DWT Component
During the synthesis stage, various experiments were performed to get optimized results post-synthesis stage by setting up optimization constraints and directives using Synopsys toolset, so that it meets the timing constraints and minimum area utilization. 
As per the output values obtained, the area and speed of the synthesized O1D-DWT component design changes drastically with respect to changes in the optimization directives and timing driven compile pass.

For Timing Driven Structuring OFF
| Configuration                        | Timing (ns) | Area (µm)        | Power (µW)      |
| -------------------------------------|--------------|------------------|-----------------|
| Multiple Output with phase inversion | 0.72 (MET)   | 1748.573918     | 103.9173 µW    |
| Single Output with phase inversion   | 0.80 (MET)   | 1748.573918     | 103.9173 µW    |

For Timing Driven Structuring ON
| Configuration                        | Timing (ns) | Area (µm)        | Power (µW)      |
| -------------------------------------|--------------|------------------|-----------------|
| No flattening                        | 0.79 (MET)   | 1681.139280     | 103.9173 µW      |

For Timing Driven Structuring (OFF) configuration with single and multiple output along with the phase inversion, in the dc_flow.tcl script, I found considerable increase in the area (1748.573918 µm) of the design as compared to Timing Driven Structuring (ON) with no flattening mode, lower area is obtained (1681.139280 µm). 
The timing report for reg2reg group path for multiple output with phase inversion is lesser (0.72) with cost of higher area, as compared to the timing report for single output with phase inversion (0.80) with low area utilization. 

  ### 2.1.2 Table of Synthesis Report for FSM Based Implementation for O1D-DWT Component
      
Following table shows the synthesis report after implementation of FSM (finite state machine) at 2 ns clock cycle for two encoding styles:	 
One-Hot encoding style and Binary encoding style.
| FSM Encoding Style | Area (µm) | Timing | Power (µW) | No. of Cells |
| ------------------- |-----------|--------|------------|--------------|
| Output Reg2Reg     | 1788.5739 | 0.61 (MET) | 110.9173 µW | 375          |
| One-Hot            | 1813.6284 | 0.61 (MET) | 110.9173 µW | 375          |

The area obtained by one hot FSM encoding style for the sequential elements that store the state is found to be greater than the area obtained by binary FSM encoding style. 
Because, unlike in binary FSM encoding style, the one hot encoding style has one flip-flop per state to store the sequential elements. 
Due to which the overall cell count leads to higher area utilization. The worst negative slack (WNS) for reg2reg group is 0.52 units and 0.63 units for binary and one hot encoding styles respectively. 
I have also tried performing power optimization and dynamic power gating to my design however, since I have no gated clocks in my design, it was giving the same power consumption report as in FSM based report.

  ### 2.1.3 Table of Final Synthesis Report at 4 ns Clock Period (Post Synthesis Report)

| Metric             | Worst Time Slack (ns) | Total Power (µW) | Total Area (µm)    |
|--------------------|-----------------------|------------------|--------------------|
| Inputs             | 2.89 (MET)            | 238.1915 µW      | 1928.922499 µm     |
| Outputs            | 3.14 (MET)            | 238.1915 µW      | 1928.922499 µm     |
| Reg2Reg            | 3.22 (MET)            | 238.1915 µW      | 1928.922499 µm     |

Area utilization report: 
```
Number of ports:                          108
Number of cells:                          326
Number of combinational cells:            226
Number of sequential cells:                92
Total cell area:                  1532.742469
Total area:                       1928.922499
```

Timing report for reg2reg path group:
```
  clock CLK (rise edge)                                              4.00       4.00
  clock network delay (ideal)                                        1.00       5.00
  clock uncertainty                                                 -0.20       4.80
  dwt_inst/DFF3_Q_regx3x/CLK (SDFFARX1_HVT)                          0.00       4.80 r
  library setup time                                                -0.18       4.62
  data required time                                                            4.62
  -------------------------------------------------------------------------------------
  data required time                                                            4.62
  data arrival time                                                            -1.40
  -------------------------------------------------------------------------------------
  slack (MET)                                                                   3.22
```

Power Consumption Report:

```
                 Internal      Switching        Leakage         Total                 Cell
Power Group      Power         Power            Power           Power  ( %) Attrs    Count
------------------------------------------------------------------------------------------
io_pad         0.0000       
     0.0000         0.0000         0.0000  (   0.00%)            
memory         0.0000            0.0000         0.0000         0.0000  (   0.00%)            
black_box      0.0000            0.0000         0.0000         0.0000  (   0.00%)            
clock_network  85.4573            0.0000        0.0000         85.4573  (  35.88%)            
register       25.4188           11.6515        1.1670e+07     48.7406  (  20.46%)      65
sequential     10.8439            5.5053        6.0979e+06     22.4472  (   9.42%)      27
combinational     52.4425        18.6665        1.0437e+07     81.5465  (  34.24%)     226
------------------------------------------------------------------------------------------
Total          174.1625 uW       35.8233 uW     2.8206e+07 pW  238.1915 uW

```

  ### 2.1.4 Analysis and Observation

* In the final report of the table, the results obtained are for the 4ns clock cycle set in the SDC constraints file under the operating condition saed32rvt_ss0p95v125c with Synopsys technology node of SAED 32 nm and to read the interconnect parasitic information it used TLUPLUS max and min libraries

* The final design synthesis has been implemented with sanity checks for timing, multi-threshold voltage constraints, DFT scan chain insertion, FSM extraction and optimization directives and clock gating for power optimization.

* The above two tables represent the timing, power and area reports after final synthesis. The total power consumed by the design is 238.1915 µW. The contribution of leakage power (174.1625 µW) is much higher as compared to the switching power (35.8233 µW) and leakage power (28.2060 µW).

* The total area utilization of the O1D-DWT chip is 1928.922499 µm found to be increased post adding several optimization constraints, timing, multi-threshold voltage and FSM based directives.

* The timing report for inputs (2.89), outputs (3.14) and reg2reg(3.22) group paths is increased due to increase in the clock period (4 ns). The reason for increasing the clock period was slack violations. I was getting slack violations in the reg2reg group path of (-1.23) and (-0.73) for 2 ns and 3 ns clock periods.

- ## 2.2 Fault Coverage & DFT Testing
The Verilog code for O1D-DWT chip, was included with the testing inputs and output ports for DFT Scan Chain Insertion. The DFT testing and fault coverage simulation was performed on Synopsys TetraMAX Tool. 
The TetraMAX tool maintains a list of potential faults in the design and assigns each such fault to a fault class according to its detectability status. 
We know that the ATPG (Automatic Test Pattern Generation) technique for sequential circuits is much more difficult than for combinational circuits. Since, in my design of O1D-DWT component, there are 6 D-Flip Flops clocked with 4 ns time period and a reset signal, are part of sequential circuit design. 
Hence, the popular design-for-testing (DFT) technique, Scan Design was implemented which simplifies the test-pattern for sequential circuit design resulting in higher fault coverage and reduces the testing costs.

  ### 2.2.1 ATPG Results Summary
                           |         Basic         |          Fast        |         Full         |
| Test Mode            | Pre-DFT | Post-DFT | Pre-DFT | Post-DFT | Pre-DFT | Post-DFT |
|----------------------|---------|----------|---------|----------|---------|----------|
| Total Faults         | 3142    | 3332     | 3142    | 3332     | 3142    | 3332     |
| Test Coverage        | 0.17    | 38.79    | 1.26    | 38.17    | 84.83   | 95.87    |
| Fault Coverage       | 0.16    | 37.18    | 1.15    | 37.18    | 77.24   | 91.50    |
| ATPG Effectiveness   | 89.97   | 94.84    | 100     | 99.70    | 90.37   | 98.59    |
| # of Internal Patterns| 1      | 5        | 3      | 5        | 6      | 21       |

In a scan chain, registers are typically connected in alphanumeric order during synthesis. These scan chains are inserted in three ATPG modes: Basic Scan, Fast Sequential Scan and Full Sequential Scan.
* Basic-Scan: The default ATPG mode is Basic-Scan. In this mode, TetraMAX operates as a full-scan, combinational-only ATPG tool. In other words, to get high test coverage, the sequential elements need to be scan elements. 
* Fast-Sequential: Fast-Sequential ATPG provides limited support for partial-scan designs (designs with some non-scan sequential elements). In this mode, multiple capture procedures are allowed between scan load and scan unload, allowing data to be propagated through non-scan sequential elements in the design.
* Full-Sequential: Full-Sequential ATPG, like Fast-Sequential ATPG, supports multiple capture cycles between scan load and unload, and supports RAM and ROM models, thus increasing test coverage in partial-scan designs.
  
  ### 2.2.2 Pre-DFT with Full Sequential Scan Chain Insertion
  ```
  Uncollapsed Stuck Fault Summary Report 
  ----------------------------------------------- 
  fault class                     code   #faults 
  ------------------------------  ----  --------- 
  Detected                         DT       2331 
    detected_by_simulation         DS      (2331) 
  Possibly detected                PT        192 
    atpg_untestable-pos_detected   AP       (131) 
    not_analyzed-pos_detected      NP        (61) 
  Undetectable                     UD        281 
    undetectable-tied              UT       (189) 
    undetectable-blocked           UB        (92) 
  ATPG untestable                  AU         66 
    atpg_untestable-not_detected   AN        (66) 
  Not detected                     ND        272 
    not-controlled                 NC       (115) 
    not-observed                   NO       (157) 
  ----------------------------------------------- 
  total faults                              3142 
  test coverage                            84.83% 
  fault coverage                           77.24% 
  ATPG effectiveness                       90.37% 
  ----------------------------------------------- 
             Pattern Summary Report 
  ----------------------------------------------- 
  #internal patterns                           6 
      #full_sequential patterns                6 
  ----------------------------------------------- 

```

  ### 2.2.3 Post-DFT with Full Sequential Scan Chain Insertion
  ### 2.2.4 Fault Simulation Results Summary
  ### 2.2.5 Pre-DFT Fault Simulation Report for O1D-DWT Chip
  ### 2.2.6 Post-DFT Fault Simulation Report for O1D-DWT Chip
  ### 2.2.7 Analysis and Observation
   - ## 2.3 Physical Layout of O1D-DWT Chip
      - ### 2.3.1 Floor Planning
      - ### 2.3.2 Placement and Legalization of Standard Cells
   - ## 2.4 Sign-off Analysis for O1D-DWT Chip
      - ### 2.4.1 Post-SignOff Timing Analysis for O1D-DWT Design
      - ### 2.4.2 Post-SignOff Power Analysis for O1D-DWT Design
      - ### 2.4.3 Post-SignOff Power Threshold Voltage (Vth) Report for Standard Cells with HVT and SVT
      - ### 2.4.4 Post-SignOff Leakage Power Report with Threshold Voltage (Vth)
      - ### 2.4.5 Post-SignOff Power Distribution Graph
      - ### 2.4.6 Noise Analysis for O1D-DWT Design
      - ### 2.4.7 Noise Analysis Report
      - ### 2.4.8 Post-SignOff Signal Integrity Analysis Report for O1D-DWT Design

## 3. Design Verification and Simulation Results
   - ## 3.1 Checks for Design Rule Violations
   - ## 3.2 Identify Coding Style Issues
   - ## 3.3 Performed Formal Verification to Ensure the Design Adheres to Specifications
   - ## 3.4 Analyze the Timing Characteristics of the Design
   - ## 3.5 Analyze and Optimize Power Consumption in the Design
   - ## 3.6 Timing SignOff
   - ## 3.7 Gate-Level Simulation

## 4. Conclusion
## 5. References
## 6. Appendix A - Verilog/SystemVerilog Code
## 7. Appendix B - Schematics

## Author
- **Kunal Kokate**
  - **Email:** kokat006@umn.edu

## License
Include information about the project's license.

## Acknowledgments
Express gratitude and credit to anyone who contributed to the project or provided support.
