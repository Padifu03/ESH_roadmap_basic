# ESH Roadmap Basic

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Board: NUCLEO-C031C6](https://img.shields.io/badge/Board-NUCLEO--C031C6-03234B?logo=stmicroelectronics)](https://www.st.com/en/evaluation-tools/nucleo-c031c6.html)
[![IDE: VS Code](https://img.shields.io/badge/IDE-VS%20Code-007ACC?logo=visualstudiocode)](https://code.visualstudio.com/)
[![Build: CMake](https://img.shields.io/badge/Build-CMake-064F8C?logo=cmake)](https://cmake.org/)

A hands-on, progressive learning roadmap for **bare-metal embedded systems development** on the **STM32C031C6T6** (Cortex-M0+). Each project builds incrementally on the previous one — from toggling an LED with raw register writes to handling hardware interrupts with debounce — all without an HAL or RTOS.

---

## Table of Contents

- [ESH Roadmap Basic](#esh-roadmap-basic)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Hardware](#hardware)
  - [Prerequisites](#prerequisites)
  - [Repository Layout](#repository-layout)
  - [Projects](#projects)
  - [Getting Started](#getting-started)
  - [Building \& Flashing](#building--flashing)
    - [Build](#build)
    - [Flash \& Debug](#flash--debug)
  - [Documentation \& Resources](#documentation--resources)
  - [Contributing](#contributing)
  - [License](#license)

---

## Overview

This repository is designed as a self-paced curriculum for learning embedded C on real hardware. Every project targets the **[NUCLEO-C031C6](https://www.st.com/en/evaluation-tools/nucleo-c031c6.html)** evaluation board and is built entirely with register-level access — no HAL abstractions. The goal is to develop a solid understanding of how peripherals work at the hardware level before moving on to higher-level frameworks.

**Key learning objectives:**

- Understand the STM32 memory-mapped peripheral model
- Write and structure bare-metal C drivers (GPIO, UART, ADC, Timers, Interrupts)
- Use CMSIS device headers for register definitions
- Configure and debug firmware with CMake, Ninja, and VS Code

---

## Hardware

| Component | Description |
|---|---|
| **MCU** | STM32C031C6T6 — ARM Cortex-M0+, 48 MHz, 32 KB Flash, 12 KB SRAM |
| **Board** | [NUCLEO-C031C6](https://www.st.com/en/evaluation-tools/nucleo-c031c6.html) |
| **Debugger** | On-board ST-LINK/V2-1 (SWD) |
| **User LED** | LD4 — PA5 |
| **User Button** | B1 — PC13 (active low) |

---

## Prerequisites

| Tool | Version | Notes |
|---|---|---|
| [Visual Studio Code](https://code.visualstudio.com/) | Latest | Primary IDE |
| [STM32 VS Code Extension](https://marketplace.visualstudio.com/items?itemName=stmicroelectronics.stm32-vscode-extension) | Latest | Build, flash & debug integration (auto-installs CMake Tools) |
| [CMake](https://cmake.org/) | >= 3.20 | Build system generator |
| [Ninja](https://ninja-build.org/) | Latest | Fast, parallel build backend |
| [GNU ARM Embedded Toolchain](https://developer.arm.com/Tools%20and%20Software/GNU%20Toolchain) | Latest | `arm-none-eabi-gcc` cross-compiler |
| [STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html) | Latest | *Optional* — device configuration & code generation |

---

## Repository Layout

```
ESH_roadmap_basic/
├── basic-00-cstruct/           # Bare-metal project skeleton
├── basic-01-headers/           # CMSIS device headers integration
├── basic-02-gpio/              # GPIO driver (LED + button)
├── basic-03-uart/              # UART driver (serial I/O)
├── basic-04-adc/               # ADC driver (analog input)
├── basic-05-systick/           # SysTick timer driver (delays)
├── basic-06-gp-timers/         # General-purpose timer driver
├── basic-07-interrupts/        # EXTI & timer interrupts with debounce
├── base-nucleoc031c6-board-mx-project/  # CubeMX reference project
├── STM32C031C6/                # Datasheets & reference manuals
├── LICENSE
└── README.md
```

Each project follows a consistent internal structure:

```
basic-XX-<topic>/
├── Src/                        # Source files (.c)
├── Inc/                        # Header files (.h)
├── chip_headers/               # CMSIS device & core headers
├── cmake/                      # Toolchain files & CMake helpers
│   ├── gnu-tools-for-stm32.cmake
│   └── vscode_generated.cmake
├── Build/                      # Build output (Debug / Release)
├── CMakeLists.txt              # CMake build configuration
├── CMakePresets.json           # CMake presets (Debug / Release)
└── stm32c031x6_flash.ld       # Linker script
```

---

## Projects

| # | Folder | Topic | Description |
|---|---|---|---|
| 00 | `basic-00-cstruct` | Project Skeleton | Minimal bare-metal C project — startup code, linker script, and a blinking LED using raw register addresses. |
| — | `base-nucleoc031c6-board-mx-project` | CubeMX Reference | STM32CubeMX-generated base project for the NUCLEO-C031C6 board. Used as a reference for peripheral initialization. |
| 01 | `basic-01-headers` | CMSIS Headers | Replaces magic addresses with CMSIS device header register definitions to blink the user LED. |
| 02 | `basic-02-gpio` | GPIO Driver | Structured GPIO driver for the user LED (PA5) and user button (PC13) with read/toggle functionality. |
| 03 | `basic-03-uart` | UART Driver | USART2 transmit/receive driver for serial communication over the ST-LINK virtual COM port. |
| 04 | `basic-04-adc` | ADC Driver | ADC single-channel conversion driver, demonstrated through a simulated volume-controller application. |
| 05 | `basic-05-systick` | SysTick Timer | SysTick-based millisecond delay driver used for precise LED timing control. |
| 06 | `basic-06-gp-timers` | General-Purpose Timers | TIM3 up/down-counter driver applied to an F1 start-race sequence game. |
| 07 | `basic-07-interrupts` | Interrupts & Debounce | EXTI interrupt on the user button (PC13) with hardware timer-based debounce. Implements a medical-device menu navigation demo cycling through modes on each button press. |

---

## Getting Started

1. **Clone the repository**

   ```bash
   git clone https://github.com/Padifu03/ESH_roadmap_basic.git
   cd ESH_roadmap_basic
   ```

2. **Open in VS Code**

   ```bash
   code .
   ```

3. **Install the [STM32 VS Code Extension](https://marketplace.visualstudio.com/items?itemName=stmicroelectronics.stm32-vscode-extension)** — search for `stmicroelectronics.stm32-vscode-extension` in the Extensions Marketplace.

   > **Tip:** The STM32 extension will automatically detect that the [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) extension is required and prompt you to install it. Accept the prompt and the CMake extension will be downloaded and configured for you — no manual setup needed.

4. **Select a project** — open the desired folder (e.g. `basic-07-interrupts`).

5. **Choose a CMake preset** — pick **Debug** or **Release** from the CMake status bar at the bottom of the VS Code window. The STM32 extension uses the CMake Tools extension under the hood to configure, build, and manage presets.

---

## Building & Flashing

### Build

Once the CMake Tools extension is installed (see [Getting Started](#getting-started)), you can build directly from VS Code:

- **CMake sidebar** — open the CMake panel and click the **Build** button, or
- **Keyboard shortcut** — press `Ctrl + Shift + B`.

Alternatively, from the terminal:

```bash
cd basic-07-interrupts
cmake --preset Debug
cmake --build --preset Debug
```

### Flash & Debug

The STM32 VS Code Extension **automatically generates** the debug launch configuration (`.vscode/launch.json`) for your project. This means the **Run and Debug** panel is ready to use out of the box — no manual `launch.json` editing required.

1. Connect the NUCLEO-C031C6 board via USB.
2. Open the **Run and Debug** panel (`Ctrl + Shift + D`).
3. Select the auto-generated **STM32 debug configuration** from the dropdown and press **F5**.

The ST-LINK debugger will flash the firmware and halt at `main()`. You get full debugging support — breakpoints, variable inspection, call stack, and peripheral register views.

---

## Documentation & Resources

| Document | Link |
|---|---|
| STM32C031C6 Reference Manual | [stm32c031c6_RM.pdf](STM32C031C6/stm32c031c6_RM.pdf) |
| STM32C031C6 Datasheet | [stm32c031c6_datasheet.pdf](STM32C031C6/stm32c031c6_datasheet.pdf) |
| STM32C031C6 User Manual | [stm32c031c6_user_manual.pdf](STM32C031C6/stm32c031c6_user_manual.pdf) |
| NUCLEO-64 Board User Manual | [stm32_nucleo64_UM.pdf](STM32C031C6/stm32_nucleo64_UM.pdf) |
| Cortex-M0+ Generic User Guide | [Cortex-M0plus_UG.pdf](STM32C031C6/Cortex-M0plus_UG.pdf) |
| STM32 VS Code Extension | [Marketplace](https://marketplace.visualstudio.com/items?itemName=stmicroelectronics.stm32-vscode-extension) |

---

## Contributing

Contributions, suggestions, and bug reports are welcome. To contribute:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feat/my-feature`).
3. Commit your changes with clear, descriptive messages.
4. Open a Pull Request against `master`.

Please keep the existing project structure and coding style consistent.

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.
