Lab5_Wardner
============
The purpose of this lab was to integrate all of the components of PRISM archetecture on an FPGA then create and run an assembly program on it.

####Functionality
#####1st Program
Demonstrated waveform Dr. Neeble on Lesson 33
#####2nd Program
Demonstrated PRISM simulation to Captain Silva after class on 25 April
#####A/B Functionality
Demonstrated FPGA implementation to Captain Silva after class on 25 April

####1st Program Operation
The given file was a wavform of a program that loads 8 to the accumulator and increments it until 0, outputting each value to port 3 at which point the program ends in an infinate loop.

#####Analysis of waveform
######35-65ns

![alt tag](https://raw.githubusercontent.com/EricWardner/Lab5_Wardner/master/2nd_instruction.PNG)
######65-105ns

![alt tag](https://raw.githubusercontent.com/EricWardner/Lab5_Wardner/master/3rd_instruction.PNG)
######65-105ns

![alt tag](https://raw.githubusercontent.com/EricWardner/Lab5_Wardner/master/4th_instruction.PNG)
######1005-1055ns

![alt tag](https://raw.githubusercontent.com/EricWardner/Lab5_Wardner/master/5th_instruction.PNG)

####2nd Program Operation
The objective of the second program was to implement an icrementer/decrementer based on input that loops between 00 and 99.

First a flowchart was created to visualize the flow of the program
![alt tag](https://raw.githubusercontent.com/EricWardner/Lab5_Wardner/master/Flowchart.png)

The implementation of this flowchart was straght-forward difficulty came in checking when the value was above 9, this was done by adding 6 to the accumulator and jumping if zero. More dificulty came when implementing on the FPGA, the clock had to be changed from 22 to 16 in order for it to run fast enough.

####Questions
**1.	When the controller’s current state is “FETCH,” what is the status of the following control lines:**

    a. PCLd: '1'
    b. IRLd: '1'
    c. ACCLd: '0'
    

**2.	The current state is Decode LoAddr and the IR contains “OUT.”  What are the control signals are asserted, and what will the next state be?**

  ``
  Signals Asserted: MARLoLd, PCLd, R_W, IOSel_L
  Next State: Direct IO Excecute
  ``

**3.	What are the three status signals sent from the PRISM datapath to the PRISM controller?**

    IRLd, PCLd, JumpSel

**4.	Why is it important that ACCLd signal be active during the execute state for the ADDI instruction?**

    So that the result is loaded into the Accumulator on the next clock cycle 

**5.	What changes are necessary to the PRISM datapath to add another instruction (SUBI, which would subtract an immediate value from the accumulator) to the instruction set?**

    Another bit would have to be added so that the ALU's mux can account for the new instruction. 
