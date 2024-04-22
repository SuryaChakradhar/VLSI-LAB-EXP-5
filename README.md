# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS
## AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.
## APPARATUS REQUIRED:
vivado 2023.2

## PROCEDURE
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.
**LOGIC DIAGRAM**

SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)


JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)


D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)


COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

## VERILOG CODE
SR FLIPFLOP:
module srff(clk,j,k,rst,q );

input s,r,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({s,r})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=1'bx;

endcase

end end

endmodule

## OUTPUT WAVEFORM:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161815325/21cf84a3-6564-4f68-914c-edd56b49910e)
## JK FLIPFLOP:
module jkff(clk,j,k,rst,q );
input j,k,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({j,k})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1; 2'b11:q=~q;

endcase

end

end

endmodule

## OUTPUT WAVEFORM:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161815325/f5b7ccf8-2d02-4439-8d0e-5cc42331eeef)
## T FLIPFLOP:
module tff(clk,reset,t,q);

input clk,reset,t;

output reg q;

always @(posedge clk)

begin

if(reset==1)

q=0;

else

begin

if(t==0)

q=q;

else

q=~q;

end

end

endmodule

## OUTPUT WAVEFORM:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161815325/f2a7e302-ae65-4f61-937f-4dc06ddf6474)
## D FLIPFLOP:
module dff(clk,d,rst,q );

input d,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

q=d;

end

endmodule

## OUTPUT WAVEFORM:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161815325/e62cba4c-5efa-4924-a6b1-378dd552a3b7)
UPDOWN COUNTER:
module updown(clk,rst,up_down,count);

input clk,rst,up_down;

output reg[3:0]count;

always@(posedge clk)

begin

if(rst==1)

count <= 4'b0000;

else if (up_down == 1'b1)

count <= count + 1'b1;

else

count <= count-1'b1;

end

endmodule

OUTPUT WAVEFORM:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161815325/715f99cd-1669-48db-8390-18e293b012b4)

MOD 10 COUNTER:
module mod(clk,rst,count);

input clk,rst;

output reg[3:0]count;

always @(posedge clk)

begin

if(rst==1 | count==4'b1001)

count <= 4'b0000;

else

count <= count +1;

end

endmodule

OUTPUT WAVEFORM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161815325/f299851a-bf50-489c-b9a8-d11d4fdb5335)
RIPPLE COUNTER:
module ripplecounter(clk,rst,q);

input clk,rst;

output [3:0]q;

tff tff1(q[0],clk,rst);

tff tff2(q[1],q[0],rst);

tff tff3(q[2],q[1],rst);

tff tff4(q[3],q[2],rst);

endmodule

module tff(q,clk,rst);

input clk,rst;

output q;

wire d;

dff df1(q,d,clk,rst);

not n1(d,q);

endmodule

module dff(q,d,clk,rst);

input d,clk,rst; output q;

reg q;

always@(posedge clk or posedge rst)

begin

if(rst)

q=1'b10;

else

q=d;

end

endmodule
OUTPUT WAVEFORM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/161815325/2417cecd-abb4-4249-bf47-43f2b359bd62)
## RESULT:
Thus,the simulation and synthesis of SR,JK,T,D flipflops,counters by using vivado has been successfully excecuted and verified.
