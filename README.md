This repository contains the MATLAB/Simulink implementation for the research work:

Design and Optimization of a Bidirectional Dual Active Bridge (DAB) DC-DC Converter using Dolphin Echolocation Algorithm for Microgrid Applications

The project demonstrates how a bio-inspired Dolphin Echolocation Algorithm (DEA) is used to automatically tune the PI controller gains of a phase-shift modulated DAB converter, resulting in superior transient performance compared to conventional manual tuning techniques.
________________________________________
📁 Repository Contents

This repo contains only the essential working files:

dab.slx        → MATLAB Simulink model of the bidirectional DAB converter  
dolphin2.m    → MATLAB script implementing the Dolphin Echolocation Algorithm (DEA)  
ResearchPaper.pdf → Complete research paper documenting theory & results
________________________________________
🎯 Project Objective

•	Develop a state-space mathematical model of a bidirectional DAB converter suitable for microgrid energy storage interfaces.

•	Implement Phase-Shift Modulation (PSM) based current control.

•	Optimize PI controller gains (Kp, Ki) using DEA to minimize the Integral Absolute Error (IAE).

•	Validate controller performance using MATLAB Simulink simulations for voltage regulation, power flow, and transient response.
________________________________________
⚙️ System Overview

Converter

•	Topology: Dual Active Bridge (DAB) bidirectional isolated DC-DC converter

•	Ports:

  o	High-Voltage side: 1000 V DC link (PV / grid interface)
  
  o	Low-Voltage side: 500 V storage bus (battery or ultracapacitor)
  
•	Transformer turns ratio: 1:2

•	Soft-switching (ZVS) operation achieved via Phase-Shift Modulation

Power Control

•	Buck mode: HV → LV energy flow

•	Boost mode: LV → HV energy flow

•	Power is regulated using phase shift between primary and secondary bridge voltages.
________________________________________
🧠 Control Strategy

•	Inner current control loop

•	PI compensator generates phase shift command

•	Feed-forward compensation for port voltage variations

•	Phase shift ensures zero steady-state error and fast dynamic tracking.
________________________________________
🐬 Dolphin Echolocation Algorithm (DEA)

The script dolphin2.m implements DEA for controller tuning:

DEA Parameters

•	Population size = 10

•	Maximum iterations = 20

•	Search ranges:

  o	Kp ∈ [0, 10]
  
  o	Ki ∈ [0, 5]

•	Fitness function = Integral of Absolute Error (IAE)

Each dolphin represents a candidate PI gain pair. Simulations run inside the optimization loop and the best candidate is selected based on lowest IAE.
________________________________________
✅ Optimized Controller Gains

After 20 DEA iterations, the optimal gains obtained were:

Kp = 5.3558
Ki = 2.8991

These gains achieved:

•	✅ 56.5% faster settling time

•	✅ 98% overshoot reduction

•	✅ 45.8% lower IAE

•	✅ 50% lower ISE

•	✅ Significantly better voltage tracking vs manual tuning

(All results reported in ResearchPaper.pdf)
________________________________________
🚀 How to Run the Project

Step-1: Requirements

•	MATLAB R2021a (or newer)

•	Simulink

•	Simscape Electrical / SimPowerSystems Toolbox
________________________________________
Step-2: Run Optimization

1.	Open MATLAB.
2.	Navigate to this repository folder.
3.	Open Simulink model:
open_system('dab.slx')
4.	Run DEA optimization:
run dolphin2.m
________________________________________
Step-3: What Happens

•	DEA injects (Kp, Ki) candidates into the workspace as Kp_var and Ki_var.

•	dab.slx runs simulations using these gains.

•	Error signal is exported via a To Workspace block as error_signal.

•	IAE is calculated and fed back into DEA.

•	DEA converges to optimal PI gains and prints:

  Optimal Kp = 5.3558
  Optimal Ki = 2.8991
  
•	Final waveforms and responses appear directly in Simulink scopes.
________________________________________
📊 Simulation Outputs

From the Simulink model and paper:

•	Output voltage tracking with low overshoot & fast settling

•	Primary and secondary bridge square-wave voltages with correct phase shift

•	Continuous conduction inductor current waveform

•	Input/output current regulation

•	DEA convergence and controller error signals
________________________________________
📄 Research Paper

Full theoretical derivations, mathematical models, power equations, DEA flowcharts, simulation results, and performance comparisons are available in:
ResearchPaper.pdf
________________________________________
🔮 Future Work

•	Experimental hardware validation using a scaled DAB prototype.

•	Advanced control techniques:

  o	Model Predictive Control (MPC)
  
  o	Sliding Mode Control
  
•	Multi-port microgrid converter extension.

•	FPGA or DSP real-time controller implementation.
________________________________________
🔑 Keywords

Dual Active Bridge • Bidirectional DC-DC Converter • Microgrid • Phase Shift Modulation •
Dolphin Echolocation Algorithm • PI Optimization • MATLAB Simulink • Meta-heuristic Control

