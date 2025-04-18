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

<img width="700" alt="testbench" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/testbench.png">

The Vin is the vpulse with V1=0V , V2=1.8V , Period =20ns , Delay time =0ns , Fall time =1ns and Pulse width =10ns
Vdc is 1.8V
To perform DC analysis we have to go to *Launch*->*ADE L*->*dc* in dc check save operating point and select component parameter as vpulse to do the dc sweep
The DC output comes out to be as shown in below figure

<img width="700" alt="dc response" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/Vol%2CVoh%2CVth.png">

Vol(output low voltage)=86.5uV

Voh(output high voltage) =1.798V

### d(vout) vs Vin 
<img width="700" alt="dc response" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/Vih%20%2CVil.png">

Vil=403.2mV 

Vih=884.71mV

### Noise Margin Calculation

NM(L)=Vil-Vol = 403.2mV-86.5uV =0.403V

NM(H) =Voh-Vih = 1.798V-884.71mV=0.9329V



### Pre-layout Transient Analysis
Transient analysis examines the time-dependent behavior of a CMOS inverter when subjected to a dynamic input signal. It helps in understanding how the output voltage transitions between logic levels and how long it takes for these transitions to occur. This analysis is essential for evaluating key performance metrics such as propagation delay, rise time, and fall time, which impact the overall speed and efficiency of digital circuits.
The Vin is the vpulse with following parameter 

<img width="500" alt="vpulse for transient" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/vpulse%20for%20transient.png">

 To perform transient analysis we have to go to *Launch* -> *ADE L* ->*trans* ,we are performing transient analysis for 200ns, the output of the transient response comes out to be 
 
 <img width="700" alt="transient response" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/transient%20analysis.png">

### Finding out Tphl , Tplh and Tp (Propagation delay)

<img width="500" alt="Propagation delay" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/Thl.png">

<img width="500" alt="Propagation delay" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/Tlh.png">

Tphl = (120.531-120.499)ns = 32 ps 

Tplh = (11.804-11.4992)ns = 304ps

Tp=(Tphl+Tplh)/2 = 168 ps

 ### Pre-layout generated netlist
 ```
Cadence (R) Virtuoso (R) Spectre (R) Circuit Simulator
Version 12.1.0.347.isr3 32bit -- 10 Jan 2013
Copyright (C) 1989-2012 Cadence Design Systems, Inc. All rights reserved worldwide. Cadence, Virtuoso and Spectre are registered trademarks of Cadence Design Systems, Inc. All others are the property of their respective holders.

Protected by U.S. Patents: 
        5,610,847; 5,790,436; 5,812,431; 5,859,785; 5,949,992; 5,987,238; 
        6,088,523; 6,101,323; 6,151,698; 6,181,754; 6,260,176; 6,278,964; 
        6,349,272; 6,374,390; 6,493,849; 6,504,885; 6,618,837; 6,636,839; 
        6,778,025; 6,832,358; 6,851,097; 6,928,626; 7,024,652; 7,035,782; 
        7,085,700; 7,143,021; 7,493,240; 7,571,401.

Includes RSA BSAFE(R) Cryptographic or Security Protocol Software from RSA Security, Inc.

User: buet   Host: cadence   HostID: 7F0100   PID: 3686
Memory  available: 619.1145 MB  physical: 1.6003 GB
CPU Type: 13th Gen Intel(R) Core(TM) i5-13450HX
          Processor PhysicalID CoreID Frequency
              0         -        -     2611.2
              1         -        -     2611.2


Simulating `input.scs' on cadence at 6:53:25 PM, Sun Apr 13, 2025 (process id: 3686).
Current working directory: /home/buet/simulation/inverter_tb/spectre/schematic/netlist.
Command line:
    /home/buet/cadence/MMSIM121/tools.lnx86/spectre/bin/32bit/spectre  \
        input.scs +escchars +log ../psf/spectre.out +inter=mpsc  \
        +mpssession=spectre2_3255_3 -format psfxl -raw ../psf  \
        +lqtimeout 900 -maxw 5 -maxn 5
spectre pid = 3686

Loading /home/buet/cadence/MMSIM121/tools.lnx86/cmi/lib/5.0/libinfineon_sh.so ...
Loading /home/buet/cadence/MMSIM121/tools.lnx86/cmi/lib/5.0/libphilips_o_sh.so ...
Loading /home/buet/cadence/MMSIM121/tools.lnx86/cmi/lib/5.0/libphilips_sh.so ...
Loading /home/buet/cadence/MMSIM121/tools.lnx86/cmi/lib/5.0/libsparam_sh.so ...
Loading /home/buet/cadence/MMSIM121/tools.lnx86/cmi/lib/5.0/libstmodels_sh.so ...
Reading file:  /home/buet/simulation/inverter_tb/spectre/schematic/netlist/input.scs
Reading file:  /home/buet/cadence/gpdk090_v4.6/models/spectre/gpdk090.scs
Reading file:  /home/buet/cadence/gpdk090_v4.6/models/spectre/gpdk090_mos.scs
Reading file:  /home/buet/cadence/gpdk090_v4.6/models/spectre/gpdk090_mos_iso.scs
Reading file:  /home/buet/cadence/gpdk090_v4.6/models/spectre/gpdk090_resistor.scs
Reading file:  /home/buet/cadence/gpdk090_v4.6/models/spectre/resd_va.va
Reading link:  /home/buet/cadence/MMSIM121/tools.lnx86/spectre/etc/ahdl/discipline.h
Reading file:  /home/buet/cadence/MMSIM121/tools.lnx86/spectre/etc/ahdl/disciplines.vams
Reading link:  /home/buet/cadence/MMSIM121/tools.lnx86/spectre/etc/ahdl/constants.h
Reading file:  /home/buet/cadence/MMSIM121/tools.lnx86/spectre/etc/ahdl/constants.vams
Reading file:  /home/buet/cadence/gpdk090_v4.6/models/spectre/rnoise_va.va
Reading file:  /home/buet/cadence/gpdk090_v4.6/models/spectre/gpdk090_capacitor.scs
Reading file:  /home/buet/cadence/gpdk090_v4.6/models/spectre/gpdk090_diode.scs
Reading file:  /home/buet/cadence/gpdk090_v4.6/models/spectre/gpdk090_bipolar.scs

Time for NDB Parsing: CPU = 316.951 ms, elapsed = 313.651 ms.
Time accumulated: CPU = 316.951 ms, elapsed = 313.651 ms.
Peak resident memory used = 32.2 Mbytes.


Time for Elaboration: CPU = 7.999 ms, elapsed = 8.61096 ms.
Time accumulated: CPU = 324.95 ms, elapsed = 322.456 ms.
Peak resident memory used = 34.7 Mbytes.


Time for EDB Visiting: CPU = 0 s, elapsed = 288.963 us.
Time accumulated: CPU = 325.949 ms, elapsed = 322.99 ms.
Peak resident memory used = 35.1 Mbytes.


Warning from spectre during initial setup.
    WARNING (CMI-2477): I10.PM0: `Rds' = 70.9091 uOhm is less than 0.001. Set to 0.


Circuit inventory:
              nodes 3
            bsim3v3 2     
          capacitor 1     
            vsource 2     


Warning from spectre during initial setup.
    WARNING (CMI-2477): I10.PM0: `Rds' = 70.9091 uOhm is less than 0.001. Set to 0.


Time for parsing: CPU = 1 ms, elapsed = 2.40397 ms.
Time accumulated: CPU = 326.949 ms, elapsed = 325.582 ms.
Peak resident memory used = 35.8 Mbytes.

Entering remote command mode using MPSC service (spectre, ipi, v0.0, spectre2_3255_3, ).

Warning from spectre.
    WARNING (SPECTRE-16707): Only tran supports psfxl format, result of other analyses will be in psfbin format.


*************************************************
Transient Analysis `tran': time = (0 s -> 200 ns)
*************************************************
DC simulation time: CPU = 0 s, elapsed = 187.159 us.
Important parameter values:
    start = 0 s
    outputstart = 0 s
    stop = 200 ns
    step = 200 ps
    maxstep = 4 ns
    ic = all
    useprevic = no
    skipdc = no
    reltol = 1e-03
    abstol(V) = 1 uV
    abstol(I) = 1 pA
    temp = 27 C
    tnom = 27 C
    tempeffects = all
    errpreset = moderate
    method = traponly
    lteratio = 3.5
    relref = sigglobal
    cmin = 0 F
    gmin = 1 pS

    tran: time = 8.33 ns     (4.17 %), step = 3.655 ns     (1.83 %)
    tran: time = 16.62 ns    (8.31 %), step = 2.127 ns     (1.06 %)
    tran: time = 27.53 ns    (13.8 %), step = 3.254 ns     (1.63 %)
    tran: time = 36.88 ns    (18.4 %), step = 2.261 ns     (1.13 %)
    tran: time = 47.35 ns    (23.7 %), step = 3.163 ns     (1.58 %)
    tran: time = 56.97 ns    (28.5 %), step = 2.303 ns     (1.15 %)
    tran: time = 67.25 ns    (33.6 %), step = 3.114 ns     (1.56 %)
    tran: time = 77.03 ns    (38.5 %), step = 2.333 ns     (1.17 %)
    tran: time = 87.16 ns    (43.6 %), step = 3.07 ns      (1.53 %)
    tran: time = 97.09 ns    (48.5 %), step = 2.365 ns     (1.18 %)
    tran: time = 107.4 ns    (53.7 %), step = 3.207 ns      (1.6 %)
    tran: time = 116.9 ns    (58.5 %), step = 2.286 ns     (1.14 %)
    tran: time = 127.3 ns    (63.6 %), step = 3.136 ns     (1.57 %)
    tran: time = 137 ns      (68.5 %), step = 2.327 ns     (1.16 %)
    tran: time = 147.2 ns    (73.6 %), step = 3.08 ns      (1.54 %)
    tran: time = 157 ns      (78.5 %), step = 2.343 ns     (1.17 %)
    tran: time = 167.1 ns    (83.6 %), step = 3.054 ns     (1.53 %)
    tran: time = 177.1 ns    (88.5 %), step = 2.368 ns     (1.18 %)
    tran: time = 187.4 ns    (93.7 %), step = 3.201 ns      (1.6 %)
    tran: time = 196.9 ns    (98.5 %), step = 2.289 ns     (1.14 %)
Number of accepted tran steps =             522

Notice from spectre during transient analysis `tran'.
    Trapezoidal ringing is detected during tran analysis.
        Please use method=trap for better results and performance.

Initial condition solution time: CPU = 0 s, elapsed = 208.855 us.
Intrinsic tran analysis time:    CPU = 110.983 ms, elapsed = 120.538 ms.
Total time required for tran analysis `tran': CPU = 110.983 ms, elapsed = 121.51 ms.
Time accumulated: CPU = 439.932 ms, elapsed = 478.203 ms.
Peak resident memory used = 37.3 Mbytes.

finalTimeOP: writing operating point information to rawfile.

******************
DC Analysis `dcOp'
******************
Important parameter values:
    reltol = 1e-03
    abstol(V) = 1 uV
    abstol(I) = 1 pA
    temp = 27 C
    tnom = 27 C
    tempeffects = all
    gmindc = 1 pS
Convergence achieved in 6 iterations.
Total time required for dc analysis `dcOp': CPU = 1 ms, elapsed = 1.37901 ms.
Time accumulated: CPU = 443.932 ms, elapsed = 492.113 ms.
Peak resident memory used = 37.4 Mbytes.

dcOpInfo: writing operating point information to rawfile.

****************************************
DC Analysis `dc': V0:dc = (0 V -> 1.8 V)
****************************************
Important parameter values:
    reltol = 1e-03
    abstol(V) = 1 uV
    abstol(I) = 1 pA
    temp = 27 C
    tnom = 27 C
    tempeffects = all
    gmindc = 1 pS
    dc: dc = 72 mV          (4 %), step = 36 mV           (2 %)
    dc: dc = 108 mV         (6 %), step = 36 mV           (2 %)
    dc: dc = 144 mV         (8 %), step = 36 mV           (2 %)
    dc: dc = 180 mV        (10 %), step = 36 mV           (2 %)
    dc: dc = 216 mV        (12 %), step = 36 mV           (2 %)
    dc: dc = 252 mV        (14 %), step = 36 mV           (2 %)
    dc: dc = 288 mV        (16 %), step = 36 mV           (2 %)
    dc: dc = 324 mV        (18 %), step = 36 mV           (2 %)
    dc: dc = 360 mV        (20 %), step = 36 mV           (2 %)
    dc: dc = 396 mV        (22 %), step = 36 mV           (2 %)
    dc: dc = 432 mV        (24 %), step = 36 mV           (2 %)
    dc: dc = 468 mV        (26 %), step = 36 mV           (2 %)
    dc: dc = 504 mV        (28 %), step = 36 mV           (2 %)
    dc: dc = 540 mV        (30 %), step = 36 mV           (2 %)
    dc: dc = 576 mV        (32 %), step = 36 mV           (2 %)
    dc: dc = 612 mV        (34 %), step = 36 mV           (2 %)
    dc: dc = 648 mV        (36 %), step = 36 mV           (2 %)
    dc: dc = 684 mV        (38 %), step = 36 mV           (2 %)
    dc: dc = 720 mV        (40 %), step = 36 mV           (2 %)
    dc: dc = 756 mV        (42 %), step = 36 mV           (2 %)
    dc: dc = 792 mV        (44 %), step = 36 mV           (2 %)
    dc: dc = 828 mV        (46 %), step = 36 mV           (2 %)
    dc: dc = 864 mV        (48 %), step = 36 mV           (2 %)
    dc: dc = 900 mV        (50 %), step = 36 mV           (2 %)
    dc: dc = 936 mV        (52 %), step = 36 mV           (2 %)
    dc: dc = 972 mV        (54 %), step = 36 mV           (2 %)
    dc: dc = 1.008 V       (56 %), step = 36 mV           (2 %)
    dc: dc = 1.044 V       (58 %), step = 36 mV           (2 %)
    dc: dc = 1.08 V        (60 %), step = 36 mV           (2 %)
    dc: dc = 1.116 V       (62 %), step = 36 mV           (2 %)
    dc: dc = 1.152 V       (64 %), step = 36 mV           (2 %)
    dc: dc = 1.188 V       (66 %), step = 36 mV           (2 %)
    dc: dc = 1.224 V       (68 %), step = 36 mV           (2 %)
    dc: dc = 1.26 V        (70 %), step = 36 mV           (2 %)
    dc: dc = 1.296 V       (72 %), step = 36 mV           (2 %)
    dc: dc = 1.332 V       (74 %), step = 36 mV           (2 %)
    dc: dc = 1.368 V       (76 %), step = 36 mV           (2 %)
    dc: dc = 1.404 V       (78 %), step = 36 mV           (2 %)
    dc: dc = 1.44 V        (80 %), step = 36 mV           (2 %)
    dc: dc = 1.476 V       (82 %), step = 36 mV           (2 %)
    dc: dc = 1.512 V       (84 %), step = 36 mV           (2 %)
    dc: dc = 1.548 V       (86 %), step = 36 mV           (2 %)
    dc: dc = 1.584 V       (88 %), step = 36 mV           (2 %)
    dc: dc = 1.62 V        (90 %), step = 36 mV           (2 %)
    dc: dc = 1.656 V       (92 %), step = 36 mV           (2 %)
    dc: dc = 1.692 V       (94 %), step = 36 mV           (2 %)
    dc: dc = 1.728 V       (96 %), step = 36 mV           (2 %)
    dc: dc = 1.764 V       (98 %), step = 36 mV           (2 %)
    dc: dc = 1.8 V        (100 %), step = 36 mV           (2 %)
Total time required for dc analysis `dc': CPU = 2.999 ms, elapsed = 5.19109 ms.
Time accumulated: CPU = 449.93 ms, elapsed = 501.581 ms.
Peak resident memory used = 37.5 Mbytes.

modelParameter: writing model parameter values to rawfile.
element: writing instance parameter values to rawfile.
outputParameter: writing output parameter values to rawfile.
designParamVals: writing netlist parameters to rawfile.
primitives: writing primitives to rawfile.
subckts: writing subcircuits to rawfile.
```

### Post-layout analysis of CMOS Inverter

 Make a new cell with name inverter and type layout then go to *connectivity*-> *generate* -> *all from source* then move the components into the design area ,
 the layout generated is shown in the figure 
 
 <img width="700" alt="layout" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/layout.jpg">

### Layout vs Schematic report

 Now we will perform the LVS check to ensure that the layout correctly represents the schematic , to perform LVS go to *Assura*->*Run LVS*
 
   <img width="500" alt="Assura" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/Assura.png">

   The result of LVS check is
   
   <img width="700" alt="LVS check" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/LVS%20result.png">

 To perform the Post-layout analysis first we have to generate the extracted view of the layout that includes both circuit connectivity and parasitic components (such as parasitic resistances and capacitances) extracted from the physical layout. It is used for post-layout simulations to ensure that the real-world implementation behaves as expected.
 To generate extracted view go to *Assura*->*Run RCX*

  <img width="700" alt="Extracted view" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/extracted%20view.png">

The DC response comes out to be 

 <img width="700" alt="Dc response post layout" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/DC%20post%20layout.png">

 Vol=87.47uV

 Voh=1.798V

 ### d(vout) vs Vin 

  <img width="700" alt="d(vout) post layout" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/d(vout)%20post_layout.png">

  Vih =880.181mV

  Vil =416.291mV
### Noise Margin Calculation

 NM(L)= Vil-Vol =416.291mV-87.47uv=0.4162V

 NM(H)= Voh-Vih =1.798V-880.181mV =0.9178V
 
 
### The transient response comes out to be 
 

  <img width="700" alt="Transient postlayout" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/transient%20post_layout.png">



### Finding out Tphl , Tplh and Tp (Propagation delay)


<img width="700" alt="Tphl postlayout" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/Tphl%20post_layout.png">

<img width="700" alt="Tplh postlayout" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/Thl%20post_layout.png">

Tphl= 40.533ns-40.500ns= 33ps

Tplh=11.8087ns-11.5026ns=306.7ps

Tp=(Tphl+Tplh)/2=169.85ps


# Power Dissipation

<img width="700" alt="Powerdissipation" src="https://github.com/RANAJI2004/CMOS-Inverter-/blob/main/power_dissipation.png">

The horizontal lines denotes the static power dissipation which is in nano watts.
The vertical spikes denotes dynamic power dissipation which is in micro watts.

  
Average Static power disspation = (4.03 + 481.99) nW/ 2 = 243.01 nW

Average Dynamic power dissipation = (79.62 + 94.75) / 2 = 87.185 μW










