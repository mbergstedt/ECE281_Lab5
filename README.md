ECE281_Lab5
===========

##Functionality
- 1st Program on FPGA
- 2nd Program in PRISM
- 2nd Program on FPGA

####Part 1
The VHDL code for Part 1 ran the following PRISM code
[!alt text](https://github.com/mbergstedt/ECE281_Lab5/blob/master/Part1.JPG?raw=true)

The program begins by loading a value into the accumulator.  It then adds one to the accumulator and outputs the
number to output port 3.  Afterwards it jumps back to the add if the value in the accumulator is negative.  Any
number that has a leading 1 in its binary value is considered negative by the computer.  Since the number first
loaded into the accumulator is 8, which has a binary value of 1000, the program will output the values 9-F before
outputting 0.  When the accumulator value returns to 0, it is no longer negative, and the program ends in an
infite loop.

The following are the controller states of the instructions run in the simulation:
Immediate Load:
[!alt text](https://github.com/mbergstedt/ECE281_Lab5/blob/master/Instruction1.JPG?raw=true)

Immediate Add:
[!alt text](https://github.com/mbergstedt/ECE281_Lab5/blob/master/Instruction2.JPG?raw=true)

Out:
[!alt text](https://github.com/mbergstedt/ECE281_Lab5/blob/master/Instruction3.JPG?raw=true)

Jump Negative:
[!alt text](https://github.com/mbergstedt/ECE281_Lab5/blob/master/Instruction4.JPG?raw=true)

The simulation does not show the controller states for the jump, since the value in the accumulator does not reach
0 until the very end of the simulation, and the program checks if jump negative is posible before going to the
jump command.

####Part 2
1) When the state is in "FETCH," the IRLd and PCLd have a value of 1, meaning they are on, while the ACCLd has a
value of 0, meaning it is off.
2) When the state is Decode LoAddr and the IR contains "OUT," MARLoLd and PCLd are asserted, and the next state
will be Direct IO Execute.
3) R/W', MemSel, and IOSel are sent from the datapath to the controller.
4) It is important that ACCLd be active during the execute state for the ADDI instruction so that the value in the
accumulator can be updated to have added the value from the instruction.
5) To include a SUBI instruction, you could include a multiplexer that choses to add the current value or the
negative of that value.
