# EXP 12: 4-BIT-RIPPLE-COUNTER
# DATE: 12th DEC 2024
**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**

/* write all the steps invloved */
~~~
    1. Type the program in Quartus software.
  
  2. Compile and run the program.
  
  3. Generate the RTL schematic and save the logic diagram.
  
  4. Create nodes for inputs and outputs to generate the timing diagram.
  
  5. For different input combinations generate the timing diagram
~~~
**PROGRAM**

/* Program for 4 Bit Ripple Counter and verify its truth table in quartus using Verilog programming.

 Developed by: JAYANI K
 
 RegisterNumber: 24005008
*/

~~~
module BRC (

input clk, // Clock input

input reset, // Reset input (active high)

output [3:0] q // 4-bit output

);

// Internal signals for flip-flops

reg [3:0] q_int;

// Assign internal register to output

assign q = q_int;

always @(posedge clk or posedge reset) begin

if (reset)

q_int[0] <= 1'b0; // Reset the first bit to 0

else

q_int[0] <= ~q_int[0]; // Toggle the first bit on clock edge

end

// Generate the other flip-flops based on the output of the previous one

genvar i;

generate

for (i = 1; i < 4; i = i + 1) begin : ripple

always @(posedge q_int[i-1] or posedge reset) begin

if (reset)

q_int[i] <= 1'b0; // Reset the bit to 0

else

q_int[i] <= ~q_int[i]; // Toggle the bit on clock edge of previous stage

end

end

endgenerate

endmodule
~~~
**RTL LOGIC FOR 4 Bit Ripple Counter**

![396565728-3b2c6aae-f987-467b-b976-77320470f4bf](https://github.com/user-attachments/assets/d462fa16-e826-4021-87bd-a3cd123da8cf)


**TIMING DIGRAMS FOR 4 Bit Ripple Counter**

![396565813-8806c89f-4343-46cc-8009-0ec20c05dec7](https://github.com/user-attachments/assets/2ff8f59c-e915-43b3-a76d-7cbda8779876)


**RESULTS**
The given Program for 4 Bit Ripple Counter and verify its truth table in quartus using Verilog programming.

