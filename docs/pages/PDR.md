---
layout: post
title: PDR
date: 2016-11-14 12:43:44 +0000
permalink: /PDR/
---

**This document still needs EXTENSIVE edits to be markdown presentable.**


![Mercer Engineering](https://github.com/BenKasson1/DocumentationAg2/blob/master/docs/assets/images/MercerEGR.jpg?raw=true")


Agricultural Multi-Sensor Nodal Network with Mesh Network Wireless Communication Topology


Client: T. Anthony Choi


PDR Document 


Presented by: 
Daniel Mackowski
Faisal Al-dhorgham
Pierre Balinda 


November 14th, 2016


Executive summary
Ideally, farmers would be able to survey their crops adequately for a low price. However, current satellite surveying methods widely used by farmers are very expensive. To provide a more cost efficient option, Dr. Anthony Choi of the Mercer University School of Engineering (MUSE) has contacted a team of MUSE students to design a multi-sensor nodal network to collect data on soil temperature along with soil moisture and pH levels. The platforms will send this information through a mesh network to the user who will then be able to make informed decisions to cut farm maintenance costs. The MUSE student engineering team is composed of Pierre Balinda, a Computer Engineer, Faisal Al-dhorgham, and Daniel Mackowski, both Electrical Engineers.

The scope of the project was restricted to a proof of concept stage in light of the complexity of design, time limit, and not having a Mechanical Engineer on the team. Focus was given to determining the best alternatives for a low-power microcontroller, wireless communication protocol chip, soil attribute sensors, user interface for data analysis and presentation, and adequate disposable, per-node power supply. The alternatives that met the feasibility criteria and proved to be the most meritorious alternative were the STM32 L4 microcontroller, ZigBee wireless communication protocol chip, Arduino’s Soil Moisture Sensor Hygrometer, SparkFun Electronics’ DS18B20 Waterproof Temperature Sensor, Luster Leaf’s Digital Soil pH Meter, a Web interface for data analysis and presentation, and 3 disposable AA alkaline batteries for a per-node power supply.

Based on the research on the alternatives, the total cost of this stage of the project is expected to be $350. MUSE will cover $300 of this budget. The client is willing to cover any remainder beyond the limit provided by MUSE. The team plans to perform tests to determine sensor reading accuracy, proper transmission of the data through the ZigBee wireless transmission protocol, and proper analysis and display of the data at the user interface. If the client, manager, and technical advisors find these decisions acceptable, the team would like to ask permission to move forward to the build and test phase of this proof of concept project.

&nbsp;

# Table of Contents

## Sections
Executive summary	

- [Table of Contents](#table-of-contents)

- [List of Figures](#list-of-figures)

- [List of Tables](#list-of-tables)

- [Glossary](#glossary)

- [Introduction](#introuction)

- [Project description](#project-description)

- [Feasibility and merit criteria, specs](#feasibility-and-merit-criteria-specs)

	- [Microcontroller](#microcontroller)

	- [Communication protocol chip](#communication-protocol-chip)

	- [Sensors](#sensors)

	- [User interface](#user-interface)

	- [Power supply](#power-supply)

- [Design alternatives](#design-alternatives)

	- [Microcontroller](#microcontroller)

	- [Communication protocol](#communication-protocol)

	- [Sensors](#sensors)

	- [User interface](#user-interface)

- [Evaluation, selection, and criteria](#evaluation-selection-and-criteria)

	- Microcontroller

	- Communication protocol

	- Sensors

	- User interface

- [Design work accomplished](#design-work-accomplished)

- [Engineering design & analysis](#engineering-design-&-analysis)

- [Determining the power supply](#determining-the-power-supply)

- [Performance prediction](#performance-prediction)

- [Project schedule](#project-schedule)

- [Budget](#budget)

- [Proposed tests](#proposed-tests)

- [Conclusion and Recommendation](#conclusion-and-recommendation)

- [Acknowledgment](#acknowledgment)

- [References](#references)

- [Appendices and annexes](#appendices-and-annexes)

- [Pseudo-code](#psuedo-code)

- [Gantt chart](#gantt-chart)

- [Bill of materials](#bill-of-materials)

- [Team Resumes](#team-resumes)

&nbsp;

## List of Figures
**Figure 1:** STM32 L4 microcontroller
14

**Figure 2:** Raspberry Pi 3 Model B
14

**Figure 3:** Microchip Technology MRF24J40MAT-I/RM ZigBee transceiver
15

**Figure 4:** Arduino Soil Moisture Sensor Hygrometer
16

**Figure 5:** Sparkfun Electronics’ “DS18B20 Waterproof Temperature Sensor”
17

**Figure 6:** Luster Leaf’s “Digital Soil pH Meter”
18

**Figure 7:** Sensor node component general locations
19

**Figure 8:** Project test site layout
20

&nbsp;

## List of Tables
**Table 1:** Microcontroller features
10

**Table 2:** Microcontroller feasibility analysis
13

**Table 3:** Microcontroller merit analysis
13

**Table 4:** Communication protocol feasibility analysis
15

**Table 5:** Communication protocol merit analysis
16

**Table 6:** Sensor node average current consumption calculations for one hour
22

**Table 7:** Typical alkaline battery life calculation values
22

**Table 8:** Bill of Materials
24

&nbsp;

## Glossary
**µC:** Microcontroller

**1WTSSSP:** Tempsensing.com’s “1-Wire Temperature Sensor with 1.2 inch Stainless Steel Probe”

**A&P app:** Analysis & Presentation application

**Arduino Hygrometer:** Arduino Soil Moisture Sensor Hygrometer

**DS18B20:** Sparkfun Electronics’ “DS18B20 Waterproof Temperature Sensor”

**IC:** Integrated Circuit

**Luster Leaf:** Luster Leaf’s “Digital Soil pH Meter”

**Mega:** Arduino Mega

**MUSE:** Mercer University School of Engineering

**OS:** Operating System

**Pi:** Raspberry Pi 3 Model B

**SFESMS:** SparkFun Electronics’ “Soil Moisture Sensor”

**TCO:**  Technical Communications

&nbsp;

# Introduction

Ideally, as the world population continues to grow past 7.4 billion, farmers all over the world would be able to keep up with the demand for more, high quality food at affordable prices. However, with the demand steadily increasing, farmers are turning to engineers and scientists for new methods and technologies capable of reducing costs and optimizing crop yield. One of the methods farmers are looking to use to increase the affordability and availability of their produce is by employing technology to ensure soil conditions are optimized for their crops in near real time. Dr. Anthony Choi of MUSE has contacted the MUSE student engineering team composed of Pierre Balinda, a Computer Engineer, Faisal Al-dhorgham, and Daniel Mackowski, both Electrical Engineers, to design a solution to this problem. The team has designed a proof of concept agricultural multi-sensor nodal network to survey and present collected data to farmers to advise them on how to optimize their land for maximum yield at minimum cost.

As the growing demand for affordable produce is nothing new to the agriculture industry, the team conducted research about similar projects on the market or currently in development and found four major smart garden sensors of interest. According to [1], they are the Edyn Garden Sensor, Koubachi Wi-Fi Plant Sensor, Parrot Flower Power, and Oso Technologies Plant Link. Each smart sensor has a plant database that allows them to give proper recommendations to the user about their specific plant’s needs. The team used these devices as models to kickstart the design process.
The Oso Technologies PlantLink costs $80, senses soil moisture, has 50,000 plants in its database, uses a Zigbee signal to transmit data and 2 AAA batteries to power it for over a year. It only has a web interface for the user. The Parrot Flower Power costs $60, senses soil moisture, temperature, sunlight, fertilizer and pesticide levels. It has 7000 plants in its database, uses a Bluetooth signal to transmit data and 1 AAA battery to power for 6 months. The Parrot only has an iOS app in as a user interface.

The Koubachi Wi-Fi Plant Sensor costs $100, senses soil moisture, temperature, and sunlight. It has 800 plants in its database. This sensor uses Wi-Fi to transmit its data and 2 AA batteries that can power it for over a year. The Koubachi sensor offers ample choices to its users when it comes to interfaces as it has an iOS, Android, and Web applications. The Edyn Garden Sensor costs $100, senses soil moisture, temperature, light, fertilizer, pesticide, and humidity levels. It has 5000 plants in its database, uses Wi-Fi to transmit data and a solar powered battery that can last 2.5 years. The Edyn sensor has an iOS and Android app that the user can use as an interface.

## Project description

This project requires the design and construction of low-power, agricultural sensor nodes capable of mesh network communication and a software system to analyze and present the data collected from the sensors. The sensors will be selected according to the client’s specifications to measure three required soil attributes of moisture level, temperature, and pH level at three equally separated depths. The nodes will be stationary columns, two feet in length, designed to be driven into the ground. The microcontroller, wireless communicator, and the power supply will be the only above ground, surface level components of each node. The nodes will have housing to protect the circuitry of the sensors, microcontroller, wireless communicator, and power supply from damage. The nodes will be battery powered and will communicate information wirelessly from node to node to transmit soil attribute data packets back to a central station that will run the analysis software. The soil attribute data packets will be created by software in the node microcontrollers and will contain the environmental data along with the location, depth, and, time of the reading from each node. The software will collect these packets to construct graphical views of the data. This will provide the end user with a clear understanding of the data to expedite decision making for maintenance of networked regions. The pseudo code for the sensor node and A&P app software can be seen in Appendix A.

## Feasibility and merit criteria, specs

The client gave the following set of specifications for the proof of concept design of the networked nodes:

* **Microcontroller:** low-power
* **Minimum number of nodes:** 3
* **Minimum number of sensor levels:** 3
* **Minimum power supply duration:** one season (six months or 180 days)
* **Minimum node depth:** 2 feet
* **Node data:**
  * Depth
  * Location
  * Time
* **Soil data:** 
  * Moisture level
  * pH level
  * Temperature
* **Wireless communication protocol:** mesh network capable 

The team decided that the following additional specifications were necessary to make engineering decisions for the proof of concept design:
Node spacing: 10m - 40m (33 ft - 130 ft)
Reading frequency: once per hour
The network needed a central station to collect the data from the other nodes and an A&P application for presenting the data to the end user in a clear and concise manner. The central station that will contain A&P application would need to communicate through a wifi communication protocol. The A&P app would need to present the collected information with daily line charts for data from each node and with separate current time graphic displays for each soil data type for the networked area to show the data values on a gradient scale at each of the 3 depths.
The team and the client discussed the scope of the project and realized the need of a mechanical engineer to create an adequately designed final product. The client decided that a proof of concept design would be sufficient for the time allowed. In light of this, more focus was given to the electrical and computer components of the project over the mechanical component. Design decisions for this stage of the project were focused on which microcontroller, wireless communication protocol, sensors, user interface, and power supply would be used. The sections to follow will cover the criteria used to determine feasibility and merit criteria for these components.
Microcontroller
Feasibility Criteria
The following criteria are factors which must be satisfied by the chosen processor:
Current consumption is less than 500 µA/MHz
Has sleep mode functionality
Merit Criteria
Out of the feasible options, low current consumption was the most important metric in determining the best low-power alternative. Better scores in Active mode current consumption per million clock cycles (µA/MHz) and Sleep mode current consumption (nA) would be given to lower consumption values.
Communication protocol chip
Feasibility Criteria
The following criteria are factors which must be satisfied by the chosen communication protocol chip:
10 meters minimum range of transmission and reception
Transmit and receive wirelessly
Operate on a low power mode
Communicate using mesh network topology
Merit Criteria
Out of the feasible options, large communication range and number of connections along with low cost and power consumption were the most important metrics in determining the best low-power alternative. The cheaper unit cost of the wireless communication chip, the better it would be. Longer maximum communication range was considered better. The same goes for maximum node connection. Low power consumption was considered in battery life in days if the communication chip was powered alone. The more days the chip could last under battery power, the better the chip would be.
Sensors
Feasibility Criteria
The following criteria are factors which must be satisfied by the chosen sensors:
Function in soil for a season 
Unit cost is less than $15
Interface with chosen microcontroller
Analog output (soil moisture sensor)
Waterproof (soil temperature sensor)
Merit Criteria
Out of the feasible options, low cost was considered an important metric for all three sensor types. The cheaper unit cost of the sensor, the better it would be. The soil temperature sensor would need to provide accurate readings over a range of temperatures that soil in growing regions could be at throughout a season. That preferred range was -15℃  to +45℃ (-5℉ to +113℉). The more of that range the sensor was designed to accurately output, the greater its merit would be.
User interface
Feasibility Criteria
The following criteria are factors which must be satisfied by the chosen user interface:
Expertise: team possesses skill set to properly develop the interface
Portability: the interface can be accessed by all popular OSs
Merit Criteria
Out of the feasible options, ease of use was considered an important metric. Ease of use refers to simplicity of accessing the A&P application and intuitive navigation within the A&P application.
Power supply
Feasibility Criteria
The following criteria are factors which must be satisfied by the chosen power supply:
Disposable battery 
Last at least one season
Minimum supply voltage of 5V
Merit Criteria
	The power supply criterion to provide a battery source that lasts for at least a season led to using reverse engineering to calculate the power the total circuit would require for a season once all other components were selected. The most suitable type of battery available would supply adequate power for the whole system for at least one season and be no less than 5V.
Design alternatives
The sections to follow will cover the design alternatives for the microcontroller, wireless communication protocol, sensors, and user interface.

Microcontroller
  
**Table 1: Microcontroller features**
  
|                                  | Pi[2]                            | Mega[3]           | Ambiq Micro[4]                | STM32 L4[5]                  | EFM32[6]                     | Atmel[7]                     |
|----------------------------------|----------------------------------|-------------------|-------------------------------|------------------------------|------------------------------|------------------------------|
| Active mode consumption (µA/MHz) | 400 x 103<sup>3</sup> (constant) | 500               | 35                            | 100                          | 219                          | 35                           |
| Sleep mode consumption (nA)      | n/a                              | n/a               | 143                           | 200                          | 1.1 x 10<sup>6</sup>         | 900                          |
| Processor                        | ARM Cortex-A53(1.2GHz)           | ATmega1280(16MHz) | 32-bit ARM Cortex-M4F (24MHz) | 32-bit ARM Cortex-M4 (80MHz) | 32-bit ARM Cortex-M3 (48MHz) | 32-bit ARM Cortex-M3 (48MHz) |
| Wi-Fi                            | Yes                              | No                | No                            | No                           | No                           | No                           |
| Bluetooth                        | Yes                              | No                | No                            | No                           | No                           | No                           |

&nbsp;

Six microcontrollers were considered as potential alternatives. The Mega, Pi, Ambiq Micro, STM32 L4, EFM32, and Atmel were considered as shown in Table 1. Active mode is the state in which the microcontroller runs its programs and ends by putting the microcontroller to sleep. Active mode consumption feature refers to the current (µA) required to go through 1 million clock cycles (1MHz). Sleep mode is a timed state in which all processes are shut off except for the timer that will “wake-up” the microcontroller once the sleep time has elapsed. Sleep mode consumption refers to the current (nA) required to keep the microcontroller on without executing any other instructions. Processor refers to the architecture used by the microcontroller. Wi-Fi and Bluetooth refer to the  available transmission protocols embedded in the microcontroller.
Communication protocol
Several protocols currently exist for wireless network communication, including ZigBee, WiFi, and Bluetooth. The IEEE 802.15.4 standard for low data rate wireless personal area networks , which will be used in this project, was completed in 2003 and was most recently updated in 2015 and will be followed by any wireless communication protocol selected for this project[8].
The ZigBee protocol of wireless communication is a fairly new protocol for wireless sensor and control network applications. It has a low data rate maximum of 250 kbps, which makes it an excellent choice for monitor and control type applications[8]. The ZigBee protocol was designed to consume very little power, allowing it to operate for months or even years without replacing its battery. It also can transmit and receive at a maximum range of 75 meters. A single ZigBee connected network can support up to 65 thousand nodes capable of being connected in a mesh network[9]. ZigBee also has a self-healing network feature that can allow the network to continue to function by finding a new route around the downed node[10].
In addition, ZigBee can automatically establish its network. ZigBee uses offset quadrature phase shift keying modulation (OQPSKM). This modulation scheme doubles the data rate while maintaining the same bandwidth by encoding two bits per symbol compared to other modulation schemes.  ZigBee only takes about a millisecond to transmit and receive data packets which is a good speed for its small packet size[11]. 
Wi-Fi, an abbreviated term that stands for wireless fidelity, is usually used for applications that use computer to computer communication, which is a good substitution for cabled network as it operates using radio frequency waves to provide network connectivity. One of its main advantage is its high data rate, but this higher data rate does consume more power. Also, Wi-Fi needs routers for data transmission, which can bottleneck mesh network topology[8].
Bluetooth low energy is another good communication choice that can work on a very low power to extend battery life. However, Bluetooth is not designed for mesh network applications. It is a master-slave method of communication where the main source can connect up to 8 cell nodes, but the cell nodes themselves cannot connect to each other. Researchers such as the Bluetooth Special Interest Group have been working to add mesh network feature to the Bluetooth communication protocol[12].
Sensors
Three options were selected as potential soil moisture sensors for this project. The Arduino Hygrometer (Part number: FC-28-D) comes in two pieces as an IC and a sensor. It has an operating voltage of 3.3 or 5 VDC, an output voltage of 0 ~ 4.2VDC, an Immersion Gold finish for corrosion protection, dimensions of 60x20x5mm and 90x58x8mm for it’s IC and sensor, respectively, and weighs 11 g[13]. The SFESMS (Part number: SEN-13322) comes as one piece. It has an operating voltage of 5 VDC, an Electronless Nickel Immersion Gold finish for corrosion protection, and a 3 pin interface[14]. DFRobot’s “Capacitive Soil Moisture Sensor” (Part number: SEN0193) comes as one piece. It has an operating voltage of 3.3 ~ 5.5 VDC, an output voltage of 0 ~ 3.0VDC, a corrosion resistant coating, a Gravity PH2.0-3 pin interface, circuit board area of 98x23mm, and weighs 15 g[15].
Two options were selected as potential soil temperature sensors for this project. The DS18B20 (Part number: SEN-11050) uses a DS18B20 digital thermometer which is accurate to ±0.5℃  in the -10℃ to +85℃ range[16]. The 1WTSSSP (Part number: 1WT_6SSP_1_30cm_2w) also uses a DS18B20 digital thermometer but is designed to operate in the -40℃ to +105℃ range[17].
Two options were selected as potential soil pH sensors for this project. DFRobot’s “pH Meter” (Part number: SEN0161) comes as two pieces as an IC and a sensor probe. It has an operating voltage of 5 VDC, an output voltage of 0 - 14 pH with an accuracy of ±0.1 pH at 25℃, an Immersion Gold finish for corrosion protection, circuit board area of 43x32mm, and a BNC sensor-IC interface and a Gravity PH2.0-3 pin IC-µC interface[18]. It is designed for use liquid solutions. The Luster Leaf is designed for testing soil pH, though little else is known about its specs as it was designed as a standalone pH tester[19]. 
User interface
Three different user interfaces were selected for this project. These interfaces will give the end user a visual representation of all the data collected. The team considered an Android app, iOS app, and a Web interface. 
Evaluation, selection, and criteria
The sections to follow will cover the feasibility and merit analysis for the following components: microcontroller, wireless communication protocol, sensors, and user interface.
Microcontroller
As per the client’s specifications, a sensor node should operate for a season without having to replace the batteries. To comply with this specification, the team set 500uA/MHz as a power consumption threshold. The microcontroller should also have a sleep-mode for a longer battery life. Sleep mode will significantly reduce the microcontroller’s power consumption. 
shows the Mega and the Pi were the only two microcontrollers to not pass the feasibility criteria. 

&nbsp;

**Table 2: Microcontroller feasibility analysis**
  
|                                    | Pi[2] | Mega[3] | Ambiq Micro[4] | STM32 L4[5] | EFM32[6] | Amtel[7] |
|------------------------------------|-------|---------|----------------|-------------|----------|----------|
| Consumption (less than 500 µA/MHz) | No    | No      | Yes            | Yes         | Yes      | Yes      |
| Sleep Mode                         | No    | No      | Yes            | Yes         | Yes      | Yes      |

&nbsp;

**Table 3: Microcontroller merit analysis**
  
|                                  | Ambiq Micro[4] | STM32 L4[5] | EFM32[6]             | Atmel[7] |
|----------------------------------|----------------|-------------|----------------------|----------|
| Active mode consumption (µA/MHz) | 35             | 100         | 219                  | 35       |
| Sleep mode consumption (nA)      | 143            | 120         | 1.1 x 10<sup>6</sup> | 900      |

&nbsp;

The feasible options were then judged based on the merit criteria. The design of the software will have the microcontroller in sleep mode for a substantially larger amount of time than it will have it in active mode. This means that a low sleep mode current consumption value is more important than a low active mode current consumption value. Due to the greater weight of the sleep mode current consumption value, the STM32 L4 microcontroller, shown in Figure 1, was selected, as Table 3 shows it has the lowest sleep mode current consumption and the second lowest active consumption.

Figure 1 STM32 L4 microcontroller[5]
Although the Pi, as shown in Figure 2, was not selected to be the node’s microcontroller, it was selected to be the central station’s microcontroller for its remarkable features. The Pi boast specs that are comparable to those of a personal computer, it has a built-in OS, a 1.2 GHz 64-bit quad-core ARM CPU, 1GB RAM, Wi-Fi (802.11n), Ethernet (802.3), Bluetooth 4.1, and Bluetooth LTE capabilities to name a few. It only needs a power supply and input and output devices[2].

Figure 2 Raspberry Pi 3 Model B[2]
Communication protocol
As per the client’s specifications, the communication protocol had to be capable of wireless, low-power, communication with mesh network topology. The communication protocol also needed to have a transmission range greater than 10 meters to meet the teams additional specifications. Table 4 shows Bluetooth was the only wireless communication protocol to not pass the feasibility criteria, as it currently is not a mesh network capable communication protocol.

&nbsp;

**Table 4 Communication protocol feasibility analysis**
  
|                    | Zigbee   | Wi-Fi     | Bluetooth[12] |
|--------------------|----------|-----------|---------------|
| 10 meter min range | Meets[7] | Meets[10] | Meets         |
| Low power          | Meets[8] | Meets[8]  | Meets         |
| Wireless           | Meets[8] | Meets[8]  | Meets         |
| Mesh network       | Meets[7] | Meets[8]  | Fails         |

&nbsp;

The feasible options were then judged based on the merit criteria. The maximum number of connectable nodes and battery life are more important than the maximum range and unit cost. The later pair was weighted less because both chip options considered have a communication range well beyond 40 meters and have a minimal cost difference. A ZigBee communication protocol chip was selected for this project. An example of which is shown in Figure 3. It was selected because, as shown in Table 5 on the following page, it has the greatest number of connections and the longer battery life.

Figure 3 Microchip Technology MRF24J40MAT-I/RM ZigBee transceiver[25]

 
&nbsp;
 
**Table 5 Communication protocol merit analysis**
  
|                         | Zigbee            | Wi-Fi              |
|-------------------------|-------------------|--------------------|
| Maximum range           | 75m[9]            | 100m[10]           |
| Cost per unit           | $11.00[20]        | $10.50[21]         |
| Maximum node connection | 65k cell nodes[9] | 2007 cell nodes[9] |
| Battery life (days)     | 100-7000[9]       | 0.1-5[9]           |

&nbsp;

Sensors
The Arduino Hygrometer, SFESMS, and DFRobot’s “Capacitive Soil Moisture Sensor” were checked against the feasibility and merit criteria to determine which potential soil moisture sensor would be selected for this project. Each of them met the feasibility criteria for microcontroller interface capability, costing less than $15, in-soil operability, and analog output capability. The Arduino Hygrometer, shown in Figure 4, was selected as the best alternative for a soil moisture sensor, as it had the cheapest price. The prices were $2.75[20], $4.95[21], and $7.90[22], respectively.

Figure 4 Arduino Soil Moisture Sensor Hygrometer[20]
The DS18B20 and the 1WTSSSP were checked against the feasibility and merit criteria to determine which potential soil temperature sensor would be selected for this project. They both met the general feasibility criteria for microcontroller interface capability, costing less than $15, and in-soil operability. The main difference between the two was the housing for the temperature sensor and the ranges they were designed to measure: the former specifically stated to be waterproof and to output on a -10℃ to +85℃ range at a cost of $9.95[16]; the later stainless steel and to output on a -40℃ to +105℃ range at a cost of $11[17]. The DS18B20, shown in Figure 5, was selected as the best alternative due to being $1.05 cheaper than the later and being explicitly waterproof in spite of the fact that it did not contain the entire low end of the desired temperature range. The -15 ℃ on the low end of the desired range was just for a margin in case soil temperatures actually get that low when the sensor is in use. The -10 ℃ (14 ℉) temperature for the low end of the selected alternative is acceptable for soil temperature measuring in agricultural environments.

Figure 5 Sparkfun Electronics’ “DS18B20 Waterproof Temperature Sensor”[16]
DFRobot’s “pH Meter” and the Luster Leaf were checked against the feasibility and merit criteria to determine which potential soil pH sensor would be selected for this project. The former was priced at $29.50 and was not designed for use in soil, though it was designed to interface with a microcontroller[23]. The later was priced at $10.99 and was designed specifically to be used in soil, but was designed as a general consumer product[19]. Despite the fact that both alternatives failed at least one feasibility criterion (microcontroller interface capability, costing less than $15, and in-soil operability), the Luster Leaf’s “Digital Soil pH Meter” was selected as the best alternative for a soil pH sensor because it was the alternative that met the most feasibility criteria. Though the chosen alternative, as shown in Figure 6 on the following page, was not designed to interface with an external microcontroller, the sensor’s circuitry can be taken out of its housing for analysis and modification to allow it to interface with a microcontroller as the project requires.

Figure 6 Luster Leaf’s “Digital Soil pH Meter”[19]
User interface
The team selected three different user interface alternatives for this project. These interfaces will give the end user a visual representation of the collected data. The team considered an Android app, iOS app, and Web interface. The Android and iOS apps are only compatible with their respective OSs, unlike the Web which can be accessed by both OSs as well as Windows and Linux OSs. As for the expertise, Daniel and Pierre have developed Android apps in the past, Pierre has some experience with web applications, and none the team members had experience with iOS apps. As for the ease of use, the team determined that all three interfaces would be easy to use for anyone who is computer literate. The Web interface was chosen as the desired alternative because it was the only truly portable interface and had the greatest ease of use.
Design work accomplished
After the client approved the team’s proposal, the team had a meeting with him to make certain of the requirements and specifications for the project along with the funding options in case the budget for the project went beyond the amount MUSE would cover. The team determined the five main components of the project to be considered in this proof of concept stage. The components are microcontroller, communication protocol, sensors, user interface, and power supply.The team then conducted intensive research to find design alternatives for each component of the project. The team then performed feasibility and merit analysis for each of the five main components of the project. Afterward, the team analyzed each component’s datasheet to make sure that the chosen components would be compatible with one another. The team then determined how the components can be integrated to work as a whole system. A simple visualization of the node below the soil, as seen in in Figure 7, shows the idea of the different depths the sensors will be attached at.Then the team considered what appropriate test plans would be to determine if the system is functioning as intended.

Figure 7 Sensor node component general locations
Figure 8, on the following page, shows a visual representation of the proof of concept design when it is implemented on a test site. The furthest node will have three different sensors at three different levels. The sensors will be secured to a central shaft and be connected to the microcontroller with a ZigBee transceiver secured to the top of the shaft. All three nodes will be placed into holes two feet deep in the soil. After that, the microcontroller will command the ZigBee transceiver to send the sensor data to the second node that is 10 to 40 meters away. The second node will only have the microcontroller and ZigBee acting as a mediator to get the data to the third node. The third node then will then send the data to the central station after receiving it from the second node.

Figure 8 Project test site layout
Ideally, each node would have the same sensor setup as the first node to obtain measurements for multiple locations on the test site. However, as this is a proof of concept project, the team will only attempt to prove the functionality of a fully equipped sensor node. Once the functionality of the project is approved, future teams can strive to turn this project into a product by proving the functionality of the mesh network and designing proper housing for the circuit components to protect the components from the elements and from impact forces from driving the sensor node into the ground.
Field testing of the final integrated system should be done in normal and abnormal atmospheric conditions. Heavy rain, as an example of abnormal atmospheric conditions, will attenuate the signal as rain can have a severe effect on wireless signals.
Engineering design & analysis
The following sections will explain the decision making process behind the selection of a disposable battery based power supply and a performance prediction of the proof of concept design.
Determining the power supply
The decision process to determine the proper power supply for a sensor node underwent reverse engineering instead of feasibility and merit analysis was due to the dependence on what the chosen microcontroller, communication protocol, and sensors would be. Table 6 indicates the average continuous current (mA) consumed for one hour of operation for each component as well as the approximated average continuous current consumption for a fully equipped sensor node. The two other nodes will consume much less current per hour at this proof of concept stage, as they will only have the microcontroller and ZigBee transceiver. Current values for non sourced rows use assumed values for the active and sleep mode currents, and all rows used assumed active and sleep mode times.
Table 6 uses a the following algorithm to determine the average continuous current (mA) required for one hour of operation by a power source in milliamp/hours (mA) at 20℃.
X=(IA*tA+IS*(3600000-tA))/3600000
IA and IS represent the respective active and sleep currents in milliamps (mA) of the chosen circuit components. Their values come from the two left-middle columns of Table 6. tA and 3600000-tA represent the number of milliseconds (ms) the circuit components will be in active and sleep modes per hour, respectively. Their values come from the two right-middle columns of Table 6. The values in the far right column of Table 6 are the result of the using the algorithm on each row. The bottom right cell contains the summation of the results of using the algorithm on each of the above rows of Table 6.

&nbsp;

**Table 6 Sensor node average current consumption calculations for one hour**
  
|                              | Current (mA) |         | Time (ms) |         | Average continuous current consumed for one hour (mA) |
|------------------------------|--------------|---------|-----------|---------|-------------------------------------------------------|
|                              | Active       | Sleep   | Active    | Sleep   |                                                       |
| Moisture sensor (x3)         | 60           | 0.03    | 1         | 3599999 | 0.03001665833                                         |
| Temperature sensor (x3) [20] | 4.5          | 0.003   | 10        | 3599990 | 0.003012491667                                        |
| pH sensor (x3)               | 15           | .03     | 1         | 3599999 | 0.03000415833                                         |
| STM32 L4 microcontroller[3]  | 0.1          | 0.00012 | 15        | 3599985 | 0.0001204161667                                       |
| ZigBee transceiver[13]       | 23           | 0.002   | 1         | 3599999 | 0.002006388333                                        |
| Sensor node total            |              |         |           |         | 0.06516011283                                         |

&nbsp;

**Table 7 Typical alkaline battery life calculation values [24]**
  
| Battery type   | Capacity (mAh) | Typical Drain (mA) |
|----------------|----------------|--------------------|
| D              | 13000          | 200                |
| C              | 6000           | 100                |
| AA             | 2400           | 50                 |
| AAA            | 1000           | 10                 |
| N              | 650            | 10                 |
| 9 Volt         | 500            | 15                 |
| 6 Volt Lantern | 11000          | 300                |
  
  
Knowing the result of Table 6, the team researched battery types to determine which would supply adequate charge for all the components for at least one season at 5V if the temperature remained a constant 20℃. It should be noted that lower drain currents can result in better capacities[24], but the capacity values given in Table 7 will be treated as constant for the purpose of this analysis. It should also be noted that the output voltage of a battery steadily depletes with use  over time. This implies that a 1.5V AA battery would deplete to around 1.25V at half its lifespan and 1V when near full depletion[24].
tlife=CBCD*0.7
Vhalf-life=n*V
tlife represents the approximate amount of time a battery will last in hours. CB and CD represent a particular battery’s capacity (mAh) and the device consumption (mA) for one hour of operation. The factor of 0.7 is to factor in the effect of environmental conditions negatively affecting the ideal result. Vhalf-life represents the voltage supplied by a number of batteries, n, and V represents the voltage supplied by a single battery at its half-life.
Using the results from Table 6, the capacity given for a AA battery in Table 7, and the tlife equation, the lifespan of a battery running a sensor node as designed would be approximately 25783 hours which is nearly six seasons, assuming 4320 hours in a season. Using the Vhalf-life equation would mean that four (4) AA alkaline batteries would reliably power a sensor node for at least three seasons. This oversupply on the power supply lifespan will be used as a defense against the result of temperature variation among other aspects that could result in a quicker loss of charge in the batteries.
Performance prediction
The team is confident in the calculations made and research conducted for the components of the proof of concept design. The good review rates of the components by other purchasers is also promising for the reliability of the components. The team believes that the proof of concept design will run smoothly and efficiently based on these three things.  
Project schedule
A graphical breakdown of this section can be seen in appendix B. Research for and work on the proposal was conducted from August 23, 2016 through September 6, 2016 when the proposal was due. Preliminary design of the project and component research began on September 6, 2016 upon the proposal’s approval and continued until October 10, 2016. During that time, the team worked on the first project report from September 30, 2016 through October 6, 2016 when it was presented. With feedback gathered from the progress report, designs were refined and the budget was adjusted to account for errors in preliminary estimations. The team performed engineering calculations and merit analysis of design alternatives from October 10, 2016 through November 8, 2016. During that time, the team worked on the second project report from November 7, 2016 through October 8, 2016 when it was presented. The team worked on the first draft PDR write-up on November 1, 2016 through November 10, 2016. The team gave the PDR write-up to a TCO team from November 11, 2016 to November 12, 2016. Final edits of the PDR took the feedback from the TCO team into account and went from November 12, 2016 through November 14, 2016, the due date of the PDR document. The team will prepare a presentation on the PDR from November 14, 2016 to November 16, 2016, and give the PDR presentation on November 17, 2016. After the PDR is presented, the team will make changes as the client, advisors, and managers specify. Once accepted, the team will order parts on November 21, 2016 and will expect all parts to arrive by December 9, 2016.


After winter break ends on January 9, 2017, the team plans to begin to build the nodes and write the code. The team expects to be done with the first build by February 24, 2017. The team plans to do the first test phase on, February 27 - 28, 2017. The team plans to assess the results of the first tests and make corrections to the system from March 1 - 6, 2017. The team expects to then perform a second round of testing on March 8 -10, 2017. Afterwards, the team plans to make more corrections based off the results of the second round of testing on March 10 - 13, 2017. The team expects to do a final round of testing and corrections on March 13 - 20, 2017. The project should be in a deliverable state by March 20, 2017.
Budget
Appendix C indicates how many units of each component is required, the unit cost, seller, and the total price of all components necessary to build the project. The team has been informed by the client that they can cover any remainder in the budget above the $300 dollars given by MUSE. The breadboard will be used while figuring out the proper wiring for the sensor node.
Proposed tests
The team will test sensor reading accuracy, accurate data transmission, accurate analysis and presentation of data by the user interface, and the true range between the nodes.
To carry out the above tests, the team will setup the node network as well as the central station at a site provided by the client that mimics the characteristics of a farm. To check for sensor reading accuracy, the team will sample soil data with the sensor node and compare it against the readings made by commercially available pH, soil moisture, and temperature sensors. 
To check for accurate data transmission, the team will send a control packet through the nodal network from the sensor node through the transmission nodes and verify that the packet received at the central station matches the information in the control packet. To check for accurate analysis and presentation of data by the user interface, a control bundle of packets will be read by the A&P application and the display charts and graphs will be analyzed to determine if the presented information matches what the control bundle should show. The team will also test the actual maximum range between nodes by placing a node at the minimum distance away from the central station, conducting the data transmission accuracy test, and then incrementing that distance by one meter until the central station no longer receives the control data packet accurately.
After an initial test under temperate conditions, the team will proceed to create environments similar to the ones at the farms by adding a lot of water to the soil to simulate the results of a heavy rainstorm, ice to simulate the results of a cold snap, and dryness to simulate the summer heat. The entire system will be tested in these environments to ensure proper functionality in different weather conditions and seasons to give a well detailed user guide to the client.
Conclusion and Recommendation
After thorough research on components of the system as well as feasibility and merit evaluation, the team recommends the uses of the following components for individual nodes. An STM32 L4 as the microcontroller, the Luster Leaf as the pH sensor, the DS18B20 as the temperature sensor, the Arduino Hygrometer as the soil moisture sensor, a ZigBee transceiver for the communication protocol, and three AA alkaline batteries as a power supply. As for the user interface and central station, the team recommends a Web interface and a Pi, respectively. The estimated budget for this system is $350 which will be provided by the MUSE and our client, Dr. Choi. With the information provided, the team would like to ask permission to move forward to the build and test phase of this proof of concept project.
Acknowledgment
	The team would like to acknowledge and thank the individuals who contributed to the successful completion of this project:our client, Dr. Anthony Choi; our technical advisors Dr. Donald Ekong, Dr. Kevin Barnett, and Dr. Edward O’Brien; and our manager Dr. Hodges Jenkins. These MUSE faculty members have been instrumental on all aspects of this project throughout this semester. The team would also like to acknowledge Ben Kasson and Carson McGorry who helped edit the PDR document as well as Ryan Alyamani and Ahmed Alshammari for illustration assistance.   
References
[1]
A. Gebhart, "Smart home garden tech buying guide," CNET, 16 September 2015. [Online]. Available: http://www.cnet.com/news/smart-outdoors-buying-guide/. [Accessed 5 September 2016].
[2]
The MagPi Magizine, "RASPBERRY PI 3 IS OUT NOW! SPECS, BENCHMARKS & MORE," The MagPi Magizine, April 2016. [Online]. Available: https://www.raspberrypi.org/magpi/raspberry-pi-3-specs-benchmarks/. [Accessed 11 November 2016].
[3]
Arduino, "Arduino Mega," Arduino, 2016. [Online]. Available: https://www.arduino.cc/en/Main/arduinoBoardMega. [Accessed 11 November 2016].
[4]
Ambiq Micro, "Ultra-Low Power Microcontroller," Ambiq Micro, 2016. [Online]. Available: http://ambiqmicro.com/low-power-microcontroller. [Accessed 11 November 2016].
[5]
Atmel Corporation, "SAM L MCUs," Atmel Corporation, 2016. [Online]. Available: http://www.atmel.com/products/microcontrollers/ARM/SAM-L.aspx. [Accessed 11 November 2016].
[6]
Silicon Laboratories, "EFM32(tm) Giant Gecko 32-bit Microcontroller," Silicon Laboratories, 2016. [Online]. Available: http://www.silabs.com/products/mcu/32-bit/efm32-giant-gecko/pages/efm32-giant-gecko.aspx. [Accessed 11 November 2016].
[7]
STMicroelectronics, "Ultra low power MCUs," STMicroelectronics, 2016. [Online]. Available: http://www.st.com/content/st_com/en/products/microcontrollers/ultra-low-power-mcus.html?querycriteria=productId=SC1544. [Accessed 11 November 2016].
[8]
EngineersGarage, "Zigbee v/s Wi-Fi," EngineersGarage, 2012. [Online]. Available: http://www.engineersgarage.com/contribution/zigbee-vs-wi-fi. [Accessed 3 November 2016].
[9]
A. Elahi and A. Gschwender, "Introduction to the ZigBee Wireless Sensor and Control Network," 2 December 2009. [Online]. Available: http://www.informit.com/articles/article.aspx?p=1409785&seqNum=2. [Accessed 25 November 2016].
[10]
Akiba, "Zigbee Mesh routing - Interactive Tutorial," FreakLabs, Inc, 7 April 2008. [Online]. Available: http://www.freaklabs.org/index.php/blog/zigbee/zigbee-mesh-routing-interactive-tutorial.html. [Accessed 10 October 2016].
[11]
Y. V. Varshney and A. K. Sharma, "Comparative Analysis of OQPSK and MSK Based Zigbee Transceiver Using MATLAB," International Journal of Advanced Research in Computer Science and Software Engineering, vol. III, no. 6, 2013.
[12]
LINK LABS, "ZigBee Vs. Bluetooth: A Use Case With Range Calculations," LINK LABS, 24 August 2015. [Online]. Available: http://www.link-labs.com/zigbee-vs-bluetooth/. [Accessed 20 October 2016].
[13]
Purlance, "FC-28-D Soil Hygrometer Detection Module + Soil Moisture Sensor - Blue," Purlance, 2016. [Online]. Available: http://www.purlance.com/product/product156.html. [Accessed 12 November 2016].
[14]
S. Al-Mutlaq and JOEL_E_B, "Soil Moisture Sensor Hookup Guide," Sparkfun Electronics, 2016. [Online]. Available: https://learn.sparkfun.com/tutorials/soil-moisture-sensor-hookup-guide?_ga=1.57324522.1113423649.1475435594. [Accessed 12 November 2016].
[15]
DFRobot, "Capacitive Soil Moisture Sensor SKU:SEN0193," DFRobot, 3 June 2016. [Online]. Available: https://www.dfrobot.com/wiki/index.php/Capacitive_Soil_Moisture_Sensor_SKU:SEN0193. [Accessed 12 November 2016].
[16]
RobotShop Inc., "DS18B20 Waterproof Temperature Sensor," RobotShop Inc., 2016. [Online]. Available: http://www.robotshop.com/en/ds18b20-waterproof-temperature-sensor.html?gclid=Cj0KEQjw4MK_BRC1n6KTtezikbIBEiQA872hYcWGqh_pki1REKfWI4uqRq2krL-2jiWfnWQp5GfIb2IaAhIw8P8HAQ. [Accessed 12 November 2016].
[17]
Tempsensing.com, "1-Wire Temperature Sensor - 1.2" Stainless Steel Probe," Tempsensing.com, 10 November 2016. [Online]. Available: http://www.tempsensing.com/sensors/1wire-temperature-sensor-6ssp1.php?gclid=Cj0KEQjw4MK_BRC1n6KTtezikbIBEiQA872hYT_YCerkh8h_7J7pR3Z-WO1uq-oWwanjUgma2iczK68aApbn8P8HAQ. [Accessed 12 November 2016].
[18]
DFRobot, "PH meter(SKU: SEN0161)," DFRobot, 10 October 2016. [Online]. Available: https://www.dfrobot.com/wiki/index.php/PH_meter(SKU:_SEN0161). [Accessed 12 November 2016].
[19]
jet.com, Inc., "Luster Leaf Digital Soil pH Meter," jet.com, Inc., 2016. [Online]. Available: https://jet.com/product/detail/bc9fc810a6f5498faebc613f84cb8f48?jcmp=pla:ggl:a_nj_dur_gen_hardware_a3_b2:tools_measuring_tools_sensors_a3_other:na:PLA_649018514_30290686342_pla-161687192220:na:na:na:2&code=PLA15&gclid=CKG8_pz90c8CFcmhMgodnb0MAA&gclsrc=ds. [Accessed 12 November 2016].
[20]
Resistor Park, "Arduino Soil Moisture Sensor Hygrometer," Resistor Park, 2016. [Online]. Available: http://www.resistorpark.com/arduino-soil-moisture-sensor-hygrometer/?utm_medium=googleshopping&utm_source=bc&gclid=CjwKEAjw-Oy_BRDg4Iqok57a4kcSJADsuDK13ziZVzMTwQQdPfXrQHpIFgU7cOPZuPxggQEuieN-qhoCzmjw_wcB. [Accessed 12 November 2016].
[21]
Sparkfun Electronics, "SparkFun Soil Moisture Sensor," Sparkfun Electronics, 2016. [Online]. Available: https://www.sparkfun.com/products/13322?_ga=1.101225281.1113423649.1475435594. [Accessed 12 November 2016].
[22]
RobotShop Inc., "Gravity Moisture Sensor - Corrosion Resistant," RobotShop Inc., 2016. [Online]. Available: http://www.robotshop.com/en/gravity-moisture-sensor-corrosion-resistant.html?gclid=Cj0KEQjw4MK_BRC1n6KTtezikbIBEiQA872hYZInarRH8yoUIUh__Pptfuj2md5py9im2J1sy8nBMsAaAv698P8HAQ. [Accessed 12 November 2016].
[23]
RobotShop Inc., "Gravity Analog pH Meter Kit," RobotShop Inc., 2016. [Online]. Available: http://www.robotshop.com/en/gravity-analog-ph-meter-kit.html. [Accessed 12 November 2016].
[24]
Techlib.com, "Battery Capacity," Techlib.com, [Online]. Available: http://www.techlib.com/reference/batteries.html. [Accessed 14 November 2016].
[25]
Digi-Key Electronics, "Microchip Technology MRF24J40MAT-I/RM," Digi-Key Electronics, Thief River Falls, 2016.
[26]
Electronix Express, "Electronix Express- Hook up Wire Kit (Solid Wire Kit) 22 Gage (25 Feet)," Amazon.com, Inc., [Online]. Available: https://www.amazon.com/Electronix-Express-Hook-Wire-Solid/dp/B00B4ZRPEY/ref=sr_1_15?ie=UTF8&qid=1478828042&sr=8-15&keywords=wire. [Accessed 11 November 2016].
[27]
AmazonBasics, "AmazonBasics AA Performance Alkaline Batteries (48-Pack) - Packaging May Vary," Amazon.com, Inc., [Online]. Available: https://www.amazon.com/AmazonBasics-Performance-Alkaline-Batteries-48-Pack/dp/B00MNV8E0C?th=1. [Accessed 11 November 2016].
[28]
Microtivity, “Microtivity IB400 400-point Experiment Breadboard,” Amazon.com, Inc., [Online]. Available: https://www.amazon.com/dp/B0084A7PI8/ref=nav_timeline_asin?_encoding=UTF8&psc=1. [Accessed 11 November 2016]

Appendices and Annexes
Pseudo-code
Sensor node
array dataArray;       	//array variable that will store all the data
While(1)      	//Endless loop to run the node
{                            	
                    	wakeup();    	//wakes up the µC
        	//receiving and storing the data in dataArray
turnOnZigBeeReceiver();
        	dataArray = receivedData;
        	turnOffZigBeeReceiver();
        	        	//collecting data from the sensors and stores it in dataArray
                    turnOnAllSensors();
                    dataArray += collectedData;
		turnOnZigBeeTransmitter();
                    sendData();  	//sends data to the next node
		turnOffZigBeeTransmitter();
                    dataArray.clear(); //clears the array for the next cycle
                    sleep(3600)  	//sleep for 1h, the passed parameter is in seconds
}
Central station
While(1)      	//endless loop
{
                    	//receiving data
turnOnZigBeeReceiver();
        	dataArray = receivedData;
        	turnOffZigBeeReceiver();
        	//analyzing and providing graphical representations
        	runPythonLibrary();
sleep(3600);             	//sleep for 1h, the passed parameter is in seconds
}

Gantt chart


 
 &nbsp;
 
| Component                              | Unit(s) | Seller        | Unit cost | Total cost |
|----------------------------------------|---------|---------------|-----------|------------|
| Arduino hygrometer[20]                 | 3       | Resistor Park | $2.75     | $8.25      |
| DS18B20[16]                            | 3       | Robotshop     | $9.95     | $29.85     |
| Luster Leaf[19]                        | 3       | Jet.com       | $10.99    | $32.97     |
| STM32 L4 microcontroller[5]            | 4       | Digi-Key      | $14.90    | $59.60     |
| ZigBee transceiver [25]                | 4       | Digi-Key      | $11.00    | $44.00     |
| Wire (x6, 25 ft spools, 22 gauge) [26] | 1       | Amazon        | $20.00    | $20.00     |
| Platform core                          | 3       | Amazon        | $20.00    | $60.00     |
| Pi[2]                                  | 1       | Amazon        | $36.90    | $36.90     |
| AA alkaline battery 48 pack [27]       | 1       | Amazon        | $11.87    | $11.87     |
| Breadboard[28]                         | 4       | Amazon        | $4.96     | $19.84     |
| Subtotal                               |         |               |           | $323.28    |
| Miscellaneous                          |         |               |           | $26.72     |
| Total                                  |         |               |           | $350.00    |

&nbsp;


Team Resumes



FAISAL ALDHORGHAM
633 College Street ● Macon, GA 31201 ● 404-916-6032 ● faisal.aldhorgham@gmail.com

OBJECTIVE		Entry Level Electrical Engineering Position  


EDUCATION		M.S.E/B.S.E Specialization in Electrical Engineering  		
			MERCER UNIVERSITY, Macon, GA  			Expected, May 2017   


Computer Skills 	MS Office	       AutoCAD	       C++ Programming		Matlab


Relevant Courses:	Linear Control		Electrical Fundamentals	Nonlinear Control
Feedback Control	Electronics I & II		Digital Logic	
Signals & Systems	Comm System I & II		Engineering Economy	 


Related Projects:  	Freshman Design Toothpick Bridge Competition: 
Cooperated on a team of 3 to design and construct a toothpick bridge 
Assembled and presented PDR designs to faculty and classmates
Constructed bridge utilizing design specifications and tested to breaking point to determine efficiency
Prepared and presented CDR which included test results and potential design Modifications to ameliorate efficiency 
AutoCAD Project:
Required to prepare and dimension component drawings.
Learned to cement integral AutoCAD techniques such as layers, sections, and dimensioning. 
Contactless Electrical Energy Transmission (C.E.E.T) Research:
Working on a control circuit that will be used for a wireless charger project 
Building and soldering circuits in lab as well as running some tests on them
Conducting research on what type of resonant convert is best suitable for making a wireless charger 
Flyback DC/DC Converter Project: 
Designed, Simulated and Tested a Flyback DC/DC Converter
Composed CDR as well as presented the entire experiment to faculty 
 VOLUNTEERISM:
Muslim Students Association (MSA) Club:
Holding public relations position and helping Mercer University community to spread the awareness of Islam in every aspect through hosting events and activities.   
International Bears Association (IBA) Club:
Getting to know students from all over the world and learn from their different perception 
Assisting new international students to get around quickly
Institute of Electrical and Electronics Engineers (IEEE) Club:  
Participating and striving to experiment distinct activities such as soldering and building circuits
 PIERRE BALINDA
		http://bit.do/Pierre-B● (678)-559-7842 ● Pierre.Balinda@live.mercer.edu
EDUCATION	
Mercer University 	Macon, GA
Bachelor of Science in Computer Engineering	Expected May 2017
ENGINEERING/EXPERIENCE	
Mercer University Summer Engineering Program			    Summer 2016
Programmed a NASA funded Universal Vehicular Operator bot program using Python 
Developed and wired a wireless power transmitter and receiver 
Mercer University Summer Engineering Program         			    Summer 2015
Designed a mobile-friendly website usable on a study abroad program in Zambia
Designed an Android app that features the same content as the website
Programming Projects	
Python									   July 2016
Programmed a NASA funded Universal Vehicular Operator bot program using Python 
Java Programming								   Jan 2015
Developed a histogram generating program that has an external input
Developed a library book searching program
Web and Document Design Project						  Jan2014
Designed the International Student Club website
 Designed a personal website prototype for faculty member 
C/C++ Programming							  August 2013
Currently developing the backend of the Machine Robotics Lab’s inventory software
Programmed a TI microcontroller for my Microcomputer class  
Arduino Programming                                                                                  August 2015-Present
Designed and programmed a home security prototype for an IoT class project
Programmed small cars and rovers that are remote controlled on the Arduino IDE	
SKILLS	
Verbal and written fluency in French, Swahili, and Kinyarwanda
Software Proficiency: C++, Java, Python, VHDL, Adobe Dreamweaver CC
Technical Skills: 3-D printing, Laser Cutter, Microsoft Office Suite
OTHER EXPERIENCE	
Academic Resource Center, Mercer University, Macon, GA 		 August 2014-Present
Serve as a Math, programming, and engineering class tutor in the academic resource center
Assist students taking C++ programming, Java programming, Algebra, Pre-calculus, Calculus I,  Calculus II, Differential Equations, and Electrical Fundamentals I to understand class materials, study for homework, and prepare for tests and exams
My programming skills have improved as well as my debugging skills as I look through students’ codes to find and fix bugs. 
 LEADERSHIP AND INVOLVEMENT	
Website designer and Vice President, International Bears Association 	Jan 2015- May 2016
Utilized Adobe Dreamweaver to design the website 
Plan, organize, and coordinate logistics for our weekly meetings/social events
DANIEL LOUIS MACKOWSKI
122 Southwind Drive ◼  Kathleen, GA  31047-3300 US
Evening Phone: (478) 988-8191 ◼  Mobile: (478) 997-2113 ◼  Email: macbow333@gmail.com

EDUCATION	
B.S.E in Electrical Engineering						   	GPA: 3.80	
Mercer University: 1501 Mercer University Drive, Macon, GA 31207		          Expected 05/2017
Recognized on Dean’s List and President’s List for outstanding academic achievement
B.S. in Christian Studies (completed coursework towards)			   	GPA: 3.89	
Brewton-Parker College: 201 David-Eliza Fountain Circle, Mount Vernon, GA  30445 08/2011-05/2013
Achieved four consecutive semesters on the Dean's List
Related Courses:
Fdbk Control & Modeling	Prob & Stat for Engineers	Intro to Differential Equations
Statics & Dynamics  I	Technical Communication	Multivariable Calculus
Thermodynamics I	Electromagnetic Applications	Intro to ASP & DSP
Electronics I & II	Microcomputer Fundamentals	Signals & Systems
Programming Knowledge:
Java for Android, C++, C#, & Assembly  Languages
Related Projects:
Freshman Design Project
Learned the Engineering Design Process while working on a team of four
Created and tested K’Nex off-road vehicle in competitive testing environment
Created and briefed test plans, design proposals, and a PDR and CDR on assigned project
Technical Communications Research Projects
Became familiarized with scholarly research engines to find reputable sources
Learned methods for primary and secondary source analysis
Reviewed proper team led slideshow presentation and evaluation techniques
Practiced creating White Papers, Trip Reports, Posters, and project proposals
INVOLVEMENT/LEADERSHIP
IEEE – Student Member: 92943990
NSLS – Presidential Member & National Engaged Leader Award
2009 Advanced Space Academy, US Space Camp, Huntsville, AL
EXPERIENCE	
Robins AFB: 215 Page Road #269, Warner Robins, GA 31098
Pathways Engineering Intern						05/2015 – 09/2015
Took inventory of project stocked parts to determine what parts still needed to be ordered to begin construction of module and delivered this information to relevant personnel
Searched design documents to aid team in analysis of project requirements
Created test documentation based off current project system operations
Tested a software modification to ensure it operated per customer/software requirements 
Mercer University: 1501 Mercer University Drive, Macon, GA 31207
Supplemental Instruction Leader – Calculus I				08/2014 – 12/2014
Created lesson plans for group study sessions following the material covered in class lectures
Help students grasp concepts lectured on in class through application of study skills, metacognitive analysis when working practice problems, and time management for scheduling effective personal study sessions
