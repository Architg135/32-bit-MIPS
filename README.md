# 32-bit-MIPS
The Verilog code implements a basic MIPS (Microprocessor without Interlocked Pipeline Stages) pipeline processor. The processor operates in a pipelined manner, with instructions passing through several stages: Instruction Fetch (IF), Instruction Decode (ID), Execution (EX), Memory Access (MEM), and Write Back (WB). 
 Here's a brief description of each part of the code:

Module and Inputs
The module mips_pipe takes two clock signals clk1 and clk2 as inputs.
Registers and Parameters
Various registers store the current state of the pipeline:
PC stores the Program Counter.
IF_ID_IR and IF_ID_NPC store the instruction and next program counter in the IF stage.
ID_EX_IR, ID_EX_NPC, ID_EX_A, ID_EX_B, and ID_EX_Imm store the instruction, next program counter, operand A, operand B, and immediate value in the ID stage.
EX_MEM_IR, EX_MEM_ALUout, EX_MEM_B, and EX_MEM_cond store the instruction, ALU output, operand B, and branch condition in the EX stage.
MEM_WB_IR, MEM_WB_ALUout, and MEM_WB_LMD store the instruction, ALU output, and load memory data in the MEM stage.
Reg is a register bank with 32 registers.
Mem is a memory array with 1024 entries.
Several parameter definitions specify opcodes and operation types (e.g., ADD, SUB, RR_ALU, LOAD).
Control Signals
HALTED indicates if the processor is halted.
TAKEN_BRANCH indicates if a branch is taken.
Instruction Fetch (IF) Stage
This stage fetches the instruction from memory. If a branch is taken, it fetches from the branch address; otherwise, it fetches from the current PC.
Instruction Decode (ID) Stage
This stage decodes the instruction and fetches the source registers' values. It also sign-extends the immediate value and determines the instruction type.
Execution (EX) Stage
This stage performs arithmetic, logical operations, memory address calculations, or evaluates branch conditions based on the instruction type.
Memory Access (MEM) Stage
This stage handles memory read and write operations. It stores the results for ALU operations and loads data from memory for load instructions.
Write Back (WB) Stage
This stage writes the results back to the register file. It updates the register with the result of ALU operations or memory loads. If a halt instruction is encountered, it sets the HALTED signal.
Summary
The code implements a simple pipelined MIPS processor capable of handling arithmetic, logical, memory, and branch instructions. The pipeline stages are synchronized using two clock signals to ensure smooth instruction flow and execution.
