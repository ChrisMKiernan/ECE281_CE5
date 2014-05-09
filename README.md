# CE5 MIPS

## Parts 1 and 2: MIPS Assembly and Machine Code

### Assembly

The program we are trying to create will add two numbers together, 44 and -37. To do this, we need to initialize two registers with the values given, then add the two numbers, then store them into a given memory address. To initialize the registers, we can create an addi (add immediate) command, and add the numbers given to the register 0, then store the value into a register. Next, we can use the register command add to add the registers together. Then we can use sw to store the word value of the two numbers into the given address space. The assembly code for this, then, is as follows:

- addi $s0, $0, x2C
- addi $s1, $0, x-25
- add $s2, $s1, $s0
- sw $s2, 54($0)

Where $s2 will hold the value of the 2 numbers we add together from $s1 and $s0.

### Machine Code

To create the machine code, I took each part of the assembly and parsed them according to the type of instruction they are. After parsing the numbers, I could convert all of them to binary. After that, the next step was to group the binary numbers together in groups of four and convert to hex. The result was an 8-digit hex number that corresponded to each of the commands. The machine code for the language above is as follows:

- 0x2010002C
- 0x2011FFDB
- 0x02119020
- 0xAC120054

### Waveform

![alt text](https://raw.githubusercontent.com/ChrisMKiernan/ECE281_CE5/master/MIPS_Waveform_Pic.PNG "The waveform of the machine code made in Part 2")

Above is the waveform created by the instructions implemented into the MIPS program. We can see all of our instructions executed perfectly, and can deduce the output of the program. We know the program works because the output of the ALU in the third nonzero ALU block is 7, then the write data block becomes 7 in the next clock cycle (44 - 37 = 7). We can also see the memwrite signal go to 1 in the last clock cycle, meaning we will be writing to memort the data in the write data block. We can also see the WE3 signal go to 0 in this cycle, this is becasue we won't be writing to a register, but will instead be reading the register $s2 and writing that value to memory 0x54.
