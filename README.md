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
*  Design library name: full_adder
*  Design cell name: Carry_tb
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Wed Feb 23 18:37:06 2022

.global gnd!
********************************************************************************
* Library          : full_adder
* Cell             : Carry_Block
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt carry_block a b c gnd_1 vdd carry
xm11 carry carry_bar gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm8 net30 a gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm7 carry_bar b net30 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm2 net9 b gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm1 net9 a gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm31 carry_bar c net9 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm12 carry carry_bar vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm10 net34 a vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm9 carry_bar b net34 vdd p105 w=0.1u l=0.03u nf=1 m=1
xm5 net23 b vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm4 net23 a vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm3 carry_bar c net23 vdd p105 w=0.1u l=0.03u nf=1 m=1
.ends carry_block

********************************************************************************
* Library          : full_adder
* Cell             : Inverter
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt inverter gnd_1 input not vdd
xm0 not input vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm1 not input gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
.ends inverter

********************************************************************************
* Library          : full_adder
* Cell             : Sum_Block
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt sum_block a b c carry_bar gnd_1 sum_bar vdd
xm29 sum_bar c net174 vdd p105 w=0.1u l=0.03u nf=1 m=1
xm30 net174 b net178 vdd p105 w=0.1u l=0.03u nf=1 m=1
xm31 net178 a net111 vdd p105 w=0.1u l=0.03u nf=1 m=1
xm18 net111 c vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm19 sum_bar carry_bar net111 vdd p105 w=0.1u l=0.03u nf=1 m=1
xm20 net111 a vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm21 net111 b vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm26 sum_bar c net160 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm28 net164 b gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm27 net160 a net164 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm23 net150 a gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm22 sum_bar carry_bar net150 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm24 net150 b gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm25 net150 c gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
.ends sum_block

********************************************************************************
* Library          : full_adder
* Cell             : Carry_tb
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xi24 a b c gnd! net55 carry carry_block
v1 net55 gnd! dc='1.8V'
v22 c gnd! dc=0 pulse ( 0 1.8 0 0.1u 0.1u 20u 40u )
v21 b gnd! dc=0 pulse ( 0 1.8 0 0.1u 0.1u 10u 20u )
v20 a gnd! dc=0 pulse ( 0 1.8 0 0.1u 0.1u 5u 10u )
c2 carry gnd! c=1p
c19 sum gnd! c=1p
xi23 gnd! net50 sum net55 inverter
xi9 gnd! carry net33 net55 inverter
xi15 a b c net33 gnd! net50 net55 sum_block

.tran '1u' '40u' name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(a) v(b) v(c) v(carry) v(sum)

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

