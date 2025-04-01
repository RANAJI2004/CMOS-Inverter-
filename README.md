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

First create a library (in my project library name is saksham) 
<img width="922" alt="create library" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/Photo%201.jpg">


