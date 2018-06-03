# MultiCycle-MIPS-Architecture-
Used Xilinix to prove Multicycle MIPS
Modified MIPS Lite (MML) Multi-cycle Design Project 
 TABLE OF CONTENTS 
 
Content                                                                               Page Numbers  
Introduction to the project                                                                                        3 
	Team member roles & contributions 	  	 	 	 	         4 
	Types of Modules used in the machine 	 	 	 	                             5 
Multicycle Datapath & Finite State Machine                                                           9 
Verilog codes                                                                                                                12 
	5.2. 2 to 1 MUX 	 	 	 	 	 	 	 	9 
	5.3. Mux 4 to 1 	 	 	 	 	 	 	 	11 
	5.6. 8-bit Shifter (Shift Left Logical) 	 	 	 	 	13  
	5.7. 5 to 16-bit Sign Extender 	 	 	 	 	 	15 
	5.8. 8 to 16 Sign Extender 	 	 	 	 	 	16 
	5.9. 5 to 16 Zero Extender 	 	 	 	 	 	18  
	5.10. 8 to 16 Zero Extender   	 	 	 	 	 	21 
	5.11. 8-bit Shifter   	 	 	 	 	 	 	23  
	5.12. 16-bit Shifter 	 	 	 	 	 	             25  
	5.13. Full Adder (ALU) 	 	 	 	 	 	             27
	5.14. ALU 1 bit (LSB) 	 	 	 	 	 	 	29 
	5.15. ALU 1 bit (MSB) 	 	 	 	 	 	 	32 
	5.16. ALU 16 bit 	 	 	 	 	 	 	 	34 
	5.17. Register File 8x16 	 	 	 	 	 	 	36 
	5.18. ALU Out 	 	 	 	 	 	 	 	38  
	5.20. ALU Controller 		 	 	 	 	 	40  
	Result and Conclusion 	 	 	 	 	 	             43 







 
Modified MIPS Lite (MML) Multi-cycle Design Project 
 
1.Introduction to the Project 
 
In this project, we designed a ‘Multi-cycle Datapath’ for the Modified MIPS-Lite (MML) Instruction Set Architecture and the components of this architecture was individually designed and verified using Verilog Hardware Descriptive Language. 
The architecture had the following specifications:  
•	Byte addressable memory 
•	8 registers (register 0 is always zero) 
•	A 16-bit word 
•	A one-word instruction with the following instruction format: 
      R-format [opcode = 5 bits] [rs = 3 bits] [rt = 3 bits] [rd = 3 bits] [func = 2 bits] 
      I-format   [opcode = 5 bits] [rs = 3 bits] [rt = 3 bits] [immediate = 5 bits] 
      IL-format [opcode = 5bits] [rs = 3 bits] [immediate = 8 bits]   J-format   [opcode = 5 bits] [address = 11 bits] 
•	6 Addressing modes: 
-	Immediate addressing 
-	Long immediate update addressing 
-	Base addressing 
-	PC-Relative addressing 
-	Pseudo direct addressing 
•	Opcode and instruction format table for each instruction is:  
	 	Instruction 	Format 	Opcode 	Instruction 	Format 	Opcode 
Add, Sub, Addu, Subu 	R 	0 	Slit 	I 	15 
And, Or, Slt, Sltu 	R 	1 	Slitu 	I 	16 
Jr 	R 	2 	Beqz 	IL 	17 
Sll 	I 	4 	Bnez 	IL 	18 
Srl 	I 	5 	Lui 	IL 	19 
Lw 	I 	6 	addiu_l 	IL 	20 
Sw 	I 	7 	addi_l 	IL 	21 
Lb 	I 	8 	Ori_l 	IL 	22 
Lbu 	I 	9 	andi_l 	IL 	23 
Sb 	I 	10 	slti_l 	IL 	24 
Addiu 	I 	11 	sltiu_l 	IL 	25 
Addi 	I 	12 	J 	J 	26 
Ori 	I 	13 	Jal 	J 	27 
Andi 	I 	14 	 	 	 
 
 
From the above Opcode and Instruction Format table, this Multicycle datapath can handle 33 different architecture, which are: 9 R-type; 13 I-type; 9 IL-Type; 2 J-type.  
 
 
2. Member Roles and Contribution 
Name	Topic	Status
 Ammar
 
 
 
 
 
 
 
 
 	16-bit shifter	Complete
	8-bit shifter	Complete
	ALU 16 bit	Problem executing test bench
	Mux 2_1	Complete
	Mux4_1	Complete
	1-bit ALU LSB	Complete
	1-bit ALU MSB	Complete
	Register file	Problem executing test bench
	Half Adder	Complete
	Full Adder	Complete
 Sadat
 
 
 	Sign Extender_5 bit	Complete
	Sign Extender_8 bit	Complete
	Zero Extender_5 bit	Complete
	Zero Extender_8 bit	Complete
	Project Report	Complete
 Sebastin
 	Positive edge triggered 16 bit with load signal	Incomplete
	Positive edge triggered 16 bit without load signal	Incomplete
 Aswath Kumar Kulasekara Pandian
 
 
 	ALUcontroller	Problem with test
	ALUOUT	Problem with test
	Multicycle datapath	Complete
	Project Report	Complete
 

3. Types of Modules Used in the Machine 
To implement the MML ISA in ISE we had to create the following modules 	 	 	 	 	 	 	 	 	 	    
•	2to1 Mux 	     	 	 	 	 	 	 	 	                 
•	4to1Mux  	 	 	 	 	 	 	 	             	 	 	                            
•	5to16 Sign Extender  	 	 	 	 	 	 	 	 
•	5to16 Zero Extender   	 	 	 	 	 	 	 
•	8to16 Sign Extender  	 	 	 	 	 	 	 	 
•	8to16 Zero Extender  	 	 	 	 	 	 	          
•	8bits_left shifter 	 	 	 	 	 	 	 	 	 
•	16-bit left shifter 	 	 	 	 	 	 	 	 	 
•	Full Adder	 	 	 	 	 	 	 	 	 
•	1 bit ALU LSB 
•	1 bit ALU MSB 	 	 	 	 	 	 	 	 	 
•	ALU 16 bit	 	 	 	 	 	 	 	 	            
•	Memory file          
•	Register file           
•	positive-edge triggered register with load signal 
•	positive-edge triggered register without load signal    	 	 	 
•	ALU controller 	 	 	 	 	 	 	 	 	 
•	ALU OUT	 	 	 	 	 	 	 	 

3.1 ALU Design 
The Arithmetic Logic Unit is used to perform arithmetic and logical operations of the instructions. In this project, the ALU performs operations such as: And, Or, Add, Sub, and Less. 
To design a 16-bit ALU we’ve design each element of the ALU individually and combined them in a single code.  
The logic 1 bit ALU is shown below: 
  
There are 2 to 1 Mux with selection line ‘Ainvert’ and ‘Binvert’ to make appropriate operation from the inputs. And the logical gates are used to perform necessary combination operation with the outputs from the 2 muxs’. The Adder is used to perform the necessary Cin and Cout operation.  
With the concept of the ALU 1 bit LSB we’ve designed an ALU 1 Bit MSB   
 
Our purpose is to use this 1bit ALU (LSB and MSB) to build 16bit ALU and we set the outpouts ‘CarryOut’ and MSB of Less for future use. 16bits ALU is built from extension 16 times of 1bit ALU.  
 
4. Multicycle Datapath & Finite State Machine   
The finite state machine has, at most, five stages for the execution of each of the given instruction. Cycle 1 is where we fetch the instruction and increment the PC; cycle 2 is for reading sources from the register file; cycle 3 is performing an ALU computation; cycle 4 is reading or writing (data) memory; and finally, cycle 5 is storing data back to the register file. 
The 5 stages/cycles are explained below: 
Cycle 1: Instruction Fetch  
    Instruction is fetched from memory and the address of the next instruction is computed 
IR = Memory[PC]; 
PC = PC + 2; 
 
Cycle 2: Instruction Decode and Register Fetch 
Read the registers from the register file $rs and $rt into A and B respectively and compute branch address using ALU and save in ALUOut 
 
Register A: = Reg[IR[rs], Register B: = Reg[IR[rt]] 
  ALUout: = PC + sign-extend(IR[imm])<<1 
 
 
Cycle 3: Execution| Memory Address| Branch Completion | Jump Completion 
 
    ALU operates on the operands, depending on class of instruction 
Memory Reference: ALU creates memory address by adding operands  
                                                    ALUout: = A + IR[ ] 
 
R-type (ALU): ALU performs operation specified by function code on values in registers A, B                                                                                                            ALU out:= A op B 
Branch: ALU compares A and B. If equal, Zero output signal is set to cause branch, and PC is updated with branch address 
                                                        PC: = ALUout  
 Jump: PC is replaced by jump address 
                                                           PC = Address 
Cycle 4: Memory Access | R-type Completion | Immediate Completion 
R-type/ Immediate: In this cycle, the R-type instruction will be executed, and the value stored in ALUout is put into the register.  
        Reg[IR[rd ]]: = ALUout 
Load Word: The address computed and stored in ALUout is put into the Memory Data Register. 
                                                        Memory[ALUout] 
Store Word: Store the value using the memory address computed in the previous step. 
                                                      Memory[ALUout]: = B 
 
Cycle 5: Write back 
Load Word: Load the value from the memory data register and store it into the register file. 
                                                       Reg[wa]: = MDR 
 
 
 
 
 
5. Verilog Module 
 
 
5.1. Mux 2 to 1 
 
Verilog Code 
  
module Mux2_1(
    input Sel,
    input A,
    input B,
    output reg Y
    );
	 // reg Y; this was causing problem
	 
	 // Structural Modelling
	 
	 /*not (Sel_, Sel);
	 and (Y1, Sel_, A);
	 and (Y2, Sel, B);
	 or (Y, Y1, Y2);*/
	 
	 // Data Flow Modellig
	 
	 // assign Y = (Sel==0) ? A : B; // continuos assignment
	 
	 // Behavioural Modelling
	 
	 always @ ( A or B or Sel) // sensitivity list
	 
	 begin
	 if ( Sel==0)
	  Y = A;
	 else
	  Y = B;
	 end
	 


endmodule 

Test File 
 
module Test_Mux2_1;

	// Inputs
	reg Sel;
	reg A;
	reg B;

	// Outputs
	wire Y;

	// Instantiate the Unit Under Test (UUT)
	Mux2_1 uut (
		.Sel(Sel), 
		.A(A), 
		.B(B), 
		.Y(Y)
	);

	initial begin
		// Initialize Inputs
		Sel = 0;
		A = 0;
		B = 0;

		// Wait 100 ns for global reset to finish
		#100;
        
		  A=1;
		  #100;
		  Sel=1;
		  #100;
		  B=1;
		// Add stimulus here

	end
      
endmodule
 
Test Result 
 
  
 
 
 
 
 
 
 
5.2. Mux 4 to 1 
 
Verilog Code 
 
module Mux4_1(
    input [1:0] Sel,
	 input D0,
    input D1,
    input D2,
    input D3,
    output reg Y
    );

/*Mux2_1 mo(Sel[0], D0, D1, Y0);
Mux2_1 m1(Sel[0], D2, D3, Y1);
Mux2_1 m3(Sel[1], Y0, Y1, Y);*/

always @ (D0 or D1 or D2 or D3 or Sel)
 begin
  case(Sel)
  2'h0 : Y=D0;
  2'h1 : Y=D1;
  2'h2 : Y=D2;
  2'h3 : Y=D3;
  endcase
 end
endmodule 
Test Module 
 
module Test_Mux4_1;

	// Inputs
	reg D0;
	reg D1;
	reg D2;
	reg D3;
	reg [1:0] Sel;

	// Outputs
	wire Y;

	// Instantiate the Unit Under Test (UUT)
	Mux4_1 uut (
		.D0(D0), 
		.D1(D1), 
		.D2(D2), 
		.D3(D3), 
		.Sel(Sel), 
		.Y(Y)
	);

	initial begin
		// Initialize Inputs
		D0 = 0;
		D1 = 0;
		D2 = 0;
		D3 = 0;
		Sel = 0;

		// Wait 100 ns for global reset to finish
		#100;
        D0=1;
		#100;
		  Sel=1;
		 #100;
		  D1=1;
		 #100;
		  Sel=2;
		 #100;
		  D2=1;
		 #100;
		  Sel=3;
		 #100;
		  D3=1;
		// Add stimulus here

	end
endmodule  
Test result 
 
  
 
 
5.3. 8 bit Shifter (Shift Left Logical) 
 
Verilog Code 
module shftr8_16(in, shft_out); 
  
input [7:0] in; output [15:0] shft_out; reg [15:0] shft_out; always @(in) begin 
shft_out = {in, 8'b00000000}; 
end 
endmodule  
 
Test File: 
 
module shftr8_16TF; 
 
 	// Inputs  	reg [7:0] in; 
 
	 	// Outputs 
	 	wire [15:0] shft_out; 
 
	 	// Instantiate the Unit Under Test (UUT) 
	 	shftr8_16 uut ( 
	 	 	.in(in),  
	 	 	.shft_out(shft_out) 
	 	); 
 
	 	initial begin 
	 	 	// Initialize Inputs 
	 	 	in = 8'b11110000; 
	 	 	// Wait 100 ns for global reset to finish 
	 	 	#100; 
in=8'b10110011; 
#100;         
 	 	  	end 
             endmodule  
Test result: 
 
  
 
 
 

5.4 5 to 16-bit Sign Extender 
 
Verilog Code 
module Sign_Extender_5to16_Bit(
    input [4:0] immediate_in,
    output reg [15:0] sign_extended_out
    );
	 
	 reg [4:0] immediate;
    reg [15:0] sign_extended;
	 
always@(immediate_in)

	begin
	sign_extended[4:0] = immediate_in;
	if(immediate_in[4]==1'b0)
	sign_extended[15:5] = 11'b00000000000;
	else
	sign_extended[15:5] = 11'b11111111111;


//	  sign_extended[4:0] <= immediate_in[4:0];
//   sign_extended[15:5] <= {11{immediate_in[4]}};
	sign_extended_out <= sign_extended;
	end

endmodule 
Test File 
 
module Test_Sign_Extender_5t016_Bit;

	// Inputs
	reg [4:0] immidiate_in;

	// Outputs
	wire [15:0] signexended_out;

	// Instantiate the Unit Under Test (UUT)
	Sign_Extender_5to16_Bit uut (
		.immidiate_in(immidiate_in), 
		.signexended_out(signexended_out)
	);

	initial begin
		// Initialize Inputs
		immidiate_in = 0;

		// Wait 100 ns for global reset to finish
		#100;
      immidiate_in = 0;  
		// Add stimulus here

	end
      
endmodule 
 
Test Result 
 
  
 
 
 
 
5.5. 8 to 16 Sign Extender 
 
Verilog Code 
module Sign_Extender_8t016_Bit;

	// Inputs
	reg [7:0] immediate_in;

	// Outputs
	wire [15:0] sign_extended_out;

	// Instantiate the Unit Under Test (UUT)
	Sign_Extender_8to16_Bit uut (
		.immediate_in(immediate_in), 
		.sign_extended_out(sign_extended_out)
	);

	initial begin
		// Initialize Inputs
		immediate_in = 0;

		// Wait 100 ns for global reset to finish
		#100;
		immediate_in = 16; 
		
		#100;
      immediate_in = 56;
		
		#100;
      immediate_in = 89;
		
		#100;
      immediate_in = 135;
        
		// Add stimulus here

	end
      
endmodule 
Test File 
 
module Test_Sign_Extender_8to16_Bit;

	// Inputs
	reg [7:0] immediate_in;

	// Outputs
	wire [15:0] sign_extended_out;

	// Instantiate the Unit Under Test (UUT)
	Sign_Extender_8to16_Bit uut (
		.immediate_in(immediate_in), 
		.sign_extended_out(sign_extended_out)
	);

	initial begin
		// Initialize Inputs
		immediate_in = 0;

		// Wait 100 ns for global reset to finish
		#100;
		immediate_in = 16; 
		
		#100;
      immediate_in = 56;
		
		#100;
      immediate_in = 89;
		
		#100;
      immediate_in = 135;
        
		// Add stimulus here

	end
      
endmodule 
 
 
Test Result 
 
  
 
 
5.6. 5 to 16 Zero Extender 
 
Verilog Code 
module Zero_Extender_5to16_Bit(
    input [4:0] immediate_in,
    output reg [15:0] zero_extended_out
    );

	 reg [4:0] immediate;
    reg [15:0] zero_extended;
	 
always@(immediate_in)

	begin
	zero_extended[4:0] = immediate_in[4:0];
   zero_extended[15:5] = 11'b00000000000;
	zero_extended_out = zero_extended;
	end



endmodule 

Test File 
 
module Test_Zero_Extender_5to16_Bit;

	// Inputs
	reg [4:0] immediate_in;

	// Outputs
	wire [15:0] zero_extended_out;

	// Instantiate the Unit Under Test (UUT)
	Zero_Extender_5to16_Bit uut (
		.immediate_in(immediate_in), 
		.zero_extended_out(zero_extended_out)
	);

	initial begin
		// Initialize Inputs
		immediate_in = 0;

		// Wait 100 ns for global reset to finish
		#100;
		immediate_in = 3;
		
		#100;
		immediate_in = 14;
		
		#100;
      immediate_in = 11;
		
		#100;
      immediate_in = 16;
		
		#100;
      immediate_in = 1;
        
		// Add stimulus here

	end
      
endmodule
 
Test Result 
 
  
 
 











5.7. 8 to 16 Zero Extender 
Verilog Code 
module Zero_Extender_8to16_Bit(
    input [7:0] immediate_in,
    output reg [15:0] zero_extended_out
    );

    reg [7:0] immediate;
    reg [15:0] zero_extended;
	 
 always@(immediate_in)
	 
	begin
	zero_extended[7:0] = immediate_in[7:0];
   zero_extended[15:8] = 11'b00000000;
	zero_extended_out = zero_extended;
	end
	 
	 
	 
    endmodule
Test File 
module Test_Zero_Extender_8to16_Bit;

	// Inputs
	reg [7:0] immediate_in;

	// Outputs
	wire [15:0] zero_extended_out;

	// Instantiate the Unit Under Test (UUT)
	Zero_Extender_8to16_Bit uut (
		.immediate_in(immediate_in), 
		.zero_extended_out(zero_extended_out)
	);

	initial begin
		// Initialize Inputs
		immediate_in = 0;

		// Wait 100 ns for global reset to finish
		#100;
		immediate_in = 3;
		
		#100;
		immediate_in = 14;
		
		#100;
      immediate_in = 11;
		
		#100;
      immediate_in = 16;
		
		#100;
      immediate_in = 103;
		
		#100;
      immediate_in = 135;

        
		// Add stimulus here

	end
      
endmodule 
Test Result 
 
  
 
 




5.8. 8-bit Shifter 
 
Verilog Code 
module Shifter_8Bit(
    input [15:0] shifter_input,
    input [3:0] shift_amount,
	 output reg [15:0] shifter_output,
	 input shift_type
    );
;
always@(shifter_input)
	begin
	if (shift_type==1)   //left shift
		shifter_output = shifter_input << shift_amount;
	else if (shift_type==0)
		shifter_output = shifter_input >> shift_amount;

	end

endmodule 
Test Module 
 
module Test_Shifter_8Bit;

	// Inputs
	reg [15:0] shifter_input;
	reg [3:0] shift_amount;
	reg shift_type;

	// Outputs
	wire [15:0] shifter_output;

	// Instantiate the Unit Under Test (UUT)
	Shifter_8Bit uut (
		.shifter_input(shifter_input), 
		.shift_amount(shift_amount), 
		.shifter_output(shifter_output), 
		.shift_type(shift_type)
	);

	initial begin
		// Initialize Inputs
		shifter_input = 0;
		shift_amount = 0;
		shift_type = 0;

		// Wait 100 ns for global reset to finish
		#100;
      shifter_input = 7;
		shift_amount = 8;
		shift_type = 1;
		
		#100;
      shifter_input = 3;
		shift_amount = 8;
		shift_type = 1;
		
		#100;
      shifter_input = 5;
		shift_amount = 8;
		shift_type = 1;
		
		#100;
      shifter_input = 11;
		shift_amount = 8;
		shift_type = 1;
        
		// Add stimulus here

	end
      
endmodule   
 
 
 
 
Test Result 
  
 
 
 
5.9. 16-bit Shifter 
 
Verilog Code 
module Shifter_16Bit(
    input [15:0] shifter_input,
	 input [3:0] shift_amount,
    output reg [15:0] shifter_output,
	 input shift_type
    );
 always@(shifter_input)
	begin
	if (shift_type==1)   //left shift
		shifter_output = shifter_input << shift_amount;
	else if (shift_type==0)
		shifter_output = shifter_input >> shift_amount;

	end
		
	
	
 

endmodule	 
 
Test File 
 
module Test_Shifter_16Bit;

	// Inputs
	reg [15:0] shifter_input;
	reg [3:0] shift_amount;
	reg shift_type;

	// Outputs
	wire [15:0] shifter_output;

	// Instantiate the Unit Under Test (UUT)
	Shifter_16Bit uut (
		.shifter_input(shifter_input), 
		.shift_amount(shift_amount), 
		.shifter_output(shifter_output), 
		.shift_type(shift_type)
	);

	initial begin
		// Initialize Inputs
		shifter_input = 0;
		shift_amount = 0;
		shift_type = 0;

		// Wait 100 ns for global reset to finish
		#100;
      shifter_input = 7;
		shift_amount = 2;
		shift_type = 1;  
		
		#100;
      shifter_input = shifter_output;
		shift_amount = 2;
		shift_type = 0;
		
		#100;
      shifter_input = 7;
		shift_amount = 3;
		shift_type = 1;
		
		
		// Add stimulus here

	end
      
endmodule 
 
  
 
 
5.10. Full Adder ( for ALU) 
 
Verilog Code 
module Full_Adder_1Bit(
    input A,
    input B,
    input Cin,
    output Sum,
    output Carry
    );
Half_Adder h0(A, B, Y0);
Half_Adder h1(Cin, Y0, Sum);
and(Carry, A, B);

 

endmodule 
Test Module: 
 
module Test_Full_Adder_1Bit;

	// Inputs
	reg A;
	reg B;
	reg Cin;

	// Outputs
	wire Sum;
	wire Carry;

	// Instantiate the Unit Under Test (UUT)
	Full_Adder_1Bit uut (
		.A(A), 
		.B(B), 
		.Cin(Cin), 
		.Sum(Sum), 
		.Carry(Carry)
	);

	initial begin
		// Initialize Inputs
		A = 0;
		B = 0;
		Cin = 0;

		// Wait 100 ns for global reset to finish
		#100;
		A=0;
		B=0;
		Cin=1;
		#100;
		A=0;
		B=1;
		Cin=0;
		#100;
		A=0;
		B=1;
		Cin=1;
		#100;
		A=1;
		B=0;
		Cin=0;
		#100;
		A=1;
		B=0;
		Cin=1;
		#100;
		A=1;
		B=1;
		Cin=0;
		#100;
		A=1;
		B=1;
		Cin=1;
		#100;
		
        
		// Add stimulus here

	end
      
endmodule 
 
 




Test Result 
 
	 	 
 
 
 
5.11 ALU 1 bit (LSB) 
 
Verilog Code 
module ALU_1Bit(
    input a0,
    input b0,
    input less,
    input [3:0] op,
	 input cin,
	 output cout_carry,
    output r_output
	 
    );
not (a0_, a0);
not (b0_, b0);
Mux2_1 m0 (op[3], a0, a0_, y0);
Mux2_1 m1 (op[2], b0, b0_, y1);
and (y2, y0, y1);
or (y3, y0, y1);
Full_Adder_1Bit f0(Y0, Y1, cin, y4_sum,cout_carry );
Mux4_1 m3 (op[1:0], y2, y3, y4, less, r_output);

endmodule 
 
 
Test Module 
 
module Test_ALU_1Bit;

	// Inputs
	reg a0;
	reg b0;
	reg less;
	reg [3:0] op;
	reg cin;

	// Outputs
	wire r_output;
	wire cout_carry;

	// Instantiate the Unit Under Test (UUT)
	ALU_1Bit uut (
		.a0(a0), 
		.b0(b0), 
		.less(less), 
		.op(op), 
		.cin(cin), 
		.r_output(r_output), 
		.cout_carry(cout_carry)
	);

	initial begin
		// Initialize Inputs
		a0 = 0;
		b0 = 0;
		less = 0;
		op = 0;
		cin = 0;

		// Wait 100 ns for global reset to finish
		#100;
      a0 = 1;
		b0 = 1;
		less = 1;
		op = 0;
		cin = 1;  
		
		#100;
      a0 = 1;
		b0 = 0;
		less = 1;
		op = 0;
		cin = 1;
		// Add stimulus here

	end
      
endmodule
 
Test Result 
 
	 	 
 
 




5.12 ALU 1 bit (MSB)
Verilog Code 
module ALU_1Bit_MSB(
    input a0,
    input b0,
    input less,
    input [3:0] op,
    input cin,
    output cout_output,
    output r_output,
    output set_v
    );

not (a0_, a0);
not (b0_, b0);
Mux2_1 m0 (op[3], a0, a0_, y0);
Mux2_1 m1 (op[2], b0, b0_, y1);
and (y2, y0, y1);
or (y3, y0, y1);
Full_Adder_1Bit f0(Y0, Y1, cin, y4_sum,cout_carry );
Mux4_1 m3 (op[1:0], y2, y3, y4, less, r_output);
xor (v, cin, cout_carry);
xor (set_v, v, y4_sum);

endmodule 


Test Module  
module Test_ALU_1Bit_MSB;

	// Inputs
	reg a0;
	reg b0;
	reg less;
	reg [3:0] op;
	reg cin;

	// Outputs
	wire cout_output;
	wire r_output;
	wire set_v;

	// Instantiate the Unit Under Test (UUT)
	ALU_1Bit_MSB uut (
		.a0(a0), 
		.b0(b0), 
		.less(less), 
		.op(op), 
		.cin(cin), 
		.cout_output(cout_output), 
		.r_output(r_output), 
		.set_v(set_v)
	);

	initial begin
		// Initialize Inputs
		a0 = 0;
		b0 = 0;
		less = 0;
		op = 0;
		cin = 0;

		// Wait 100 ns for global reset to finish
		#100;
        
		// Add stimulus here

	end
      
endmodule 


Test Result 
  
 
 
5.13. ALU 16 bit 
 
Verilog Code 
module ALU_16Bit(
    input [15:0] a,
    input [15:0] b,
	 input [3:0] op,
    input cin,
	 output [15:0] cout_carry,
	 output [15:0] r_output,
	 output zero
	 
    );
	 
	 wire cin, cout;
	 ALU_1Bit A0(a[0], b[0], op, cin, 1, cout_carry[0], r_output[0]);
	 ALU_1Bit A1(a[1], b[1], op, cout_carry[0], 1'b0, cout_carry[1], r_output[1]);
	 ALU_1Bit A2(a[2], b[2], op, cout_carry[1], 1'b0, cout_carry[2], r_output[2]);
	 ALU_1Bit A3(a[3], b[3], op, cout_carry[2], 1'b0, cout_carry[3], r_output[3]);
	 ALU_1Bit A4(a[4], b[4], op, cout_carry[3], 1'b0, cout_carry[4], r_output[4]);
	 ALU_1Bit A5(a[5], b[5], op, cout_carry[4], 1'b0, cout_carry[5], r_output[5]);
	 ALU_1Bit A6(a[6], b[6], op, cout_carry[5], 1'b0, cout_carry[6], r_output[6]);
	 ALU_1Bit A7(a[7], b[7], op, cout_carry[6], 1'b0, cout_carry[7], r_output[7]);
	 ALU_1Bit A8(a[8], b[8], op, cout_carry[7], 1'b0, cout_carry[8], r_output[8]);
	 ALU_1Bit A9(a[9], b[9], op, cout_carry[8], 1'b0, cout_carry[9], r_output[9]);
	 ALU_1Bit A10(a[10], b[10], op, cout_carry[9],  1'b0, cout_carry[10], r_output[10]);
	 ALU_1Bit A11(a[11], b[11], op, cout_carry[10], 1'b0, cout_carry[11], r_output[11]);
	 ALU_1Bit A12(a[12], b[12], op, cout_carry[11], 1'b0, cout_carry[12], r_output[12]);
	 ALU_1Bit A13(a[13], b[13], op, cout_carry[12], 1'b0, cout_carry[13], r_output[13]);
	 ALU_1Bit A14(a[14], b[14], op, cout_carry[13], 1'b0, cout_carry[14], r_output[14]);
	 ALU_1Bit_MSB A15(a[15], b[15], op, cout_carry[14], 1'b0, r_output[15], v, set_v);
// why lsb is 1 and rest zeroes
// because of the condition of set less than
// slt $9,$10,$8
// if $10-$8 is < 0
// $9 =001 so the lsb matters
// alu_lsb alu0(a[0], b[0], cin, op, 1 , r[0], c1);
// alu_lsb alu1(a[1], b[1], c1, op, 1'b0 r[1], c2);
// alu_lsb alu2(a[2], b[2], c2, op, 1'b0 r[2], c3);
// alu_msb alu15(a[15], b[15], c15, op, 1'b0, r[15], v, setv, cout)

	 
	 /*ALU_1Bit A0(a[0], b[0], cin,*/ 
	 


endmodule 
Test File: 
 
module Test_ALU_16Bit;

	// Inputs
	reg [15:0] a;
	reg [15:0] b;
	reg [3:0] op;
	reg cin;

	// Outputs
	wire [15:0] cout_carry;
	wire [15:0] r_output;
	wire zero;

	// Instantiate the Unit Under Test (UUT)
	ALU_16Bit uut (
		.a(a), 
		.b(b), 
		.op(op), 
		.cin(cin), 
		.cout_carry(cout_carry), 
		.r_output(r_output), 
		.zero(zero)
	);

	initial begin
		// Initialize Inputs
		a = 0;
		b = 0;
		op = 0;
		cin = 0;

		// Wait 100 ns for global reset to finish
		#100;
        
		// Add stimulus here

	end
      
endmodule
 
Test Result 
  
 
 
 
 
5.14. Register File  
 
Verilog Code 
module Reg_16Bit(
    output [15:0] Read_Data_1,
	 output [15:0] Read_Data_2,
	 input [15:0] Read_Address_1,
    input [15:0] Read_Address_2,
    input [2:0] Write_Address,
    input [2:0] Write_Data,
    input Reg_Write
    );
	 
reg [15:0] Reg_File_16 [15:0];

assign Read_Data_1 = Reg_File_16[Read_Address_1];
assign Read_Data_2 = Reg_File_16[Read_Address_2];

always @ (Reg_Write)
	begin
	if (Reg_Write)
		Reg_File_16[Write_Address] = Write_Data;
	end

endmodule 
Test File 
 
module Test_Reg_16Bit;

	// Inputs
	reg [15:0] Read_Address_1;
	reg [15:0] Read_Address_2;
	reg [2:0] Write_Address;
	reg [2:0] Write_Data;
	reg Reg_Write;

	// Outputs
	wire [15:0] Read_Data_1;
	wire [15:0] Read_Data_2;

	// Instantiate the Unit Under Test (UUT)
	Reg_16Bit uut (
		.Read_Data_1(Read_Data_1), 
		.Read_Data_2(Read_Data_2), 
		.Read_Address_1(Read_Address_1), 
		.Read_Address_2(Read_Address_2), 
		.Write_Address(Write_Address), 
		.Write_Data(Write_Data), 
		.Reg_Write(Reg_Write)
	);

	initial begin
		// Initialize Inputs
		Read_Address_1 = 0;
		Read_Address_2 = 0;
		Write_Address = 0;
		Write_Data = 0;
		Reg_Write = 0;

		// Wait 100 ns for global reset to finish
		#100;
      Read_Address_1 = 4;
		Read_Address_2 = 5;
		Write_Address = 7;
		Write_Data = 21;
		Reg_Write = 1;  
		// Add stimulus here

	end
      
endmodule 
Test Result 
 
	 	 
 
 
5.15. ALU Out 
 
Verilog Code 
module aluout(aluresult,clk,aluout1); 
    input [15:0] aluresult;     input clk; 
    output [15:0] aluout1; 
  
 reg [15:0] aluout1; 
 
    always @(posedge clk)  	 begin 
    assign aluout1=aluresult; end 
endmodule 
 
Test File 
 
module sktest; // Inputs reg [15:0] aluresult; reg clk; 
 
// Outputs wire [15:0] aluout1; 
 
// Instantiate the Unit Under Test (UUT) 
aluout uut ( .aluresult(aluresult),  
.clk(clk),  
.aluout1(aluout1) 
); 
 
initial begin 
// Initialize Inputs 
//aluresult = 0; 
//clk = 0; 
 
// Wait 100 ns for global reset to finish 
//#100; 
         
// Add stimulus here aluresult = 5; 
clk = 1; 
#100; 
 
end endmodule 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
Test Result 
  
 
 
 
 

 
5.16 ALU Controller 
 
Verilog Code 
module alucontroller(  Operation,opcode,func,ALUOp 
    ); 
 
   input [1:0]opcode;  
	 	// Changed to generic 2-bits; We can control what goes into ALU controller                       
// when we put together the whole thing  
   input [2:0]ALUOp;   
	 	input [1:0]func;   
	 	output [2:0]Operation;  
   reg [2:0]Operation;   
	 	wire [3:0]sel;    
   assign sel=({opcode,func});    
	 	always @(sel or ALUOp)   
	 	begin    if (ALUOp==3'b010)  
   begin     case(sel)        //opcode=0     
	 	 	4'b0000 : Operation=3'b010;  //add      
	 	 	4'b0001 : Operation=3'b110;  //subtract    
	 	 	4'b0010 : Operation=3'b010;  //add unsigned    
	 	 	4'b0011 : Operation=3'b110;  //subtract unsigned  //opcode=1   
	 	 	4'b0100 : Operation=3'b000; //and      
	 	 	4'b0101 : Operation=3'b001; //or    
4'b0110 : Operation=3'b111; //slt     
	 	4'b0111 : Operation=3'b111; //sltu        //opcode=2     
	 	4'b1000 : Operation=3'bxxx; //jr       
	 	4'b1001 : Operation=3'bxxx; //unused    
	 	4'b1010 : Operation=3'bxxx; //unused       
 	 	4'b1011 : Operation=3'bxxx; //unused    //opcode=3 unused      	default Operation=3'bxxx;   
   endcase    
	 	end       
	 	else if(ALUOp==3'b000)begin   //add          
   Operation=3'b010;       
   end  
   else if (ALUOp==3'b001)begin            Operation=3'b110;    //sub          end  
   else if (ALUOp==3'b011)begin            Operation=3'b111;  //slt        
	 	end   
	 	else if (ALUOp==3'b100)begin            Operation=3'b001;   // or    
	 	end  
   else if (ALUOp==3'b101)begin            Operation=3'b000; //and      
	 	end    
	 	end     
  endmodule 
 
Test File 
 
module alucontrollertf; 
 
 	// Inputs  	reg [1:0] opcode;  	reg [1:0] func; 
	 	reg [2:0] ALUOp; 
 
	 	// Outputs 
	 	wire [2:0] Operation; 
 
	 	// Instantiate the Unit Under Test (UUT) 
	 	alucontroller uut ( 
	 	 	.Operation(Operation),  
	 	 	.opcode(opcode),  
	 	 	.func(func),  
	 	 	.ALUOp(ALUOp) 
	 	); 
 
 	initial begin  	 	// Initialize Inputs  	 	opcode = 0;  	 	func = 0;  	 	ALUOp = 0; 
	 	 	// Wait 100 ns for global reset to finish 
	 	 	#100; 
                          opcode = 1; 
	 	 	#100; 
                         opcode =2;  
            func =1 ; 
	 	 	#100; 
                         ALUOp = 1; 
	 	 	#100; opcode = 3; 
	 	 	#100; ALUOp =2; 
	 	 	#100; func =2; 
	 	 	#100; opcode=0; 
	 	 	#100; opcode=7; 
	 	 	#100; func = 3; 
	 	 	#100; opcode=10 ; 
 	 	#100; ALUOp=3;  	 	#100; opcode=14;  	end endmodule 
 
Test Result 
 
  

 
 
 
 
 
6. Result and Conclusion 
 
This project is incomplete as we are still left with coding for parallel load register with and without signal and Main Controller, Clock generator and Memory File. This multicycle datapath can breakdown multiple instructions into smaller steps and this will allow faster clock. The instructions are broken into 5 different states and these states are controlled by the finite State Machine. Our design can handle 33 different instructions. Each instruction is categorized in 4 different kind of format these are: The R-Type, J-type, I-Type, and IL-type.  
 
 
 
 
