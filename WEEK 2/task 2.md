📁 File Examined:
~~~bash
caravel.v
~~~
🧠 Objective:
Understand the hierarchy and functionality of the SoC's top-level module (vsdcaravel), and extract architectural insights.

1. 🔧 Four Major Submodules Instantiated in caravel.v:
padframe — handles all I/O interfacing with physical pads

caravel_core — the heart of the SoC, containing logic for clock, reset, user project, flash, etc.

copyright_block, caravel_logo, caravel_motto, open_source, user_id_textblock — these are text/logo macros for identification (important during fabrication)

2. 🔄 Signals Crossing the "Management Protect" Boundary:
These signals connect user design logic with the management SoC (isolated for security):

mprj_io_in, mprj_io_out, mprj_io_oeb

la_data_in, la_data_out, la_oenb, la_iena

user_irq_core, user_clock2, wb_* signals for wishbone bus

3. ⏱️ Clock and Reset Synchronization:
Clock and reset signals are managed hierarchically:

Start at padframe → generate clock_core, resetb_core_h

Go to caravel_core → passed to caravel_clocking module

Then generate caravel_clk and caravel_rstn for use across modules
