![GitHub Logo](https://github.com/gnea/gnea-Media/blob/master/Grbl%20Logo/Grbl%20Logo%20250px.png?raw=true)

***
Fork of https://github.com/gnea/grbl/ (damn good Arduino CNC shield controller, accepts g-code)
***
This fork is meant to be used with cheap clone components - an Arduino-compatible board with a CH340, and a chinese clone of CNC Shield 3.0
That hardware works out of the box with grbl/grbl 0.8, but 0.9 introduced some changes:
115200 baud, swapped Z-limit+(D12) and sspnEn(D11)


So, this fork changes:
Serial baud rate changed from 115200 to 57600 (115200being reportedly problematic with CH340 or even ATmega328 - see https://github.com/grbl/grbl/issues/837, https://github.com/grbl/grbl/issues/598#issuecomment-74577116) Supposedly 2000000 works great, too, but most UIs don't support it.

More changes to follow, not necessarily in the same vein


***
Misc:

Settings to remember:
* * $RST=* # reset EEPROM to default
* laser mode: $32=1. M3 =const.power, M4: dynamic
* $SLP - only a reset will wake
* ctrl-x (0x18) soft reset
* ! / ~ hold/resume (check what the sender does when "pause" is pressed



do not use drivers without connected motors (they'll push max current).
do not change motor connections while powered
A4988 are weaker than DRV8825



***
Useful links:
https://github.com/gnea/grbl/wiki/Grbl-v1.1-Configuration
Single-line fonts (for tracing text):
http://imajeenyus.com/computer/20150110_single_line_fonts/index.shtml#hershey
http://ncplot.com/stickfont/stickfont.htm



http://diyprojects.eu/arduino-cnc-shield-version-3-0-with-grbl-v0-9/
http://blog.protoneer.co.nz/arduino-cnc-shield-v3-00-assembly-guide/
http://www.shapeoko.com/wiki/index.php/G-Code


image to G-code: makercam.com (https://youtu.be/2xMfkTrx_0U?t=304)
also: inkscape? http://www.instructables.com/id/CNC-Laser-Engraver-With-GRBL-and-Arduino/?ALLSTEPS. Also has settings, compare with https://github.com/grbl/grbl/wiki/Configuring-Grbl-v0.9 (newest: https://github.com/gnea/grbl/wiki/Grbl-v1.1-Configuration)
https://github.com/villamany/3dpBurner-Image2Gcode/releases

***
Fragment of (no longer available) Inventables post about baud rate and pin swap:

Be careful of the Asian clones of protoneer's CNC SHIELD. You want v3.51 from Protoneer, because it is compatible with GRBL v.9's changes to z-limit pin swap. "Arduino CNC Shield V3.51 – GRBL v0.9 compatible (PWM Spindle + Soft limits)"
the Amazon link you provided is a CLONE of the older 3.0 ( grbl .8 and before only card ).
Also beware ANY Arduino CLONE card with a CH340 USB to Serial chip. the CH240's have a u-code bug causing data
corruption of the serial traffic at speeds of 115k & above. This is a KNOWN issue on the GRBL Forums.