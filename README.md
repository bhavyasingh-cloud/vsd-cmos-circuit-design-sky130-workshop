# vsd-cmos-circuit-design-sky130-workshop
CMOS circuit design and spice simulations using Sky130 technology
## About
This repository contains my work, images and stimulations results from the VSD CMOS Circuit Design and SPICE simulation workshop using Sky130 technology.
## Table Of Contents
### Day 1
- [Basics of NMOS Drain Current (Id) vs Drain-to-source Voltage (Vds)](#ngspicesky130---day-1---basics-of-nmos-drain-current-id-vs-drain-to-source-voltage-vds)
  - [NgspiceSky130_D1SK1 - Introduction to Circuit Design and SPICE simulations](#ngspicesky130_d1sk1---introduction-to-circuit-design-and-spice-simulations)
  - [NgspiceSky130_D1SK2 - NMOS resistive region and saturation region of operation](#ngspicesky130_d1sk2---nmos-resistive-region-and-saturation-region-of-operation)
  - [NgspiceSky130_D1SK3 - Introduction to SPICE](#ngspicesky130_d1sk3---introduction-to-spice)

### Day 2
- [Velocity saturation and basics of CMOS inverter VTC](#ngspicesky130---day-2---velocity-saturation-and-basics-of-cmos-inverter-vtc)
  - [NgspiceSky130_D2SK1 - SPICE simulation for lower nodes and velocity saturation effect](#ngspicesky130_d2sk1---spice-simulation-for-lower-nodes-and-velocity-saturation-effect)
  - [NgspiceSky130_D2SK2 - CMOS voltage transfer characteristics (VTC)](#ngspicesky130_d2sk2---cmos-voltage-transfer-characteristics-vtc)

### Day 3
- [CMOS Switching threshold and dynamic simulations](#ngspicesky130---day-3---cmos-switching-threshold-and-dynamic-simulations)
  - [NgspiceSky130_D3SK1 - Voltage transfer characteristics – SPICE simulations](#ngspicesky130_d3sk1---voltage-transfer-characteristics--spice-simulations)
  - [NgspiceSky130_D3SK2 - Static behavior evaluation – CMOS inverter robustness – Switching Threshold](#ngspicesky130_d3sk2---static-behavior-evaluation--cmos-inverter-robustness--switching-threshold)

### Day 4
- [CMOS Noise Margin robustness evaluation](#ngspicesky130---day-4---cmos-noise-margin-robustness-evaluation)
  - [NgspiceSky130_D4SK1 - Static behavior evaluation – CMOS inverter robustness – Noise margin](#ngspicesky130_d4sk1---static-behavior-evaluation--cmos-inverter-robustness--noise-margin)

### Day 5
- [CMOS power supply and device variation robustness evaluation](#ngspicesky130---day-5---cmos-power-supply-and-device-variation-robustness-evaluation)
  - [NgspiceSky130_D5SK1 - Static behavior evaluation – CMOS inverter robustness – Power supply variation](#ngspicesky130_d5sk1---static-behavior-evaluation--cmos-inverter-robustness--power-supply-variation)
  - [NgspiceSky130_D5SK2 - Static behavior evaluation – CMOS inverter robustness – Device variation](#ngspicesky130_d5sk2---static-behavior-evaluation--cmos-inverter-robustness--device-variation)
    
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


## DAY 2-Velocity saturation and basics of CMOS inverter VTC
### SPICE simulation for lower nodes and velocity saturation effect
### L1 SPICE simulation for lower nodes
This curve is from previous SPICE simulation in which Id is at y-axis and Vds is at x-axis

<img width="1219" height="733" alt="Screenshot 2026-06-05 082454" src="https://github.com/user-attachments/assets/10446a2f-2cc6-47d3-930e-314be5bbfd50" />

the above graph the area left of curve; Vds=Vgs-Vt is Linear region as current is increasing linearly, the area right is Saturation region with slight increase in current due to velocity saturation and below is the Cut off region.Also this case is when the channel length is large.

Now we are taking different W and L, but the ration of W/L is same as previous, so the Id should not change. But this is not the case practically.

Below is the spice deck, where only the values of W and L is changed, rest everything remains same.

<img width="787" height="486" alt="Screenshot 2026-06-05 083333" src="https://github.com/user-attachments/assets/d164e057-a7fe-40cd-8d80-1c258515bea6" />

### L2 Drain current vs gate voltage for long and short channel device
Now we are comparing between Long and Short channel device

<img width="1341" height="715" alt="Screenshot 2026-06-05 082845" src="https://github.com/user-attachments/assets/6d0fe567-63ec-4d3f-b8b5-3946e808be0f" />

Some of the observations are:
1. If we see Id values for different Vgs and for Vds=2.5V, there is a quadratic dependency of Id on Vgs. Whereas for short channel device, at Vds=2.5V, the current is increasing linearly due to velocity saturation.

<img width="1350" height="735" alt="Screenshot 2026-06-05 085153" src="https://github.com/user-attachments/assets/c4390ca0-2275-4861-82df-d2a1eae3bcbe" />

Now we will plot graph of Id vs Vgs and sweeping Vds or keeping Vds constant = 2.5V.

<img width="788" height="491" alt="Screenshot 2026-06-05 091608" src="https://github.com/user-attachments/assets/4f4dba9b-5359-478c-884d-a39203f5a998" />

syntax explains that what will be there on left hand side will be sweeped at every value on right hand side. For example here for every value of Vdd, Vin will be sweeped. The plot we get is quadratic, it is only when Vds=2.5V 

<img width="554" height="442" alt="Screenshot 2026-06-05 091641" src="https://github.com/user-attachments/assets/ee39e779-6ccd-4600-a80e-f5c3984aedd3" />

velocity saturation: is a phenomenon that occurs in short-channel MOSFETs when the electric field in the channel becomes very high.

<img width="1357" height="668" alt="Screenshot 2026-06-05 090333" src="https://github.com/user-attachments/assets/0f81471d-5f82-4030-9530-1a67e5abb93f" />

### L3 Velocity saturation at lower and higher electric fields
For short channel we will see more of a linear behaviour as the Vgs increases. This is due to velocity saturation effect.

<img width="986" height="488" alt="Screenshot 2026-06-05 092209" src="https://github.com/user-attachments/assets/a756b1e8-ceb5-40b1-b728-13c93aae4edf" />

We know velocity and electric field are related to each other with equation v=uE, where v is velocity, E is electric field and u is mobility. Velocity increases linearly with electric field over certain electric field value after which it gets saturated. This is due to scattering at higher fields and mobility decreases. 

<img width="891" height="471" alt="Screenshot 2026-06-05 092308" src="https://github.com/user-attachments/assets/4cc40e7b-d9f5-4d4e-b479-eb8960d22551" />

Velocity saturation happens for higher gate-source voltages.

<img width="925" height="438" alt="Screenshot 2026-06-05 092332" src="https://github.com/user-attachments/assets/119799a3-a545-4a39-8ca2-20de74831052" />

<img width="949" height="418" alt="Screenshot 2026-06-05 092410" src="https://github.com/user-attachments/assets/fa7b0b01-5235-463b-9931-8d87687fc1b3" />

### L4 Velocity saturation drain current model
Let us take Vgs-Vt=Vgt because we will be taking Vgs as large values. Current equation we will be using as shown above, For lower values of Vds we will neglect the 'lambda' term.

There is one more technology paramter which is "Vdsat", it is the velocity of gate when the device just enters the Velocity saturation region.

<img width="820" height="190" alt="Screenshot 2026-06-05 092923" src="https://github.com/user-attachments/assets/2823e681-b37d-4051-834c-3d8dde8bbdd9" />

Saturation region:

<img width="995" height="523" alt="Screenshot 2026-06-05 092959" src="https://github.com/user-attachments/assets/14c3f128-99e2-48b8-9417-bb8b7067277d" />

Resistive region:

<img width="1043" height="526" alt="Screenshot 2026-06-05 093011" src="https://github.com/user-attachments/assets/3ac59572-cdd7-4f0a-85f7-fc9a6473c67b" />

Veocity Saturation region:

<img width="1200" height="573" alt="Screenshot 2026-06-05 093057" src="https://github.com/user-attachments/assets/c49219dc-7a8b-4e9d-86ae-21bb3da75ec5" />

In the above equation, it seems when W is constant and L is lowered then Id should increase, But it is not so practically.

Observation 2 - The saturation current for lower nodes is low instead of being high. This is because Velocity saturation tends to saturate the device early so the peak current we see for lower nodes is much lesser than for higher nodes. 

<img width="1274" height="561" alt="Screenshot 2026-06-05 093531" src="https://github.com/user-attachments/assets/545421cc-182c-4f35-916a-7b36d9db1d55" />

### L5 Labs Sky130 Id-Vgs

<img width="1461" height="645" alt="image" src="https://github.com/user-attachments/assets/ecc712f4-2ac5-4fca-9688-c5384a0437ae" />


<img width="1537" height="639" alt="image" src="https://github.com/user-attachments/assets/eeaefb61-d7bf-4a9e-af55-664eb8417635" />



### L6 Labs Sky130 Vt
<img width="917" height="742" alt="image" src="https://github.com/user-attachments/assets/92208646-1be8-4695-a00b-76e115b972fd" />

<img width="1111" height="638" alt="image" src="https://github.com/user-attachments/assets/8f93a5ee-3684-4311-8592-a8fc77dacdbf" />


### CMOS voltage transfer characteristics (VTC)
### L1 MOSFET as a switch
We will now look at the device parameters from the switch point of view.

<img width="877" height="360" alt="Screenshot 2026-06-05 094159" src="https://github.com/user-attachments/assets/29bfcea8-0d15-41ea-bc35-ea7afa029b56" />

When |Vgs|<Vt, device is OFF and it acts as open switch
When |Vgs|>Vt, device is ON and it acts as closed switch

<img width="1082" height="591" alt="image" src="https://github.com/user-attachments/assets/4ab676ad-bf29-42e3-bddd-438e51d3ed40" />

### L2 Introduction to standard MOS voltage current parameters

We are trying to get the equivalent circuit of CMOS when Vin is 'high' and 'low', so that we can get the Voltage Transfer Characteristics (VTC) and therefore calculate the delay of the cell.
 
1. When we take Vin as 'high' and equal to Vdd, PMOS will be OFF and NMOS will be ON.
2. When we take Vin as 'low' or equal to '0', PMOS will be ON and NMOS will be OFF. 

<img width="1157" height="610" alt="image" src="https://github.com/user-attachments/assets/65ac88ef-2cde-4d30-9a6b-bd3bad8a93e7" />

1. when Vin=Vdd there is a direct path that exists between Vss and Vout, the capacitor CL discharges through the resistor.
2. when Vin=0 there is a direct path between Vdd and Vout, CL charges.

Let us give the naming convention of the CMOS:

<img width="477" height="591" alt="image" src="https://github.com/user-attachments/assets/ad029fdb-9ee6-4e73-871d-e271b2b72273" />

 current in both the condition is Idsn(drain to source for NMOS) and Idsp(Drain to source for PMOS) And Idsp = -Idsn, both are opposite in direction to each other.

 ### L3 PMOS/NMOS drain current vs drain voltage

 <img width="378" height="591" alt="image" src="https://github.com/user-attachments/assets/9e3e1b01-f900-4f1a-8b4e-afbf3c1ecc10" />

 The curve between Idsn Vs Vdsn and Idsp Vs Vdsp, it is as shown below.

 <img width="838" height="423" alt="image" src="https://github.com/user-attachments/assets/f4e784ed-f881-437e-92a6-9812decaabba" />

### L4 Step1- Convert PMOS gate-source-voltage to Vin

We have seen various internal voltages, but actually in terms of user's perspective we can't see the internal voltages and only see the external Vin and Vout. From these we calculate the VTC and eventually we get to know the delay.

Now we will see the steps to obtain Voltage Transfer Characteristics(VTC) for static CMOS inverter: Assumption: Let us assume that it is a long channel device with Vdd=2V

<img width="351" height="229" alt="image" src="https://github.com/user-attachments/assets/186d48ed-baf2-42f2-aa93-3095041d3490" />

We will fix the Vgs values as shown below 
We know that Vgsp= Vin-Vdd, So we get the above values.So we get Vin = Vgsp+Vdd, we are trying to convert all the voltages as function of Vin and Vout.
We will try to plot the graph of PMOS in terms of Idsn, the plot will be as shown below. We can see that the corresponding Vin value of Vgsp is being plotted as shown in the above table.

<img width="821" height="423" alt="image" src="https://github.com/user-attachments/assets/d295a218-6464-4298-aeec-e807037d1664" />

### L5 Step2 & Step3- Convert PMOS and NMOS drain-source-voltage to Vout
Now we will be converting the Vdsp and function of output voltage Vin. We know Vdsp = Vout-Vdd.
Let us convert Vdsp into Vout. So to get Vout there is a shift of Vdd towards left hand side.

<img width="1320" height="385" alt="image" src="https://github.com/user-attachments/assets/ae4dd0d4-12e9-4aa4-9d7f-92fa7e5014b4" />

We can see that whenever Vout=2V that means Vdsp=0V and Vdd=2V (given), then The current is zero and capacitor at the output is discharged. This is true only when PMOS is in combination with NMOS and forms a CMOS inverter.

Let us take another example, when Vout=0V, that means -Vdsp=2V and Vdd=2V, so at every gate voltage of Vin we will see a finite current whenever Vout=0V. As Vout=0V, the capacitor is completely discharged and we need to charge that, so that is the charging current required. 
So, here we get the load curve for PMOS

<img width="499" height="386" alt="image" src="https://github.com/user-attachments/assets/c074b5bf-1069-4c1b-a9b0-a9fa4ce9a29e" />

Now we will try to get the "load curve" for NMOS transistor from this equations.

<img width="220" height="65" alt="image" src="https://github.com/user-attachments/assets/87150da9-8436-4e7d-a012-f4cd6baf490a" />

It is actually simple as Vgsn = Vin and Vdsn = Vout, directly we can get the graphs.

<img width="401" height="283" alt="image" src="https://github.com/user-attachments/assets/920c0822-7bb1-433f-aa13-0e1eb6f7b657" />

<img width="875" height="369" alt="image" src="https://github.com/user-attachments/assets/19e4b690-dbfe-4244-b268-a03f38ccdcb5" />

### L6 Step4- Merge PMOS-NMOS load curves and plot VTC
Now,merge the above two curves and obtain the voltage transfer characteristics(VTC) for CMOS inverter.

<img width="964" height="288" alt="image" src="https://github.com/user-attachments/assets/7eabf5f5-ae93-4c64-bd35-0f8dbe32016c" />

find out the common point between Vin and Vout of both NMOS and PMOS.

<img width="425" height="272" alt="image" src="https://github.com/user-attachments/assets/1f0b96b1-df76-4fa4-b71c-3555350d4341" />

So the range of Vin and Vout is 0V-2V.

When Vin = 0V, Vout = 2V; NMOS is Cut Off and PMOS is in Linear region.
When Vin = 0.5V, 1.5V<Vout<2V; NMOS is in Saturation region and PMOS is in Linear region.
When Vin = 1V, 0.5V<Vout<1.5V; NMOS and PMOS are in Saturation region.
When Vin = 1.5V, 0<Vout<0.5V; NMOS is Linear region and PMOS is in Saturation region.
When Vin = 2V, Vout = 0V; NMOS is in linear region and PMOS is Cut Off.

<img width="1091" height="508" alt="image" src="https://github.com/user-attachments/assets/06cf38f2-b4bf-44c7-a1f8-c92c266eb17f" />



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

<img width="750" height="804" alt="image" src="https://github.com/user-attachments/assets/59854022-fb6a-4c0e-8a71-4a3ed8bd5971" />

<img width="941" height="801" alt="image" src="https://github.com/user-attachments/assets/f4a6da85-01db-4d4e-97b6-d1d53fd5a7a9" />

<img width="1134" height="650" alt="image" src="https://github.com/user-attachments/assets/88fa5a9e-f681-4f74-bfb7-b4822af9a557" />

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

 

## DAY 4-CMOS Noise Margin robustness evaluation
### Static behaviour evaluation-CMOS inverter robustness-Noise Margin
### L1 Introduction to Noise Margin
Now we will learn CMOS inverter's robustness towards the Noise Margin. Also we see the Noise margin evaluation for CMOS inverter. 

Noise Margin: It is a measure of how much unwanted electrical noise a logic circuit can tolerate on its input without producing an incorrect output. 
For example if we consider an ideal Inverter, for inputs 0/1 it gives output as 1/0. The slope of switch is infinite. 
But practically the slope won't be infinite, due to presence of resistances and capacitances there will be delay. Therefore we will get a finite slope 

<img width="911" height="571" alt="Screenshot 2026-06-05 115433" src="https://github.com/user-attachments/assets/463695c4-ea83-489a-8003-45a1704a281d" />

whenever the input is between 0 to VIL(input low voltage); the output will be VOH(output high). 
And whenever the input is between VIH(input high voltage) and Vdd; output will be VOL(output low voltage). 

<img width="799" height="624" alt="Screenshot 2026-06-05 115556" src="https://github.com/user-attachments/assets/3a103fc7-12e7-48f7-be79-b141cc6304b3" />

### L2 Noise Margin voltage paramters
Considering the more practical scenarios and non idealities of an inverter, the curve we get is as shown below. So here the when the 0 output is VOH output is 0VOL as VOH will be output high for the next inverter which will be connected and 0 as it will be the output low for the next inverter. 
Also, the slope is approximately -1, as for increase in input, output is reducing. 

<img width="964" height="628" alt="Screenshot 2026-06-05 120022" src="https://github.com/user-attachments/assets/6d6b3d8d-7497-4c38-b422-62eda7c04c6f" />

### L3 Noise margin equation and summary
Now we will calculate the noise margin equation, for that we will plot the voltages on the same scale.

<img width="700" height="404" alt="image" src="https://github.com/user-attachments/assets/f6e45cf0-689f-4804-9071-a90bedb4ff9c" />

Noise margin High NH - value between VIH and VOH. 
Noise Margin Low NL - value between VIL and VOL. 

Any value which lies in between noise margins is considered either 1/0 and considered to be tolerable. Apart from this region the value is "Undefined" and the logic level can swing between 'high' and 'low'.

<img width="841" height="521" alt="Screenshot 2026-06-05 120252" src="https://github.com/user-attachments/assets/04c18e50-b0c3-457e-b2c2-8e2348dd77a1" />

<img width="888" height="548" alt="Screenshot 2026-06-05 120752" src="https://github.com/user-attachments/assets/f6105724-b4d2-4528-b4dc-decc920a4065" />

### L4 Noise margin variation with respect to PMOS width
We will evaluate the noise margin depending upon the PMOS width and ultimately prove that how CMOS inverter is robust to the noise margins.
First, we will find the points where the slope = -1 and extend the lines towards x-y axis.

<img width="1307" height="712" alt="Screenshot 2026-06-05 121139" src="https://github.com/user-attachments/assets/ed1716ee-9e30-46b9-8a22-0004ff17197c" />

<img width="1326" height="587" alt="Screenshot 2026-06-05 133257" src="https://github.com/user-attachments/assets/6cb14026-fe48-4390-813d-fd181451ba9e" />

<img width="1328" height="575" alt="Screenshot 2026-06-05 133324" src="https://github.com/user-attachments/assets/352be46a-f199-4de7-9084-35d43a69471e" />

<img width="1314" height="601" alt="Screenshot 2026-06-05 133356" src="https://github.com/user-attachments/assets/a4a4e7f7-61c3-4dac-806e-7e808ae4d732" />

<img width="1307" height="587" alt="Screenshot 2026-06-05 133417" src="https://github.com/user-attachments/assets/02bf165f-6b52-43f0-85e1-6d2a01d95700" />

For (W/L)p=4(W/L)p and (W/L)p=5(W/L)p noise margins are same, so even if we increase the widths further noise margin will be static. 

<img width="761" height="289" alt="Screenshot 2026-06-05 121227" src="https://github.com/user-attachments/assets/68735092-c2a3-4ed0-bd26-bb8933d0efea" />

Here also we can verify the robustness of CMOS inverter. 
Also we come to know the ranges for "Digital design" and "Analog design" in the CMOS inverter.

<img width="1201" height="634" alt="Screenshot 2026-06-05 133755" src="https://github.com/user-attachments/assets/d255c8f6-46e7-4425-8f0e-46c6f503b5cf" />

<img width="1193" height="621" alt="image" src="https://github.com/user-attachments/assets/952e5e9a-72f2-4d2c-95d8-e0eda183a8fd" />

### L5 Sky130 Noise margin labs
We will now plot Noise margins
<img width="705" height="796" alt="image" src="https://github.com/user-attachments/assets/055c01cd-de52-40af-bd53-41e125be380e" />

<img width="1192" height="809" alt="image" src="https://github.com/user-attachments/assets/74bd3a8c-68dc-4b5b-a60a-8c5ed2ec1123" />

<img width="1026" height="612" alt="image" src="https://github.com/user-attachments/assets/2e2a57bb-6f0c-489a-b604-ce1002260dc0" />


## DAY 5 - CMOS power supply and device variation robustness evaluation

 ### Static behavior evaluation – CMOS inverter robustness – Power supply variation
 ### L1 Smart SPICE simulation for power supply variations
 
 As technology scales, the supply voltage is reduced to lower power consumption.

 To study the robustness of the CMOS inverter, the supply voltage was varied from 1.8 V to lower values while observing the Voltage Transfer Characteristics (VTC). Ideally, reducing the supply voltage should not significantly alter the inverter's switching behavior.
 
 <img width="1123" height="685" alt="image" src="https://github.com/user-attachments/assets/7e63fe80-ab67-4325-b88a-a9734fec652c" />


 <img width="808" height="449" alt="image" src="https://github.com/user-attachments/assets/4f862ac7-e3e7-4465-be17-032b5c9d0c7d" /> 
 
 Here we will do some scripting under ".control" and ".endc" . All the other commands will remain same as they were previously.

 <img width="738" height="563" alt="image" src="https://github.com/user-attachments/assets/031eafef-bc6d-4655-8195-8560f5225971" />
 
 The above plot shows the changes in CMOS curves as we chnage the supply voltages while the width of the channel is kept constant.

 ### L2 Advantages and disadvantages using low supply voltage
  <img width="876" height="543" alt="image" src="https://github.com/user-attachments/assets/0f4eab6a-1791-4b56-ab0b-18d3e522ddd8" />
  <img width="907" height="553" alt="image" src="https://github.com/user-attachments/assets/ddc4de95-459c-4ca8-964b-993b8b6d22f5" />

  <img width="623" height="183" alt="image" src="https://github.com/user-attachments/assets/48546de0-3a46-47fe-b082-4ee30d3b441f" />

  Along with the advantages of operation at 0.5v over 2.5, there are also certain disadvantages. that's why it 0.5V is not commmonly used in operating devices.

  <img width="958" height="547" alt="image" src="https://github.com/user-attachments/assets/28f44eb1-e720-4f2d-bbcc-d4b350e7110e" />

 The main disadvantage is the rise and fall delay due to which load capacitance doesn't even get enough time for charging and dischanging.
 Ths causes major performance impact.

### L3 Sky130 Supply Variation Labs

<img width="1600" height="770" alt="image" src="https://github.com/user-attachments/assets/c96c82d4-bebf-4cc0-b097-78c957e321b8" />

<img width="1111" height="812" alt="image" src="https://github.com/user-attachments/assets/e619fbe1-50a8-4eb1-ab9f-9318c7144498" />

<img width="1047" height="809" alt="image" src="https://github.com/user-attachments/assets/8131dac0-dd12-450c-99c5-2c09a9ec4a2f" />

<img width="1277" height="702" alt="image" src="https://github.com/user-attachments/assets/24cfe18d-b8f5-4a43-9c69-280da40ffe9d" />


### Static behavior evaluation – CMOS inverter robustness – Device variation

### L1 Sources of variation – Etching process

During fabrication, the gate dimensions may change. Etching is one of the sources of variation.

<img width="1147" height="619" alt="image" src="https://github.com/user-attachments/assets/37cb71a9-e050-495c-a263-009a93182a9c" />

For a single inverter layout, we see the length of gate, the width(common area between polysilicon and diffusion). Due to etching process there can be a variation in length and width of CMOS.

<img width="1269" height="648" alt="image" src="https://github.com/user-attachments/assets/b55b6457-d26b-4cd3-8ea7-09bc3ae0c729" />



<img width="1253" height="671" alt="image" src="https://github.com/user-attachments/assets/35733311-c5f3-47d9-9e94-a9164f27246e" />

We will get a very different kind of distorted structure at the leftmost side to the rightmost side of the chain imverters.
While the middle portion structure remains the same.

The variation in L and W can change the drain current of CMOS inverter.

<img width="912" height="604" alt="image" src="https://github.com/user-attachments/assets/551d4356-121a-4146-8944-3f020c583a30" />

### L2 Sources of variation – oxide thickness

Oxide thickness is another source of variation.
Here is the cross sectional view of the mosfet:
<img width="967" height="544" alt="image" src="https://github.com/user-attachments/assets/dd9df165-c4d9-4256-b8c1-132879d9d0c5" />

 The oxide under polysilicon gate, while fabricating the thickness can vary. There is a difference between ideal thickness and actual thickness.
Similar to the previous case, the variation in structure at the left and right most side is more. While the middle portion structure remains the same.

<img width="1293" height="625" alt="image" src="https://github.com/user-attachments/assets/65c43d3f-57cc-44f9-b6c7-e3bd0652fc33" />

<img width="766" height="106" alt="image" src="https://github.com/user-attachments/assets/028a1c7c-1bf0-49c3-83a3-2f7ef36bd845" />

### L3 Smart SPICE simulation for device variations
nNow we have to see how does the change in drain current affects the behaviour of the CMOS.
Ideally it should be least responsive towards the device variations.
We will experimentally see the dc curve variations with respect to the device variations.

<img width="1128" height="503" alt="image" src="https://github.com/user-attachments/assets/9373674b-a1ed-482d-a1da-3a193bc42226" />

Strong PMOS means it has the least resistance value 
Weak NMOS means it has the highest resistance value.
And vice versa.

<img width="521" height="453" alt="image" src="https://github.com/user-attachments/assets/203972a5-fd2f-4d47-ad4b-d83624be1c5d" />
<img width="701" height="433" alt="image" src="https://github.com/user-attachments/assets/8f439d9e-8b7a-4687-9ea0-5c56cb7268ca" />



<img width="737" height="573" alt= "image" src="https://github.com/user-attachments/assets/895b9014-d52d-4fc1-b93c-cd85e5974e8a" />

 ### L4 Conclusion
 
Here, we will be looking for two parameters to study the robustness of CMOS inverter :
-Noise margin
-Switching threshold

<img width="1088" height="537" alt="image" src="https://github.com/user-attachments/assets/3f818b33-ea80-44e8-8821-f219416d1c0a" />

The Switching threshold 'Vm' is shifted right in case of strong PMOS and shifted left in case of Strong NMOS.

<img width="950" height="532" alt="image" src="https://github.com/user-attachments/assets/15de20c8-d5a0-499d-ae17-5c23f81caf1b" />

As we see there is not much variation in Noise Margins in both the extreme cases, that means it behaves as a robust inverter in both the cases.

### L5 Sky130 Device Variation Labs

<img width="1024" height="800" alt="image" src="https://github.com/user-attachments/assets/83f1c209-bacf-4328-9fbb-8b1639de593f" />

<img width="1113" height="805" alt="image" src="https://github.com/user-attachments/assets/97f13543-73d6-4e79-bcb1-3e0ced83c358" />

<img width="1055" height="742" alt="image" src="https://github.com/user-attachments/assets/6fd23148-2a5a-442d-a475-07dc321a7b59" />


## Tools Used
 - Sky130 PDK
 - ngspice
 - noVNC
