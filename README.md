# CMOS-Inverter-GPDK90-Cadence
Design and analysis of a CMOS inverter using the GPDK 90nm technology in Cadence Virtuoso. Includes transient & DC simulations.

  * [CMOS Inverter](#cmos-inverter)
       * [Creating cmos inverter schematic](#creating-CMOS-Inverter-schematic)
           * [Pre-layout DC Analysis](#pre-layout-dc-analysis)
           * [Pre-layout Transient Analysis](#pre-layout-transient-analysis)
           * [Pre-layout generated netlist](#Pre-layout-generated-netlist)
       * [Post-layout analysis of CMOS Inverter](#Post-layout-analysis-of-CMOS-Inverter)
           * [Post-layout DC Analysis](#post-layout-dc-analysis)
           * [Post-layout Transient Analysis](#post-layout-transient-analysis)
           *  [Generated post-layout netlist](#generated-post-layout-netlist)
       * [Layout vs Schematic report](#layout-vs-schematic-report)

   <a name="cmos-inverter"></a>
 ## CMOS INVERTER

 A CMOS inverter is a type of digital circuit that converts a digital input signal from one state (e.g., 0 or 1) to its opposite state (e.g., 1 or 0). It is a fundamental component of digital electronics that is widely used in digital systems such as microprocessors, digital logic circuits, and digital-to-analog converters.

A CMOS inverter is typically made up of two complementary transistors, one p-type (pMOS) and one n-type (nMOS). The pMOS transistor pulls the output high, while the nMOS transistor pulls the output low. When the inverter's input is high (1), the nMOS transistor is turned on and the pMOS transistor is turned off, resulting in a low output. When the inverter's input is low (0), the pMOS transistor is turned on and the nMOS transistor is turned off, resulting in a high output.

One of the primary advantages of CMOS inverters is their low power consumption, as the transistors are only turned on when the input changes state, rather than constantly drawing current. Moreover, CMOS inverters are highly scalable and easily integrated into larger circuits, making them a popular choice for digital system design.


<a name="creating-cmos-inverter-schematic"></a>
## Creating CMOS Inverter schematic

First Create a Library

<img width="400" alt="create library" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/Photo%201.jpg">

Now  create a cellview for design and give the design name , the schematic i created is shown in the figure

<img width="700" alt="schematic" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/Schematic.jpg">

After creating the schematic , the symbol of the schematic is made 

<img width="700" alt="symbol" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/symbol%20view.jpg">



<a name="pre-layout-dc-analysis"></a>
### Pre-layout DC Analysis
DC analysis is used to generate the Voltage Transfer Characteristics (VTC) curve of the circuit. This involves sweeping Vin across a range of values, from high to low, to observe how the circuit responds at different input voltage levels. 

So to perform DC analysis we have to first make a *testbench* or *simulation* setup on which we will give inputs and measure outputs

<img width="700" alt="testbench" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/inverter%20testbench.jpg">

The Vin is the vpulse with V1=OV , V2=1.8V , Period =20ns , Delay time =0ns , Fall time =1ns and Pulse width =10ns
Vdc is 1.8V
To perform DC analysis we have to go to *Launch*->*ADE L*->*dc* in dc check save operating point and select component parameter as vpulse to do the dc sweep
The DC output comes out to be as shown in below figure

<img width="700" alt="dc response" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/DC%20response.jpg">









