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
1) output wire led_red  , // Red -- Shows output as red color in the RGB LED.
2) output wire led_blue , // Blue -- Shows output as blue color in the RGB LED.
3) output wire led_green , // Green -- Shows output as green color in the RGB LED.
4) output wire testwire --It is a single bit output, provides debugging signal.
These four output wires show us the output of our programming.

5) hw_clk (Input): Hardware oscillator clock input -- It connects to the hardware oscillator. It provides the system clock signal that controls the board's timing.

## Internal Components:
The module has three main internal components:

1) Internal Oscillator (SB_HFOSC) instantiation - Stablises internal clock signal

 CLKHF_DIV = "0b10" (binary 2) [enables for clock division]

*)Control Signals:

i) CLKHFPU = 1'b1 : Validates power-up

ii) CLKHFEN = 1'b1 : Empowers oscillator

iii) CLKHF : The output signal which is connected to the internal oscillator.

2) Frequency counter logic driven by the internal oscillator:
It implements a 28-bit register and increases or adds to a value which occurs at every rising edge (transition from low to high) of the int_osc signal. Bit 5 is interconnected to testwire for controlling, Provides a way to correct the working oscillator and timing.

3) RGB LED driver instantiation with defined current parameters -
Pattern:

RGBLEDEN = 1'b1 : Enables LED operation

RGB0PWM = 1'b0 : Executes Red LED minimum radiance

RGB1PWM = 1'b0 : Executes Green LED minimum radiance

RGB2PWM = 1'b1 : Executes Blue LED maximum radiance

CURREN = 1'b1 : Enables current control

Current settings: The minimum current is set to all LEDs is "0b000001"

Output connections:

RGB0--(led_red)

RGB--(led_green)

RGB2--(led_blue)  

# Creating the PCF file:
The PCF (Physical Constraint File) file has been referred from this link given below:
 https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/VSDSquadronFM.pcf

led_red- set_io -> Pin 39

led_blue- set_io-> Pin 40

led_green -set_io -> Pin 41

hw_clk- set_io -> Pin 20

testwire- set_io -> Pin 17

## Commands:
1. set_io led_red 39 - Helps to send logical signals to control the LED to impile the color red.
2. set_io led_blue 40 - Helps to send logical signals to control the LED to impile the color blue.
3. set_io led_green 41 - Helps to send logical signals to control the LED to impile the color green.
4. set_io hw_clk 20 - Assigns hardware clock signal to receive the clock inputs.
5. set_io testwire 17 - Helps for testing and debugging.

Pin assignments have been marked in the data sheet as purple colored circles.
![image](https://github.com/user-attachments/assets/cee7652c-c99b-420e-978d-e8a95147c767)

# Integrating with the VSDSquadron FPGA Mini Board:
Setting up the hardware and codings:
1) View the datasheet of the board and understand its aspects.
2) Correlate the datasheet with the board
3) Refer the connections of the board to the device with the datasheet and refer the codings to clear, build and to run the program in the board.

4) The result after uploading the program into the board:

https://github.com/user-attachments/assets/62f57dd3-ce6b-4bee-aabb-2581b359b503

The program has been successfully completed!

# Summary:
The verilog code has the control to implement the RGB LED, it also implements an UART transmitter. It has an internal oscillator to have the control flow of clock signals to the Board. There are four output wires which show us the output of our programming, One input wire provides the system clock signal that controls the board's timing. This module contains the three main internal components:
1) Internal Oscillator (SB_HFOSC) instantiation - Stablises internal clock signal, 

2) Frequency counter logic driven by the internal oscillator

3) RGB LED driver instantiation with defined current parameters

4) Pin mappings from the PCF file:

led_red--> Pin 39

led_blue--> Pin 40

led_green--> Pin 41

hw_clk--> Pin 20

testwire--> Pin 17

Integration steps: 1) View the datasheet of the board and understand its aspects.
2) Correlate the datasheet with the board
3) Refer the connections of the board to the device with the datasheet and refer the codings to clear, build and to run the program in the board.

4) The result after uploading the program into the board:

https://github.com/user-attachments/assets/62f57dd3-ce6b-4bee-aabb-2581b359b503

# Challenges faced and solutions implemented:
Had to update the USB Settings in the laptop as it did not detect the option to connect with the board. Watched some videos on youtube and changed the settings. The verilog code was a bit tough to understand but understood it with the help of  .

(https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/Makefile) 

# TASK-2:
# UART LOOPBACK PROJECT:

## Objective: Implement a UART loopback mechanism where transmitted data is immediately received back, facilitating testing of UART functionality.

UART - Stands for Universal Asynchronous Receiver-Transmitter (Hardware Communication Protocol). It is similar to a working principle of bluetooth. It is a serial communicating device used for short distance communication between devices, commonly used in computers, chips, microcontrollers etc... It has two pins, the TX (Transmitter) pin and RX (Receiver) pin.When the data is transmitted to the TX pin, it will instantly change its route path and receives the data to the RX pin of the respective module which is being programmed. 

## Studying the exisiting code:

The code has been studied and referred from the below link:

https://www.google.com/url?q=https%3A%2F%2Fgithub.com%2Fthesourcerer8%2FVSDSquadron_FM%2Ftree%2Fmain%2Fuart_loopback&sa=D&source=calendar&usd=2&usg=AOvVaw2tz_YfIWz3X_XvprabSjtQ

set_io  uarttx 14
set_io  uartrx 15

The above two codes defines the uart_loopback implementation mechanism.
The module explains six ports:

Three RGB LED outputs (led_red, led_blue, led_green)
UART transmit/receive pins (uarttx, uartrx)
System clock input (hw_clk)
Internal Component Analysis
Internal Oscilliator (SB_HFOSC)
Implements a high-frequency oscillator
Uses CLKHF_DIV = "0b10" for frequency division
Generates internal clock signal (int_osc)
Frequency Counter
28-bit counter
Increments on every positive edge of internal oscillator
Used for timing generation
UART Loopback
Direct connection between transmit and receive pins
Echoes back any received UART data immediately
RGB LED Driver (SB_RGBA_DRV)
Controls three RGB channels
Uses PWM (Pulse Width Modulation) for brightness control
Current settings configured for each channel
Maps UART input directly to LED intensity
Operation Analysis
UART Input Processing
Received UART data appears on uartrx pin
Data is immediately looped back out through uarttx
Same data drives all RGB channels simultaneously
LED Control
RGB driver converts UART signal to PWM output
All LEDs respond identically to input signal
Current limiting set to minimum (0b000001) for each channel
Timing Generation
Internal oscillator provides clock reference
Frequency counter generates timing signals
Used for PWM generation and LED control
