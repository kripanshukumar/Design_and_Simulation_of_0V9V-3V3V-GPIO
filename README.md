# Design_and_Simulation_of_0.9V-3.3V-GPIO_on_CMOS_28nm_Technology

## Table of Contents
  * [Introduction](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#introduction)
  * [Software](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#software-used)
  * [CMOS Analysis](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#cmos-analysis)
  * [Sub-Circuit Components](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#sub-circuit-components)
  * [Circuit Design](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#circuit-design)
  * [Working](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#working)
  * [Simulation](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#simulation)
  * [Waveforms](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#waveforms)
  * [Conclusion](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#conclusion)
  * [Author](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#author)
  * [Acknowledfements](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#acknowledgements)
  * [Referneces](https://github.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/blob/main/README.md#referneces)

## Introduction
Wether it is a Microcontrollers, FPGAs or some ASIC they all have one thing in common and tha is GPIO. GPIO stands for General Purpose Input Output. As the name suggest it can be used as both input and output depending on the state of control signals. GPIO is usually a subpart of a large system, primarily used for getting data from physical word or external devices or giving command to external devices. This repository is offers a GPIO design which works on 0.9V core and 3.3 I/O logic level. All the communication or control signal logic is base on 0.9V design and the I/O functionality of GPIO operates at 3.3V logic.

## Software Used
The two major softwares without which this project was impossible are Synopsys Custom Compiler and Synopsys Primewave. A huge thanks to the Synposys India and IIT Hyderabad for providing the access to these elite softwares.

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Synopsys/setup%20screen.png" width=54% height=54%> <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Synopsys/Home%20page.png" width=44% height=54%><p align="center">Fig 1.(a) Synopsys Custom Compiler</p>


* **Custom Compiler™**
 is a fresh, modern solution for full-custom analog, custom digital, and mixed-signal integrated circuit (IC) design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. Designed to handle the most challenging requirements of FinFET process technologies, it delivers industry-leading productivity, performance, and ease-of-use while remaining easy to adopt for users of legacy tools.

* **PrimeWave Design Environment** features a powerful TCL-based scripting capability enabling customization of simulation campaigns including grid-based job distribution and monitoring. PrimeWave Design Environment has a built-in high-capacity waveform viewer that supports advanced visualization and charting capabilities including statistical analysis, histograms, and scatterplots. It also provides HTML-based reporting to facilitate design reviews.

## CMOS Analysis
To know the behaviour of a system we must know the behaviour of the building blocks. The analysis and simulations are done to get the I-V characteristics of both 28nm NMOS and PMOS at the width of 0.1 um. 

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/MOS_Characteristics/NMOS.png" width=50% height=50%><img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/MOS_Characteristics/PMOS.png" width=50% height=50%>
<p align="center">Fig 2.(a) NMOS and PMOS I-V Characteristics</p>

## Sub-Circuit Components
The list and breif descriptio of sub-circuit components used in this build are as follows:
#### CMOS Inverter/ NOT gate:
This is the first and the very basic building block of the system. The output of the CMOS inverter is balanced by making the width of PMOS double the width of NMOS. The push-pull current capacity of this CMOS inverter is 30uA and the operating voltage is 0.9V. The circuit design and Voltage transfer characteristics of inverter are as follows:

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NOT/NOT_Schematic.png" width=41% height=41%>      <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NOT/VTC.png" width=58% height=58%><p align="center">Fig 3.(a) Inverter Schematic and VTC curve</p>

#### NOR gate:
Like any simple CMOS based nor gate this gate is made using two PMOS in series on HIGH side and two NMOS in parallel in low side. To cover the work case scenario when the output is to be pulled high, as the two PMOS resistance add up, so the width of PMOS taken is double the width of PMOS in balanced CMOS ciruit.

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NOR/Schematics.png" width=42% height=42%>      <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NOR/Waveform.png" width=56% height=56%>
<p align="center">Fig 3.(b) NOR gate and waveform</p>

#### NAND gate:
Unlike NOR in NAND we have two PMOS in parallel in HIGH side and two NMOS in serier in LOW side. In worst case scenario when the output is to be pulled low, due to series connection of NMOS the resistance adds up so to compensate this the NMOS width shoud be double of the NMOS width of a standard CMOS inverter.

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NAND/schematics.png" width=37% height=37%>  <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/NAND/waveform.png" width=60% height=60%><p align="center">Fig 3.(c) NAND gate and waveform</p>

#### 0.9V to 3.3v Level Shifter:
As the name suggests Level Shifter is used to convert the signal of one logic level to a different logic level, in this case we are converting a 0.9V logic to 3.3V logic. This device is use to convert the input signal of 0.9V to 3.3V so that the CMOS working at 3.3V can be operated properly.
<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Level_Shifter/Schematic.png" width=55% height=55%> <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Level_Shifter/Waveform.png" width=42% height=42%> 
<p align="center">Fig 3.(d) Schmitt Trigger </p>

#### Schmitt Trigger:
Schmitt Trigger plays an important role in converting the 3.3V signal arriving at the I/0 port into the 0.9V logic level which can be transmitter further. Schmitt Trigger has two important voltage threshold Vth+ and Vth-. When the input signal in above Vth+ the Schmitt Trigger outputs logic high and when the input signal is below Vth- the Schmitt Trigger outputs logic low. If the signal is between Vth+ and Vth- then the output of Schmitt Trigger does not change its state.

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Schmitt_Trigger/schematics.png" width=47% height=55%> <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Schmitt_Trigger/Waveform.png" width=50% height=50%><p align="center">Fig 3.(e) Level Shifter Schematic and Output</p> 

#### MOSFET Driver:

One of the most curcial sub circuit of the GPIO is MOSFET driver. This drive takes two input namely "EN" and "DATA IN". "EN" stands for enable and when this pin is high the output of the CMOS driven by this driver is either low or high depending on the data input value. If the EN pin is LOW then both PMOS and NMOS of CMOS are inactive this allow other circuitary to perform operations on the I/O port. Last but not the least, this drive has the feature of dead time in between the transistion from low to high. The dead time for between OUTPUT HIGH and OUTPUT LOW while going from  high to low is 5ns and 10ns while going from low to high.

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Driver/Schematics.png" width=54% height=54%> <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Driver/waveform.png" width=44% height=44%> 
<p align="center">Fig 3.(f) MOSFET Driver Circuit and Output</p>
<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Driver/ON%20DEAD%20TIME.png" width=49% height=49%> <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/Driver/OFF%20DEAD%20TIME.png" width=49% height=49%><p align="center">Fig 3.(g) Dead time betwen LOW to HIGH and HIGH to LOW transition</p>

#### Gates constructed using above components:
* OR GATE

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/OR/Schematics.png" width=100% height=100%><p align="center">Fig 3.(h) OR Gate Schematic</p>p>      
     
* AND GATE

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/Sub_Circuits/AND/Schematics.png" width=100% height=100%><p align="center">Fig 3.(h) AND Gate Schematic</p>p>  

## Circuit Design

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/GPIO/Schematics.png" width=100% height=100%>
<p align="center">Fig 4(a). GPIO Schematic</p>

The above figure represent the schematic of GPIO. The GPIO mainly consists of three section namely INPUT, OUTPUT, and INPUT PULL UP/DOWN. The ESD diodes are special arrangement of NMOS and the drop of ESP diode is nearly around 0.7V. The control signals are:

* PU_PU_EN-----------------Enable Pull Up/Pull Down
* INPUT_EN-----------------Enable data at INPUT port
* OUTPUT_EN---------------Enable Output 

The data pins are:

* PUD-------------------------Pull Up/Down state
* DIGITAL_OUT---------------Output data
* INPUT-----------------------Input port for 0.9V   
* PAD-------------------------PAD is the I/O connection point

## Working

The whole circuit of GPIO is divided into three blocks which are INPUT PULL UP/DOWN, INPUT, and OUTPUT. The working of these three blocks are explains below:

### INPUT PULL UP/DOWN
A 10 K Ohm resistor is attached to the output pad which is driven by the output of complementary MOSFETS M14 and M13. As the output port can be used for other purposes the circuit is made to allow the CMOS output to go into any three states which are PULL UP, PULL DOWN, and HIGH IMPEDANCE. In PULL UP mode the 10 K resistance is connected to 3.3V through M14 and in PULL DOWN mode the same resistor is connected to VSS or 0V through M13. Talking about HIGH IMPEDANCE state, it is acheived by turning both the PMOS(M14) and NMOS(M13) OFF supplying 3.3.3V to PMOS and 0V to NMOS. In this mode other other sub-circuits of GPIO can take control of the output port. As the MOSFETS operate at 3.3V running then with 0.9V logic won't be of any use, so the 0.9V is converted in 3.3V logic using the *"Level Shifter"*. The logic of applied on the gates of PMOS and NMOS are as follows:

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/GPIO/PUPD/PMOS%20Truth%20Table.png" align="justify" width=25% height=25%> <img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/GPIO/PUPD/NMOST%20Truth%20Table.png" align="justify" width=25% height=25%>



### INPUT

INPUT is enabled or disable by the INPUT_EN (logic high) pin. This sub-circuit of the GPIO consist of one AND gate and a Schmitt Trigger. Here the Schmitt Trigger get whatever is on the I/O port and is between 3.3V to 0V, it then converts the signal to 0.9V logic. Schmitt Trigger is used because it rejects a band of voltage range which migh otherwise had changed the output.

### OUTPUT

Going with the flow OUTPUT is enable or disable by the OUTPUT_EN (active high) control signal. The circuit at GPIO level consists of CMOS with high current capability and a MOSFET driver to drive the Gate of these MOSFETS. The drive inbuilt RC based dead time circuit. As the MOSFETS driven by this driver work in mA range the current spike during transition from low to high may affect the circuit performance. To eliminate this the PMOS it turned 5ns after the NMOS is turned off and when swithcing from HIGH to LOW the PMOS is turned OFF 10ns before the NMOS turns on.

## Simulation
<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/GPIO/Simulation/SIMULATION.png" align="justify" width=100% height=100%><p align="center">Fig 6(a). Simulation Circuit</p>
To provide different combination of control signal, output data and PU/PD states we are using the pulse generator from the analogLib. All the pulse sources are operating on 50% duty cycle. To generate analog signal at the output PAD a sine wave source is connected with the PAD by the means of 1M Ohm, this big resistance allow us to simulate all I/O features at same time. The description of timeperiod and frequency of different pulses are as follows:

> INPUT_EN------------------4000ns | 250Khz (Square Wave)

> OUTPUT_EN----------------2000ns | 500Khz (Square Wave)

> PU_PD_EN------------------2000ns | 500Khz (Square Wave)

> DIGITAL_OUT---------------0066ns | 15.1Mhz (Square Wave)

> PUD-------------------------0176ns | 5.68Mhz (Square Wave)

> EXTENAL_INPUT------------0500ns | 2.00Mhz (Sine Wave)

### Waveforms
<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/GPIO/Simulation/Waveform.png" align="justify" width=100% height=100%><p align="center">Fig 6(b). ALL MODES</p>

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/GPIO/Simulation/INPUT%20MODE.png" align="justify" width=100% height=100%><p align="center">Fig 6(c). INPUT MODE</p>

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/GPIO/Simulation/INPUT%20PU_PD%20MODE.png" align="justify" width=100% height=100%><p align="center">Fig 6(d). INPUT PULL UP/PULL DOWN MODE</p>

<img src="https://raw.githubusercontent.com/kripanshukumar/Design_and_Simulation_of_0.9V-3.3V-GPIO_based_on_CMOS_28nm_Technology/main/GPIO/Simulation/OUTPUT%20MODE.png" align="justify" width=100% height=100%><p align="center">Fig 6(e). OUTPUT MODE</p>

## Conclusion
This repository presents the design and simulation of 0.9V-3.3V GPIO on 28nm technology node and offers reference for basic GPIO designing. Future works can include addition of INTERRUPT, ANALOG INPUT and PIN CAPTURE.
## Author
Kripanshu Kumar, B.Eng(ECE), Punjab University, Chandigarh

## Acknowledgements

- [Kunal Ghosh, Co-founder, VSD Corp. Pvt Ltd.](https://www.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3B0xcWjpLDThSEo6S9UPO9Tw%3D%3D)
- Chinmay Panda, IIT Hyderabad
- [Synopsis Team/Company](synopsys.com/company/contact-synopsys/office-locations/india/about-synopsys-india.html)
- [IIT Hyderabad](https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/)
- Active and vibrant hackathon community

## Referneces
1 GPIO DESIGN, LAYOUT, SIMULATION AND ESD CLAMP PLACEMENT CALCULATOR by Shiju Abraham.

2 STM32 microcontroller GPIO configuration for hardware settings and low-power consumption.

3 Design and Implementation of General-Purpose Input Output (GPIO) Protocol Bhavnil Patel, Bhargav TarparaP.
