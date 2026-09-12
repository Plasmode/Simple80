# Instruction for Assembling and Installing non-banked CPM3 for Simple80
The CP/M3 distribution files are compressed with arj.exe. Upload cpm3.arj to Simple80 using XMODEM:

*xmodem cpm3.arj /r*

decompress with unarj.com:

*unarj e cpm3*

CP/M3 is now installed on the CF disk.

To install the CPM3 loader, send CPMLDR.HEX in Simple80 monitor and type 'c3' command to install CPM3 loader in track 0 of CF disk. To boot CPM3, type 'b3' command in Simple80 monitor.


** Rebuilding CP/M 3 BIOS
There are two programs associated with CP/M3 BIOS, cbios3 and scb. [ZMAC](http://48k.ca/zmac.html) is the Z80 assembler for assembling cbios3 and scb. The commands are:

*zmac –rel cbios3*

*zmac –rel scb*

The resulting relocatable outputs, cbios3.rel and scb.rel are uploaded to Simple80 via XMODEMl

*xmodem cbios3.rel /r*

*xmodem scb.rel /r*

*link bios3[os]=cbios3,scb* ← create updated BIOS3.SPR

Generate an updated cpm3.sys using gencpm.com

gencpm:

- set to no banked
- N to double allocation vector
- N to hashing for drive A/B/C/D
- Y to overlay data buffer and directory buffer for A/B/C/D
- also share buffers with drive A

** Rebuilding CPMLDR
CPMLDR is a barebone disk operating system specifically for loading CP/M. Like CP/M, it also needs a corresponding BIOS to interface to specific hardware. The BIOS is 'ldrbios'. Here is the process of rebuilding CPMLDR with an updated ldrbios:

assemble ldrbios with zmac,

*zmac –rel ldrbios*

xmodem ldrbios.rel to CP/M environment

*xmodem ldrbios.rel /r*

Then link ldrbios with cpmldr to higher address such as 0x1100 to avoid conflicting with loading CP/M's CCP

*link cpmldr[l1100]=cpmldr,ldrbios*

xmodem the resulting cpmldr.com to PC

*xmodem cpmldr.com /s*

convert it to Intel hex format with offset of 0x1100

*bin2hex /o0x1100 cpmldr.com cpmldr.hex*

Send cpmldr.hex to Simple80 and use monitor command 'c3' to install cpmldr.

