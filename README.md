## emonDC

A dual-channel bidirectional internet connected power datalogger and meter for DC applications. With integral DC-DC buck power supply, 12-bit ADC, configurable reference voltage for bidirectional measurement, backup battery powered RTC, local microSD card data-logging, and extensibility through RFM radio module and LCD.

### Project status: prototype release, Summer 2018.

#### Features

- Two channel shunt monitoring via 2 x LMP8481 chips. Each channel with either screw clamps or solder pads for internal/external shunt option.
- Internet connectivity through ESP8266 module, ESP-12S.
- 

# README to be revised..

#####Measurement of direct current (DC).

This is a project description but also a collection of ideas and findings. All thoughts welcome.
The diversity of approaches could be illustrated by these two websites:
https://www.coolcomponents.co.uk/attopilot-voltage-and-current-sense-breakout-180a.html
http://www.victronenergy.com/upload/documents/Datasheet-Battery-monitoring-EN.pdf
My approach won’t be the only way but you’ll get an idea as you read on. Hopefully it makes sense. I welcome any and all feedback and hope for this to be as complete a project in theory before I begin schematic and PCB designs. Hey, I might even be close to making a decision by now… Also, this isn’t intended to claim ownership of the idea, if anyone wants to pick up the pieces and go for it they’re welcome.

emonDC Project
This unit will be a dual  shunt-monitoring device with wireless Tx capabilities. The device will be powered from the DC voltage source it is measuring, or from batteries. Because of potential outdoor applications the form will make possible the use of Waterproof I.P. rated boxes. A metal case matching emonTX style needs looking at also. The unit design will aim primarily at domestic DC applications, for example, solar photovoltaic and wind generation systems with either grid-tie inverters or battery systems.
Safety needs consideration in different ways. Firstly, short circuit protection needs to exist at different levels of the hardware design to avoid inadvertent damage to the unit, by mal-assembly on part of the manufacturer (PCB) or user (installation). This can be achieved with adding particular components, such as fuses and backup series resistors, in the event of a short. The layout of the components will factor in safety also.
Secondly, protection of connected devices and users from floating ground voltages in certain applications. This can be achieved with a bright yellow warning label stating ‘disconnect DC system before attaching USB/FTDI’ or ‘check for common ground between this unit and devices to be connected before making connection’ or something similar, pending advice.
Hall-effect DC monitoring ICs are simple and provide a degree of electrical isolation, however, they are inflexible and costly. Shunt monitoring provides much greater flexibility, accuracy and cost-effectiveness.

1. The range of requirements in DC monitoring applications require a flexible approach because of…
a. Unidirectional and bidirectional requirements.
b. Amperage Ranges and associated cable cross sectional areas (CSA). For example, household 100A cables are 25mm2 or 16mm2, whereas wire for headers and breadboard carrying up to about 5A are about 0.9mm2. The target measurement range has significant physical design implications. 
c. Different cable/wire CSAs require terminations suitable to their size and application (screw terminals, bolted bus bars, soldered connections, etc.) there is no single solution.
d. Whole battery systems can be monitored with one shunt or individual cells of the system can require a multi-cell monitoring unit.
e. There are also high humidity, marine and automotive applications.

2. If we consider cable sizes and the range of amperages in terms of a suitable termination, the issues make it difficult to see any one PCB realistically and cost-effectively meeting all requirements.
This possibly leads to the solution of designing several different systems according to the requirements. First suggestions might look like:
emonDC50 – Bidirectional DC monitor with integrated yet replaceable / bypassable shunt, accepting up to 6mm2 cable up to 50A, but with customizable sensitivity down for micro amps.
emonDC500 – Unidirectional shunt monitor with external shunt rated up to 500A.
emonDC500duo – Two unidirectional shunt monitors in parallel for measuring two external shunts rated up to 500A, for battery/generator applications.

3. Another option might be to have a two-part system where Tx functions are separated from shunt monitoring functions in two separate PCBs, connected via RJ11 or ribbon cable. This could lend itself to multi-source monitoring effectively. Several different model of the DC monitoring PCB could be developed for a range of applications. Also, the standalone Tx PCB may lend itself to other emon projects in the future.

4. Given the nature of solar, wind and various DC applications there a requirement for a protected, regulated supply. Protected from over voltage. Regulated, smoothed output for powering the shunt monitor, Arduino and RF chip.

5. Failsafe monitoring... Fuses between the shunt and monitor to protect from short circuit conditions.

6. High-side vs. low-side sensing… This shunt monitor needs to be capable of handling both applications, which means using a shunt monitor IC capable of high-side measurement. The device should ideally handle a large common-mode voltage, say up to 80V, and protection be in place for voltage over the common-mode voltage limit of the chip.

Project Aims
Follow on from previous research.
Create as flexible as possible unit. Aiming primarily at domestic solar and wind applications.
Compare hall-effect type to shunt monitor type DC measuring approaches, particularly in relation to safety, accuracy and flexibility.
Integrate wireless Tx function using RFM69CW.
Explore potential for AC monitoring applications.
To ascertain for certain the viability or necessity of a two part system. Such as Part A: Tx PCB and Part B: DC monitoring shield.
Investigate a calibration routine storing data in EEPROM.
Look at case design.
Look at the energy efficiency of different manufacturing approaches.
Make a unit!

Unit Features
Focusing on the proposed emonDC50…
Single PCB approach.
emonTx functions including RF and Arduino.
DC monitoring chip capable of bidirectional monitoring for 24V wind and solar systems.. common mode voltage capability of 40V ish..
Screw terminal or soldered connections accepting 6mm2.
Replaceable shunt or perhaps a jumper to disconnect the onboard shunt, then through holes for connecting a specified resistor.


Questions…
What’s the relationship to different amperages, cables sizes and suitable cable terminations at the device?
Would a particular amperage range require soldered connection? Do specific applications require soldered connections?
Could the PCB safely handle the required amps? What’s the current carrying capacity of header pins and PCB track?
Can PCB track be used as the shunt?
How does heat dissipate through the PCB and how does this effect the value being monitored? Is a temp sensor required for factoring in temperature drift?

###Licence
- Hardware licensed according to the TAPR Open Hardware Licence v1.0. Documentation free to use and change.
https://www.tapr.org/TAPR_Open_Hardware_License_v1.0.txt
- Software licensed licensed to GNU General Public License v3. Free to use and change.
https://www.gnu.org/licenses/gpl.html


Notes:
In wind and solar applications cable is often sized according to the length of the run from the generator to the batteries, in this instance the installer will have to adapt for the relevant termination.