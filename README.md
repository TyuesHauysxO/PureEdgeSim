# PureEdgeSim: A simulation toolkit for performance evaluation of Fog and pure Edge computing environments

[![DOI](https://zenodo.org/badge/163447483.svg)](https://zenodo.org/badge/latestdoi/163447483)  [![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)  [![Build Status](https://travis-ci.com/CharafeddineMechalikh/PureEdgeSim.svg?branch=master)](https://travis-ci.com/CharafeddineMechalikh/PureEdgeSim)  [![Codacy Badge](https://api.codacy.com/project/badge/Grade/25ee278611014a9bb242297480703cf9)](https://www.codacy.com/manual/CharafeddineMechalikh/PureEdgeSim?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=CharafeddineMechalikh/PureEdgeSim&amp;utm_campaign=Badge_Grade)   [![Maintainability](https://api.codeclimate.com/v1/badges/a1ffecb5230fc5771b93/maintainability)](https://codeclimate.com/github/CharafeddineMechalikh/PureEdgeSim/maintainability)   [![codebeat badge](https://codebeat.co/badges/bbe172a2-1169-4bbe-b6a6-0505631babc6)](https://codebeat.co/projects/github-com-charafeddinemechalikh-pureedgesim-master)

## For more information read the wiki here: [PureEdgeSim WIKI](https://github.com/CharafeddineMechalikh/PureEdgeSim/wiki) 
A simulation tutorial can be found [here](https://drive.google.com/open?id=1Qg7UTop7Wa7TZQ8MOrXZkyo1Rga455Qm)  

## 1. Background

Fog and Edge (Mist) computing, two emerging computing paradigms that aim to overcome the Cloud computing limitations by bringing its applications at the Edge of the network. Thus, reducing both the latency and the Cloud workload and leading to a more scalable network. Nevertheless, in these distributed environments where many devices need to offload their tasks to one another (either to increase their lifetime or to minimize the task completion delay) many issues such as resources management strategies has to be solved. Instead of testing them on a real distributed system, the simulation makes it possible to evaluate the proposed strategies and algorithms in a repeatable, controllable and cost-effective way before their actual deployment. However, when it comes to simulation tools, Edge and Fog computing still did not get the attention they deserve (with only few simulators for Fog computing such as iFogSim, EdgeCloudSim. Meanwhile, no simulator for pure Edge computing).

We introduce PureEdgeSim, a new simulator based on [CloudSim Plus](http://Cloudsimplus.org) that is designed to simulate Cloud, Fog, and Edge computing environments. It allows to evaluate the performance of resources management strategies in terms of network usage, latency, resources utilization, energy consumption, etc. and enables the simulation of several scenarios such as the Internet of Things (IoT), connected vehicles/ VANETs/MANET, pure Edge computing environments (peer-to peer networks such as mobile devices Cloud), and mobile Edge computing. 

## Why it is named "Pure"EdgeSim  (Pure Edge Computing Simulator)

Although Fog and Edge computing are usually referred to as the same paradigm, the main difference between them is their locations. In the pure Edge computing (which this simulator is named after), Edge nodes are deployed in the Edge devices themselves following peer-to-peer architecture. Therefore, it provides even lower latency than Fog computing, while in Fog computing, the Fog nodes are deployed on servers, mini-Clouds, etc. following a client-server architecture (D’Angelo, M. 2016). That is why the PureEdgeSim is named so.
   
## 2. PureEdgeSim Architecture

PureEdgeSim enables the simulation of resource management strategies and allows to evaluate the performance of Cloud, Fog, and pure Edge computing environments. It grantees high scalability by enabling the simulation of thousands of devices. Besides, it supports the Edge devices heterogeneity (i.e. whether this device is mobile or not, whether battery-powered or not, different  applications requirements: tasks file size, tasks CPU utilization,and latency requirement, etc.) 

![Environment](https://github.com/CharafeddineMechalikh/PureEdgeSim/blob/master/PureEdgeSim/files/scenario.JPG)

A simple representation of the simulation scenarios

It provides a task orchestrator module that orchestrates the tasks and enables the multi-tiers simulations scenarios where many computing paradigms can be used in conjunction with one another. Besides, it provides an even more realistic network model (as compared to state of the art simulators) that continuously changes the allocated bandwidth for each task being transferred depending on the network traffic. 

It consists of the following 7 modules:

*   Scenario Manager, that loads  the simulation parameters and the user scenario from the input files (`.xml` and `.prop` files in `/settings/` folder) where the user specifies. It consists of two classes, the File Parser that  checks the input files and loads the  the simulation parameters, and the Simulation Parameters class which represents a placeholder for the different parameters.


*   Simulation Manager, that initiates the simulation environment, schedules all the events and generates the output. It consists of two important classes, the Simulation Manager class which manages the simulation, schedules the tasks generation, etc. The Simulation Logger class that generates the simulation output saves it in comma-separated value (CSV) format in order to easily exploit them later using any spreadsheet editor (e.g. Microsoft Excel...).


*   Data Centers Manager: it generates and manages all the data centers and devices (i.e. Cloud, Fog or Edge). It consists of two classes: the Edge Data Center class, that contains the specific properties of Edge devices such as the location, the mobility, the energy source, and the capacity/ remaining energy if it is battery-powered. The second class is the Server Manager which generates the needed servers and Edge devices, their hosts and their virtual machines.


*   Tasks Generator which is behind the tasks generation, -currently- it assigns an application such as e-health, smart-home, and augmented-reality (that can be defined in `settings/applications.xml` file) to each Edge device. Then, it will generates the needed tasks according to the assigned type, which guarantees the heterogeneity of applications.  


*   The Network Module: that consists mainly of the Network Model class.which is behind the transfer of tasks/containers/ request... 


*   The Tasks Orchestrator, which is the decision maker, where the user can define the orchestration algorithm. 


*   The Location Manager, which generates the mobility path of mobile devices.
   
![Architecture](https://github.com/CharafeddineMechalikh/PureEdgeSim/blob/master/PureEdgeSim/files/modules.PNG)

PureEdgeSim architecture

## 3. What can be simulated with PureEdgeSim

*   Cloud, Fog, and pure Edge computing scenarios


*   And basicaly, any scenario that involves computing on distributed nodes or mobility, for example:

VANETs/MANET networks, IoT applications, Mobile Devices Clouds, Mobile Edge Computing,... 
  
## 4. PureEdgeSim features

*   Realistic network and energy models as compared to other simulators.

*   Mobility support which is ignored by most simulators: 

A ready to use mobility model (mode models will be added).

The user can easily add new models based on his needs.

The user can specify the dimentions of the simulated area and the speed of mobile devices. 

The mobility model will assign a random location to each device.

Then the mobile devices will change their location according to the model in use.
*   The support for devices heterogeneity:

The user can define heterogenous Edge device, Fog servers, and Cloud Data Centers in the corresponding `.xml` files. 

He will decide wether and Edge device is mobile or not, wether it is battery-powered or not ( and the size of its battery), 

and how much computing capacity it has.

The devices without computing capacity are considered as simple sensors that only generate data/tasks. 

The user can also define the applications that are in use, their cpu utilization, their files sizes and their latency. requirements. 
*   The scalability, generate handreds of devices, with a single click. 

*   A rich collection of metrics:

The simulation output  (the `.csv` file) includes + 40 metrics ready to be plotted.

Also, new metrics can be derived from those.

*   Ease of use:

More than 60 charts can be generated automatically.

Other charts can be easily generated from the csv file using any spreadsheet software (e.g. Microsoft Excel).

Readable code and an architecture that is easy to understand.

*   Wide applicability and extensibility:

The support for many simulation scenarios : IoT, VANETs/MANET Clouds, Fog computing environments..

The user can evaluate the orchestration algorithms, the architectures,...

The upport for many devices and applications types...

Various simulation parameters that meet the requirement of any scenario...

The user can implement new orchestration algorithms(machine learning algorithms: fuzzy decision trees for example)

He can also implement new network, energy, mobility, or tasks generation models. 

He can groupe Edge devices into clusters, deploy the orchestrator node in the cluster head for example,

and form a sort of Edge devices Cloud.

He can also solve the registry scalability issue by mirroring the containers images close to the Edge,

and so on...   

Basically any scenario that involves data centers, servers, or geo-distributed devices.

*   Full control of the simulation environment:

The user can trade-off between simulation duration and its accuracy. 

To decrease the simultion time, the user can also enable parallelism. 


Example of real time charts :

![Real time charts](https://github.com/CharafeddineMechalikh/PureEdgeSim/blob/master/PureEdgeSim/files/real%20time.gif)

Real time analysis of simulation environment

## Authors : Charafeddine MECHALIKH, Hajer TAKTAK, Faouzi MOUSSA

## Please cite it as 

Mechalikh, C., Taktak, H., Moussa, F.: PureEdgeSim: A Simulation Toolkit for Performance Evaluation of Cloud, Fog, and Pure Edge Computing Environments. The 2019 International Conference on High Performance Computing & Simulation (2019) 700-707

Other publication using PureEdgeSim can be found [here](https://www.researchgate.net/profile/Charafeddine_Mechalikh/research)

*For any questions, contact me at charafeddine.mechalikh@gmail.com*   
