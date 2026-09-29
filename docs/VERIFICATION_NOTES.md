# Final Verification Notes Before GitHub Submission

These notes identify items that should be verified against the final hardware/firmware so the GitHub repository does not contain contradictory information.

## 1. DS18B20 pin — corrected

The final implementation uses:

```c
#define DQ_PIN 20   // P0.20
```

The stale `P0.11` comments in `ds18b20.c` and `MainNode/main.c` have been corrected to **P0.20**.

## 2. Ultrasonic sensor naming — verify hardware

The institute abstract specifies **HC-SR05**. The supplied software driver is named `hcsr04.c` and contains HC-SR04 comments. This package does not silently change the driver or claim a different sensor. Verify the exact part number printed on the sensor used in the lab and make the README/circuit diagram match that hardware.

## 3. Reverse-distance output — verify final flashed firmware

One extracted demonstration frame shows a reverse display of approximately **38 cm** together with `SAFE`. The current source code defines:

- `> 100 cm` → SAFE
- `> 40 cm and <= 100 cm` → WARNING
- `<= 40 cm` → STOP

Therefore the 38 cm / SAFE frame should **not** be presented as proof of the current threshold logic until the final flashed firmware and test result are checked. If the current source is the final intended implementation, re-test the reverse thresholds and capture new screenshots for SAFE, WARNING and STOP.

## 4. Circuit diagram

The package contains a software-derived pin/wiring reference. Replace/add the final laboratory circuit schematic before final institute submission if your institute requires the actual electrical schematic.
