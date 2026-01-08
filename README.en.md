# Introduction
An attempt to repair a Sigma AF‑Kappa lens with a Sony A‑Mount by replacing the faulty ASIC with an ATtiny microcontroller.
The implementation is not fully compatible with the protocol observed from the lens due to limitations in the reverse‑engineering process.
However, this approach restores the lens from a total failure to a usable condition.
The data frame used in the source code comes from a lens with parameters similar to the Sigma AF‑Kappa and is not a perfect match.

# Implementation
The program was tested using an ATtiny24A (the microcontroller should be small and provide at least 7 GPIO pins).
The microcontroller must be programmed and mounted in place of the removed ASIC, with pads insulated.
Connect the lens push-pull barrel contact traces and bayonet pins to the ATtiny24A as follows:
```
ATTINY24A       - SIGMA
- Pin 14 (VCC)  - 5V (Bayonet)
- Pin 13 (PA0)  - Contact trace "0"
- Pin 12 (PA1)  - Contact trace "1"
- Pin 11 (PA2)  - Contact trace "2"
- Pin 10 (PA3)  - Contact trace "3"
- Pin 9  (SCK)  - CLK  (Bayonet)
- Pin 8  (MISO) - MOSI (Bayonet)
- Pin 5  (INT0) - SS   (Bayonet)
- Pin 4  (RST)  - via 10k resistor to 5V
- Pin 1  (GND)  - Ground
```
Measure the barrel contact traces with a continuity tester to ensure the microcontroller pins are connected to the correctly numbered traces.
Example photo of an ATtiny24A installation:
![Photo](circuitry.png)

# Build
The code was written for avr‑gcc but can also be built in the Arduino IDE. You can use [SpenceKonde/ATTinyCore](https://github.com/SpenceKonde/ATTinyCore).
