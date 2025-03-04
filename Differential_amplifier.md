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
# Procedure: 
## Circuit 1 :-
**Step 1**
DC analysis: Design Rd and Rss.  
Find the q point of the mosfet.
M1 Q-point=(1.81V,0.454mA)| Vgs=1.02V
M2 Q-point=(1.81V,0.454mA)| Vgs=1.02V
Analysis :  
1)Increase ViCM to 1.9V and observe Vocm,Vp. justify the results.  
2) Calulate maximum input swing and output swing.  
3) Gain equation using small signal model.  
**Step 2**  
Transient analysis.   
Apply Vin p-p max and verify the o/p, calculate gain if the o/p is linear.  
**Step 3**  
Ac analysis.    
Find te 3dB bandwidth.  
## Circuit 2 :-
Repeat the same procedure as before\ 
Dc Analysis -> fix the appropriate Q point\
Transient Analysis -> Output and input swing\
Frequency Analysis -> Bandwidth
## Circuit 3 :-
Fix Vb(appropriate value),W/L of M3\
DC analysis\
Transient Analysis\
AC analysis

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
I have changed the Rd value from 3.281K ohm to 3.286K ohm.
I have kept same Q-point to both MOSFETS.
**2)** Transient Analysis :
![Image](https://github.com/user-attachments/assets/e2be59de-82c8-40ba-9efc-eddd8b3db88b)

Here we can observe the voltage waveforms of Vout1 and Vout2 which is 180 degree phase shifted.

**3)** AC Analysis :
![Image](https://github.com/user-attachments/assets/1a67bc17-88eb-4a6c-8e4e-c5f76eae6a0f)

Here we can observe the gain of 10.021 dB which is nearly equal to our calculated  gain value of 13.08 dB.
Both MOSFET gain is same.

**4)** DC Sweep :
![Image](https://github.com/user-attachments/assets/3df004f3-ea6d-4b67-8b1b-7dce35cda4b0

**Circuit 4**
**1)** Setting up the Q-point :
![Image](https://github.com/user-attachments/assets/a70d670c-3939-4119-ad15-57642030e7a9)

Here I have replaced the Resistor to a current source of current value 0.909mA.
Later we observed that id1 = id2 =0.454mA exactly and Vds=1.81V.

**2)** Transient Analysis :
![Image](https://github.com/user-attachments/assets/538830fa-ca41-4e7b-8b54-8d85b242c619) 

Here wew can observe the voltage waveforms of Vout1 and Vout2 which is 180 degree phase shift.

**3)** AC Analysis :
![Image](https://github.com/user-attachments/assets/b82b93e4-bacd-45f0-92fe-2cd44295960e) 

Here we observed the same gain as previous circuit1 of 10.021dB which is nearly equal to our calculated gain value of 13.08dB.
Both MOSFET gain is same.

**4)** DC Sweep :
![Image](https://github.com/user-attachments/assets/f3d24081-8f0e-4221-ac6d-ee93d2fa0385)

**Circuit 3** 
**1)** Setting up the Q-point and finding Vb value :
![Image](https://github.com/user-attachments/assets/d2c10ec6-4369-40dd-b90b-17c05844c5c7)

Here I have replaced current source to NMOSFET by giving Vb=1.066 (Vb=Vp+Vth => =0.7+0.366 => 1.066V)
By gioving thus Vb the MOSFET acts in saturation region which means it is acting like current source by flowing constant cutrrent.
I changed W value of M3 from 0.0013mm to 0.004689mm to get 0.909mA.
Later we observed that id1 = id2 =0.454mA exactly and Vds=1.81V.

**2)** Transient Analysis :
![Image](https://github.com/user-attachments/assets/264ab7f3-b746-4d66-b163-42f0d2c7c6e1)

Here wew can observe the voltage waveforms of Vout1 and Vout2 which is 180 degree phase shift.

**3)** AC Analysis :
![Image](https://github.com/user-attachments/assets/0310e346-5db0-4073-bfeb-0afacf174cdb)

Here we observed the same gain as previous circuit1 of 10.021dB which is nearly equal to our calculated gain value of 13.08dB.
Both MOSFET gain is same.

**4)** DC Sweep :
![Image](https://github.com/user-attachments/assets/4150935d-2ede-4308-a621-01f91648f890)



 

