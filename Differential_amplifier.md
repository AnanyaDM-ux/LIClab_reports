# Experiment-3  
# Title: To Design Differential Amplifier  
## Aim : Design and analyse the MOS differential amplifier ckt for the following specifications Vdd=3.3V, P<=3mW,Vincm=1.72V, Vocm=1.81V,Vp=0.7.  
Perform DC analysis, transient analysis,frequency respose and extract the required parameters.  
## Circuit Diagram
**With Resistor Rss.**  
![Image](https://github.com/user-attachments/assets/2e192266-cfd9-49f0-bb6e-c6fc76139817) 
**With current source**  
  

**When the current source is replaced by NMOSFET**  
![Image](https://github.com/user-attachments/assets/2a208a29-d99b-42bb-8d9a-e49d194c0abd)
## Theory
A differential amplifier is a circuit that amplifies the difference between two input signals while rejecting any signals common to both inputs. It is widely used in analog circuit design, particularly in operational amplifiers and communication systems.

The basic differential amplifier consists of two identical transistors with their emitters (or sources in MOSFETs) connected together and biased by a current source. The outputs are taken from the collectors (or drains) of the transistors. The circuit operates based on the difference between the two input voltages, making it highly effective in eliminating common-mode noise and interference.

In an ideal differential amplifier, only the differential input signal affects the output, while any common-mode signal is completely rejected. However, in practical implementations, factors such as mismatched components and circuit imperfections introduce some degree of common-mode gain.

The circuit can be analyzed using small-signal models to determine its gain, input impedance, and output characteristics. The gain of a differential amplifier is determined by the transconductance of the transistors and the load resistance used in the circuit. For improved performance, active loads such as current mirrors are often used instead of resistors.

Differential amplifiers are fundamental components in modern electronic systems, forming the input stage of most operational amplifiers and other analog signal-processing circuits.
# Procedure:   
**Step 1**
DC analysis: Design RSS and Rd.  
Find the q point of the mosfet.    
Analysis :  
1)Increase ViCm to 1.2V and observe Vocm,Vp. justify the results.  
2) Calulate maximum input swing and output swing.  
3) Gain equation using small signal model.  
**Step 2**  
Transient analysis.   
Apply Vin p-p max and verify the o/p, calculate gain if the o/p is linear.  
**Step 3**  
Ac analysis.    
Find te 3dB bandwidth.  
## With Rss resistor
Dc analysis:
when ViCm = 1V
Vocm=1.1V
Vp=0.4V
Id=0.25mA
![Image](https://github.com/user-attachments/assets/a76109bf-f904-4dba-aabb-cbbbfa041a37)
Q point of the mosfet:(Vds,Id)@Vgs constant=(0.7V,0.25m)@Vgs=0.6V

![image](https://thub.com/user-attachments/assets/ef7ebb49-df71-4195-8d35-65dd2094e162)

## Analysis:
**a)** when ViCm is 1.2V
Vout,Vp and Id increases respectively.
Vout=0.75V
Vp=0.54V
Id=0.35mA
Vgs 0.675V
