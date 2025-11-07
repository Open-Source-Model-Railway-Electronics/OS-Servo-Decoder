# OS-Servo-Decoders Manual
Supports: OS-Servo-Decoder

## 📘 Introduction
The OS-Servo-Decoder is a simple and robust DCC accessory decoder designed for driving up to 8 servo motors. It supports modern model railroads with flexible configuration options, external relay modules for polarity switching (optional) and direct control using both input switches, DCC accessory commands and locomotive functions (F1–F8).

---

## 📚 Table of Contents

1. [Features](#-features)
2. [Connecting the Decoder](#-connecting-the-decoder)
3. [Controlling the Servo Outputs](#-controlling-the-servo-outputs)
4. [DCC Configuration Mode](#-dcc-configuration-mode)
5. [Button Configuration Mode](#-button-configuration-mode)
6. [Storing Servo Positions](#-storing-servo-positions)
7. [Loco Function Modes](#-loco-function-modes)
8. [Address Offset](#-address-offset)
9. [Auto-Toggle Mode](#-auto-toggle-mode)
10. [Summary](#-summary)

---

## 🔧 Features
- Controls up to 8 servos  
- Uses pluggable screw terminals for easy wiring  
- External relay modules  
- Fully supports:  
  - Standard turnout movement  
  - Polarity switching (where supported)  
  - Adjustable servo end positions (via buttons)  
- Standalone configuration: no PC, CVs or programmers required  
- Optional DCC locomotive function control (F1–F18)  
- Supports Roco 4-address offset  

---

## 🔌 Connecting the Decoder
The OS-Servo-Decoders use the same wiring layout as the OS-Solenoid-Decoder:

- **Top header:** Connect either DCC track voltage or a DC power supply (max 19V)  
- ⚠️ **Important:** Do not use AC voltage  
- **Servo headers:** Connect each servo motor to the 3-pin connector  
  - Standard layout: **GND — +5V — Signal**  
- **Relay Connectors:** A, COM, B  

---

## 💪 Controlling the Servo Outputs
_(Section intentionally left for expansion in future versions.)_

---

## 🛠️ DCC Configuration Mode
The decoder supports an advanced DCC configuration mode that works entirely from your throttle.

---

## 🛠️ Button Configuration Mode
_(Section intentionally left for expansion in future versions.)_

---

## 🌟 Storing Servo Positions
While in Run Mode, use these functions to program:

- **F1 = ON ➔** Save current position as *CURVED*  
- **F2 = ON ➔** Save current position as *STRAIGHT*  
- **F3 = ON ➔** Invert frog relay *(6-relay model only)*  
- **F0 = OFF ➔** Exit Run Mode  

---

## 🚗 Loco Function Modes
In Config Mode, you can choose to control the decoder using loco function keys instead of accessory commands.

- **F4 = ON ➔** Disable loco control *(default)*  
- **F5 = ON ➔** Enable loco function mode *(F1–F16)* — uses 1 address  
- **F6 = ON ➔** Enable 4-function mode *(F1–F4)* — uses 2 addresses  

This allows ultra-fast switching using throttles like Roco Lokmaus or Multimaus.

---

## ⚖️ Address Offset
To compensate for Roco’s offset of 4, use:

- **F7 = ON ➔** Enable 4-address offset  

---

## ⏰ Auto-Toggle Mode
Enable auto-toggling of a selected motor:

- **F8 = ON ➔** Motor toggles every 5 seconds  
  - Speed is controlled by throttle  
  - Throttle direction does not matter  
  - Throttle 0 = slow, Max = fast  

In this mode, the motor is no longer slaved to throttle function keys.

---

## 📊 Summary
- Use the buttons for direct setup and servo adjustment  
- Use DCC loco address **9999** with **F0, F1, F2 OFF** to enter config mode  
- Use **F1/F2** to store servo positions  
- Use **F4–F8** to enable loco function control, address offset or toggle modes  

All OS-Servo-Decoders share this interface and logic.  
No computer needed. No CVs. Just wire it, address it, and run it.
