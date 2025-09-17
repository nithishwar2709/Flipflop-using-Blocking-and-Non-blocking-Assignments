# Flipflop-using-Blocking-and-Non-blocking-Assignments
## Exp 3 -Write and simulate D, SR, JK, T Flipflops using Blocking and Non blocking Assignments
## Aim: 
  **To design and simulate D, SR, JK, T Flipflops using Blocking and Non blocking Assignments in Verilog HDL and verify its functionality through a testbench using the Vivado 2023.1 simulation environment.**
## Apparatus Required:
  **Vivado 2023.1**
## Procedure:
Launch Vivado Open Vivado 2023.1 by double-clicking the Vivado icon or searching for it in the Start menu. 
Create a New Project Click on "Create Project" from the Vivado Quick Start window. In the New Project Wizard: Project Name: Enter a name for the project (e.g., Mux4_to_1). 
Project Location: Select the folder where the project will be saved. Click Next. 
Project Type: Select RTL Project, then click Next. Add Sources: Click on "Add Files" to add the Verilog files (e.g., mux4_to_1_gate.v, mux4_to_1_dataflow.v, etc.). 
Make sure to check the box "Copy sources into project" to avoid any external file dependencies. 
Click Next.
Add Constraints: Skip this step by clicking Next (since no constraints are needed for simulation). 
Default Part Selection: You can choose a part based on the FPGA board you are using (if any). 
If no board is used, you can choose any part, for example, xc7a35ticsg324-1L (Artix-7). 
Click Next, then Finish.
Add Verilog Source Files In the "Sources" window, right-click on "Design Sources" and select Add Sources if you didn't add all files earlier.
Add the Verilog files and the testbench. 
Check Syntax Expand the "Flow Navigator" on the left side of the Vivado interface. 
Simulate the Design In the Flow Navigator, under "Simulation", click on "Run Simulation" → "Run Behavioral Simulation". 
Vivado will open the Simulations Window, and the waveform window will show the signals defined in the testbench. 
View and Analyze Simulation Results Adjust Simulation Time To run a longer simulation or adjust timing, go to the Simulation Settings by clicking "Simulation" → "Simulation Settings". Under "Simulation", modify the Run Time (e.g., set to 1000ns).
Generate Simulation Report Once the simulation is complete, you can generate a simulation report by right-clicking on the simulation results window and selecting "Export Simulation Results".
Save the report for reference in your lab records. Save and Document Results Save your project by clicking File → Save Project.
Take screenshots of the waveform window and include them in your lab report to document your results. 
You can include the timing diagram from the simulation window showing the correct functionality of the Seven Segment across different select inputs and data inputs. 
Close the Simulation Once done, by going to Simulation → "Close Simulation.
## Input/Output Signal Diagram:
### D FF:
<img width="365" height="270" alt="image" src="https://github.com/user-attachments/assets/1280773a-80fd-406c-b473-41b032fb568e" />

### SR FF:
<img width="370" height="226" alt="image" src="https://github.com/user-attachments/assets/e59a7b61-fd99-43f7-98e3-03818284bffd" />

### JK FF:
<img width="412" height="267" alt="image" src="https://github.com/user-attachments/assets/571f9fca-eb08-4424-bf7c-2c85e131a3f1" />

### T FF:
<img width="410" height="257" alt="image" src="https://github.com/user-attachments/assets/995f03f8-efca-4801-b1e4-5d0cb720e2ad" />

## RTL Code:

### D Flip Flop (BLOCK):
```
module dff_block(clk,rst,d,dout);
    input clk,rst,d;
    output reg dout;
    always@ (posedge clk)
    begin
        if(rst)
            dout = 1'b0;
        else
            dout = d;
     end
endmodule

```
### T Flip Flop (BLOCK):
```
module tff_block(clk,rst,Tout,T);
    input clk,rst,T;
    output reg Tout;
    always@ (posedge clk)
     begin
     if(rst)
        Tout = 1'b0;
     else if(T)
        Tout = ~Tout;
     else
        Tout = Tout;
     end
endmodule

```
### JK Flip Flop (BLOCK):
```
module jkff_block(clk,rst,J,K,Q);
    input clk,rst,J,K;
    output reg Q;
    always@(posedge clk)
      begin
        case({J,K})
            2'b00 : Q = Q;
            2'b01 : Q = 0;
            2'b10 : Q = 1;
            2'b11 : Q = ~Q;
            default : Q = Q;
         endcase
     end
endmodule

```
### SR Flip Flop (BLOCK):
```
module srff_block(clk,S,R,Q);
    input clk,S,R;
    output reg Q;
    
    always @(posedge clk) 
        begin
            case ({S,R})
                2'b00: Q = Q;      
                2'b01: Q = 0;      
                2'b10: Q = 1;      
                2'b11: Q = 1'bx;   
                default: Q = Q;
            endcase
        end
endmodule

```
### D Flip Flop (NON BLOCK):
```
module dff_non_block(clk,rst,d,dout);
    input clk,rst,d;
    output reg dout;
    always@ (posedge clk)
    begin
        if(rst)
            dout <= 1'b0;
        else
            dout <= d;
     end
endmodule
```
### T Flip Flop (NON BLOCK):
```
module tff_non_block(clk,rst,T,Tout);
    input clk,rst,T;
    output reg Tout;
    
    always@(posedge clk) 
      begin
         if(rst)
            Tout <= 1'b0;
         else if(T)
            Tout <= ~Tout;
         else
            Tout <= Tout;
   end
endmodule
```
### JK Flip Flop (NON BLOCK):
```
module jkff_non_block(clk,rst,J,K,Q);
    input clk,rst,J,K;
    output reg Q;
    always@(posedge clk)
      begin
        case({J,K})
            2'b00 : Q <= Q;
            2'b01 : Q <= 0;
            2'b10 : Q <= 1;
            2'b11 : Q <= ~Q;
            default : Q <= Q;
         endcase
     end
endmodule
```

### SR Flip Flop (NON BLOCK):
```
module srff_non_block(clk,S,R,Q);
    input clk,S,R;
    output reg Q;
    
    always @(posedge clk) 
        begin
            case ({S,R})
                2'b00: Q <= Q;      
                2'b01: Q <= 0;      
                2'b10: Q <= 1;      
                2'b11: Q <= 1'bx;   
                default: Q <= Q;
            endcase
        end
endmodule
```

## TestBench:
### D Flip Flop:
```
module dff_block_tb;
    reg clk_t,rst_t,d_t;
    wire dout_t;
    dff_block dut(.clk(clk_t),.rst(rst_t),.d(d_t),.dout(dout_t));
    initial
      begin
        clk_t = 1'b0;
        rst_t = 1'b1;
     #20
        rst_t = 1'b0;
        d_t   = 1'b0;
     #20
        d_t = 1'b1;
     end
     always 
        #10 clk_t = ~clk_t;
endmodule

```
### T Flip Flop:
```
module tff_block_tb;
    reg clk_t,rst_t,T_t;
    wire Tout_t;
    
    tff_block dut(.clk(clk_t),.rst(rst_t),.T(T_t),.Tout(Tout_t));
    
    initial
     begin
        clk_t = 1'b0;
        rst_t = 1'b1;
     #20
        rst_t = 1'b0;
        T_t = 1'b0;
     #20
        T_t = 1'b1;
     end
     
     always 
        #10 clk_t = ~clk_t;
endmodule

```
### JK Flip Flop:
```
module jkff_block_tb;
    reg clk_t,rst_t,J_t,K_t;
    wire Q_t;
    
    jkff_block dut(.clk(clk_t),.rst(rst_t),.J(J_t),.K(K_t),.Q(Q_t));
    
    initial
      begin
        clk_t = 1'b0;
        rst_t = 1'b1;
      #20
        rst_t = 1'b0;
        J_t = 1'b0;
        K_t = 1'b0;
      #20
        J_t = 1'b0;
        K_t = 1'b1;
      #20
        J_t = 1'b1;
        K_t = 1'b0;
      #20
        J_t = 1'b1;
        K_t = 1'b1;
     end
     
     always 
        #10 clk_t = ~clk_t;  
endmodule

```
### ST Flip Flop:
```
module srff_block_tb;
  reg clk, S, R;
  wire Q;
  srff_block dut(.clk(clk),.S(S),.R(R),.Q(Q));
  initial begin
   clk = 0;
  forever #10 clk = ~clk; 
  end
  initial begin
    S = 0; R = 0;
    #100 S = 1; R = 0;   
    #100 S = 0; R = 0;   
    #100 S = 0; R = 1;   
    #100 S = 1; R = 1;  
    #100 S = 0; R = 0;
 end
endmodule
```
### D Flip Flop (NON BLOCK):
```
module dff_non_block_tb;
    reg clk_t,rst_t,d_t;
    wire dout_t;
    
    dff_non_block dut(.clk(clk_t),.rst(rst_t),.d(d_t),.dout(dout_t));
    
    initial
      begin
        clk_t = 1'b0;
        rst_t = 1'b1;
     #20
        rst_t = 1'b0;
        d_t   = 1'b0;
     #20
        d_t = 1'b1;
     end
     
     always 
        #10 clk_t = ~clk_t;
endmodule
```
### T Flip Flop (NON BLOCK):
```
module tff_non_block_tb;
    reg clk_t,rst_t,T_t;
    wire Tout_t;
    
    tff_non_block dut(.clk(clk_t),.rst(rst_t),.T(T_t),.Tout(Tout_t));
    
    initial
     begin
        clk_t = 1'b0;
        rst_t = 1'b1;
     #20
        rst_t = 1'b0;
        T_t = 1'b0;
     #20
        T_t = 1'b1;
     end
     
     always 
        #10 clk_t = ~clk_t;
endmodule
```
### JK Flip Flop (NON BLOCK):
```
module jkff_non_block_tb;
    reg clk_t,rst_t,J_t,K_t;
    wire Q_t;
    
    jkff_non_block dut(.clk(clk_t),.rst(rst_t),.J(J_t),.K(K_t),.Q(Q_t));
    
    initial
      begin
        clk_t = 1'b0;
        rst_t = 1'b1;
      #20
        rst_t = 1'b0;
        J_t = 1'b0;
        K_t = 1'b0;
      #20
        J_t = 1'b0;
        K_t = 1'b1;
      #20
        J_t = 1'b1;
        K_t = 1'b0;
      #20
        J_t = 1'b1;
        K_t = 1'b1;
     end
     
     always 
        #10 clk_t = ~clk_t;  
endmodule
```

### SR Flip Flop (NON BLOCK):
```
module srff_non_block_tb;
  reg clk, S, R;
  wire Q;
  srff_non_block dut(.clk(clk),.S(S),.R(R),.Q(Q));
  initial begin
   clk = 0;
  forever #10 clk = ~clk; 
  end
  initial begin
    S = 0; R = 0;
    #100 S = 1; R = 0;   
    #100 S = 0; R = 0;   
    #100 S = 0; R = 1;   
    #100 S = 1; R = 1;  
    #100 S = 0; R = 0;
 end
endmodule
```
## Output waveform:

### D Flip Flop BLOCK:
<img width="1919" height="1199" alt="Screenshot 2025-09-16 153446" src="https://github.com/user-attachments/assets/523aadc4-1f35-4e81-b2cf-14bdf07aff27" />

### T Flip Flop BLOCK:
<img width="1919" height="1199" alt="Screenshot 2025-09-16 213315" src="https://github.com/user-attachments/assets/4d95a340-ee3a-4eb4-b0a7-4ee3366043a4" />

### JK Flip Flop BLOCK:
<img width="1917" height="1199" alt="Screenshot 2025-09-16 163127" src="https://github.com/user-attachments/assets/d45c69c5-95dd-4e45-8bec-dc02a1108d32" />

### SR Flip Flop BLOCK:
<img width="1917" height="1199" alt="image" src="https://github.com/user-attachments/assets/6c6593ed-9dfa-4800-949d-d7878bd37e65" />

### D Flip Flop NON BLOCK:
<img width="1919" height="1199" alt="Screenshot 2025-09-16 154915" src="https://github.com/user-attachments/assets/08a70aac-7d34-4939-abfc-c4810bcd2750" />

### T Flip Flop NON BLOCK:
<img width="1919" height="1199" alt="Screenshot 2025-09-17 131336" src="https://github.com/user-attachments/assets/047e7acb-a91a-42b4-b251-fc07a91e72be" />

### JK Flip Flop NON BLOCK:
<img width="1919" height="1199" alt="Screenshot 2025-09-17 132015" src="https://github.com/user-attachments/assets/a2e46665-c220-402d-ad7f-44bac2ed3c1f" />

### SR Flip Flop NON BLOCK:
<img width="1919" height="1199" alt="Screenshot 2025-09-17 133515" src="https://github.com/user-attachments/assets/10c510c3-ffb3-4bdd-bf79-1d5de6bda616" />



## Conclusion:

**In this experiment, JK, SR, D, and T flip-flops were designed and simulated using Verilog HDL.
Each flip-flop functioned correctly by performing set, reset, toggle, and hold operations as expected.
The simulation results confirmed the proper working of flip-flops in sequential circuit design.
This provided practical insight into designing memory elements using Verilog.**
