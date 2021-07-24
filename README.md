Let's make stuff move.

This is custom 3D printer firmware with full auto level function.

Here is how to first time setup your printer with this firmware through RS-232

Z-Offset Instructions:
1. Home 3D printer
2. M851 Z0 - Reset Z0Offset
3. M500 - Store setting to eeprom
4. M501 - Set active parameters
5. M503 - Display Active Parameters
6. G28 Z - Home Z Axis
7. G1 F60 Z0 - Move nozzle to true 0 offset
8. M211 S0 - Switch off soft endstops
9. Move nozzle towards bed slowly until the paper can barely move
10. Take note of the Z on the printer display (take that number and add the measurment of the calibration sheet or device used)
11. M851 Z X.XX (X.XX being your z offset achieved)
12. M211 S1 - Enable Soft Endstops
13. M500 - Save settings to Eeprom
14. M501 - Set Active Parameters
15. M503 - display current settings

current setting is : M851 Z-0.60

M420 S1 ; enable bed leveling On

other command 
M106 ; enable fan 100%
M501 ; Read all parameters from EEPROM 
M420 S1 ; enable bed leveling  ; S0 for disable
M420 V ; print leveling matrix
G29 S ; Mesh and store value to eeprom

M48 ; repeatability test to test probe accuracy

M420 S1 ; enable bed leveling On

M301 [C<value>] [D<value>] [E<index>] [I<value>] [L<value>] [P<value>] ;Set the values that control the PID loop for a hotend.

official UBL bed level
M502          ; Reset settings to configuration defaults...
M500          ; ...and Save to EEPROM. Use this on a new install.
M501          ; Read back in the saved EEPROM.

M190 S65      ; Not required, but having the printer at temperature helps accuracy
M104 S210     ; Not required, but having the printer at temperature helps accuracy

G28           ; Home XYZ.
G29 P1        ; Do automated probing of the bed.
G29 P2 B T    ; Manual probing of locations. USUALLY NOT NEEDED!
G29 P3 T      ; Repeat until all mesh points are filled in.

G29 T         ; View the Z compensation values.
G29 S1        ; Save UBL mesh points to EEPROM.
G29 F 10.0    ; Set Fade Height for correction at 10.0 mm.
G29 A         ; Activate the UBL System.
M500          ; Save current setup. WARNING - UBL will be active at power up, before any G28.


  For I3 mega your can use this code to begining your G-code file in CURA
  
G21 ;metric values
M420 S1 ; enable bed leveling On
G90 ;absolute positioning
M82 ;set extruder to absolute mode
M107 ;start with the fan off
G28 X0 Y0 ;move X/Y to min endstops
G28 Z0 ;move Z to min endstops
G1 Z15.0 F{speed_travel} ;move the platform down 15mm
G92 E0 ;zero the extruded length
G1 F200 E3 ;extrude 3mm of feed stock
G92 E0 ;zero the extruded length again
G1 F{speed_travel}
G0 Y20 F{speed_travel}
M117 Printing...
G5
  

<!---
BirdJirad/BirdJirad is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
