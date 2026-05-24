> 🌐 &nbsp; 🇬🇧 EN &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-Servo-Decoders Manual

## 📘 Introduction
The OS-Servo-Decoder is a simple and robust DCC accessory decoder designed for driving up to 8 servo motors. It supports modern model railroads with flexible configuration options, external relay modules for polarity switching (optional) and direct control using both input switches, DCC accessory commands and locomotive functions (F1–F8).

---

## 📚 Table of Contents

- [OS-Servo-Decoders Manual](#os-servo-decoders-manual)
  - [📘 Introduction](#-introduction)
  - [📚 Table of Contents](#-table-of-contents)
  - [🔧 Features](#-features)
  - [🔌 Connecting the Decoder](#-connecting-the-decoder)
  - [💪 Controlling the Servo Outputs](#-controlling-the-servo-outputs)
  - [🛠️ DCC Configuration Mode](#️-dcc-configuration-mode)
  - [🛠️ Button Configuration Mode](#️-button-configuration-mode)
  - [🌟 Storing Servo Positions](#-storing-servo-positions)
  - [🚗 Loco Function Modes](#-loco-function-modes)
  - [⚖️ Address Offset](#️-address-offset)
  - [⏰ Auto-Toggle Mode](#-auto-toggle-mode)
  - [📊 Summary](#-summary)

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

![OS-Servo-Decoder-8 with different relay extension configurations](board_w_extensions.png)

*The OS-Servo-Decoder-8 shown with various relay extension modules plugged in (top-left: latching relays; top-right: general-purpose relays; bottom: combinations with servos connected).*

The OS-Servo-Decoder-8 uses the same wiring layout as the OS-Solenoid-Decoder:

- **Top header (POW / DCC):** Connect either DCC track voltage or a DC power supply (max 19 V)
- ⚠️ **Important:** Do not use AC voltage — this will damage the decoder
- **Servo headers (right side):** Connect each servo motor to the 3-pin connector
  - Standard pinout: **GND — +5 V — Signal**
- **Relay connectors (left side):** A, COM, B — for OS relay extension modules

---

## 💪 Controlling the Servo Outputs

Each servo output is controlled by a DCC accessory address. When the decoder receives a DCC command for an assigned address, it moves the servo smoothly to the stored position for that command state (STRAIGHT or CURVED).

- Sending the **STRAIGHT** command moves the servo to its stored straight end position.
- Sending the **CURVED** command moves the servo to its stored curved end position.
- If relay extension modules are fitted, the relay contacts switch in sync with the servo for frog polarization.

Servo end positions are stored using loco function keys — see [Storing Servo Positions](#-storing-servo-positions) below.

---

## 🛠️ DCC Configuration Mode

The decoder supports a configuration mode that works entirely from your DCC throttle — no computer, no CV programmer required.

To enter configuration mode, select loco address **9999** on your throttle and set **F0, F1, and F2 all to OFF**. The decoder will enter config mode and accept function key commands.

Once in config mode, use the function keys (F1–F8) to set options as described in the sections below. Press **F0 = OFF** to exit and return to normal operation.

---

## 🛠️ Button Configuration Mode

The board has two physical buttons: **CONFIGURE** and **TOGGLE**.

- **CONFIGURE** — enters configuration mode directly, without needing a throttle. The decoder responds with LED feedback indicating the active setting.
- **TOGGLE** — manually toggles the currently selected servo output between its two stored positions. Useful for testing movement and adjusting end positions.

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
- **F5 = ON ➔** Enable loco function mode *(F1–F8)* — uses 1 address  
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
