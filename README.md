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
- \( I<sub>D</sub> = 55 \, \mu A \),
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
1. Width is directly proportional to Drain current. Hence other parameters become constant.
2. From DC analysis we get the dc operating point and confirms whether the mosfet is in saturation region.
3. Transient analysis shows how the mosfet behaves for the time varying AC signal(sine wave).
4. We get amplified output with phase shift of 180 degree between input and output.
5. From AC analysis we get gain and frequency.
   <br>


### Circuit Diagram 2:

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
<br>
### Procedure :
1. Build the common source amplifier circuit as the circuit diagram using LTspice.
2. Set the Resistor value as 1K, DC voltage as 1.8V, Gate voltage as 0.9V.
3. Download the library file [tsmc018 (1).txt](https://github.com/user-attachments/files/18785407/tsmc018.1.txt)
4. Create a folder. Save the library file and LTspice file to the folder.
5. Import the library file to LTspice using spice directive(.op).
6. Set the mosfet model name CMOSN as given in the library file, length as 180nm, width as 1uF.
7. Find the current value for the given power rating.
8. DC analysis: In edit simulation option, change to dc offset to get list of values obtained from the circuit. We should get the calculated current value in the simulation result.So that we need vary the value of width since width is directly proportional to Drain current(Id) keeping other parameters constant.
9. Transient analysis: In edit simulation option, change from dc offset to transient. Set the dc offset as 0.9V, Amplitude 50mV, frequency 1KHz. Keep stop time for 3ms and run to get the expected waveform.
10. AC analysis : In edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of points per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected ac waveform. 
