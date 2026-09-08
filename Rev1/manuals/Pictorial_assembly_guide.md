# Pictorial Assembly Guide for Simple80 Rev1.2
Blank board, component side
![blanktop](Simple80_rev1_2_blank_top.jpg)

Blank board, solder side
![blanksolder](Simple80_rev1_2_blank_solder.jpg)

Resistors are all 4.7K except R17
![resistor](Simple80_rev1_2_resistor_top.jpg)

Capacitors are 0.1uF except C4 (10uF tantalum) and C13 (100pF ceramic)
![capacitor](Simple80_rev1_2_capacitor_top.jpg)

Install IC sockets. The spacing between U1 and U4 is tight, so slide socket for U4 away from U1 to create more space for jumper blocks between U1 and U4.
![socket](Simple80_rev1_2_socket_top.jpg)

Finish up except CF adapter
![all](Simple80_rev1_2_all_top.jpg)

Board will boot and sign on without CF adapter. However, it will hang waiting for CF disk ready.

Inserting a 4.7K resistor between D7 and GND as indicated with red arrows will enable boot to complete.
![fully](Simple80_rev1_2_populated_top.jpg)
