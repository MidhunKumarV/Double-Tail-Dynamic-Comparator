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
## Reference Circuit
![alt text](https://github.com/MidhunKumarV/Double-Tail-Dynamic-Comparator/blob/main/Images/ref_ckt.gif)

                      Double-Tail-Dynamic-Comparator
## Reference Circuit Working
The double-tail comparator has 2 phase. In reset phase when CLK = 0, both tails such as Mtail1, and Mtail2 are off. During this time transistors M3 and M4 charge fn and fp nodes to VDD, which makes transistors MR1 and MR2 to discharge the output nodes such as outp and outn to ground. In decision-making phase, when CLK =VDD, both tail turn on, M3-M4 turn off and voltages at nodes fn and fp start to drop with the rate defined by IMtail1/Cfn(p) and a input-dependent differential voltage ΔVfn(p) will build up.  The intermediate stage formed by MR1 and MR2 passes ΔVfn(p) to the cross-coupled inverters and also provides a good shielding between input and output, resulting in reduced value of kickback noise. In reset phase when the nodes become charged from ground to VDD power consumption arises. 
