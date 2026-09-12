# Getting Started with Simple80
### Introduction
This is a guide for setting up Simple80 after assembly is completed and the board is fully populated. The assembly instruction for Simple80 is here.

### Program the EPROM
Simple80's EPROM socket can accept both 28-pin EPROM device such as 27C512 or 32-pin EPROM device such as AT49F040. Two EPROM programming files are supplied in the Software section: Simple80_Monitor and SCMonitor_for_Simple80. Only one of the file should be selected depending on user application. To run CP/M2.2, Simple80_Monitor needs to be programmed in the EPROM. The remaining document assumes Simple80_Monitor is programmed in the EPROM.

### Power up Simple80
Simple80 requires 5V power at a minimum of 250mA. The power comes in through a 2.1mm X 5.5mm power plug with center lead as 5V and barrel as ground. A CP2102 6-pin USB-to-serial adapter can be plugged directly in P2. A serial emulator such as TeraTerm is needed to interface to Simple80. The serial port setting are 115200 N-8-1.

Insert a CF disk in the CF adapter prior to powering up.

Apply 5V power, the power consumption should be around 60-80mA and the terminal should display this log on message:

*>Simple80 Monitor v0.6 7/2/19*

*Type 'h' to display help menu.*

Type 't' follow by carriage return to do memory test. It should print 'OK' every second or so. type carriage return to stop memory test

### Prepare CF disk for CP/M2.2
Format the CF disk by type 'x' follow by drive letters 'A', 'B', 'C', 'D' in **upper case**. Please note this will erase whatever files that was in the CF disk.

Send [cpm22all.hex](https://github.com/Plasmode/Simple80/blob/main/Rev0/software/simple80_rev0_cpm22.zip) to Simple80. In TeraTerm 'send' means File → Send file… → pick the file in drop down menu.

Once send is completed, type 'c2' followed by carriage return to save cpm22all in CF disk.

Once cpm22all is saved in CF disk, it can be invoked by type 'b2' followed by carriage return. The CP/M sign on message will display
```
Copyright 1979 © by Digital Research
CP/M 2.2 for Simple80 Rev 0.2 IOByte & JmpTbl 7/2/19

a>
```
Once in CP/M environment, press reset button to return to Simple80 monitor.

In Simple80 monitor, send xmodem.hex.

Once send is completed, type 'b2' to enter CP/M2.2. At CP/M command prompt, type 'save 17 xmodem.com' to save RAM image as xmodem.com. This will create the first file on the new CF disk.

xmodem is used to transfer all subsequent files to the new CF disk. The command is “xmodem filename /r”. Start xmodem transfer in TeraTerm: File→Transfer→XMODEM→Send and pick the file to send.

File file to transfer via xmodem is unarj.com ← please note this file needs to be unzipped first into unarj.com

Second file to transfer is cpm22dri.arj ← please note this file needs to be unzipped first into cpm22dri.arj

cpm22dri.arj is compressed CP/M22 distribution. To uncompress it, type 'unarj e cpm22dri'. Once the decompression is done, CP/M2.2 is ready to run!

builderpages/plasmo/simple80/getting_started_gu
