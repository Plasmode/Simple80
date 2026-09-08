# Simple80 Rev1 
This is rev 1 of Simple80 with the compact flash interface integrated on board. The motherboard has all necessary hardware to run CP/M. It is no longer zero glue logic like the Simple80, but is software compatible with the original Simple80.


![rev1.1](Simple80_rev1_1_topview.jpg)
### Features
- Z80 at 7.3728MHz
- Dual serial port SIO
- 128K RAM
- 64K PROM or EEPROM
- CP/M 2.2 and CP/M 3
- Three classic RC2014 expansion connectors
- 100mm X 100mm pc board
- Compact flash interface
- 
![rev1.1](Simple80_rev1_1_topview_slanted.jpg)
### Theory of operation
This is a classical microprocessor design with CPU, I/O, RAM and ROM but with one unusual feature: To keep the part count at minimal, both RAM and ROM are chip selected when Z80 is accessing the memory space. To boot up, only ROM's output enable is asserted at reset; In this mode RAM is selected but write-only; the first routine in ROM firmware is to read its own code and write it back into the same location for the entire ROM program; this unusual operation does not affect the read-only ROM, but duplicate the ROM program into the write-only RAM. When the duplication operation is completed, the firmware enable the RAM's output enable and disable ROM's output enable so now the program is running in RAM.

### Design Information
- Rev 1.2 [Schematic](simple80_r1_2_scm.pdf) of Simple80 Motherboard
- Rev 1.2 PC board [Gerber files](simple80_r1_2_gerber.zip) of Simple80 motherboard. The pc boards were made by JLCPCB
- Bill of Materials for Simple80

### Software
Simple80 rev1 is software compatible with Simple80. Please see [Software](../Rev0/software) section of Simple80 rev0.

### Manuals
[Pictorial assembly guide](manuals/Pictorial_assembly_guide.md) for Simple80, rev1.2

