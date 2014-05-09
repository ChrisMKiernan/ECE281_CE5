# CE5 MIPS

## Parts 1 and 2: MIPS Assembly and Machine Code

### Assembly

The program we are trying to create will add two numbers together, 44 and -37. To do this, we need to initialize two registers with the values given, then add the two numbers, then store them into a given memory address. To initialize the registers, we can create an addi (add immediate) command, and add the numbers given to the register 0, then store the value into a register. Next, we can use the register command add to add the registers together. Then we can use sw to store the word value of the two numbers into the given address space. The assembly code for this, then, is as follows:

- addi $s0, $0, x2C
- addi $s1, $0, x-25
- add $s2, $s1, $s0
- sw $s2, 54($0)

Where $s2 will hold the value of the 2 numbers we add together from $s1 and $s0

### Machine Code

To create the machine code, I took each part of the assembly and parsed them according to the type of instruction they are. After parsing the numbers, I could convert all of them to binary. After that, the next step was to group the binary numbers together in groups of four and convert to hex. The result was an 8-digit hex number that corresponded to each of the commands. The machine code for the language above is as follows:

- 0x2010002C
- 0x2011FFDB
- 0x02119020
- 0xAC120054
