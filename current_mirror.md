 Experiment 3:
# Current Mirror Circuit
## Part A
## Aim:
 Design and Analyze Current mirror circuit as active load in amplifier circuit.
**Given** :
- Power Supply (V<sub>DD</sub>) = 1.8V.
- Power Consumption (P) <= 1mW. 
- Gain (A<sub>v</sub>) > -10V/V.

### Perform
- DC Ananlysis
- Transient Analysis
- AC Analysis
- Extract required parameters

## Components Required:
- MOSFET(NMOS,PMOS)
- Resistors
- Current source
- Voltage supply
- Connecting wires

## Theory
# Current mirrors
A current mirror as an active load refers to a circuit configuration where a current mirror replaces a passive resistor or other conventional load to improve gain and performance in amplifier circuits. It provides a high output resistance, ensuring better current sourcing and sinking with minimal voltage dependency

## Working Principle
A current mirror is a circuit composed of two or more transistors that accurately replicate a reference current in a different branch. It is often used as an active load in amplifier circuits like differential or common-emitter amplifiers, providing several benefits:

-High output impedance: Increases circuit gain.
-Better linearity: Enhances small-signal amplification.
-Precise current matching: Reduces sensitivity to supply voltage variations.

A simple current mirror typically uses two matched MOSFETs. The first transistor sets the reference current, while the second mirrors this current under similar operating conditions. However, real-world current mirrors are susceptible to variations in process, voltage, and temperature (PVT), which can lead to mismatched mirrored currents.

#Challenges Due to PVT Variations:
-Process Variations (P): Differences in manufacturing can cause discrepancies in transistor characteristics.
-Supply Voltage Variations (V): Changes in power supply levels can alter the operating point, resulting in unstable output current.
-Temperature Variations (T): Temperature shifts affect the MOSFET threshold voltage, causing current drift.

#Generating a Bias Voltage Independent of PVT:
-PMOS: Used for sourcing current.
-NMOS: Used for sinking current to ground.

A stable bias voltage can be achieved using a golden reference current or a bandgap reference circuit to minimize the impact of PVT variations.

## Circuit Diagram

![Image](https://github.com/user-attachments/assets/f5bd39e0-d8e9-46bd-954a-145ff21f8ad8)

- Input bias Voltages(V<sub>2</sub> and V<sub>3</sub>= 0.95V): A DC current that flows into or out of the amplifier's input pins to establish a defined operating point, ensuring proper amplification and preventing saturation. 
- Power Supply(V<sub>1</sub>=1.8V): Provides the necessary DC voltage levels (positive and negative) to bias the MOSFETs, enabling them to operate in the desired amplification region and ensuring proper signal amplification and stability.
- Output Nodes(V<sub>out1</sub>): The output is taken from this terminal.
- PMOS(M2,M3) and NMOS(M1): NMOS typically acting as a current sink (drawing current towards ground) and PMOS acting as a current source (supplying current from the positive supply). 
- Current source (I<sub>ref</sub>): The current source's role is to provide a stable and well-defined reference current

Calculations:<br>
I<sub>t</sub>=P/V<sub>DD</sub>.<br>
I<sub>t</sub>=I<sub>ref</sub>+I<sub>x</sub>.<br>

## PART - A
## DC Analysis(1:1)

### Steps to Perform DC Analysis in LTspice XVII:
1. Construct the circuit as shown in the provided diagram, and set the voltage sources and resistor values according to the calculated parameters.  
2. Open the **SPICE Directive** and type **.lib filename.lib** or **.lib filepath.lib** to load the necessary library file.  
3. Click **OK** and place the resulting command on the schematic.  
4. After importing the library, label both MOSFETs as **CMOSN**.  
5. Set the channel length of M<sub>1</sub> to **180 nm**, and adjust the width to achieve the desired **I<sub>D</sub>** and **V<sub>out</sub>**.  
6. Apply the same procedure to the M<sub>2</sub> MOSFET.  
7. Go to **Edit Simulation Command** and choose **DC op pnt** for DC operating point analysis.  
8. Click **OK** and place the simulation command on the schematic.  
9. Run the simulation, and a pop-up window will display the operating point details, including the values of **V<sub>out</sub>** and **I<sub>D</sub>**.

As we know I<sub>t</sub>=I<sub>ref</sub>+I<sub>x</sub><br>
Therefore, for 1:1 ratio I<sub>ref</sub>=Ix<sub>x</sub>br>
So,I<sub>ref</sub>=I<sub>t</sub>/2<br>
I<sub>t</sub>=P/V<sub>DD</sub><br>
I<sub>t</sub>=1mW/1.8V<br>
I<sub>t</sub>=0.555mA.<br>
Therefore,I<sub>ref</sub>=0.2778mA.<br>

To obtain the current value according to the given ratio, the provided values of W/L for M1 is 3um/180nm , M2 is 3um/180nm, and M3 is 3um/180nm.<br>
Vin is selected in such a way that it should be in saturation region so the given Vin is 0.838V.<br>

OUTPUT:

![Image](https://github.com/user-attachments/assets/a41e51b1-a35c-475c-854d-16af4a2f0c67)

### Analyzing the current mirroring circuit by changing the w and L but maintaing the same ratio.

**(a)L=180nm.**

We know the (w/L) ratio is 16.667.

Therefore for L=180nm the w=3um.

|Mosfet     |  I<sub>d</sub>                 | 
|-----------|---------------------|
|  M1       |   0.000277527       |             
|  M2       |   0.000277527       |         
|  M3       |   0.0002778         |             

**(b)L=500nm.**

We know the (w/L) ratio is 16.667.

Therefore for L=500nm the w=8.334um.

|Mosfet     |  I<sub>d</sub>                  |  
|-----------|-----------------------|
|  M1       |   0.000281241         |             
|  M2       |   0.000281241         |             
|  M3       |   0.0002778           |             

**(c)L=1um.**

We know the (w/L) ratio is 16.667.

Therefore for L=1um the w=16.667um.


|Mosfet     |  I<sub>d</sub>                   | 
|-----------|-----------------------|
|  M1       |   0.000280654         |             
|  M2       |   0.000280654         |             
|  M3       |   0.0002778           |             

## Transient Analysis

OUTPUT:

![Image](https://github.com/user-attachments/assets/6041cebc-b8d6-4d4c-9611-35583355ceef)

The Expected gain of the circuit is -10V/V.But the obtained gain from the transient analysis is -10.12V/V.

## AC Analysis

 OUTPUT:
 
![Image](https://github.com/user-attachments/assets/34f2279c-0fd6-4b1c-90f6-f3d95a0443d6)

The Expected gain in db of the circuit is 20db.But the obtained gain from the AC analysis(frequency response) is 22.117db.

|Parameter      |Theory value  | Practical value |
|---------------|--------------|-----------------|
|Av(in dB)      | 20dB         | 22.117dB         |
|Av(in V/V)     | 10           | 10.12            |

**3db Bandwidth:**

The obatined 3db B.W=2.253GHz.

![Image](https://github.com/user-attachments/assets/4c9f54bb-8fcd-49f3-8c97-8d90e143613e)

## DC Analysis:(for mirror ratio 1:2)

As we know I<sub>t</sub>=I<sub>ref</sub>+I<sub>x</sub><br>
Therefore, for 1:2 ratio 2*I<sub>ref</sub>=I<sub>x</sub><br>
So,I<sub>ref</sub>=I<sub>t</sub>/3<br>
I<sub>t</sub>=P/V<sub>DD</sub<br>
I<sub>t</sub>=1mW/1.8V<br>
I<sub>t</sub>=0.555mA.<br>
Therefore,I<sub>ref</sub>=0.185mA.<br>

To obtain the current value according to the given ratio, the provided values of W/L for M1 is 6um/180nm , M2 is 6um/180nm, and M3 is 3um/180nm.<br>
Vin is selected in such a way that it should be in saturation region so the given Vin is 0.763V.<br>

![Image](https://github.com/user-attachments/assets/792237e5-ca5c-4a18-938d-8cf86e65bf7f)

OUTPUT:

![Image](https://github.com/user-attachments/assets/d6b1ba32-0f98-43f5-b57a-8624733312e1)

## Transient Analysis

OUTPUT:

![Image](https://github.com/user-attachments/assets/a13ee9d1-08a3-441e-9a23-c97182fb14e6)

The Expected gain of the circuit is -10V/V.But the obtained gain from the transient analysis is -11.36V/V.


## AC Analysis

OUTPUT 
![Image](https://github.com/user-attachments/assets/9cd5cb62-1b5b-4c7b-858b-704d2a5a957e)

 The Expected gain in db of the circuit is 21.34db.But the obtained gain from the AC analysis(frequency response) is 24.55db.

|Parameter      |Theory value  | Practical value |
|---------------|--------------|-----------------|
|Av(in dB)      | 21.34dB      | 24.55dB         |
|Av(in V/V)     | 10           | 11.36          |

**3db Bandwidth:**

The obatined 3db B.W=1.186GHz.

![Image](https://github.com/user-attachments/assets/60a9df80-3b1b-41b5-b14f-8215f75df050)

### **Comparison Table:**
| **Parameter**  | **Mirror Ratio 1:1** (Theory) | **Mirror Ratio 1:1** (Practical) | **Mirror Ratio 1:2** (Theory) | **Mirror Ratio 1:2** (Practical) |
|---------------|-----------------------------|-----------------------------|-----------------------------|-----------------------------|
| Av (in dB)    | 20 dB                        | 22.117 dB                     | 21.34 dB                     | 24.55 dB                     |
| Av (in V/V)   | 10                           | 10.12                          | 10                           | 11.36                         |
| 3 dB Bandwidth | -                            | 2.253 GHz                     | -                            | 1.186 GHz                     |  


## Inference:
The designed current mirror circuit successfully replicates the reference current with minimal error, demonstrating effective current mirroring across various W/L ratios.  

- Adjusting the W/L ratio while keeping the proportionality constant shows that the drain current (**I<sub>D</sub>**) remains stable, confirming the circuit's reliability.  
- The observed amplifier gain is slightly higher than theoretical estimates for both mirror ratios, likely due to minor mismatches in transistor characteristics or simulation inaccuracies.  
- Increasing the mirror ratio from **1:1** to **1:2** boosts the gain, as expected, but also reduces the bandwidth from **2.253 GHz** to **1.186 GHz**.  
- Overall, the simulation results closely match the theoretical predictions, validating the circuit design and simulation approach.

## Part B

## Aim:
Design the differential amplifier using the same design specification as Experiment-3. Perform DC analysis,trasient and AC analysis.

## DC Analysis

- Repeat the same steps as mentioned in the above section.

![Image](https://github.com/user-attachments/assets/8ef76f51-e4b2-469e-b4ed-2fa01ff3582b)

Here’s a well-structured explanation of the DC Analysis for your circuit while ensuring that all MOSFETs operate in the saturation region and match the experimental results.

1. Circuit Overview

The circuit comprises six MOSFETs (labeled M1 through M6), each with specified (W/L) ratios. It is essential to ensure that all transistors operate in the saturation region throughout the analysis for accurate performance. The given width-to-length ratios for the transistors are as follows:

- M1: 108 μm / 180 nm
- M2: 108 μm / 180 nm
- M4: 108 μm / 180 nm
- M3: 49.1 μm / 180 nm
- M5: 57.33 μm / 180 nm
- M6: 57.33 μm / 180 nm

To preserve consistency with Experiment 3, the circuit must maintain the same DC operating point, which includes both the current levels and node voltages. Accordingly, the biasing conditions are selected to match those of the previous experiment.

![Image](https://github.com/user-attachments/assets/2cceda88-b45c-4953-82ef-5f89d74089e1)


## Transient Analysis

- Repeat the same steps as mentioned in the above section.

Circuit Diagram:

![Image](https://github.com/user-attachments/assets/d9721172-90ac-4507-80cb-f209b5f9fdb8)


INPUT:

![Image](https://github.com/user-attachments/assets/d29de8c7-91f6-471f-8afc-b95161aa0ed0)

OUTPUT:

![Image](https://github.com/user-attachments/assets/fcf711dc-4d72-4097-9948-bab749e0348f)

The Expected gain of the circuit is -8.6V/V.But the obtained gain from the transient analysis is -13.979V/V.

## AC Analysis

- Repeat the same steps as mentioned in the above section.

Circuit Diagram:

![Image](https://github.com/user-attachments/assets/1bfcd546-2f16-4a24-a6f2-53143182cb63)


The Expected gain in db of the circuit is 22.72db.But the obtained gain from the AC analysis(frequency response) is 23.46db.

|Parameter      |Theory value  | Practical value |
|---------------|--------------|-----------------|
|Av(in dB)      | 21.34dB      | 23.46dB          |
|Av(in V/V)     | 8.6          | 13.979           |

![Image](https://github.com/user-attachments/assets/f399a75e-d2e7-4f46-930b-c552aec7adb2)



**3db Bandwidth:**

The obatined 3db B.W=400.0834MHz.

 ![Image](https://github.com/user-attachments/assets/e4acc891-9d80-4cc1-9dfb-543e7616c284)


## Inference

- The observed gain, which exceeds expected values, may be attributed to additional gain contributions arising from parasitic effects or mismatches between devices.

- The measured high bandwidth of 406.16 MHz indicates that the amplifier is well-suited for high-frequency applications.

- Moreover, the deviation in gain could also result from an underestimation of the drain resistance or variations in transconductance across the devices.
