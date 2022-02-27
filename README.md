# Design of Double-Tail-Dynamic-Comparator
* This repository presents the design of a Double-Tail-Dynamic-Comparator implemented using Synopsys Custom Compiler on 28nm CMOS Technology. This project was done as part of [Cloud Based Analog IC Design Hackathon](https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/) conducted by IIT Hyderabad, sponsored by Synopsys India and VLSI System Design (VSD) Corp. Pvt. Ltd India.
## Table of Contents
1. Introduction
2. Reference Circuit 
3. Reference Circuit Working
4. Implementation
5. Schematic Netlist
6. Waveforms
7. References
8. Acknowledgements
## Introduction
Comparator is one of the fundamental building blocks in most analog-to-digital converters (ADCs). Many highspeed ADCs, such as flash ADCs, require high-speed, lowpower comparators with small chip area. Dynamic comparators are superior to static counterpart because of positive feedback which increases latching speed and lower static power consumption. As there are some drawbacks in conventional dynamic comparator a conventional double-tail comparator is used. The structure has less stacking and therefore can works at lower supply voltages on comparing with the conventional dynamic comparator. The advantage of double-tail dynamic comparator is that there is a separate input gain stage and output latch stage. The grouping of input and output stages as two distinct stages make this type of comparator to have a lower and more stable offset voltage.
## Reference Circuit and Waveform
![alt text](https://github.com/MidhunKumarV/Double-Tail-Dynamic-Comparator/blob/main/Images/ref_ckt.gif)

                                    Double-Tail-Dynamic-Comparator
![alt text](https://github.com/MidhunKumarV/Double-Tail-Dynamic-Comparator/blob/main/Images/ref_waveform.gif)

                                    Transient response of reference comparator
## Reference Circuit Working
The double-tail comparator has 2 phase. In reset phase when CLK = 0, both tails such as Mtail1, and Mtail2 are off. During this time transistors M3 and M4 charge fn and fp nodes to VDD, which makes transistors MR1 and MR2 to discharge the output nodes such as outp and outn to ground. In decision-making phase, when CLK =VDD, both tail turn on, M3-M4 turn off and voltages at nodes fn and fp start to drop with the rate defined by IMtail1/Cfn(p) and a input-dependent differential voltage ΔVfn(p) will build up.  The intermediate stage formed by MR1 and MR2 passes ΔVfn(p) to the cross-coupled inverters and also provides a good shielding between input and output, resulting in reduced value of kickback noise. In reset phase when the nodes become charged from ground to VDD power consumption arises. 
## Implementation
![alt text](https://github.com/MidhunKumarV/Double-Tail-Dynamic-Comparator/blob/main/Images/ckt.jpg)

                                                Circuit Schematic
## Schematic Netlist 
```*  Generated for: PrimeSim
*  Design library name: mid_lib1
*  Design cell name: comparator
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Sun Feb 27 06:31:42 2022

.global gnd!
********************************************************************************
* Library          : mid_lib1
* Cell             : comparator
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xm14 clkb clk gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm6 outp net35 gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm5 outn net31 gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm4 outp outn gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm3 outn outp gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm2 net7 clk gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm1 net35 inp net7 gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm0 net31 inn net7 gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm15 clkb clk vdd vdd p105 w=0.2u l=0.03u nf=1 m=1
xm11 net47 clkb vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm10 outp outn net47 vdd p105 w=0.2u l=0.03u nf=1 m=1
xm9 outn outp net47 vdd p105 w=0.2u l=0.03u nf=1 m=1
xm8 net35 clk vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm7 net31 clk vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
v28 net74 gnd! dc=0.5
v24 vdd gnd! dc=1
v41 net71 gnd! dc=0.5
v42 inp net74 dc=0 pulse ( 0 0.5 2.5u 0.1u 0.1u 2.5u 5u )
v27 inn net71 dc=0 pulse ( 0 0.5 0 0.1u 0.1u 2.5u 5u )
v26 clk gnd! dc=0 pulse ( 0 1 0 0.001u 0.001u 0.5u 1u )








.tran '0.1u' '20u' name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(clk) v(inn) v(inp) v(net31) v(net35) v(outn) v(outp)

.temp 25



.option primesim_output=wdf


.option parhier = LOCAL






.end
```
## Waveforms
![alt text](https://github.com/MidhunKumarV/Double-Tail-Dynamic-Comparator/blob/main/Images/Transient%20response.jpg)

                                                Transient Response 
![alt text](https://github.com/MidhunKumarV/Double-Tail-Dynamic-Comparator/blob/main/Images/signal%20behavior.jpg)

                                                Signal Behavior
## References
[1] D. Schinkel, E. Mensink, E. Klumperink, et al. "A double-tail latch-type voltage sense amplifier with 18ps Setup+Hold time," in IEEE Int. Solid-State Circuits Conf (ISSCC),p.314-605(2007).
[2] S. Baghel, D. K. Mishra. "Design and Analysis of Double-Tail Dynamic Comparator for Flash ADCs", 2018 International Conference on Circuits and Systems in Digital Enterprise Technology (ICCSDET), 2018
## Acknowledgements
Kunal Ghosh, Founder, VSD Corp. Pvt. Ltd
Indian Institute Of Technology (IIT), Hyderabad
Synopsys
## Author
Midhun Kumar V, Mtech at IIT Delhi
