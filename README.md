# EXPERIMENT 1
## DC, Transient and AC analysis of Common Source Amplifier Using LTspice
### Components : 
CMOSN (length-180nm), 1K-Resistor, 2-Voltage source (1.8V, 0.9V), Wires, AC ground.

### Circuit Diagram 1 : 
\
![Image](https://github.com/user-attachments/assets/10fcd548-9b0b-4178-88a1-8ae4740b3d00)

### Theory :
# NMOS Transistor Common-Source Amplifier

The common source amplifier is most widely used amplifier configurations in analog electronics. It provides high voltage gain and is commonly used in signal amplification applications. The behaviour of amplifier is observed in three domains: DC analysis which determines the biasing and operating point, Transient analysis, which evalusted its time domain response, and AC analysis which examines its small signal behaviour and frequency response.\
<br>
DC analysis: In DC analysis the goal is to establish the stable operationg point for the MOSFET, ensuring it remains in the saturation region for proper amplification.The MOSFET operates in the saturation region when drain-source voltage(V<sub>DS</sub>) is greater than the overdrive voltage (V<sub>OV</sub>=V<sub>GS</sub>-V<sub>TH</sub>). the drain current is given by\
 <br>       I<sub>D</sub>= 1/2K<sub>n</sub>(V<sub>OV</sub>)<sup>2</sup> \
<br>V<sub>DS</sub> and I<sub>D</sub> provides the operating point of the MOSFET.\
<br>Transient analysis : Transient analysis examines how the amplifier responds to time varying signals, such as pulse inputs or sudden changes in voltage. The behaviour is influenced by the charging and discharging of capacitors including coupling capacitors and bypass capacitors.The response of the amplifier due to the sudden changes in the input is limited by its time constants which depends upon the capacitance and resistance in the circuit. Transient analysis is crucial in high speed applications where rise time, fall time, propagation delay determines the amplifier's suitability for fast signals.\
<br>AC analysis: In AC analysis MOSFET treated as a linear small-signal amplifier, where the drain current is proportional to small variations in gate volatge\
<br>i<sub>D</sub>=g<sub>m</sub>v<sub>gs</sub>\
<br>where g<sub>m</sub> is transconductance. Therefore, The volatge gain of the amplifier is give by \
<br>A<sub>v</sub>= -g<sub>m</sub>(R<sub>D</sub>||R<sub>L</sub>\)
<br>The negative sign indicates the 180 degree phase shift between the input and output signals. The input impedance is primarilydetermined by the gate biasing resitors whereas output impedance is largely influenced by the resistor R<sub>D</sub> . At low frequency the gain is effected by coupling capacitors and bypass capacitors, while at high frequencies by paracitic capacitors.\

## NMOS Transistor in Saturation Region

For the NMOS transistor to operate in the saturation region, the condition must be met:

\[
V<sub>DS</sub> = V<sub>GS</sub> - V<sub>th</sub>
\]

Where:
- \( V<sub>GS</sub> \) is the gate-to-source voltage (given as 0.9V),
- \( V<sub>DS</sub> \) is the drain-to-source voltage,
- \( V<sub>th</sub> \) is the threshold voltage of the NMOS.

The drain current in the saturation region is given by:

\[
I<sub>D</sub> = {1}/{2} u<sub>n</sub> C<sub>ox</sub> {W}/{L} (V<sub>GS</sub> - V<sub>th</sub>)<sup>2</sup>
\]

Where:
- \( I<sub>D</sub> \) is the drain current (55µA),
- \( u<sub>n</sub>\) is the electron mobility,
- \( C<sub>ox</sub> \) is the oxide capacitance per unit area,
- \( W \) is the width of the NMOS transistor,
- \( L \) is the length of the NMOS transistor,
- \( V<sub>GS</sub> \) is the gate-to-source voltage,
- \( V<sub>th</sub> \) is the threshold voltage.

## Width Calculation for Desired Current

Rearranging the equation for (W):

\[
W = {2 I<sub>D</sub> L}/{u<sub>n</sub> C<sub>ox</sub>} (V<sub>GS</sub> - V<sub>th</sub>)<sup>2</sup>}
\]

By substituting the known parameters (including process-dependent values for (u<sub>n</sub>) and (C<sub>ox</sub>), we can determine the required width ( W ) to achieve the desired drain current of 55µA.

### Parameters to Substitute:
- \( I<sub>D</sub> = 55 \, u<sub>n</sub> \),
- \( L ) is the length of the NMOS transistor,
- \( u<sub>n</sub>) and \( C<sub>ox</sub>} \) are process-dependent constants (typically given in the datasheet or technology library),
- \( V<sub>GS</sub> = 0.9 \, V \),
- \( V<sub>th</sub> \) is the threshold voltage (typically provided in the datasheet).

### Procedure :
1. Construct the common-source amplifier circuit in LTspice according to the given schematic.
2. Assign resistor values as 1KΩ, DC supply voltage as 1.8V, and gate voltage as 0.9V.
3. Download the library file tsmc018 (1).txt.
4. Create a dedicated folder and save both the LTspice file and the downloaded library file in it.
5. Import the library file into LTspice using a SPICE directive (.op).
6. Set the MOSFET model name as CMOSN, with a channel length of 180nm and a width of 1µm, as specified in the library file.
7. Calculate the drain current for the given power conditions.
8. DC Analysis: In the simulation settings, switch to DC sweep mode to obtain a range of current values. Since drain current (Id) is directly proportional to 
   width (W), adjust the width while keeping other parameters constant until the calculated current value matches the simulated result.
9. Transient Analysis: Modify the simulation settings from DC sweep to transient analysis. Set the DC offset to 0.9V, an amplitude of 50mV, and a frequency of 
   1kHz. Set the stop time to 3ms and run the simulation to observe the expected waveform.
10.AC Analysis: Change the simulation type from transient to AC analysis. Choose a decade sweep, set 20 points per decade, and define the frequency range from 
    0.1Hz to 1THz to obtain the expected AC response.

### Calculatiom: 
Take power as 100uW\
We know that P=VI , where V=1.8V here \
Therefore, I = 55.5uA\
From loop equation : V<sub>DD</sub> = I<sub>D</sub>R<sub>D</sub> + V<sub>out</sub> \
where V<sub>DD</sub>= 1.8, I<sub>D</sub>=55.5uA, R<sub>D</sub>=1KHz\
Therefore V<sub>out</sub>= 1.745V\
Hence Q point= (1.745V, 55.5uA)
### Tabular Column:
| Width | CurrentI<sub>D</sub> | V<sub>out</sub>  |
|-------|----------------------|------------------|
|  1um  |        152.7uA       |      1.64V       |
| 0.8um |        127.8uA       |      1.67V       |
| 0.4um |        78.37uA       |      1.721V      |
| 0.3um |        66.39uA       |      1.733V      |
| 0.2um |        55.2uA        |      1.744V      |
|0.201um|        55.3uA        |      1.744V      |
|0.203um|        55.5uA        |      1.745V      |
### Result:
1. DC analysis:
   ![Image](https://github.com/user-attachments/assets/2e5ca3cb-b2a1-490a-89df-37e9c614dba4)

   we got I<sub>D</sub>= 55.5uA\
          width = 0.203um\
   Vout= 1.745V\
   we get DC operating point as (1.745V, 55.5uA)
3. Transient analysis:
   ![Image](https://github.com/user-attachments/assets/f5a2507b-378b-4717-b850-3a16025447a4)

   we got V<sub>out</sub>= 1.745V for width of 0.203um\
   And a phase shift of 180 degree.
5. AC analysis:
   ![Image](https://github.com/user-attachments/assets/c864c284-7340-4d79-b87c-cdabfe5a9c49)

    we got frequency = 210.45GHz\
          Gain(dB) = -9.104dB\
### Inference: 
1. The drain current increases proportionally with the MOSFET’s width while keeping other parameters unchanged.
2. DC Analysis determines the DC operating point and verifies whether the MOSFET remains in the saturation region.
3. Transient Analysis examines the MOSFET’s response to a time-varying AC input (sine wave).
4. The circuit provides an amplified output, with a 180-degree phase shift between the input and output signals.
5. AC Analysis helps determine the circuit’s gain and frequency characteristics.
   <br>


### Circuit Diagram 2:
![Image](https://github.com/user-attachments/assets/34782522-ccf9-47a9-a6dd-cfde838df83e)

### Components: 
PMOSFET,NMOSFET (180nm), voltage supply(1.8,0.7), AC ground, wires.


### Theory :

The common source amplifier is most widely used amplifier configurations in analog electronics. It provides high voltage gain and is commonly used in signal amplification applications. The behaviour of amplifier is observed in three domains: DC analysis which determines the biasing and operating point, Transient analysis, which evalusted its time domain response, and AC analysis which examines its small signal behaviour and frequency response.\
<br>
DC analysis: In DC analysis the goal is to establish the stable operationg point for the MOSFET, ensuring it remains in the saturation region for proper amplification.The MOSFET operates in the saturation region when drain-source voltage(V<sub>DS</sub>) is greater than the overdrive voltage (V<sub>OV</sub>=V<sub>GS</sub>-V<sub>TH</sub>). the drain current is given by\
 <br>       I<sub>D</sub>= 1/2K<sub>n</sub>(V<sub>OV</sub>)<sup>2</sup> \
<br>V<sub>DS</sub> and I<sub>D</sub> provides the operating point of the MOSFET.\
<br>Transient analysis : Transient analysis examines how the amplifier responds to time varying signals, such as pulse inputs or sudden changes in voltage. The behaviour is influenced by the charging and discharging of capacitors including coupling capacitors and bypass capacitors.The response of the amplifier due to the sudden changes in the input is limited by its time constants which depends upon the capacitance and resistance in the circuit. Transient analysis is crucial in high speed applications where rise time, fall time, propagation delay determines the amplifier's suitability for fast signals.\
<br>AC analysis: In AC analysis MOSFET treated as a linear small-signal amplifier, where the drain current is proportional to small variations in gate volatge\
<br>i<sub>D</sub>=g<sub>m</sub>v<sub>gs</sub>\
<br>where g<sub>m</sub> is transconductance. Therefore, The volatge gain of the amplifier is give by \
<br>A<sub>v</sub>= -g<sub>m</sub>(R<sub>D</sub>||R<sub>L</sub>\)
<br>The negative sign indicates the 180 degree phase shift between the input and output signals. The input impedance is primarilydetermined by the gate biasing resitors whereas output impedance is largely influenced by the resistor R<sub>D</sub> . At low frequency the gain is effected by coupling capacitors and bypass capacitors, while at high frequencies by paracitic capacitors.\

## NMOS Transistor in Saturation Region

For the NMOS transistor to operate in the saturation region, the condition must be met:

\[
V<sub>DS</sub> = V<sub>GS</sub> - V<sub>th</sub>
\]

Where:
- \( V<sub>GS</sub> \) is the gate-to-source voltage (given as 0.9V),
- \( V<sub>DS</sub> \) is the drain-to-source voltage,
- \( V<sub>th</sub> \) is the threshold voltage of the NMOS.

The drain current in the saturation region is given by:

\[
I<sub>D</sub> = {1}/{2} u<sub>n</sub> C<sub>ox</sub> {W}/{L} (V<sub>GS</sub> - V<sub>th</sub>)<sup>2</sup>
\]

Where:
- \( I<sub>D</sub> \) is the drain current (55µA),
- \( u<sub>n</sub>\) is the electron mobility,
- \( C<sub>ox</sub> \) is the oxide capacitance per unit area,
- \( W \) is the width of the NMOS transistor,
- \( L \) is the length of the NMOS transistor,
- \( V<sub>GS</sub> \) is the gate-to-source voltage,
- \( V<sub>th</sub> \) is the threshold voltage.

## Width Calculation for Desired Current

Rearranging the equation for (W):

\[
W = {2 I<sub>D</sub> L}/{u<sub>n</sub> C<sub>ox</sub>} (V<sub>GS</sub> - V<sub>th</sub>)<sup>2</sup>}
\]

By substituting the known parameters (including process-dependent values for (u<sub>n</sub>) and (C<sub>ox</sub>), we can determine the required width ( W ) to achieve the desired drain current of 55µA.

### Parameters to Substitute:
- \( I<sub>D</sub> = 55 \, u<sub>n</sub> \),
- \( L ) is the length of the NMOS transistor,
- \( u<sub>n</sub>) and \( C<sub>ox</sub>} \) are process-dependent constants (typically given in the datasheet or technology library),
- \( V<sub>GS</sub> = 0.9 \, V \),
- \( V<sub>th</sub> \) is the threshold voltage (typically provided in the datasheet).
<br>

### Procedure :
1. Construct the common-source amplifier circuit in LTspice following the provided schematic.
2. Set the resistor value to 1KΩ, the DC supply voltage to 1.8V, and the gate voltage to 0.9V.
3. Download the library file tsmc018 (1).txt from this link.
4. Create a new folder and save both the library file and the LTspice project file in it.
5. Import the library file into LTspice using the .op Spice directive.
6. Assign the MOSFET model name CMOSN from the library file, with a channel length of 180nm and a width of 1µm.
7. Determine the drain current based on the given power specifications.
8. DC Analysis: In the simulation settings, select DC Sweep to observe a range of values obtained from the circuit. Adjust the transistor width since the drain 
   current (Iₙ) is directly proportional to width while keeping other parameters fixed. Ensure that the calculated and simulated currents match.
9. Transient Analysis: Modify the simulation settings from DC Sweep to Transient mode. Set the DC offset to 0.9V, amplitude to 50mV, and frequency to 1kHz. Run 
   the simulation with a stop time of 3ms to generate the expected waveform.
10.AC Analysis: Switch from Transient to AC Analysis in the simulation settings. Choose a decade sweep with 20 points per decade and set the frequency range from 
   0.1Hz to 1THz to obtain the desired AC response.

### Calculatiom: 
Take power as 100uW\
We know that P=VI , where V=1.8V here \
Therefore, I = 55.5uA\
We get Vout= 1.704 which is V<sub>DS</sub>\
we get Q point = (V<sub>DS</sub>, I<sub>D</sub>)= (1.704V, 55.5uA)\

### Tabular Column:
| Width | CurrentI<sub>D</sub> | V<sub>out</sub>  |
|-------|----------------------|------------------|
|  1um  |        50.9uA        |      1.704V      |
|1.01um |        51.4uA        |      1.704V      |
|1.04um |        52.9uA        |      1.704V      |
|1.06um |        53.9uA        |      1.704V      |
|1.09um |        55.3uA        |      1.704V      |
|1.092um|        55.4uA        |      1.704V      |
|1.093um|        55.5uA        |      1.704V      |
<br>

### Simulation Result:
1. DC analysis :
   ![Image](https://github.com/user-attachments/assets/5e143440-2592-4977-a32f-65df705e79ad)
    we got I<sub>D</sub>= 55.5uA\
          width = 1.093um\
   Vout= 1.704V\
   we get DC operating point as (1.704V, 55.5uA)
  
2. Transient analysis:
   ![Image](https://github.com/user-attachments/assets/42a6d74e-5929-43ee-b509-860aeef264ed)
    we got V<sub>out</sub>= 1.704V for width of 1.093um\
   And a phase shift of 180 degree.
  
3. AC analysis:
   ![Image](https://github.com/user-attachments/assets/5a442856-bc1a-40ce-924e-62b7c430a3ac)
we got frequency = 75.739GHz\
          Gain(dB) = 70.149mdB

### Inference: 
1. A MOSFET in a diode-connected configuration always operates in the saturation region.
2. The drain current increases proportionally with the MOSFET's width, assuming all other parameters remain unchanged.
3. DC Analysis helps determine the operating point and verifies whether the MOSFET is functioning in the saturation region.
4. Transient Analysis illustrates the MOSFET's response to a time-varying AC input (sine wave).
5. The circuit produces an amplified output, exhibiting a 180-degree phase shift between the input and output signals.
6. AC Analysis provides insight into the circuit's gain and frequency response.
   <br>
