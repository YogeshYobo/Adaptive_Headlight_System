# Adaptive-Headlight-System

STM32-Based Smart Adaptive Headlight Control System

Overview This project implements a Smart Adaptive Headlight Control
System using the STM32F411RE Nucleo Board. The system automatically
adjusts vehicle headlight brightness based on real-time environmental
conditions such as: - Day / Night - Oncoming vehicle glare - Rain /
Fog - Smoke - Cloudy or street light conditions

The goal is to improve driver visibility, reduce glare for oncoming
vehicles, and enhance overall road safety through intelligent
automation.

System Architecture The STM32 microcontroller acts as the central
controller and performs: - Multi-channel ADC sensor acquisition -
DMA-based data transfer for efficiency - Real-time sensor processing -
State machine-based decision making - PWM-based LED brightness control -
I2C communication for color sensor integration

Hardware Used - STM32F411RE Nucleo Board (ARM Cortex-M4 @100MHz) - Front
LDR (Oncoming vehicle detection) - Top LDR (Ambient light detection) -
MQ-2 Smoke Sensor - MH-Water Rain/Moisture Sensor - TCS34725 RGB Color
Sensor (I2C-based) - LED Headlight Module - Power Supply & Basic
Prototyping Components

Technologies Used - Embedded C - STM32CubeIDE - STM32 HAL Drivers - ADC
with DMA - Timer-based PWM Control - I2C Communication (400kHz Fast
Mode) - Interrupt Handling - Finite State Machine (FSM) Architecture

Core Functionalities Implemented

1.  Multi-Sensor Data Acquisition

-   4-channel ADC using DMA
-   Periodic sampling using timer interrupts (5ms)
-   RGB color sensing every 10ms via I2C

2.  Intelligent Environment Detection The system evaluates:

-   Lux value
-   Correlated Color Temperature (CCT)
-   Smoke level
-   Moisture level
-   Ambient light intensity

Based on these parameters, it determines: - STATE_DAY - STATE_DARK -
STATE_RAINY_FOG_SMOKE - STATE_CLOUDY - STATE_STREET_LIGHT

3.  Adaptive Beam Control

-   Low Beam
-   High Beam
-   Both Beam
-   Automatic beam switching based on glare detection

4.  PWM-Based Brightness Control

-   10 kHz PWM for LED brightness
-   Dynamic duty cycle adjustment:
    -   50% (Normal)
    -   90% (Cloudy)
    -   100% (Dark / Rain / Smoke)

Working Principle 1. Sensors continuously monitor environmental
conditions. 2. ADC values are transferred using DMA to reduce CPU load.
3. RGB sensor provides lux and color temperature data via I2C. 4. A
state machine processes all inputs. 5. PWM duty cycle is updated
accordingly. 6. Headlight intensity adapts in real-time.

Key Embedded Concepts Demonstrated - Real-time embedded design -
Peripheral configuration using STM32CubeMX - DMA optimization -
Interrupt-driven architecture - I2C sensor integration - PWM motor/LED
control - Finite State Machine implementation - Automotive-inspired
adaptive system logic

Advantages - Fully automatic headlight control - Reduced glare for
oncoming vehicles - Improved visibility in adverse conditions -
Efficient and low CPU usage (DMA-based) - Scalable architecture (CAN
integration possible)

Future Improvements - CAN Bus integration for automotive networks -
Steering angle-based adaptive beam direction - Camera-based glare
detection - Machine learning-based environment classification -
Automotive-grade sensors for production deployment

Learning Outcome This project strengthened practical knowledge in: -
STM32 architecture - Peripheral-level programming - Real-time decision
making - Sensor fusion techniques - Embedded system optimization
