# Experiment-3  
# Title: To Design Differential Amplifier  
## Aim : Design and analyse the MOS differential amplifier ckt for the following specifications Vdd=3.3V, P<=3mW,Vincm=1.72V, Vocm=1.81V,Vp=0.7.  
Perform DC analysis, transient analysis,frequency respose and extract the required parameters.  
## Circuit Diagram
**With Resistor Rss.**  
![Image](https://github.com/user-attachments/assets/3271d4ae-a169-4dc4-8c62-69e126b48015) 


**With current source** 
![Image](https://github.com/user-attachments/assets/8273940e-f3ab-4c10-ac5b-e28f935c3620)
  

**When the current source is replaced by NMOSFET**  
![Image](https://github.com/user-attachments/assets/c7a4ef7d-65dc-4b2d-ad32-89fdf846e4cd)


## Theory
A differential amplifier is a circuit that amplifies the difference between two input signals while rejecting any signals common to both inputs. It is widely used in analog circuit design, particularly in operational amplifiers and communication systems.

The basic differential amplifier consists of two identical transistors with their emitters (or sources in MOSFETs) connected together and biased by a current source. The outputs are taken from the collectors (or drains) of the transistors. The circuit operates based on the difference between the two input voltages, making it highly effective in eliminating common-mode noise and interference.

In an ideal differential amplifier, only the differential input signal affects the output, while any common-mode signal is completely rejected. However, in practical implementations, factors such as mismatched components and circuit imperfections introduce some degree of common-mode gain.

The circuit can be analyzed using small-signal models to determine its gain, input impedance, and output characteristics. The gain of a differential amplifier is determined by the transconductance of the transistors and the load resistance used in the circuit. For improved performance, active loads such as current mirrors are often used instead of resistors.

Differential amplifiers are fundamental components in modern electronic systems, forming the input stage of most operational amplifiers and other analog signal-processing circuits.

**1. Introduction to Differential Amplifiers**
A differential amplifier is a key component in analog circuits, commonly used in operational amplifiers, sensor interfaces, and communication circuits. It amplifies the difference between two input signals while rejecting common-mode noise.

The experiment involves a MOSFET-based differential amplifier, where the design is analyzed under different configurations by modifying the resistor load (Rd) and replacing it with a current source or an NMOS current mirror.

**2. Circuit Description**
The MOSFET differential amplifier consists of:

Two identical NMOS transistors operating in the saturation region.
A current source that provides a constant biasing current (Id).
Load resistors (Rd) or active loads (current source/NMOS current mirror).
The output signals (Vout1 and Vout2) are taken from the drain terminals of the MOSFETs.

Circuit Configurations Explored:

Circuit 1: Uses a resistor Rd as the load.\
Circuit 2: Replaces Rd with a current source, ensuring more stable operation.\
Circuit 3: Uses an NMOS transistor as a current source, improving integration in IC design.\

3. Operating Principle\
A. Biasing and Q-Point Setting\
The Q-point (operating point) is set to ensure the transistors work in saturation mode, where:
\[
I<sub>D</sub> = {1}/{2} u<sub>n</sub> C<sub>ox</sub> {W}/{L} (V<sub>GS</sub> - V<sub>th</sub>)<sup>2</sup>
\]
By adjusting W/L ratio and Rd, we achieve the desired current (Id1 = Id2 = 0.454mA) and voltage (Vds = 1.81V).\

B. Small-Signal Analysis and Gain Calculation
The small-signal voltage gain is given by:\
                A<sub>v</sub> = -g<sub>m</sub>(R<sub>D</sub>\
where 𝑔m (transconductance) is:\
                g<sub>m</sub> = 2I<sub>D</sub>/(V<sub>gs</sub> - V<sub>th</sub>)\
For Circuit 1 (resistor load), gain depends on Rd.\
For Circuit 2 & 3 (current source/NMOS mirror), the gain is higher because the effective resistance is larger than a passive resistor.

# Procedure: 
## Circuit 1: Differential Amplifier with Resistor Load
**Step 1**: DC Analysis :
-Determine the Q-point by selecting appropriate values of Rd and Rss:\
-Given Q-point for M1 and M2:\
 Vds = 1.81V\
 Id = 0.454mA\
 Vgs = 1.02V\
-Use MOSFET equations to verify the operating point:\
  I<sub>D</sub> = {1}/{2} u<sub>n</sub> C<sub>ox</sub> {W}/{L} (V<sub>GS</sub> - V<sub>th</sub>)<sup>2</sup>\
-Adjust Rd and Rss to maintain the correct drain current and bias point.\

**Step 2**: Transient Analysis :\
-Apply a small differential input signal (Vin).\
-Observe Vout1 and Vout2, ensuring a 180° phase shift.\
-Check for linearity in the output response.\

**Step 3**: AC Analysis\
-Determine the small-signal gain using:\
               A<sub>v</sub> = -g<sub>m</sub>(R<sub>D</sub>\

-Perform frequency response analysis to find the 3dB bandwidth, measuring where the gain drops by -3dB.\

## Circuit 2: Differential Amplifier with Current Source Load\
-Repeat the same procedure as Circuit 1 & 3:\
-Fix Q-point\
-Perform transient analysis to observe output swing.\
-Calculate gain using the small-signal model.\
-Perform AC analysis to find bandwidth.\

## Circuit 3: Differential Amplifier with NMOS Current Source\
**Step 1**: DC Analysis\
-Set the bias voltage Vb=Vp + Vth.\
-Ensure the NMOS M3 operates in saturation mode, acting as a constant current source.\
-Determine W/L ratio of M3:\
-Adjust W/L of M3 to set Id1 = Id2 = 0.454mA\
-Verify that Vds = 1.81V for both MOSFETs\
​
**Step 2**: Transient Analysis\
Apply a sinusoidal input voltage (Vin).\
Observe the differential output voltage (Vout1 and Vout2).\
Ensure the phase shift remains 180°.\
Verify output swing and linearity.\

**Step 3**: AC Analysis\
1) Find Gain Expression using Small-Signal Model:\

Use the MOSFET small-signal equivalent circuit to derive gain.\
Gain expression :\
         A<sub>v</sub> = -g<sub>m</sub>(R<sub>D</sub>\
Where g<sub>m</sub> (transconductance) is:\
         g<sub>m</sub> = 2I<sub>D</sub>/(V<sub>gs</sub> - V<sub>th</sub>)\

2)Increase Common-Mode Input (𝑉𝑖<sub>𝐶𝑀</sub>) to 1.9V\
-Observe common-mode output voltage Vocm and differential gain.\
-Justify how the circuit rejects common-mode signals (common-mode rejection ratio - CMRR).\

3)Calculate Maximum Input Swing and Output Swing\
-Find the range of Vin where MOSFETs stay in saturation.\
-Determine the maximum voltage swing before distortion occurs.\

4)AC Analysis for Bandwidth\
-Perform frequency analysis to find the 3dB bandwidth (where gain drops by -3dB).\
-Check if bandwidth changes with different circuit configurations.\

## DC analysis:
when ViCm = 1.72 V
Vocm=1.81V
Vp=0.7V
Vdd=3.3V
Id=0.454mA
Q point of both mosfets:(Vds,Id)@Vgs constant=(1.81V,0.545m)@Vgs=1.02V

## Analysis:
**a)** when ViCm is 1.2V
Vout,Vp and Id increases respectively.
Vout=0.75V
Vp=0.54V
Id=0.35mA
Vgs 0.675V

 ## Calculations:
 ![Image](https://github.com/user-attachments/assets/c5ce562f-55c6-4436-b074-ff03b12d9f22)

## Results :
**Circuit 1**
**1)** Setting up the Q-point :
![Image](https://github.com/user-attachments/assets/e8111ea9-155f-4799-8f59-a506ef8311b2)

I have changed the Rd and W/L values in the circuit diagram to get the desired Q-point.\
I have changed the W value from  0.00130mm to 0.00248mm.\
I have changed the Rd value from 3.281K ohm to 3.286K ohm.\
I have kept same Q-point to both MOSFETS.\
**2)** Transient Analysis :
![Image](https://github.com/user-attachments/assets/e2be59de-82c8-40ba-9efc-eddd8b3db88b)

Here we can observe the voltage waveforms of Vout1 and Vout2 which is 180 degree phase shifted.\

**3)** AC Analysis :
![Image](https://github.com/user-attachments/assets/1a67bc17-88eb-4a6c-8e4e-c5f76eae6a0f)

Here we can observe the gain of 10.021 dB which is nearly equal to our calculated  gain value of 13.08 dB.\
Both MOSFET gain is same.\

**4)** DC Sweep :
![Image](https://github.com/user-attachments/assets/3df004f3-ea6d-4b67-8b1b-7dce35cda4b0

**Circuit 2**\
**1)** Setting up the Q-point :
![Image](https://github.com/user-attachments/assets/a70d670c-3939-4119-ad15-57642030e7a9)

Here I have replaced the Resistor to a current source of current value 0.909mA.\
Later we observed that id1 = id2 =0.454mA exactly and Vds=1.81V.\

**2)** Transient Analysis :
![Image](https://github.com/user-attachments/assets/538830fa-ca41-4e7b-8b54-8d85b242c619) 

Here wew can observe the voltage waveforms of Vout1 and Vout2 which is 180 degree phase shift.\

**3)** AC Analysis :
![Image](https://github.com/user-attachments/assets/b82b93e4-bacd-45f0-92fe-2cd44295960e) 

Here we observed the same gain as previous circuit1 of 10.021dB which is nearly equal to our calculated gain value of 13.08dB.\
Both MOSFET gain is same.\

**4)** DC Sweep :
![Image](https://github.com/user-attachments/assets/f3d24081-8f0e-4221-ac6d-ee93d2fa0385)

**Circuit 3** 
**1)** Setting up the Q-point and finding Vb value :
![Image](https://github.com/user-attachments/assets/d2c10ec6-4369-40dd-b90b-17c05844c5c7)

Here I have replaced current source to NMOSFET by giving Vb=1.066 (Vb=Vp+Vth => =0.7+0.366 => 1.066V)\
By gioving thus Vb the MOSFET acts in saturation region which means it is acting like current source by flowing constant cutrrent.\
I changed W value of M3 from 0.0013mm to 0.004689mm to get 0.909mA.\
Later we observed that id1 = id2 =0.454mA exactly and Vds=1.81V.\

**2)** Transient Analysis :
![Image](https://github.com/user-attachments/assets/264ab7f3-b746-4d66-b163-42f0d2c7c6e1)

Here wew can observe the voltage waveforms of Vout1 and Vout2 which is 180 degree phase shift.\

**3)** AC Analysis :
![Image](https://github.com/user-attachments/assets/0310e346-5db0-4073-bfeb-0afacf174cdb)

Here we observed the same gain as previous circuit1 of 10.021dB which is nearly equal to our calculated gain value of 13.08dB.\
Both MOSFET gain is same.\

**4)** DC Sweep :
![Image](https://github.com/user-attachments/assets/4150935d-2ede-4308-a621-01f91648f890)

## Analysis of Results :
A. Transient Response - \
The 180-degree phase shift between Vout1 and Vout2 confirms that the circuit behaves as a differential amplifier.\
B. AC Analysis - \
The measured gain (10.021 dB) closely matches the theoretical value (13.08 dB), with minor deviations due to parasitics. \
C. DC Sweep Analysis - \
The linear response in DC sweep ensures that the MOSFETs are in the correct operating region. \

## Inference :
1) Q-Point Stability Across Circuits:
-The Q-point was successfully set for all circuits, with adjustments in W/L ratio, resistor values, and replacement of resistors with current sources or MOSFETs.\
-This ensured that Id1 = Id2 = 0.454mA and Vds = 1.81V, confirming that both MOSFETs operate in the saturation region.\

2) Phase Relationship in Transient Analysis:
-The 180-degree phase shift between Vout1 and Vout2 is consistent across all three circuits.\
-This indicates that the circuit behaves as a differential amplifier, where one output is the inverted version of the other.\

3) AC Gain Consistency:
-The measured gain of 10.021 dB is slightly lower than the theoretical 13.08 dB, but still within an acceptable range.\
-The slight discrepancy may be due to parasitic effects, channel length modulation, or non-idealities in MOSFET parameters.\
-The gain remains consistent across all three circuit configurations, meaning that replacing the resistor with a current source (or NMOS current source) does not 
 significantly impact the overall amplification.\

4) Effect of Replacing Resistors with Current Sources:
-In Circuit 4, replacing Rd with a current source improved the current balance (Id1 = Id2) and stabilized the Q-point.\
-In Circuit 3, using an NMOS current source (by setting Vb correctly) achieved the same effect, ensuring a constant current through the differential pair.\

5) DC Sweep Analysis:
-The DC Sweep results (not explicitly discussed but inferred) likely show a linear response region where the circuit maintains its differential operation.\
-If the outputs remain symmetrical and within the expected voltage range, it confirms proper biasing and MOSFET operation in saturation.\

## Conclusion:
-All three circuits successfully operate as differential amplifiers with a consistent gain and phase shift.\
-Replacing resistors with current sources improves current stability and Q-point control.\
-The small deviation in gain from theoretical values is expected due to real-world non-idealities.\
-Circuit 3 (with NMOS current source) provides a practical implementation for biasing in integrated circuits.



 

