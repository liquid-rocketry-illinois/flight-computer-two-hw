# LRI Flight Computer Two "Crystalline Echo"
KiCad PCB repository for Crystalline Echo, LRI's third avionics board, the second with active control, and the first based on the STM32 microcontroller platform. It shares much of its feature set and sensors with FC1 "Electric Angel", but brings three major improvements: the replacement of the unstable and buggy RP2350, the switch to eMMC mass storage, and the implementation of a custom 169MHz radio transceiver based on the CC112x chipset. Crystalline Echo can do many things: it can fly model rockets with active controls, act as a wireless comms link for liquid powertrain operation, or maybe someday, both at the same time.

Crystalline Echo integrates the STM32H533RE microcontroller. It is intended to be used with the STM32 HAL C/C++ framework and FreeRTOS; Arduino support for this chip is both limited and limiting. Through the HAL, hardware features for CAN FD, eMMC, and cryptography acceleration can be used.

Crystalline Echo is a 50mm x 100mm rectangle and is designed to fit longitudinally in an avionics bay. Its physical design is inspired by the TeleMega series of altimeters.

Ingredients:
* The "brain", an STmicroelectronics STM32H533RE
* Various digital sensors
    * TDK InvenSense ICM-42688-P high-accuracy 6DoF IMU
    * Bosch BMI088 6DoF IMU for backup and a higher (24 g) acceleration limit
    * STmicroelectronics LIS2MDL 3-axis magnetometer
    * TE Connectivity MS5611 barometer/altimeter
    * Sensirion SHT40 for ambient temperature and humidity
    * u-blox MAX-M10S GNSS receiver and a u.FL antenna connector
* A 169MHz GFSK radio transceiver IC (Texas Instruments CC1125) and a u.FL antenna connector
* A 32GB eMMC chip for even more vibration-resistant datalogging
* A piezo buzzer for providing auditory feedback
* An STDC14 connector for programming the main MCU
* A USB Type-C 2.0 port for device enumeration use cases (CDC data streaming, mass storage, etc)
* A power monitor IC
* A power mux for utilizing battery (2S or 3S lithium packs supported) or USB power
* A 3.3V-output buck converter
