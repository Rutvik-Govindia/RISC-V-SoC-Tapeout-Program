Week 3 Task: Post-Synthesis GLS & STA Fundamentals
This repository/document outlines the objectives, tools, and deliverables for Week 3, focusing on the essential steps following logic synthesis: Gate-Level Simulation (GLS) and Static Timing Analysis (STA) fundamentals.

1. Overall Objective
The primary objective is to validate synthesized circuit functionality and analyze its timing performance.

Understand and perform Gate-Level Simulation (GLS) after synthesis.

Validate the circuit's functionality using the synthesized netlist.

Get introduced to Static Timing Analysis (STA) concepts.

Perform practical timing experiments using OpenSTA.

2. Part 1: Gate-Level Simulation (GLS)
(Based on standard VLSI workflow, though not explicitly detailed in the provided PDF, this typically involves:)

Goal: Verify that the synthesized netlist (including gate delays) still behaves functionally the same as the Register Transfer Level (RTL) code.

Tools: Standard simulation tools (e.g., Icarus Verilog, VCS, QuestaSim).

Process: Run the testbench against the synthesized netlist, back-annotated with Standard Delay Format (SDF) information.

3. Part 2: Fundamentals of Static Timing Analysis (STA)
The core focus is on understanding the theoretical foundations of STA.

Learning Resource
If STA is a new topic, a foundational course is recommended:

Course: STA Fundamentals - Udemy (Link and coupon code provided in the original task document).

Key Concepts to Summarize (Deliverable Focus)
The final deliverable for Part 2 is a one-page summary or key notes focusing on the following areas:

Setup Check: Ensures data at the sequential element's input is stable before the active clock edge arrives. This check is crucial to prevent "too slow" data paths and ensure data is captured correctly by the next clock.

Hold Check: Ensures data at the sequential element's input remains stable after the active clock edge. This check prevents "too fast" data paths that could violate the data integrity during the clock transition.

Slack: The difference between the required time and the arrival time of a signal.


Slack=Required Time−Arrival Time
Positive Slack: The timing requirement is met (Pass).

Negative Slack: A timing violation has occurred (Fail). This value indicates how much the timing needs to be improved.

Clock Definitions: Involves the proper specification of the clock period, waveform, source, and clock uncertainty (jitter and skew) for accurate timing analysis.

Path-Based Analysis: STA analyzes every possible timing path (Data, Input, Output, Pin-to-Pin) in the design to ensure all meet the defined constraints.