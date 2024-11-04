# SRAM-PUF Based Authentication on Arduino

This repository contains the implementation of SRAM-PUF (Physical Unclonable Function) based authentication on Arduino. SRAM-PUF is used to generate unique, device-specific cryptographic keys by leveraging the inherent randomness of SRAM on microcontrollers. This project targets the Arduino Uno microcontroller.

## Features

- Extract cryptographic keys from SRAM PUF.
- Use these keys for secure, hardware-bound authentication.
- Compatible with Arduino Uno and and adaptable for othyers similar.

## Getting Started

### Prerequisites

- [Arduino IDE](https://www.arduino.cc/en/software) installed.
- requiremnts.txt installed
- A compatible Arduino board (tested on Arduino Uno).
- Basic knowledge of Arduino programming and hardware setup.

### Setting Up the Bootloader

1. **Compile the Bootloader**:
   - Run the command `./scripts/compile_bootloader.sh` in your terminal. This compiles the bootloader necessary for FE and PUF-based authentication.

2. **Upload the ArduinoISP Firmware** (run only once on another board):
   - Open Arduino IDE, go to `File > Examples > 11.ArduinoISP > ArduinoISP`.
   - Connect the Arduino board you will use as the programmer (not the target board to be programmed).
   - In Arduino IDE, under the `Tools` menu, select:
     - **Board**: The board model of the programmer.
     - **Serial Port**: The port associated with the programmer.
   - Upload the ArduinoISP sketch to the programmer board.

3. **Flash the Bootloader**:
   - Wire your Arduino boards as specified for using Arduino as ISP.
   - Run the command `./scripts/flash_bootloader.sh path_to_bootloader` to flash the bootloader to the target board.

4. **Connecting the Target via USB**:
   - Once the bootloader is flashed, disconnect the programmer board.
   - Connect the target Arduino directly to your computer using USB.

### Interacting with the System

- **Serial Communication**:
   - Open the serial interface using Minicom (or an equivalent serial terminal) to interact with the device:
     ```bash
     minicom -D /dev/ttyACM0 -b 115200
     ```
   - This connects to the target Arduino at a baud rate of 115200.

- **Commands**:
   - Commands to control and test the PUF-based authentication system can be found in `main.c`.
