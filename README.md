# Digital-Micro-Library-System--FPGA-Nexys4DDR
An FPGA-based embedded display and audio system built in Verilog, deployed on a Nexys 4DDR board. The system delivers interactive lesson modules with real-time peripheral control - no processor, pure hardware logic. This project presents the design and implementation of a Digital Micro Library on the 
Nexys4 DDR FPGA platform utilizing Verilog HDL. The system employs a finite state machine 
architecture controlled via push-button inputs, allowing users to select among various instructional 
states represented either by descriptive text (e.g., “START”, “LESSON1”) or numerical codes 
(“0”-“4”), which are rendered on the onboard eight-digit seven-segment display. The module 
integrates a mono audio tone generator such that each instructional state produces a distinct, 
audible frequency output through the FPGA’s PMOD header, enabling direct feedback via 
earphones. The system leverages hardware resource mapping, combinational and sequential logic 
for display multiplexing, and safe analog interfacing for auditory output. The design encompasses 
state encoding, segment pattern generation, clock division for human-perceptible tonal output, and 
user interface reliability. Applications for this platform include education, interactive tutorials, 
digital instrumentation, and embedded system demonstrations. The project provides a hardware
efficient, user-friendly instructional module for FPGA-based embedded learning systems. 

# What It Does
- Cycles through lesson content stored in hardware using push-button inputs.
- Drives a 7-segment display with multiplexed output for real-time text rendering.
- Generates audio tone feedback at specific frequencies using PWM.
- Entirely controlled by a Finite State Machine (FSM) written in Verilog.

# Technical Highlights
- Board:	Nexys 4DDR (Artix-7 FPGA)
- Language:	Verilog HDL
- Tool:	Xilinx Vivado
- Display:	7-segment multiplexing (8 digits)
- Audio:	PWM-based frequency generation
- Control:	FSM with push-button debouncing

# Key Modules
- FSM Controller (`fsm_controller.v`)
States: IDLE → LOAD → DISPLAY → WAIT → NEXT;
Handles state transitions on button press.
Outputs module index to display and audio drivers.

- 7-Segment Multiplexer (`seg7_mux.v`)
Cycles through 8 digit positions at ~1kHz refresh.
Converts BCD/hex values to segment encoding.
Handles common-anode display logic.

- Audio Tone Generator (`tone_gen.v`)
Generates square waves at target frequencies.
Frequency = `CLK_FREQ / (2 × DIVISOR)`
Different tones mapped to different lesson states,

# Validation
- Simulated all modules using Vivado's built-in simulator before synthesis.
- Verified waveforms for FSM state transitions, display timing, and audio frequency accuracy.
- Successfully deployed and tested on physical Nexys 4DDR hardware.

# Tools Used
- Xilinx Vivado 2023.x
- Nexys 4DDR (Digilent)
- Verilog HDL
