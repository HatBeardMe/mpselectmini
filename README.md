# mpselectmini

## Cura 2.7 Machine Settings

### Printer Settings
X (width): 135mm

Y (depth): 130mm

Z (height): 120mm

Build plate shape: Rectangular

Origin at center: no

Heated Bed: yes

Gcode flavor: Marlin

### Printhead Settings
X min: 0mm

Y min: 0mm

X max: 0mm

Y max: 0mm

Gantry height: 0 mm

Number of extruders: 1

Material diameter: 1.75mm

Nozzle size: 0.4mm

### Start Gcode
```
G28 ; home all axes
G1 Z0.2 F1200 ; raise nozzle
G92 E0 ; reset extrusion distance
G1 X10 ; move X-carriage 10mm to prep for wipe
G1 Y100 E12 F600 ; purge nozzle & wipe
G92 E0 ; reset extrusion distance from wipe action
```

### End Gcode
```
M104 S0 ; turn off hotend heater
M140 S0 ; turn off bed heater
G91 ; Switch to use Relative Coordinates
G1 E-2 F300 ; retract the filament a bit before lifting the nozzle to release some of the pressure
G1 Z1 ; raise Z 1mm from current position
G1 E-2 F300 ; retract filament even more
G90 ; Switch back to using Absolute Coordinates
G1 X20 ; move X axis close to tower but hopefully far enough to keep the fan from rattling
G1 Y115 ; move bed forward for easier part removal
M84 ; disable motors
G4 S600 ; keep fan running for 600 seconds to cool hotend and allow the fan to be turned off
M107 ; turn off fan
```
