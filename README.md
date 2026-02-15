# ESH Roadmap Basic

A collection of embedded systems development exercises and projects focused on STM32 microcontroller programming using the STM32CubeIDE development environment.

## Overview

This repository contains a structured learning roadmap for embedded systems development, starting with the basics. Each folder represents a different exercise or project that builds upon fundamental concepts and gradually increases in complexity.

## Project Structure

Each project folder is organized as follows:

```
basic-XX-<description>/
├── Src/                   # Source code files (.c, .h)
├── Startup/               # Startup files (assembly)
├── Debug/                 # Build output and debug files
├── STM32C031C6TX_FLASH.ld # Linker script
└── <project>.launch       # STM32CubeIDE launch configuration
```

### Current Projects

- **basic-00-cstruct-stm32c0**: Introduction to STM32C031C6TX microcontroller programming with basic C structure and setup

## Requirements

- **STM32CubeIDE**: Latest version (for development and debugging)
- **STM32CubeMX**: For device configuration and code generation (optional)
- **Compiler**: ARM GCC Toolchain (included with STM32CubeIDE)
- **Windows/Linux/macOS**: Development environment

## Getting Started

1. Clone the repository
2. Open STM32CubeIDE
3. Import project: `File → Open Projects from File System`
4. Navigate to the desired project folder (e.g., `basic-00-cstruct-stm32c0`)
5. Build and debug using the IDE tools

## Tools & Technologies

- **IDE**: STM32CubeIDE (Eclipse-based)
- **Microcontroller**: STM32C031C6TX
- **Language**: C
- **Build System**: Make (STM32CubeIDE generated)

## Resources

- [STM32 Nucleo 64 Documentation](STM32C031C6\stm32_nucleo64_UM.pdf)
- [STM32C0 Reference Manual](STM32C031C6\stm32c031c6_RM.pdf)
- 

## License

See [LICENSE](LICENSE) file for details.
