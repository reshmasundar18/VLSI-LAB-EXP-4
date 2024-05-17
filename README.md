### SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

##  AIM: 
        To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

## APPARATUS REQUIRED:
                       Xilinx 14.7 Spartan6 FPGA

##  PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.

STEP:2  Select the device family, device, package and speed.  

STEP:3  Select new source in the New Project and select Verilog Module as the Source type.

STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.

STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax. 

STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.  

STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.

STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is 
        obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.

STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.

STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

# SR FLIPFLOP:

# LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

# PROGRAM:
```
srff(s,r,q,clk,reset);
input s,r,clk,reset;
output reg q;
always @(posedge clk)
begin
if(reset==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bx;
endcase
end
end
endmodule
```

# OUTPUT:
![Screenshot 2024-05-17 113506](https://github.com/reshmasundar18/VLSI-LAB-EXP-4/assets/166894571/f9038acb-9680-4197-bd4d-828473004032)


# JK FLIPFLOP:

# LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

# PROGRAM:
`
module jkff(j,k,q,clk,reset);
input j,k,clk,reset;
output reg q;
always @(posedge clk)
begin
if(reset==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
`

# OUTPUT:
![Screenshot 2024-05-17 113709](https://github.com/reshmasundar18/VLSI-LAB-EXP-4/assets/166894571/dfaf261a-af42-459e-a8e1-6a2551db264b)


# T FLIPFLOP:

# LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

# PROGRAM:
`
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
`

# OUTPUT:
![Screenshot 2024-05-17 113828](https://github.com/reshmasundar18/VLSI-LAB-EXP-4/assets/166894571/6aeb568a-2ebf-4660-a5b6-5724f8785f04)


# D FLIPFLOP:

# LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

# PROGRAM:
`
module dff(clk,reset,d,q);
input clk,d,reset;
output reg q;
always@(posedge clk)
begin
if(reset)
q<=1'b0;
else
q<=d;
end
endmodule
`

# OUTPUT:
![Screenshot 2024-05-17 113957](https://github.com/reshmasundar18/VLSI-LAB-EXP-4/assets/166894571/4a2d55f5-b14f-4bc4-9d6c-76096c92271a)

# MOD 10 COUNTER:

# LOGIC DIAGRAM:
![Screenshot 2024-05-17 114108](https://github.com/reshmasundar18/VLSI-LAB-EXP-4/assets/166894571/7c4a843d-5a1e-4e3d-80c1-628402860495)

# PROGRAM:
`
module mod_10(clk,rst,out); 
input clk,rst;
output reg[3:0]out; 
always@(posedge clk)
begin if(rst==1|out==9) 
out=4'b0;
else
out=out+1;
end
endmodule
`

# OUTPUT:
![Screenshot 2024-05-17 115226](https://github.com/reshmasundar18/VLSI-LAB-EXP-4/assets/166894571/0c594e66-b8c9-4592-88b5-6e37e5766cd6)

# UP-DOWN-COUNTER:

# LOGIC DIAGRAM:
![Screenshot 2024-05-17 115340](https://github.com/reshmasundar18/VLSI-LAB-EXP-4/assets/166894571/a48b4417-75a7-4257-994d-544ac3aa1e7d)

# PROGRAM:
`
module updowncounter(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always @(posedge clk)
begin
if(rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
`

# OUTPUT:
![Screenshot 2024-05-17 120242](https://github.com/reshmasundar18/VLSI-LAB-EXP-4/assets/166894571/917b065a-4151-4f2c-93bb-df04d1a157d7)

# RIPPLE CARRY COUNTER:

# LOGIC DIAGRAM:
![Screenshot 2024-05-17 122350](https://github.com/reshmasundar18/VLSI-LAB-EXP-4/assets/166894571/94a6a4cc-5e4f-48fb-ae40-35e75639c2de)

# PROGRAM:
`
module ripple_carry_counter(q, clk, reset);
output [3:0] q;
input clk, reset;
T_FF tff0(q[0], clk, reset);
T_FF tff1(q[1], q[0], reset);
T_FF tff2(q[2], q[1], reset);
T_FF tff3(q[3], q[2], reset);
endmodule

module T_FF(q, clk, reset);
output q;
input clk, reset;
wire d;
D_FF dff0(q, d, clk, reset);
not n1(d, q); 
endmodule

module D_FF(q, d, clk, reset);
output q;
input d, clk, reset;
reg q;
always @(posedge reset or negedge clk)
if (reset)
q = 1'b0;
else
q = d;
endmodule
`

# OUTPUT:
![Screenshot 2024-05-17 122840](https://github.com/reshmasundar18/VLSI-LAB-EXP-4/assets/166894571/99f56f4e-8a5a-4e54-a85a-247bee819a15)


## RESULT:
           Thus, the simulation of sequential logic circuits are implementented and simulated successfully using Xilinx ISE.
          


