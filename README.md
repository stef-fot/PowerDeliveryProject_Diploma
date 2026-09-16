# USB-C Power Delivery Implementation

**Embedded USB-C Power Delivery (USB-PD) on the STM32G474, developed as part of a thesis on embedded systems and power management.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](#license)
[![Platform](https://img.shields.io/badge/platform-STM32G474-blue.svg)](#hardware-requirements)
[![Status](https://img.shields.io/badge/status-thesis%20project-orange.svg)](#overview)

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Hardware Requirements](#hardware-requirements)
- [Software Components](#software-components)
- [Installation & Usage](#installation--usage)
- [Future Improvements](#future-improvements)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

---

## Overview

This project implements USB-C Power Delivery (USB-C PD) in C on an embedded system. The goal is to negotiate power contracts between a USB-C power source and a power sink device, with the user selecting the target voltage directly on the board.

It was developed as part of a thesis on embedded systems and power management.

## Features

| Feature | Description |
|---|---|
| **USB-PD Communication** | Handles power negotiation via the Configuration Channel (CC) lines. |
| **Dynamic Power Selection** | Supports three voltage modes: `5V`, `9V`, and `12V`. |
| **Joystick Control** | The user selects the desired voltage using the joystick on the STM32G474; the system then requests it over USB-PD. |
| **LED Confirmation** | An LED indicator confirms the selection once negotiation succeeds. |
| **Real-time Monitoring** | Logs power delivery status, including voltage, current, and contract negotiation. |
| **Safety Mechanisms** | Protects against overvoltage, undervoltage, and excessive current draw. |

## Hardware Requirements

- STM32G474 microcontroller
- USB-C power source (charger or power adapter)
- USB-C sink device (custom board or test device)
- Joystick for voltage selection
- LED indicators for confirmation

## Software Components

- Embedded firmware handling USB-PD communication
- Event-driven architecture for power contract negotiation, triggered by joystick input
- Low-level CC line interaction to determine source/sink roles

## Installation & Usage

### 1. Clone the repository

```sh
git clone https://github.com/yourusername/usb-c-pd.git
cd usb-c-pd
```

### 2. Compile the firmware

Make sure a compatible ARM GCC toolchain is installed, then run:

```sh
make
```

### 3. Flash the microcontroller

Upload the firmware using STM32CubeProgrammer or OpenOCD:

```sh
st-flash write firmware.bin 0x8000000
```

### 4. Select a power mode

1. Use the joystick on the STM32G474 to request **5V**, **9V**, or **12V**.
2. The system sends a USB-PD request to the power source.
3. Once negotiation succeeds, the matching **LED indicator** lights up.

### 5. Monitor power negotiation

- Use a **USB analyzer** or **serial output** to track the power contract exchange.
- Debug logs are available via **UART**.

## Future Improvements

- [ ] **Programmable APDO integration** – support for adjustable voltage/current profiles
- [ ] **Enhanced debugging & logging** – improved real-time tracing for power negotiation
- [ ] **Graphical monitoring UI** – a web-based dashboard for live power monitoring

## Contributing

Pull requests are welcome. For major changes, please open an **issue** first to discuss what you'd like to change.

## License

This project is licensed under the **MIT License**.

## Author

Developed as part of a thesis on **USB Power Delivery** and **embedded systems**.

Feel free to reach out with questions or feedback.
