# PING PONG MEMORY NIOS 

## Description
This project is a simple two-NIOS II project that uses two shared memories and only will read and write when the memory is free. The first NIOS II will write FFFFFFFF in the first memory when its done writing the information in all the memory, then the second NIOS II will read the information and write 0xFFFFFFF0 in the first memory when its done reading all the information. The second NIOS II will write FFFFFFFF in the second memory when its done writing the information in all the memory, then the first NIOS II will read the information and write 0xFFFFFFF0 in the second memory when its done reading all the information. This process will repeat until the user stops the program.

## How to use
1. Download the project
2. Open the project in Quartus
3. Compile the project
4. Program the FPGA (maybe you need to change the device -- Auto Detect)
5. Open the NIOS II Software Build Tools for Eclipse
6. Import the project (File -> Import -> General -> Existing Projects into Workspace -> Select root directory -> Browse(DE10_Standard_Audio_2\software) -> Select the projects (DE10_Standard_Audio and Parte2) -> Finish)
7. Compile the project (Project -> Build All)
8. Run as debug (Run -> Debug As -> Nios II Hardware) for the first NIOS II 
9. Run as debug (Run -> Debug As -> ) for the second NIOS II ## check the name of the second NIOS II
10. Watch the Nios II Console for the results, due to the fact we are saving integers in the memory, the numbers will use 4 bytes of memory. So it will write until 2500 in each memory.

## How to do in your own project
1. Create a new project
2. Create a 2 NIOS II  and 2 shared memories in platform designer
3. Connect the shared memories to the NIOS II and connect the NIOS II to the JTAG UART as shown in the image below
4. Connect the shared memories to the NIOS II.
5. Compile the project
6. Program the FPGA (maybe you need to change the device -- Auto Detect)
7. Open the NIOS II Software Build Tools for Eclipse
8. Create a new project (File -> New -> NIOS II Application and BSP from Template -> Hello World Nios II Application -> Next -> Finish)
9. Adjust the reserved space for the shared memory in the linker script (BSP -> Linker Script -> memory -> adjust the space for the shared memory)
10. Create a new project for the second NIOS II  and repeat the steps 1 to 9
11. Get the base address of the shared memories in the linker.h file
12. Write the code in the main.c to write in the shared memory (check the code in the project -- DE10_Standard_Audio_2\software\DE10_Standard_Audio\main.c)
13. Write the code in the main.c to read in the shared memory (check the code in the project -- DE10_Standard_Audio_2\software\Parte2\hello_world.c)
14. Compile the project (Project -> Build All)
15. Run as debug (Run -> Debug As -> Nios II Hardware) for the first NIOS II -- remember to select the correct NIOS II and the correct project (ELF File)
16. Run as debug (Run -> Debug As -> ) for the second NIOS II -- remember to select the correct NIOS II and the correct project (ELF File)
17. Watch the Nios II Console for the results, due to the fact we are saving integers in the memory, the numbers will use 4 bytes of memory. So it will write until 2500 in each memory. You can change the number of bytes that you want to write in the memory in the main.c file using short int, int, long int, etc.

## changes that you need to do in the code
1. Change the base address of the shared memory in the linker.h file
2. Change the number of bytes that you want to write in the memory in the main.c file using short int, int, long int, etc.
3. Change the number of bytes that you want to read in the memory in the main.c file using short int, int, long int, etc.
4. Change the size of the memory in the linker script and in the main.c file (calculate by doing the base address of the memory + the size of the memory in hexa)

