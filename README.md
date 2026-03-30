# CAN_DASHBOARD
The CAN Dashboard is an embedded system application that uses the Controller Area Network (CAN) protocol to display real-time data from an ECU. It is implemented on an STM32 microcontroller, enabling efficient communication between different modules in a vehicle or system.

🚗 CAN ECU Dashboard System – Overview

This project demonstrates a CAN-based multi-ECU dashboard system using an STM32 microcontroller in a mini car simulation.

The system consists of three ECUs connected via a CAN Bus:

ECU 1 – Vehicle Status

Handles data like indicators, speed, and temperature.

ECU 2 – Engine & Time

Processes engine-related parameters such as gear, RPM, and time.

ECU 3 – Dashboard Receiver

Receives data from the CAN bus and displays it using UART.

All ECUs communicate over a shared CAN Bus, where:

Each message is identified using CAN IDs

Filters are used to receive specific data

Interrupts ensure real-time communication

The final output is displayed as a dashboard showing:

Time ⏱️

Speed 🚀

RPM ⚙️

Gear 🔧

Temperature 🌡️

Indicator status 💡

# 📘 Theory

🔧 Embedded Systems & ECU Overview

An Electronic Control Unit (ECU) is a microcontroller-based system used to control and monitor electrical systems in real-time applications such as automotive, industrial automation, and robotics.

This project is built on an STM32 microcontroller, which is widely used in embedded systems due to its:

High performance

Low power consumption

Rich peripheral support

# Microcontroller: STM32F429ZIT6

The project uses the STM32F429 series, based on the ARM Cortex-M4 core.

Key Features:

32-bit ARM Cortex-M4 CPU

Floating Point Unit (FPU)

High clock speed (~180 MHz)

Multiple communication interfaces (UART, SPI, I2C, CAN)

GPIO for hardware control

The project is developed using STM32CubeIDE, which provides:

Hardware abstraction via HAL (Hardware Abstraction Layer)Peripheral configuration using .ioc file Auto-generated initialization code

Main Components:

main.c → Application entry point

stm32f4xx_hal_*.c → Peripheral drivers

system_stm32f4xx.c → System clock configuration

startup_stm32f429zitx.s → Boot/startup code

🔌 Peripheral Interfaces

The ECU interacts with external components using:

1. GPIO (General Purpose Input Output)

Used for:

Reading sensor inputs

Controlling actuators (LEDs, relays, etc.)

2. Timers

Used for:

Generating delays

PWM signals

Periodic interrupts

3. Communication Protocols

Depending on your configuration:

UART → Serial communication

SPI → High-speed data transfer

I2C → Sensor interfacing

⏱️ Real-Time Operation

Embedded systems like this ECU operate in real-time, meaning:

Tasks must execute within strict timing constraintsInterrupts are used for fast responseDeterministic behavior is critical

🔄 Interrupt Handling

The file stm32f4xx_it.c manages interrupts such as:

Timer interrupts

External pin interrupts

Communication events

Interrupts allow the system to respond immediately to events without polling.

🧩 Memory Management

The project uses:

Flash memory → Stores program code
RAM → Stores variables and runtime data

Linker scripts:

STM32F429ZITX_FLASH.ld

STM32F429ZITX_RAM.ld

These define how memory is allocated.

🚀 Application Flow

System initializes (clock + peripherals)

HAL libraries configure hardware

Main loop runs continuously:

while (1)

{

    // Application logic
    
}
