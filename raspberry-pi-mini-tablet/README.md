Portable Raspberry Pi 5 Mini Tablet with 3.5" GPIO Display

Overview
This project documents the assembly and configuration of a compact Raspberry Pi 5 portable system integrated inside a PLA+ enclosure with a 3.5-inch GPIO touchscreen display. The goal was to create a small, self-contained mobile Linux workstation suitable for diagnostics, lightweight development, and field experiments.

Problem
After hardware assembly, the device powered on correctly but the 3.5" GPIO display remained completely white. The system activity LEDs indicated that the operating system was running, but no video output appeared on the screen.

Diagnosis
Initial troubleshooting focused on possible operating system compatibility issues.

Steps performed:
• Verified hardware installation and GPIO alignment  
• Confirmed Raspberry Pi boot activity through LED indicators  
• Reinstalled operating systems using Raspberry Pi Imager  
• Tested Parrot OS installation (system booted but display unsupported)

Research indicated that many GPIO-based SPI displays currently have limited or no driver support on several Linux distributions running on the Raspberry Pi 5.

Tools Used
Raspberry Pi 5  
3.5" GPIO Touch Display (SPI interface)  
PLA+ enclosure  
Active cooling fan with heatsink  
Thermal adhesive pads  
Raspberry Pi Imager  
Windows PowerShell / SSH access

Implementation
Hardware assembly included:

1. Installing the Raspberry Pi 5 board into the enclosure and securing it using four corner mounting screws.
2. Applying thermal adhesive pads to the CPU and memory module.
3. Installing an active cooling fan and heatsink assembly secured with spring screws for proper pressure and heat dissipation.
4. Connecting the fan power to the dedicated header near the GPIO pins.
5. Mounting the 3.5" GPIO display directly onto the GPIO header while carefully aligning all pins.

Software troubleshooting steps:

1. Installed Parrot OS using Raspberry Pi Imager.
2. System booted successfully but the display remained blank due to missing drivers.
3. Reinstalled the official Raspberry Pi OS (Trixie).
4. Connected to the device remotely using SSH by creating an empty `ssh` file in the boot partition.
5. Accessed the Raspberry Pi over the network and modified the boot configuration.

Display activation required editing the `config.txt` file to enable SPI display output.

Example configuration used:

dtparam=spi=on
dtoverlay=piscreen,rotate=270,speed=16000000,fps=30
hdmi_blanking=2


After rebooting the device, the display initialized correctly and the system booted directly onto the touchscreen.

Result
The system successfully booted with the GPIO touchscreen functioning as the primary display, effectively transforming the Raspberry Pi 5 into a compact handheld mini-tablet suitable for mobile tasks and experimentation.

Skills Demonstrated
Hardware assembly and embedded system integration  
Thermal management for SBC devices  
Linux troubleshooting and system configuration  
SSH remote access and headless setup  
Boot configuration and device overlay management  
GPIO peripheral integration
