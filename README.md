# Flipflop-using-Blocking-and-Non-blocking-Assignments
## Exp 3 -Write and simulate D, SR, JK, T Flipflops using Blocking and Non blocking Assignments
  ## Aim: 
  To design and simulate D, SR, JK, T Flipflops using Blocking and Non blocking Assignments in Verilog HDL and verify its functionality through a testbench using the Vivado 2023.1 simulation environment.
##  Apparatus Required:
  Vivado 2023.1
Procedure:
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
Close the Simulation Once done, by going to Simulation → "Close Simulation
Input/Output Signal Diagram:
## Input/Output Signal Diagram:
### D FF:
<img width="365" height="270" alt="image" src="https://github.com/user-attachments/assets/1280773a-80fd-406c-b473-41b032fb568e" />

### SR FF:
<img width="370" height="226" alt="image" src="https://github.com/user-attachments/assets/e59a7b61-fd99-43f7-98e3-03818284bffd" />

### JK FF:
<img width="412" height="267" alt="image" src="https://github.com/user-attachments/assets/571f9fca-eb08-4424-bf7c-2c85e131a3f1" />
### T FF:

RTL Code:

TestBench:
### T FF:
<img width="410" height="257" alt="image" src="https://github.com/user-attachments/assets/995f03f8-efca-4801-b1e4-5d0cb720e2ad" />

Output waveform:

Conclusion:
## RTL Code:

### D Flip Flop:
```
```
### D Flip Flop:
```
```
### D Flip Flop:
```
```
### D Flip Flop:
```
```


## TestBench:

### D Flip Flop:
```
```
### D Flip Flop:
```
```
### D Flip Flop:
```
```
### D Flip Flop:
```
```


## Output waveform:

### D FF BLOCK:
<img width="1919" height="1199" alt="Screenshot 2025-09-16 153446" src="https://github.com/user-attachments/assets/523aadc4-1f35-4e81-b2cf-14bdf07aff27" />

### T FF BLOCK:
<img width="1919" height="1199" alt="Screenshot 2025-09-16 213315" src="https://github.com/user-attachments/assets/4d95a340-ee3a-4eb4-b0a7-4ee3366043a4" />

### JK FF BLOCK:
<img width="1917" height="1199" alt="Screenshot 2025-09-16 163127" src="https://github.com/user-attachments/assets/d45c69c5-95dd-4e45-8bec-dc02a1108d32" />

### SR FF BLOCK:
<img width="1917" height="1199" alt="image" src="https://github.com/user-attachments/assets/6c6593ed-9dfa-4800-949d-d7878bd37e65" />

## Conclusion:

In this experiment, JK, SR, D, and T flip-flops were designed and simulated using Verilog HDL.
Each flip-flop functioned correctly by performing set, reset, toggle, and hold operations as expected.
The simulation results confirmed the proper working of flip-flops in sequential circuit design.
This provided practical insight into designing memory elements using Verilog.
