# cs2200-project-4-solved
**TO GET THIS SOLUTION VISIT:** [CS2200 Project 4 Solved](https://www.ankitcodinghub.com/product/cs2200-1-13/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;109906&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS2200 Project 4 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
We have spent the last few weeks implementing our 32-bit datapath. The simple 32-bit LC-901 is capable of performing advanced computational tasks and logical decision making. Now it is time for us to move on to something more advanced—the upgraded LC-901a enables the ability for programs to be interrupted. Your assignment is to fully implement and test interrupts using the provided datapath and CircuitSim. You will hook up the interrupt and data lines to the new timer device, modify the datapath and microcontroller to support interrupt operations, and write an interrupt handler to operate this new device. Then you will connect a second, more complex device: the water level sensor.

2 Requirements

• The LC-901a assembler is written in Python. If you do not have Python 2.6 or newer installed on your system, you will need to install it before you continue.

3 What We Have Provided

• A reference guide to the LC-901a is located in Appendix A: LC-901a Instruction Set Architecture. Please read this first before you move on! The reference introduces several new instructions that you will implement for this project.

• A CircuitSim circuit (int-devices.sim) containing a timer device and water level sensor subcircuit that you will use for this project. You should copy and paste the contents of the new devices into subcircuits in your main circuit file.

• A timer device that will generate an interupt signal at regular intervals. The pinout and functionality of this device are described in Adding an External Timer Device.

• A water level sensor that will generate an interrupt signal at regular intervals, and provides key press data. The pinout and functionality of this device are described in Adding a water level sensor.

• An incomplete assembly program prj2.s that you will complete and use to test your interrupt capabilities.

• An assembler with support for the new instructions to assemble the test program.

• We will also release a microcode.xlsx microcode file that meets the requirements of Project 1, but feel free to supply your own.

4 Phase 1 – Implementing a Basic Interrupt

Figure 1: Basic Interrupt Hardware for the LC-901a Processor

For this assignment, you will add interrupt support to the LC-901a datapath. Then, you will test your new capabilities to handle interrupts using an external timer device.

Work in the LC-901a.sim file. If you wish to use your existing datapath, make a copy with this name, and add the devices we provided.

4.1 Interrupt Hardware Support

First, you will need to add the hardware support for interrupts.

You must do the following:

1. Our processor needs a way to turn interrupts on and off. Create a new one-bit “Interrupt Enable” (IE) register. You’ll connect this register to your microcontroller in a later step.

2. Create the INT line. The external device you will create in 4.2 will pull this line high (assert a ’1’) when they wish to interrupt the processor. Because multiple devices can share a single INT line, only one device can write to it at once. When a device does not have an interrupt, it neither pulls the line high nor low. You must accomodate this in your hardware by making sure that the final value going to the microcontroller always has a value (i.e. not a blue wire in CircuitSim).

3. When a device receives an IntAck signal, it will drive a 32-bit device ID onto the I/O Data Bus. To prevent devices from interfering with the processor, the I/O Data Bus is attached to the Main Bus with a tri-state driver. Create this driver and the bus, and attach the microcontroller’s DrDATA signal to the driver.

4. Modify the datapath so that the PC starts at 0x8 when the processor is reset. Normally the PC starts at 0x00, however we need to make space for the interrupt vector table (IVT). Therefore, when you actually load in the test code that you will write, it needs to start at 0x8. Please make sure that your solution ensures that datapath can never execute from below 0x8 – or in other words, force the PC to drive the value 0x8 if the PC is pointing in the range of the vector table.

5. Create hardware to support selecting the register $k0 within the microcode. This is needed by some interrupt related instructions. Because we need to access $k0 outside of regular instructions, we cannot use the Rx / Ry / Rz bits. HINT: Use only the register selection bits that the main ROM already outputs to select $k0.

6. Put your name and GTID on your CircuitSim data path in a comment box so that we know it is your work.

4.2 Adding an External Timer Device

Hardware timers are an essential device in any CPU design. They allow the CPU to monitor the passing of various time intervals, without dedicating CPU instructions to the cause.

The ability of timers to raise interrupts also enables preemptive multitasking, where the operating system periodically interrupts a running process to let another process take a turn. Timers are also essential to ensuring a single misbehaving program cannot freeze up your entire computer.

You will connect an external timer device to the datapath. It is internally configured to have a device ID of 0x0 and a 2000-cycle tick timer interval.

• CLK: The clock input to the device. Make sure you connect this to the same clock as the rest of your circuit.

• INT: The device will begin to assert this line when its time interval has elapsed. It will not be lowered until the cycle after it receives an INTA signal.

• INTA IN: When the INTA IN line is asserted while the device has asserted the INT line, it will drive its device ID to the DATA line and lower its INT line on the next clock cycle.

• INTA OUT: When the INTA IN line is asserted while the device does not have an interrupt pending, its value will be propagated to INTA OUT. This allows for daisy chaining of devices.

• DATA: The device will drive its ID (0x0) to this line after receiving an INTA.

The INT and DATA lines from the timer should be connected to the appropriate buses that you added in the previous section.

4.3 Microcontroller Interrupt Support

Before beginning this part, be sure you have read through Appendix A: LC-901a Instruction Set Architecture and Appendix B: Microcontrol Unit and pay special attention to the new instructions. However, for this part of the project, you do not need to worry about the LdDAR signal or the IN instruction.

In this part of the assignment you will modify the microcontroller and the microcode of the LC-901a to support interrupts. You will need to do the following:

1. Be sure to read the appendix on the microcontroller before starting this section.

2. Modify the microcontroller to support asserting four new signals:

(a) LdEnInt &amp; EnInt to control whether interrupts are enabled/disabled. You will use these 2 signals to control the value of your interrupts enabled register.

(b) IntAck to send an interrupt acknowledge to the device.

(c) DrDATA to drive the value on the I/O Data Bus to the Main Bus.

3. Extend the size of the ROM accordingly.

4. Add the fourth ROM described in Appendix B: Microcontrol Unit to handle onInt.

5. Modify the FETCH macrostate microcode so that we actively check for interrupts. Normally this is done within the INT macrostate (as described in Chapter 4 of the book and in the lectures) but we are rolling this functionality in the FETCH macrostate for the sake of simplicity. You can accomplish this by doing the following:

(a) First check to see if the CPU should be interrupted. To be interrupted, two conditions must be true: (1) interrupts are enabled (i.e., the IE register must hold a ’1’), and (2), a device must be asserting an interrupt.

(b) If not, continue with FETCH normally.

(c) If the CPU should be interrupted, then perform the following:

i. Save the current PC to the register $k0.

ii. Disable interrupts.

iii. Assert the interrupt acknowledge signal (IntAck). Next, drive the device ID from the I/O Data Bus and use it to index into the interrupt vector table to retrieve the new PC value. The device will drive its device ID onto the I/O Data Bus one clock cycle after it receives the IntAck signal.

iv. This new PC value should then be loaded into the PC.

Note: onInt works in the same manner that ChkCmp did in Project 1. The processor should branch to the appropriate microstate depending on the value of onInt. onInt should be true when interrupts are enabled AND when there is an interrupt to be acknowledged.

Note: To protect the separation between user program and the handler code (which is part of the OS), the mode bit exists in every architecture. The mode bit ensures that the handler code will use a different stack in memory for saving/restoring registers and other information as needed in supporting the interrupt mechanism. For this project, the mode bit has been omitted for simplicity.

6. Implement the microcode for three new instructions for supporting interrupts as described in Chapter 4. These are the EI, DI, and RETI instructions. You need to write the microcode in the main ROM controlling the datapath for these three new instructions. Keep in mind that:

(a) EI sets the IE register to 1.

(b) DI sets the IE register to 0.

(c) RETI loads $k0 into the PC, and enables interrupts.

4.4 Implementing the Timer Interrupt Handler

Our datapath and microcontroller now fully support interrupts from devices, BUT we must now implement the interrupt handler timer_handler within the prj2.s file to support interrupts from the timer device while also not interfering with the correct operation of any user programs.

In prj2.s, we provide you with a program that runs in the background. For this part of the project, you need to write interrupt handler for the timer device (device ID 0x0). You should refer to Chapter 4 of the textbook to see how to write a correct interrupt handler. As detailed in that chapter, your handler will need to do the following:

1. First save the current value of $k0 (the return address to where you came from to the current handler) 2. Enable interrupts (which should have been disabled implicitly by the processor within the INT macrostate).

3. Save the state of the interrupted program.

4. Implement the actual work to be done in the handler. In the case of this project, we want you to increment a counter variable in memory, which we have already provided at the label ticks.

5. Restore the state of the original program and return using RETI.

The handler you have written for the timer device should run every time the device’s interrupt is triggered. Make sure to write the handler such that interrupts can be nested. With that in mind, interrupts should be enabled for as long as possible within the handlers.

You will need to do the following:

1. Write the interrupt handler (should follow the above instructions or simply refer to Chapter 4 in your book). In the case of this project, we want the interrupt handler to keep time in memory at the predetermined location: 0xFFFF

2. Load the starting address of the first handler you just implemented in prj2.s into the interrupt vector table at the appropriate addresses (the table is indexed using the device ID of the interrupting device).

Test your design before moving onto the next section. If it works correctly, you should see a location in memory increment as the program runs.

5 Phase 2 – Implementing Interrupts from Input Devices

Figure 2: Interrupt Hardware for the LC-901a with Basic I/O Support

Your datapath can now detect when external devices are ready, but cannot get data from input devices. In this part of the project, you will add functionality for device-addressed input. You will then make use of this functionality by adding a device simulating a water level sensor and writing a simple handler for the device.

5.1 Basic I/O Support

Before adding the water level sensor, you will first need to add support for device addressed I/O. In order to get input from a device such as a water level sensor, you will write a value to an Address Bus, which instructs the device with that address (which in this case is the same as the device ID) to write its output data to the I/O Data Bus.

You must do the following:

1. Create the device address register (DAR) and connect its enable to the LdDAR signal from your microcontroller. This register gets its input from the Main Bus, and its output will be directly connected to the Address Bus. It will allow us to send assert a value on the Address Bus while using the Main Bus for other operations.

2. Modify the microcontroller to support a new control signal, LdDAR. This signal will be used in order to enable writing to the DAR.

3. Implement the IN instruction in your microcode. This instruction takes a device address from the immediate, loads it into the DAR, and writes the value on the data bus into a register. When it is done, it must clear the DAR to zero (since interrupts use the data bus to communicate device IDs). Examine the format of the IN instruction and consider what signals you might raise in order to write a constant zero into the DAR.

Note: The DAR is the same as the ETR if you see that wording used in the textbook or from lecture.

5.2 Adding a water level sensor

You will connect a water level sensor to your datapath that simulates the water level sensor in the Tech Green Cistern. Its internals are similar to the timer device, meaning it asserts interrupts and handles acknowledgements in the same way. Every 2500 cycles, it will assert an interrupt signaling that a new measurement has been collected. This measurement can be fetched as a 32-bit word by writing the device’s address to the ADDR line.

The water level sensor is internally configured to have a device ID of 0x1

Place the water level sensor in your datapath circuit. This device will share the INT and DATA lines with the timer you added previously. However, it should receive its INTA signal from the INTA OUT pin on the timer device. This ensures that if both the timer and keyboard raise an interrupt at the same time, the timer will be acknowledged first, and the water level sensor will be acknowledged after. This is known as “daisy chaining” devices.

5.3 Implementing the Water Level Sensor Interrupt Handler

The handler for your water level sensor will work similarly to the one you wrote for the timer device. However, instead of incrementing a timer at a memory location, you will accumulate the readings the water level sensor gives you to a memory location pointed to by the label total water.

In addition to the usual overhead of an interrupt handler, your water level sensor handler must do the following:

1. Use the IN instruction to obtain the most recent water level reading. Note that all water levels will be 2’s complement numbers.

2. Add the value obtained by the water level sensor to the total water level collected so far.

Make sure that properly you install the location of the new handler into the IVT.

6 Deliverables

Please submit the following files to gradescope:

• CircuitSim datapath file (LC-901a.sim)

• Microcode file (microcode.xlsx)

• Assembly code (prj2.s)

Always re-download your assignment from gradescope after submitting to ensure that all necessary files were properly uploaded. If what we download does not work, you will get a 0 regardless of what is on your machine.

This project will be demoed. In order to receive full credit, you must sign up for a demo slot and complete the demo. We will announce when demo times are released.

7 Appendix A: LC-901a Instruction Set Architecture

The LC-901a is a simple, yet capable computer architecture. The LC-901a combines attributes of both ARM and the LC-2200 ISA defined in the Ramachandran &amp; Leahy textbook for CS 2200.

The LC-901a is a word-addressable, 32-bit computer. All addresses refer to words, i.e. the first word (four bytes) in memory occupies address 0x0, the second word, 0x1, etc.

All memory addresses are truncated to 16 bits on access, discarding the 16 most significant bits if the address was stored in a 32-bit register. This provides roughly 64 KB of addressable memory.

7.1 Registers

The LC-901a has 16 general-purpose registers. While there are no hardware-enforced restraints on the uses of these registers, your code is expected to follow the conventions outlined below.

Table 1: Registers and their Uses

Register Number Name Use Callee Save?

0 $zero Always Zero NA

1 $at Assembler/Target Address NA

2 $v0 Return Value No

3 $a0 Argument 1 No

4 $a1 Argument 2 No

5 $a2 Argument 3 No

6 $t0 Temporary Variable No

7 $t1 Temporary Variable No

8 $t2 Temporary Variable No

9 $s0 Saved Register Yes

10 $s1 Saved Register Yes

11 $s2 Saved Register Yes

12 $k0 Reserved for OS and Traps NA

13 $sp Stack Pointer No

14 $fp Frame Pointer Yes

15 $ra Return Address No

1. Register 0 is always read as zero. Any values written to it are discarded. Note: for the purposes of this project, you must implement the zero register. Regardless of what is written to this register, it should always output zero.

3. Register 2 is where you should store any returned value from a subroutine call.

4. Registers 3 – 5 are used to store function/subroutine arguments. Note: registers 2 through 8 should be placed on the stack if the caller wants to retain those values. These registers are fair game for the callee (subroutine) to trash.

5. Registers 6 – 8 are designated for temporary variables. The caller must save these registers if they want these values to be retained.

7. Register 12 is reserved for handling interrupts. While it should be implemented, it otherwise will not have any special use on this assignment.

8. Register 13 is your anchor on the stack. It keeps track of the top of the activation record for a subroutine.

9. Register 14 is used to point to the first address on the activation record for the currently executing process.

10. Register 15 is used to store the address a subroutine should return to when it is finished executing.

7.2 Instruction Overview

The LC-901a supports a variety of instruction forms, only a few of which we will use for this project. The instructions we will implement in this project are summarized below.

Table 2: LC-901a Instruction Set

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0000 DR SR1 unused SR2

0001 DR SR1 unused SR2

0010 DR SR1 immval20

0011 DR BaseR offset20

0100 SR BaseR offset20

0101 SR1 SR2 offset20

0110 RA AT unused

0111 unused

1000 SR1 SR2 offset20

1001 DR unused PCoffset20

1010 unused

1011 unused

1100 unused

1101 DR 0000 addr20

1111 DR unused

ADD

NAND

ADDI

LW

SW

BEQ

JALR

HALT

BLT

LEA

EI

DI

RETI

IN

INC

7.2.1 Conditional Branching

Conditional branching in the LC-901a ISA is provided via two instructions: the BLT (”branch if less than”) and BEQ (”branch if equal”) instructions. The BEQ will branch to address ”incrementedPC + offset20” only if SR1 and SR2 are equal. However, BLT will branch to address ”incrementedPC + offset20” only if SR1 is strictly less than SR2.

7.3 Detailed Instruction Reference

7.3.1 ADD

Assembler Syntax

ADD DR, SR1, SR2

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0000 DR SR1 unused SR2

Operation

DR = SR1 + SR2;

Description

The ADD instruction obtains the first source operand from the SR1 register. The second source operand is obtained from the SR2 register. The second operand is added to the first source operand, and the result is stored in DR.

7.3.2 NAND

Assembler Syntax

NAND DR, SR1, SR2

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0001 DR SR1 unused SR2

Operation

DR = ~(SR1 &amp; SR2);

Description

The NAND instruction performs a logical NAND (AND NOT) on the source operands obtained from SR1 and SR2. The result is stored in DR.

HINT: A logical NOT can be achieved by performing a NAND with both source operands the same.

For instance,

NAND DR, SR1, SR1

…achieves the following logical operation: DR←SR1.

7.3.3 ADDI

Assembler Syntax

ADDI DR, SR1, immval20

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0010 DR SR1 immval20

Operation

DR = SR1 + SEXT(immval20);

Description

The ADDI instruction obtains the first source operand from the SR1 register. The second source operand is obtained by sign-extending the immval20 field to 32 bits. The resulting operand is added to the first source operand, and the result is stored in DR.

7.3.4 LW

Assembler Syntax

LW DR, offset20(BaseR)

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0011 DR BaseR offset20

Operation

DR = MEM[BaseR + SEXT(offset20)];

Description

An address is computed by sign-extending bits [19:0] to 32 bits and then adding this result to the contents of the register specified by bits [23:20]. The 32-bit word at this address is loaded into DR.

7.3.5 SW

SW SR, offset20(BaseR)

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0100 SR BaseR offset20

Operation

MEM[BaseR + SEXT(offset20)] = SR;

Description

An address is computed by sign-extending bits [19:0] to 32 bits and then adding this result to the contents of the register specified by bits [23:20]. The 32-bit word obtained from register SR is then stored at this address.

7.3.6 BEQ

Assembler Syntax

BEQ SR1, SR2, offset20

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0101 SR1 SR2 offset20

Operation

if (SR1 == SR2) {

PC = incrementedPC + offset20

}

Description

A branch is taken if SR1 and SR2 are equal. If this is the case, the PC will be set to the sum of the incremented PC (since we have already undergone fetch) and the sign-extended offset[19:0].

7.3.7 JALR

JALR RA, AT

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0110 RA AT unused

Operation

RA = PC;

PC = AT;

Description

First, the incremented PC (address of the instruction + 1) is stored into register RA. Next, the PC is loaded with the value of register AT, and the computer resumes execution at the new PC.

7.3.8 HALT

Assembler Syntax

HALT

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0111 unused

Description

The machine is brought to a halt and executes no further instructions.

7.3.9 BLT

Assembler Syntax

BLT SR1, SR2, offset20

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1000 SR1 SR2 offset20

Operation

if (SR1 &lt; SR2) {

PC = incrementedPC + offset20

}

Description

A branch is taken if SR1 is (strictly) less than SR2. If this is the case, the PC will be set to the sum of the incremented PC (since we have already undergone fetch) and the sign-extended offset[19:0].

7.3.10 LEA

LEA DR, label

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1001 DR unused PCoffset20

Operation

DR = PC + SEXT(PCoffset20);

Description

An address is computed by sign-extending bits [19:0] to 32 bits and adding this result to the incremented PC (address of instruction + 1). It then stores the computed address into register DR.

7.3.11 EI

Assembler Syntax

EI

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1010 unused

Operation

IE = 1;

Description

The Interrupts Enabled register is set to 1, enabling interrupts.

7.3.12 DI

Assembler Syntax

DI

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1011 unused

Operation

IE = 0;

Description

The Interrupts Enabled register is set to 0, disabling interrupts.

7.3.13 RETI

Assembler Syntax

RETI

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1100 unused

Operation

PC = $k0;

IE = 1;

Description

The PC is restored to the return address stored in $k0. The Interrupts Enabled register is set to 1, enabling interrupts.

7.3.14 IN

Assembler Syntax

IN DR, DeviceADDR

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1101 DR 0000 addr20

Operation

DAR = addr20;

DR = DeviceData; DAR = 0;

Description

The value in addr20 is sign-extended to determine the 32-bit device address. This address is then loaded into the Device Address Register (DAR). The processor then reads a single word value off the device data bus, and writes this value to the DR register. The DAR is then reset to zero, ending the device bus cycle.

7.3.15 INC

Assembler Syntax

INC DR

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1111 DR unused

Operation

DR = DR + 1;

Description

Increments the value stored in register DR by one and stores the computed result into the same register DR.

8 Appendix B: Microcontrol Unit

You will make a microcontrol unit which will drive all of the control signals to various items on the datapath. This Finite State Machine (FSM) can be constructed in a variety of ways. You could implement it with combinational logic and flip flops, or you could hard-wire signals using a single ROM. The single ROM solution will waste a tremendous amount of space since most of the microstates do not depend on the opcode or the conditional test to determine which signals to assert. For example, since the condition line is an input for the address, every microstate would have to have an address for condition = 0 as well as condition = 1, even though this only matters for one particular microstate.

To solve this problem, we will use a four ROM microcontroller. In this arrangement, we will have four ROMs:

• the main ROM, which outputs the control signals,

• the sequencer ROM, which helps to determine which microstate to go at the end of the FETCH state,

• the condition ROM, which helps determine whether or not to branch during the BEQ and BLT instructions.

• and the interrupt ROM, which helps determine whether or not to go to the INT macrostate if an interrupt is present.

Examine the following:

Figure 3: Four ROM Microcontrol Unit

As you can see, there are four different locations that the next state can come from: part of the output from the previous state (main ROM), the sequencer ROM, the condition ROM, or the interrupt ROM. The mux controls which of these sources gets through to the state register. If the previous state’s “next state” field determines where to go, neither the OPTest nor ChkCmp signals will be asserted. If the opcode from the IR determines the next state (such as at the end of the FETCH state), the OPTest signal will be asserted. If the comparison circuitry determines the next state (such as in the BEQ and BLT instructions), the ChkCmp signal will be asserted. If we need to check the interrupt ROM (at the end of execute or the beginning of fetch macrostates) then we assert ChkCmp and OPTest.

The sequencer ROM should have one address per instruction, the condition ROM should have one address for condition true and one for condition false, and the interrupt ROM should have one address for OnInt true and one for OnInt false.

The microcode.xlsx spreadsheet has been updated to include a new section that can be used to fill out the interrupt ROM.

Note that there are 5 new control signals that need to be outputted from the main ROM onto the datapath (LdEnInt, EnInt, IntAck, DrData, LdDar).

Table 3: ROM Output Signals

Bit Purpose Bit Purpose Bit Purpose Bit Purpose Bit Purpose Bit Purpose

0 NextState[0] 6 DrREG 12 LdIR 18 WrMEM 24 ChkCmp 30 LdDAR

1 NextState[1] 7 DrMEM 13 LdMAR 19 RegSelLo 25 TypeCmp

2 NextState[2] 8 DrALU 14 LdA 20 RegSelHi 26 LdEnInt

3 NextState[3] 9 DrPC 15 LdB 21 ALULo 27 EnInt

4 NextState[4] 10 DrOFF 16 LdCmp 22 ALUHi 28 IntAck

5 NextState[5] 11 LdPC 17 WrREG 23 OPTest 29 DrData

Table 4: Register Selection Map

RegSelHi RegSelLo Register

0 0 RX (IR[27:24])

0 1 RY (IR[23:20])

1 0 RZ (IR[3:0])

1 1 $k0

Table 5: ALU Function Map

ALUHi ALUlLo Function

0 0 ADD

0 1 SUB

1 0 NAND

1 1 A + 1
