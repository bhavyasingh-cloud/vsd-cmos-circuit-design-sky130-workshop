# vsd-cmos-circuit-design-sky130-workshop
CMOS circuit design and spice simulations using Sky130 technology
## About
This repository contains my work, images and stimulations results from the VSD CMOS Circuit Design and SPICE simulation workshop using Sky130 technology.
## Course Flow
### DAY 1 Basics of NMOS Drain current (Id) vs Drain-to-source Voltage (Vds)
   #### Topics covered
   ### Introduction to Circuit Design and SPICE simulation
   ### L1 Why do we need SPICE simulations?
   SPICE is used to simulate and analyze electronic circuits before actually building them.
   The clock Tree synthesis, crosstalks, and timing are built on SPICE (Simulation Program with Integrated Circuit Emphasis), without SPICE there won't be delay      and if there are no delays physical design flow, crosstalk won't make any sense.
    
 <img width="1327" height="664" alt="image" src="https://github.com/user-attachments/assets/5819c6a9-d84d-4ace-ac4e-359fd8e61bc5" />

 The tables shown for CBUF '1' and CBUF '2' are cell characterization tables
 For a buffer, delay depends mainly on:

 -Input Slew (how fast the input signal rises/falls).
 
 -Output Load Capacitance (how much capacitance the output has to drive.

So instead of having one fixed delay, the buffer has many possible delays.

 ### L2 Introduction to basic element in Circuit design – NMOS
 <img width="1133" height="460" alt="image" src="https://github.com/user-attachments/assets/d24d4d07-cf9d-47b9-9755-467f1edf0d13" />

 -Threshold Voltage
 
   -When Vgs=0 => source and drain terminal both are grounded, Body is also ground. 
   P-substrate and n+ act as PN junction diode and as there is no potential so there is a high resistance. 
   No channel formation is there.

   -When Vgs>0 => gate is now positively charged and due to this there will be Accumulation of negative charges at the surface of substrate.

   <img width="1315" height="488" alt="image" src="https://github.com/user-attachments/assets/14582745-f24f-4166-8158-2bbf55bd34e4" />

   ### L3 Strong inversion and threshold voltage

   <img width="1249" height="613" alt="image" src="https://github.com/user-attachments/assets/5791693c-ae12-433d-9cf5-a7503b54fa03" />

   -strong inversion
   
At a certain gate voltage:

Electron concentration near the surface becomes greater than hole concentration.
The surface effectively behaves as n-type.

This phenomenon is called strong inversion.

An n-type conducting layer forms under the gate.

This layer is called the inversion channel.

 -threshold voltage

 The gate voltage at which strong inversion occurs is called the threshold voltage.

 <img width="1275" height="577" alt="image" src="https://github.com/user-attachments/assets/346c70e1-4707-44b3-97a7-66db141c2fdb" />

 ### L4 Threshold voltage with positive substrate potential
 
 Semiconductor surface inverts to n tye at Vgs = Vto + V1
 
 <img width="1342" height="629" alt="image" src="https://github.com/user-attachments/assets/ed7bd1f1-5df6-45bf-b396-f89d3af809b9" />

 The figure shows:

Vsb>0

For an NMOS:

Source is at a higher potential than the body.
Source-body junction becomes more reverse biased.
Depletion region becomes wider.

As the depletion region widens, more gate voltage is needed to attract enough electrons and form the inversion channel.

Therefore:

Threshold voltage increases

This phenomenon is called the Body Effect.

note : The parameters such as Gamma comes from foundaries after simulation of which in SPICE we get the value for Vt (Threshold Voltage).

 


   

### DAY 2
### DAY 3
### DAY 4
### DAY 5
## Tools Used
 - Sky130 PDK
 - ngspice
 - noVNC
