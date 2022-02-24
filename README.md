# Design of Double-Tail-Dynamic-Comparator
* This repository presents the design of a Double-Tail-Dynamic-Comparator implemented using Synopsys Custom Compiler on 28nm CMOS Technology. This project was done as part of [Cloud Based Analog IC Design Hackathon](https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/) conducted by IIT Hyderabad, sponsored by Synopsys India and VLSI System Design (VSD) Corp. Pvt. Ltd India.
## Table of Contents
1. Introduction
2. Reference Circuit 
3. Reference Circuit Working
4. Implementation
5. Schematic Netlist
6. Waveforms
## Introduction
Comparator is one of the fundamental building blocks in most analog-to-digital converters (ADCs). Many highspeed ADCs, such as flash ADCs, require high-speed, lowpower comparators with small chip area. Dynamic comparators are superior to static counterpart because of positive feedback which increases latching speed and lower static power consumption. As there are some drawbacks in conventional dynamic comparator a conventional double-tail comparator is used. The structure has less stacking and therefore can works at lower supply voltages on comparing with the conventional dynamic comparator. The advantage of double-tail dynamic comparator is that there is a separate input gain stage and output latch stage. The grouping of input and output stages as two distinct stages make this type of comparator to have a lower and more stable offset voltage.
