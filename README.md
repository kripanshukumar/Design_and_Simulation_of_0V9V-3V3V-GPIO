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
<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/MOS_Characteristics/NMOS.png" width=50% height=50%><img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/MOS_Characteristics/PMOS.png" width=50% height=50%>

## Sub-Circuit Components
The list and breif descriptio of sub-circuit components used in this build are as follows:
#### CMOS Inverter/ NOT gate:
This is the first and the very basic building block of the system. The output of the CMOS inverter is balanced by making the width of PMOS double the width of NMOS. The push-pull current capacity of this CMOS inverter is 30uA and the operating voltage is 0.9V. The circuit design and Voltage transfer characteristics of inverter are as follows:

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NOT/NOT_Schematic.png" width=38% height=38%>      <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NOT/VTC.png" width=54% height=54%>

#### NOR gate:
Like any simple CMOS based nor gate this gate is made using two PMOS in series on HIGH side and two NMOS in parallel in low side. To cover the work case scenario when the output is to be pulled high, as the two PMOS resistance add up, so the width of PMOS taken is double the width of PMOS in balanced CMOS ciruit.

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NOR/Schematics.png" width=40% height=40%>      <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NOR/Waveform.png" width=53% height=53%>

#### NAND gate:
Unlike NOR in NAND we have two PMOS in parallel in HIGH side and two NMOS in serier in LOW side. In worst case scenario when the output is to be pulled low, due to series connection of NMOS the resistance adds up so to compensate this the NMOS width shoud be double of the NMOS width of a standard CMOS inverter.

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NAND/schematics.png" width=37% height=37%>  <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NAND/waveform.png" width=60% height=60%>

#### 0.9V to 3.3v Level Shifter:
As the name suggests Level Shifter is used to convert the signal of one logic level to a different logic level, in this case we are converting a 0.9V logic to 3.3V logic. This device is use to convert the input signal of 0.9V to 3.3V so that the CMOS working at 3.3V can be operated properly.
<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Level_Shifter/Schematic.png" width=55% height=55%> <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Level_Shifter/Waveform.png" width=42% height=42%> 

#### Schmitt Trigger:
Schmitt Trigger plays an important role in converting the 3.3V signal arriving at the I/0 port into the 0.9V logic level which can be transmitter further. Schmitt Trigger has two important voltage threshold Vth+ and Vth-. When the input signal in above Vth+ the Schmitt Trigger outputs logic high and when the input signal is below Vth- the Schmitt Trigger outputs logic low. If the signal is between Vth+ and Vth- then the output of Schmitt Trigger does not change its state.

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Schmitt_Trigger/schematics.png" width=47% height=55%> <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Schmitt_Trigger/Waveform.png" width=50% height=50%> 

#### MOSFET Driver:

One of the most curcial sub circuit of the GPIO is MOSFET driver. This drive takes two input namely "EN" and "DATA IN". "EN" stands for enable and when this pin is high the output of the CMOS driven by this driver is either low or high depending on the data input value. If the EN pin is LOW then both PMOS and NMOS of CMOS are inactive this allow other circuitary to perform operations on the I/O port. Last but not the least, this drive has the feature of dead time in between the transistion from low to high. The dead time for between OUTPUT HIGH and OUTPUT LOW while going from  high to low is 5ns and 10ns while going from low to high.

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Driver/Schematics.png" width=54% height=54%> <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Driver/waveform.png" width=44% height=44%> 
<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Driver/ON%20DEAD%20TIME.png" width=49% height=49%> <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Driver/OFF%20DEAD%20TIME.png" width=49% height=49%> 

#### Components constructed using above components:
* OR GATE

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/OR/Schematics.png" width=55% height=55%>      
     
* AND GATE

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/AND/Schematics.png" width=53% height=53%>




## Circuit Design
## Simulation

## Performance
## Conclusion
## Author
## Acknowledfements
## Referneces

