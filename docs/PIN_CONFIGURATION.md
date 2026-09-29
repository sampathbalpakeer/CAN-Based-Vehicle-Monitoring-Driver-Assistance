# Pin Configuration and Wiring Reference

This document is a **software-derived wiring reference** from the current source files. It is not a replacement for the original laboratory circuit schematic. Verify the physical wiring against the final hardware before submission.

## Main Node (LPC2129)

| Function | LPC2129 connection in current source |
|---|---|
| DS18B20 DQ | **P0.20** |
| LCD data D0-D7 | P0.8-P0.15 |
| LCD RS | P0.16 |
| LCD RW | P0.17 |
| LCD EN | P0.18 |
| Mode Select Switch / EINT0 | P0.1 |
| Left Indicator Switch / EINT1 | P0.3 |
| Right Indicator Switch / EINT2 | P0.7 |
| Buzzer | P0.19 |
| CAN1 RX | P0.25 |
| CAN1 TX | Dedicated CAN1 TX pin |

### DS18B20 notes

- DQ is **P0.20** in the implementation (`DQ_PIN 20`).
- The driver uses a 1-Wire bit-banged interface.
- The source comment specifies an external 4.7 kΩ pull-up from DQ to VDD.

## Fuel Node (LPC2129)

| Function | LPC2129 connection in current source |
|---|---|
| Fuel gauge wiper | P0.28 / AD0.1 / ADC channel CH1 |
| CAN1 RX | P0.25 |
| CAN1 TX | Dedicated CAN1 TX pin |

## Indicator & Reverse Alert Node (LPC2129)

| Function | LPC2129 connection in current source |
|---|---|
| Indicator LEDs | P0.0-P0.7 |
| Reverse STOP LED | P0.19 |
| Buzzer | P0.20 |
| Ultrasonic TRIG | P0.16 |
| Ultrasonic ECHO | P0.17 |
| CAN1 RX | P0.25 |
| CAN1 TX | Dedicated CAN1 TX pin |

## CAN message map

| Standard CAN ID | Sender | Receiver | Purpose |
|---|---|---|---|
| 0x100 | Fuel Node | Main Node | Fuel percentage |
| 0x200 | Main Node | Indicator & Reverse Alert Node | Vehicle mode / indicator command |
| 0x300 | Indicator & Reverse Alert Node | Main Node | Reverse distance / status |

> **Important:** The institute abstract names the ultrasonic sensor as **HC-SR05**, while the supplied source driver is named `hcsr04.c` and its comments identify **HC-SR04**. Confirm the exact sensor marking on your final hardware before publishing the repository as a final hardware record.
