---
layout: page
title: Proposal
date: 2016-11-14 11:43:44 +0000
permalink: /Proposal/
---
![Mercer Engineering](https://github.com/BenKasson1/DocumentationAg2/blob/master/docs/assets/images/MercerEGR.jpg?raw=true)

## Multi-Sensor Mesh Network for Agricultural Analysis

**Client:** T. Anthony Choi

**Presented by:**  
Daniel Mackowski  
Faisal Al-dhorgham  
Pierre Balinda 

September 6th, 2016

### Executive Summary
Ideally, farmers would survey the health of their crops adequately for a low price. However, the current satellite surveying method widely used by farmers is very expensive. To provide a more cost efficient option, Dr. Anthony Choi of the Mercer University School of Engineering (MUSE) has contacted a team of MUSE students to design multi-sensor platform that will collect data on soil humidity levels, pH levels, and temperature. The platforms will send this information through a mesh network to the farmer who will in turn make informed decisions to cut costs of unnecessary watering and pesticide and fertilizer spraying. The MUSE student engineering team is composed of Pierre Balinda, a Computer Engineer, Faisal Al-dhorgham, and Daniel Mackowski, both Electrical Engineers.

The team performed in-depth research about similar devices that are currently on the market or being developed. The team found four major devices that performed similarly to what the client has requested. These devices had a retail price range of $80-$100. The price varied based on sensors present, power source, data transmission system, and supported user interface application platforms. After reviewing these devices, the team came up with a rough design that would incorporate most of the sensor types found in the research and form a mesh network of multiple nodes that would transfer the data efficiently. This rough design will cost $670. Since the MUSE caps the budget at $300, the additional $370 will be covered by the client, Dr. Choi. 

The team will come up with different solutions which will undergo a rigorous feasibility and merit criteria testing. The winning solution will then be submitted to the client and manager as the chosen design in the Preliminary Design Review on Monday November 14th, 2016 and presented during the week of November 14th – 19th, 2016. Upon acceptance, the team will then start working on the prototype that will be delivered to the client on Friday April 28th 2017.
In conclusion, the team would like to ask for permission to go forward with this project.

### Problem Statement

Ideally, as the world population continues to grow past 7.4 billion, farmers all over the world would be able to keep up with the demand for more quality food at affordable prices. However, with the demand steadily increasing, farmers are turning to engineers and scientists for new methods and technologies capable of reducing costs and optimizing crop yield. One of the methods farmers are looking to use to increase the affordability and availability of their produce is by employing technology to ensure soil conditions are optimized for their crops in near real time. Dr. Anthony Choi of the Mercer University School of Engineering (MUSE) has contacted the MUSE student engineering team composed of Pierre Balinda, a Computer Engineer, Faisal Al-dhorgham, and Daniel Mackowski, both Electrical Engineers, to design a solution to this problem. The team will research currently available solutions and design and implement a mesh network of multi-sensor platforms to survey and present collected data to farmers.

### Deliverables
This project requires the design and construction of a mesh network of environmental sensor nodes and a software system to analyze and present the data collected from the sensors. The sensors will be designed to the client’s specifications to measure various soil attributes at multiple depths. The nodes will be battery powered and will communicate information wirelessly from node to node to transmit information back to a computer that will run the analysis software. The software will collect the location, depth, and, time data from each node along with the environmental data to construct graphical views of the data. This will provide the end user with a clear understanding of the data to expedite decision making for maintenance of the region where the network is located.

### Background

As the growing demand for affordable produce is nothing new to the agriculture industry, the team conducted research about similar projects on the market or currently in development and found four major smart garden sensors of interest. According to [1], they are the Edyn Garden Sensor, Koubachi Wi-Fi Plant Sensor, Parrot Flower Power, and Oso Technologies Plant Link. Each smart sensor has a plant database that allows them to give proper recommendations to the user about their specific plant’s needs.

The Oso Technologies PlantLink costs $80, senses soil moisture, has 50,000 plants in its database, uses a Zigbee signal to transmit data and 2 AAA batteries to power it for over a year. It only has a web interface for the user. The Parrot Flower Power costs $60, senses soil moisture, temperature, sunlight, fertilizer and pesticide levels. It has 7000 plants in its database, uses a Bluetooth signal to transmit data and 1 AAA battery to power for 6 months. The Parrot only has an iOS app in as a user interface.

The Koubachi Wi-Fi Plant Sensor costs $100, senses soil moisture, temperature, and sunlight. It has 800 plants in its database. This sensor uses Wi-Fi to transmit its data and 2 AA batteries that can power it for over a year. The Koubachi sensor offers ample choices to its users when it comes to interfaces as it has an iOS, Android, and Web applications.

The Edyn Garden Sensor costs $100, senses soil moisture, temperature, light, fertilizer, pesticide, and humidity levels. It has 5000 plants in its database, uses Wi-Fi to transmit data and a solar powered battery that can last 2.5 years. The Edyn sensor has an iOS and Android app that the user can use as an interface.

The team will use these devices as models to kickstart the design process. 

### Proposed Possible Solutions/Methods 

The team will design a multi-sensor platform durable enough to be driven into the soil. Each platform will have sensors for soil water levels, pH levels (for determining fertilizer or pesticide presence), and temperature at different depths of the soil to provide farmers with data necessary to optimize soil quality, shortening growth time and increasing crop yield. This device will rely on battery power to run the entire node for at least a full planting cycle for corn, which is about four months. 

The device will be able to transmit the data to a central station via mesh network transmission principles. The central station will have an application that the farmers can easily download onto their phones. It will send a notification to the farmers when the data is collected and analyzed so they can open the app and make care decisions for their crops based on what information is presented by the app.  The data will be displayed with multiple selectable views to distinguish the soil water levels from fertilizer levels and so forth. 

In this project, the team will initially design a single platform that will measure all expected soil qualities and transmit the data back to the central station (the farmer’s phone) which will run the analysis app. As time permits, the the team will build up to five of these multi-sensor platforms to be driven into the soil at specific distances apart from each other to create a network over an area to test the mesh network capabilities of the system. The mesh network will allow low power signals to be transmitted over long distances by being sent from node to node until they reach the central station. The platforms will be designed to operate in two states, low power to preserve battery life, and an active state to take readings from the sensors and transmit information to a nearby node.  

### Project Plan

Design of the system will begin upon proposal approval. Each team member will perform research for similar products on the market to gain a better understanding of the technology required for this project. Preliminary design should be complete by September 29, 2016. The team will then prepare a progress report on the research and design status of the project to that point one either Thursday, October 6, 2016, or Tuesday, October 11, 2016. With feedback gathered from the progres report, designs will be refined and the budget will be adjusted to account for errors in preliminary estimations. The team will begin work on the PDR after the first progress report presentation. Final decisions on the project design will be made by Thursday, October 26, 2016. As work on the PDR draws to a close, the team will prepare a second progress report for either Tuesday, November 8, 2016, or Thursday, November 10, 2016. Final edits of the PDR will take the feedback from the progress report into account and will end on Friday, November 11, 2016. The team will present the PDR on the week of Monday, November 14, 2016. After the PDR is presented, the team will make changes as the client and advisors specify. Once accepted, The team will order parts on the week of Monday, December 5, 2016.

Design implementation as described in the PDR will begin on Monday, January 9, 2017. Pierre will write the software that will transmit, analyze, and present the data. Faisal and Daniel will design and build the nodes from built and bought components. Components will be tested separately as they are completed starting on Tuesday, January 31, 2017. Pierre will test the accuracy of data collected at each sensor platform. Daniel will test the system for accuracy of data transmission. Faisal will test the readability of acquired data by the presentation software. The team will prepare a progress report for the week of Monday, February 13, 2017, and use feedback acquired to refine the implementation process. The team will begin to write the CDR after the progress report. Component building should finish by the week of Monday, February 27, 2017. At this time, component integration and testing of the completed system will begin. The team will prepare a progress report for the week of Monday, March 13, 2017, and use feedback acquired to refine tests and system design. Integration and testing should end by Friday, March 31, 2017. Final edits of the CDR should be finished by the week of Monday, April 3, 2017. After the team presents the CDR, the team will give the completed project to the client by Friday, April 28, 2017.

### Team/Work assignment

The team is composed of a Computer Engineering student (Pierre Balinda) and two Electrical Engineering students (Daniel Mackowski and Faisal Al-dhorgham). Based on the major focus of these engineering students, the team decided to assign the software portion of the project to Pierre and the electrical and mechanical portions to Daniel and Faisal. As for the writing aspects, the tasks will be equally distributed among the team members.

### Resources Requirements (money, items to interface,..)

The team will have to buy the soil moisture level and pH sensors since there is inadequate time to design them. The team will also need to buy other circuit components necessary to complete the project if they are unavailable. The team also needs to buy a steel housing unit or parts to make one to protect the microcontroller and electronic components from damage. The team will also need access to development software to create the system to transmit and present the data to the end user. Initial estimates place the cost of the project at $670.

### Budget

These are initial estimates. All values are subject to change based on feedback from the client and advisors. Calculations are based on the assumptions that there will be five sensor platforms, each five feet (~1.524 meters) deep with two sensors each for moisture and nitrate levels every two feet (~60.96 centimeters).

| Item                          | Price/unit     | Number of units          | Total cost |
|-------------------------------|----------------|--------------------------|------------|
| Microcontroller               | $50 each       | 5                        | $250       |
| Moisture sensor               | $5 each        |  4 × 5 = 20              | $100       |
| pH sensor                     | $5 each        | 4 × 5 = 20               | $100       |
| Wireless transmitter/receiver | $2 each        | 5                        | $10        |
| Wire                          | $0.50 per foot | (3 × 1 × 1) * 4 * 5 =100 | $50        |
| Platform core                 | $20 each       | 5                        | $100       |
|                               |                | Subtotal                 | $610       |
| ~10% cushion                  |                |                          | $60        |
|                               |                | Total                    | $670       |

Items will be more specific once the team conducts further research. Some items may disappear from the list or break down further into component parts that the team will then assemble into custom components for the system.

### Summary

In summary, the team composed of Pierre Balinda, Faisal Al-dhorgham, and Daniel Mackowski plan on designing, with the approval of the client, advisors, and managers, a multi-sensor platform mesh network that will cost roughly $670. Since the MUSE caps the budget at $300, the additional $370 will be covered by the client, Dr. Choi. The PDR will be submitted on Monday November 14th, 2016 and the prototype delivered to the client on Friday April 28th, 2017. The team would like to ask for permission and funds to go forward with this project.

References
[1] Gebhart. (2015).  Smart Home Garden Tech Buying Guide [Online]. Available:   
         [http://www.cnet.com/news/smart-outdoors-buying-guide/](http://www.cnet.com/news/smart-outdoors-buying-guide/)

[2] Adamchuk, Viacheslav, 2003 Fourth European Conference on Precision Agriculture, Berlin, 
        Germany 
        [https://www.agriculture.purdue.edu/ssmc/frames/Dec2003_Purdue_NL1.htm](https://www.agriculture.purdue.edu/ssmc/frames/Dec2003_Purdue_NL1.htm)

[3]Adamchuk, V.I., J.W. Hummel, M.T. Morgan, and S.K. Upadhyaya. 2004. On-the-go soil 
      sensors for precision agriculture. Computers and Electronics in Agriculture 44(1):71-91. 

[4]Bongiovanni, R. and J. Lowenberg-DeBoer. “Economics of Variable Rate Lime in Indiana,” 
     Proceedings of the 4th International Conference on Precision Agriculture, SSSA, Madison, 
     WI, 1998, p. 1653-1665. 

[5] Whipker, L. and J. Akridge, 2004 Precision Agricultural Services Dealership Survey Results.
      Available in the Publications pages at [http://www2.agriculture.purdue.edu/ssmc/](http://www2.agriculture.purdue.edu/ssmc/). 
