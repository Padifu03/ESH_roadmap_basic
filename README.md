# ESH Roadmap Basic

A collection of embedded systems development exercises and projects focused on STM32 microcontroller programming using Visual Studio Code with the [STM32 VS Code Extension](https://marketplace.visualstudio.com/items?itemName=stmicroelectronics.stm32-vscode-extension).

## Overview

This repository contains a structured learning roadmap for embedded systems development, starting with the basics. Each folder represents a different exercise or project that builds upon fundamental concepts and gradually increases in complexity.

## Project Structure

Each project folder is organized as follows:

```txt
basic-XX-<description>/
├── Src/                        # Source code files (.c)
├── Inc/                        # Header files (.h)
├── cmake/                      # CMake toolchain and generated files
│   ├── gnu-tools-for-stm32.cmake
│   └── vscode_generated.cmake
├── build/                      # Build output (Debug/Release)
├── CMakeLists.txt              # CMake build configuration
├── CMakePresets.json            # CMake presets (Debug/Release)
└── stm32c031x6_flash.ld        # Linker script
```

### Current Projects

- **basic-00-cstruct**: Introduction to STM32C031C6T6 microcontroller programming with basic C structure and setup
- **base-nucleoc031c6-board-mx-project**: STM32CubeMX-generated base project for the Nucleo-C031C6 board
- **basic-01-headers**: NUCLE-C031C6 project which takes hardware CubeMx-generated drivers code and use it to blink the user led.

## Requirements

- **VS Code**: Latest version with the [STM32 VS Code Extension](https://marketplace.visualstudio.com/items?itemName=stmicroelectronics.stm32-vscode-extension)
- **STM32CubeMX**: For device configuration and code generation (optional)
- **CMake**: Version 3.20 or later
- **Ninja**: Build system
- **Compiler**: GNU ARM Embedded Toolchain (GNU Tools for STM32)
- **Windows/Linux/macOS**: Development environment

## Getting Started

1. Clone the repository
2. Open the workspace in VS Code
3. Install the [STM32 VS Code Extension](https://marketplace.visualstudio.com/items?itemName=stmicroelectronics.stm32-vscode-extension) if not already installed
4. Navigate to the desired project folder (e.g., `basic-00-cstruct`)
5. Select a CMake preset (Debug or Release) from the CMake extension status bar
6. Build the project using the CMake build command (`Ctrl+Shift+B` or CMake sidebar)
7. Flash and debug using the STM32 extension debug configurations

## Tools & Technologies

- **Editor**: Visual Studio Code
- **Extension**: STM32 VS Code Extension
- **Microcontroller**: STM32C031C6T6
- **Board**: Nucleo-C031C6
- **Language**: C
- **Build System**: CMake + Ninja
- **Toolchain**: GNU Tools for STM32 (ARM GCC)

## Resources

- [STM32 Nucleo 64 Documentation](STM32C031C6/stm32_nucleo64_UM.pdf)
- [STM32C0 Reference Manual](STM32C031C6/stm32c031c6_RM.pdf)

## License

See [LICENSE](LICENSE) file for details.
