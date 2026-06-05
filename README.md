# vsd-cmos-circuit-design-sky130-workshop
CMOS circuit design and spice simulations using Sky130 technology
## About
This repository contains my work, images and stimulations results from the VSD CMOS Circuit Design and SPICE simulation workshop using Sky130 technology.
## Course Flow
## DAY 1 Basics of NMOS Drain current (Id) vs Drain-to-source Voltage (Vds)
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

### NMOS resistive region and saturation region of operation
###  L1 Resistive region of operation with small drain-source voltage
<img width="825" height="523" alt="image" src="https://github.com/user-attachments/assets/98ff41be-5638-45f8-a8b7-d7128a31719f" />

For "Resistive region" of operation we apply Drain-source voltage. If we keep on increasing the Gate-source voltage, the channel width keeps on increasing.
The net Induced charges is propotional to (Vgs-Vt).

Now let's apply very small Vds at start. And keep Vt=0.45V, Vgs also small initially.
We can see that the source is grounded and Drain is at some potential, so there will also be a voltage gradient accross the channel.

Also, the Effective channel length is much lesser than the original channel length.
y-axis represents the width of transistor and x axis is the voltage across the channel.
On applying Vds, every point on x axis will vary w.r.t to Vgs-V(x), this will decide the current equation.

### L2 Drift current theory

<img width="1403" height="693" alt="image" src="https://github.com/user-attachments/assets/d5f6100b-182d-4703-af6c-1acd580f1ca2" /><img width="408" height="426" alt="image" src="https://github.com/user-attachments/assets/e097dcc4-bc40-41e3-99f0-a93431dffa76" />

The effective channel voltage will vary w.r.t x.

for example at x=0, Vgs=1V and V(x)=0, So the Vgs-Vx=1V. 

At x=Vds=0.05V, Vgs-Vx=0.95V. Now if we see the induced chagre equation, it is proportional to the effective channel voltage.

As we know there are two types of currents; Dift and Diffusion current, Here there is Drift current due to potential difference across the channel.

###  L3 Drain current model for linear region of operation
To get the drain current, the top view of transistor is required.
<img width="687" height="638" alt="image" src="https://github.com/user-attachments/assets/f49fcef3-21a9-40d9-bfb6-85750d3332ec" />
<img width="413" height="595" alt="image" src="https://github.com/user-attachments/assets/f5d457e5-debe-479d-8027-8cd1a9d5b294" />
<img width="438" height="449" alt="image" src="https://github.com/user-attachments/assets/f4cfa9db-33e1-4ee2-bfff-4542b9587e1a" />
<img width="683" height="426" alt="image" src="https://github.com/user-attachments/assets/62d5de09-e978-495d-8b3a-09b27ac883da" />

### L4 SPICE conclusion to resistive operation
<img width="1237" height="568" alt="image" src="https://github.com/user-attachments/assets/50951011-55d2-4721-b847-c7c9bcb92533" />

 TO ANSWER How do we calculate Id for different values of 'Vgs' and at every value of 'Vgs', sweep Vds till (Vgs-Vt) using linear equation for Id?
We need to do SPICE simulations.

### L5 Pinch-off region condition

-Saturation Region
The region of operation when Drain-source voltage exceeds the value (Vgs-Vt), the region of operation is called "Saturation Region".
In this regio the channel is saturated and can not do anything further.

When Vgs-Vds is greater than Vt, there will be a conducting channel.

When Vgs-Vds is equal to Vt, we will see at drain side, just Inversion has happened as it is equal to Vt, so channel will start disappearing at drain side.

-Pinch off Voltage
When the channel starts to disappear, is termed as "Pinch off region"

<img width="1307" height="609" alt="image" src="https://github.com/user-attachments/assets/63cf7655-6bb8-4e94-bcd9-65757c87a4e5" />

### L6 Drain current model for saturation region of operation

<img width="1211" height="622" alt="image" src="https://github.com/user-attachments/assets/f67bb23c-c791-4c39-b68f-c844afee5cc3" />

In saturation region, the channel voltage will remain constant as 'Vgs-Vt', and the drain current will not depend on Vds.
To get drain current equation in saturation region we will replace Vds as Vgs-Vt.


According to the equation, the mosfet acts as perfect current source. But this is not true, when we increase Vds we will that Depletion region at drain increases and so channel length further reduces.Therefore, we see a slight dependency of Vds over Id. This is called "Channel Length Modulation".

 ### Introduction to SPICE
### L1 Basic SPICE setup

<img width="990" height="565" alt="image" src="https://github.com/user-attachments/assets/0c84b06e-0c87-4c8e-94a3-5b3d3a585c12" />

The encircled parameters arwe called spice model parameters. These may or may not be constants.

These are directly coming from the foundary, we don't need to derive them.

<img width="240" height="448" alt="image" src="https://github.com/user-attachments/assets/f038e7f4-4482-4d00-8047-1139db3f5b11" />


### L2 Circuit description in SPICE syntax

To define a spice netlist :

-firstly nodes are identified

 <img width="583" height="388" alt="image" src="https://github.com/user-attachments/assets/6b6dcc11-3517-428b-9dcc-83357b096cf1" />

-nodes are named.

-code is written

<img width="1255" height="586" alt="image" src="https://github.com/user-attachments/assets/562d1285-208e-452e-8af4-8c7bc1397877" />

### L3 Define technology parameters

<img width="514" height="299" alt="image" src="https://github.com/user-attachments/assets/462c5b94-bb37-4fa6-826e-8eeb99004a1d" />

<img width="564" height="228" alt="image" src="https://github.com/user-attachments/assets/ced04329-5c48-46f0-b02d-4e9c3c553a6c" />


 -Stars("*") are used for comments.
 
 -Inside the brackets, technology paramteters will exist. Similarly for pmos also.
 
 -Plugging in the packaged file in .mod file and call this file in top level SPICE netlist.

  ### L4 First SPICE simulation
  <img width="953" height="564" alt="image" src="https://github.com/user-attachments/assets/6e966048-88e1-4c82-8a13-c891c07db18f" />

  <img width="1002" height="548" alt="image" src="https://github.com/user-attachments/assets/02072bf2-1c5d-4911-bd0a-b63adfaeca68" />
  <img width="867" height="679" alt="image" src="https://github.com/user-attachments/assets/6be42a51-c639-49e3-9a51-8c3b22007deb" />


### DAY 2

## DAY 3 - CMOS Switching threshold and dynamic simulations
### Voltage transfer characteristics – SPICE simulations
### L1 SPICE deck creation for CMOS inverter

SPICE Deck
-component connectivity

-component values

-nodes identification

<img width="769" height="591" alt="image" src="https://github.com/user-attachments/assets/bab3f079-6bb8-46bc-9993-c7d2077e52cd" />

-name nodes

<img width="554" height="543" alt="image" src="https://github.com/user-attachments/assets/56fbe28a-9d63-486c-8298-ede7c85dd043" />

Now to write SPICE deck:

<img width="1188" height="468" alt="image" src="https://github.com/user-attachments/assets/cc915119-9604-42de-b76d-c0ba8c07cbba" />

### L2 SPICE simulation for CMOS inverter

Simulation Commands

The gate input voltage sweeps from 0 to 2.5V with steps of 0.05. We need to find the VTC, for this we will be sweeping the input voltage and measuring the output voltage.
Final step is to describe the Model files, all the information about the technological parameteres is given inside the model files.

<img width="1242" height="501" alt="image" src="https://github.com/user-attachments/assets/6b345e40-b79a-4eb6-9d8e-5b55be96c9bf" />

Now, SPICE waveform : Wn=Wp=0.375u, Ln=Lp=0.25u, Wn/ln=Wp/Lp=1.5

<img width="660" height="529" alt="image" src="https://github.com/user-attachments/assets/8316d8cd-91c8-41d3-8f18-6de4f0dd1f5b" />

And, SPICE waveform :  Wn= 0.375u, Wp= 0.9375u, Ln,p=0.25u; Wn/Ln=1.5, Wp/Lp=2.5 (PMOS width is 2.5 times more than NMOS)

<img width="747" height="569" alt="image" src="https://github.com/user-attachments/assets/2d2600b3-35d6-4bcc-b0af-0f1c290cbb7d" />

 -Observation :  the previous graph is left shifted slightly. This happens because NMOS is more stronger than PMOS in previous graph.

### L3 Labs Sky130 SPICE simulation for CMOS

<img width="863" height="718" alt="image" src="https://github.com/user-attachments/assets/22bfe93d-23ec-458c-b39d-92d4b1dc6809" />

### Static behavior evaluation – CMOS inverter robustness – Switching Threshold
###  L1 Switching Threshold, Vm

<img width="1174" height="579" alt="image" src="https://github.com/user-attachments/assets/49611c40-1e8a-4727-9823-1e876fb0c071" />

To find out the Switching threshold, Vm in both the cases by drawing a 45 degree line.
So, in first case Vm comes out to be somewhere around 0.9V and in second case Vm=1.2V.

<img width="1146" height="434" alt="image" src="https://github.com/user-attachments/assets/291353a5-3071-49a2-82ea-d3a4a7a3c867" />

here PMOS and NMOS both are in saturation region.
Current flows from both pmos and nmos

<img width="1100" height="512" alt="image" src="https://github.com/user-attachments/assets/47082040-5cf1-4e14-8f29-c2b137ecad15" />

### L2 Analytical expression of Vm as a function of (W/L)p and (W/L)n

<img width="512" height="253" alt="image" src="https://github.com/user-attachments/assets/517e1180-bc00-4930-9695-e8f5bb7a669e" />

<img width="546" height="211" alt="image" src="https://github.com/user-attachments/assets/d28f524e-e4a5-4037-baf6-72793a5b3388" />

<img width="796" height="225" alt="image" src="https://github.com/user-attachments/assets/c4932e26-8af9-4ecc-9a1a-18b4be1d1eda" />

### L3 Analytical expression of (W/L)p and (W/L)n as a function of Vm

For calculating the value of W/L for PMOS and NMOS when Vm is given.

 letting Switching threshold is exatly half of the power supply Vdd = 2.5V, therefore required Vm = 1.25V.
<img width="900" height="131" alt="image" src="https://github.com/user-attachments/assets/5f5e0153-8ae7-4bd9-8aa3-43fb759f5eb5" />

<img width="837" height="118" alt="image" src="https://github.com/user-attachments/assets/90d8b51f-f8d4-4265-8d93-040fc84c3998" />

<img width="477" height="89" alt="image" src="https://github.com/user-attachments/assets/0123bbb6-4760-452d-87fe-3ad1777aa9ab" />

<img width="760" height="85" alt="image" src="https://github.com/user-attachments/assets/a8b6eb79-0e73-49d3-b66b-e28314cbcd31" />

<img width="503" height="117" alt="image" src="https://github.com/user-attachments/assets/adcc711c-2c5e-42f9-98fa-e9af80a932c1" />

<img width="531" height="139" alt="image" src="https://github.com/user-attachments/assets/1a667d8a-3717-423c-a456-c25c63fb0493" />

As RHS all are constants. So , If we know Vm then we can get the W/L ratios.

<img width="297" height="225" alt="image" src="https://github.com/user-attachments/assets/3509753f-4ecf-4d6b-b5e4-2ff6762125bf" />

### L4 Static and dynamic simulation of CMOS inverter

When Wn/Ln = Wp/Lp = 1.5

<img width="1115" height="554" alt="image" src="https://github.com/user-attachments/assets/e8dcb91a-9e15-426e-89ec-348c60bd9cd1" />

To find Rise time and Fall time => We do transient analysis

<img width="1283" height="482" alt="image" src="https://github.com/user-attachments/assets/5f608a46-9043-4c61-8b1a-2899ce08ab4a" />

###  L5 Static and dynamic simulation of CMOS inverter with increased PMOS width

   Now when Wp/Lp = 2 Wn/Ln
   
   <img width="746" height="603" alt="image" src="https://github.com/user-attachments/assets/dc5ca89c-750d-4cf1-b742-836ddf77e867" />

   When Wp/Lp = 3 Wn/Ln
   
   <img width="694" height="494" alt="image" src="https://github.com/user-attachments/assets/fedd5773-9c80-4e35-b1e9-485275a22b80" />

   When Wp/Lp = 4 Wn/Ln
  
  <img width="686" height="494" alt="image" src="https://github.com/user-attachments/assets/14f9d4d0-266b-4307-bd62-d004d82a6ad3" />

   And when Wp/Lp = 5 Wn/Ln
  
   <img width="886" height="508" alt="image" src="https://github.com/user-attachments/assets/5b7f16df-9837-45a8-9b2e-3d48e33b2f5f" />

   Vm is increasing for the increasing value of width of PMOS transistors as the PMOS has become more stronger and it needs more current to charge the output load    capacitor.
   
<img width="678" height="227" alt="image" src="https://github.com/user-attachments/assets/ea52289b-4a74-47ce-bc10-fffee8ffb6b6" />

Rise delay decreases with increase in PMOS width, this shows the time required to charge the output capacitor decreases significantly this is because we have a bigger area.

 ### L6 Applications of CMOS inverter in clock network and STA

 <img width="1125" height="278" alt="image" src="https://github.com/user-attachments/assets/809717a9-f28a-4322-b833-ad95ba9127de" />

 Key obseravations of the L5 experiments :
 
 -During fabrication, there can be slight variation in sizes of PMOS and NMOS from the required one, but the robustness of CMOS inverter is such that, there is not much difference in the Vm with change in sizes.

-RISE-FALL delay being approximately equal for Wp/Lp = 2 Wn/Ln, shows "Symmetry" of CMOS inverter. This is a typical characteristic of Clock Inverter/buffer where we want the rise delay and fall delay to be equal.

  <img width="1257" height="680" alt="image" src="https://github.com/user-attachments/assets/47e623e1-7e40-4827-9a4e-34b718741935" />

 <img width="1059" height="287" alt="image" src="https://github.com/user-attachments/assets/8fdbd4a8-c86e-43e3-93f4-9e13b8ea35d3" />

<img width="1244" height="667" alt="image" src="https://github.com/user-attachments/assets/c0d1d632-3ac9-45bd-9d65-8f6585d44f3d" />

 




### DAY 4
### DAY 5
## Tools Used
 - Sky130 PDK
 - ngspice
 - noVNC
