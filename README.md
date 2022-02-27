# Design_and_Simulation_of_0.9V-3.3V-GPIO_on_CMOS_28nm_Technology

## Table of Contents
  * Introduction
  * Software
  * CMOS Analysis
  * Sub-Circuit Components
  * Circuit Design
  * Simulation
  * Performance
  * Conclusion
  * Author
  * Acknowledfements
  * Referneces

## Introduction
Wether it is a Microcontrollers, FPGAs or some ASIC they all have one thing in common and tha is GPIO. GPIO stands for General Purpose Input Output. As the name suggest it can be used as both input and output depending on the state of control signals. GPIO is usually a subpart of a large system, primarily used for getting data from physical word or external devices or giving command to external devices. This repository is offers a GPIO design which works on 0.9V core and 3.3 I/O logic level. All the communication or control signal logic is base on 0.9V design and the I/O functionality of GPIO operates at 3.3V logic.

## Software Used
The two major softwares without which this project was impossible are Synopsys Custom Compiler and Synopsys Primewave. A huge thanks to the Synposys India and IIT Hyderabad for providing the access to these elite softwares.

Custom Compiler™ is a fresh, modern solution for full-custom analog, custom digital, and mixed-signal integrated circuit (IC) design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. Designed to handle the most challenging requirements of FinFET process technologies, it delivers industry-leading productivity, performance, and ease-of-use while remaining easy to adopt for users of legacy tools.
PrimeWave Design Environment features a powerful TCL-based scripting capability enabling customization of simulation campaigns including grid-based job distribution and monitoring. PrimeWave Design Environment has a built-in high-capacity waveform viewer that supports advanced visualization and charting capabilities including statistical analysis, histograms, and scatterplots. It also provides HTML-based reporting to facilitate design reviews.

## CMOS Analysis
To know the behaviour of a system we must know the behaviour of the building blocks. The analysis and simulations are done to get the I-V characteristics of both 28nm NMOS and PMOS at the width of 0.1 um. 

#### NMOS and PMOS I-V Characteristics
<img src="https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/MOS_Characteristics/NMOS.png" width=50% height=50%><img src="https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/MOS_Characteristics/PMOS.png" width=50% height=50%>

## Sub-Circuit Components
## Circuit Design
## Simulation

## Performance
## Conclusion
## Author
## Acknowledfements
## Referneces

