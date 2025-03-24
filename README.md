# FPGA-VSD-Projects (TASK-1)
# INTRODUCTION

## FPGA:
1) The FPGA (Field Programmable Gate Array), used for implementing and coding programs.
2) It is powered by the Lattice UltraPlus ICE40UP5K FPGA.
3) It offers 1 megabit of single port RAM (Random Access Memory), 120 kilobits of Dual Port RAM, and 8 multipliers which helps the chip to solve logical math problems for versatile design.
   capabilities.
4) The Lattice UltraPlus ICE40UP5K FPGA has 5,040 Logic Cells (Approximately 5.3K Look-Up Tables).

## Connectivity:
1) The board has been equipped with Future Technology Devices International Future Technology 232H (FTDI FT232H USB to Serial Peripheral Interface (SPI) device for smooth interaction of messages between the devices.
2) Future Technology Devices International pins can be accessed through test points for optimization and easy troubleshooting.

## General Purpose I/O (GPIO):
1) The total GPIOSs in the FPGA are brought out for painless prototyping and interfacing.

## Memory:
1)Integrated 4MB SPI flash for storage of data and data organization.

## LED Indicators:
1) RGB Light Emitting Diode has been installed in the board for manual functionality.

## FPGA Board:
The VSDSquadron FPGA Mini (FM) board is a low cost, small tool for prototyping and
embedded system development. With powerful ICE40UP5K FPGA, onboard programming, dynamic
GPIO access, SPI flash, and integrated power regulation, it enables efficient design, testing, and
deployment, making it ideal for developers, hobbyists, and educators exploring FPGA applications.The capabilities of this board are listed below:

1) 48-lead QFN package

2) 5.3K LUTs for flexible logic design

3) 1Mb SPRAM and 120Kb DPRAM for efficient memory usage

4) Onboard FTDI FT232H USB-to-SPI interface for programming and communication

5) All 32 FPGA GPIO accessible for rapid prototyping

6) Integrated 4MB SPI flash for configuration and data storage

7) RGB LED for user-defined signaling
      
8) Onboard 3.3V and 1.2V power regulators, with the ability to supply 3.3V externally

For more data on about the VSDSquadron FPGA Mini (FM)  device, refer to https://www.vlsisystemdesign.com/wp-content/uploads/2024/12/iCE40_UltraPlus_Sheet.pdf

## Key components of the VSDSquadron FPGA Mini (FM) board:

![image](https://github.com/user-attachments/assets/2e5dc09d-2362-4eb5-bfea-6a3246b8178a)

## Components of the board:
![image](https://github.com/user-attachments/assets/511b320e-c7f4-4065-84c3-08259e85a693)

## Dimensions:
1) Formation factor is 57.00 x 29.00 mm

3) Maximum height at the top side is 8mm

5) Maximum height at the bottom side is 1mm

# Understanding the Verilog Code:
The verilog code has been referred from this link given below:
https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/top.v

## Review of the module declaration:
In the module top, there are 4 output wires. They are:
output wire led_red  , // Red -- Shows output as red color in the RGB LED.
output wire led_blue , // Blue -- Shows output as blue color in the RGB LED.
output wire led_green , // Green -- Shows output as green color in the RGB LED.
output wire testwire --It is a single bit output, provides debugging signal.
These four output wires show us the output of our programming.

hw_clk (Input): Hardware oscillator clock input -- It connects to the hardware oscillator. It provides the system clock signal that controls the board's timing.

## Internal Components:
The module has three main internal components:
1) Internal Oscillator (SB_HFOSC) instantiation - 

2) Frequency counter logic driven by the internal oscillator

3) RGB LED driver instantiation with defined current parameters




 

## Creating the PCF file:
The PCF file has been refereed from this link given below:
 https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/VSDSquadronFM.pcf

led_red -> Pin 39

led_blue -> Pin 40

led_green -> Pin 41

hw_clk -> Pin 20

testwire -> Pin 17

Pin assignments have been marked in the data sheet.
![image](https://github.com/user-attachments/assets/cee7652c-c99b-420e-978d-e8a95147c767)

# Challenges faced and solutions implemented:
Had to update the USB Settings in the laptop as it did not detect the option to connect with the board. Watched some videos on youtube and changed the settings.
