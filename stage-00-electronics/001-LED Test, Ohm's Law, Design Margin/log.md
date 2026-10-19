# EXP-001 — Arduino Leonardo Verification & LED Blink

**Date:** 19 October 2026  
**Stage:** 00 — Electronics Fundamentals  
**Board:** Arduino Leonardo  
**Status:** Completed — Successful  
**Keywords:** Ohm's Law, Design Margin, LED Current Limiting, Digital Output, Arduino

---

## 1. Objective

To verify that my Arduino Leonardo was still functional after a long period of inactivity by building and testing a simple LED blinking circuit.

This experiment also served as a refresher on Ohm's Law, current-limiting resistor calculations, digital output control and basic electronic component selection.

## 2. Components & Circuit

| Component | Specification |
|---|---|
| Microcontroller | Arduino Leonardo |
| Digital Output Pin | D13 |
| LED | 5 mm Red LED |
| Forward Voltage (Vf) | 2.0–2.2 V |
| Rated Forward Current (If) | 20 mA |
| Resistor | 220 Ω |
| Ground | Arduino GND |

**Circuit connection:**

`D13 → 220 Ω Resistor → LED Anode (+) → LED Cathode (−) → GND`

When D13 is HIGH, current flows through the resistor and LED, causing the LED to illuminate. When D13 is LOW, the LED turns off.

## 3. Theory — Ohm's Law

Ohm's Law describes the relationship between voltage, current and resistance:

**V = IR**

Where:

- **V — Voltage (V):** Electrical potential difference.
- **I — Current (A):** Rate of electric charge flow.
- **R — Resistance (Ω):** Opposition to electrical current.

For the LED circuit, the required current-limiting resistance can be estimated using:

**R = (Vs − Vf) / I**

Where:

- **Vs — Supply Voltage:** Approximately 5 V (D13 HIGH output)
- **Vf — Forward Voltage:** 2.0–2.2 V
- **I — Target LED Current:** Selected according to the circuit requirements

A current-limiting resistor is necessary to prevent excessive current flowing through the LED.

## 4. Resistor Calculation & Selection

The LED has a rated forward current of 20 mA, but it does not need to operate at this current to produce visible light.

Assuming a 5 V output and a nominal forward voltage of 2.0 V:

| Resistor | Calculation | Estimated Current |
|---|---|---|
| 150 Ω | R = (5 − 2) / 0.02 = 150 Ω | 20.0 mA |
| **220 Ω** | I = (5 − 2) / 220 | **13.6 mA** |
| 330 Ω | I = (5 − 2) / 330 | 9.1 mA |

### Why 220 Ω?

Only 150 Ω and 220 Ω resistors were available during the experiment.

Although 150 Ω was calculated using the LED's rated current of 20 mA, I chose 220 Ω to reduce the operating current.

The estimated current with a 220 Ω resistor is approximately 12.7–13.6 mA, considering the LED's forward-voltage range of 2.0–2.2 V.

A 330 Ω resistor would have been a more conservative choice, but 220 Ω was sufficient for the purpose of this test.

## 5. Engineering Principle — Design Margin

An important concept introduced in this experiment is **Design Margin**.

Electronic components do not necessarily need to operate continuously at their rated limits.

As long as the circuit meets its functional requirements, choosing a lower operating current can reduce power consumption and provide additional margin relative to component ratings.

In this experiment:

- **150 Ω:** Approximately 20 mA, corresponding to the LED's rated current under the assumed conditions.
- **220 Ω:** Approximately 13.6 mA, providing a lower-current operating point.
- **330 Ω:** Approximately 9.1 mA, offering additional current margin.

Although 330 Ω would be preferable for a conservative LED test, the available 220 Ω resistor was also suitable.

This demonstrated that component selection involves more than calculating a nominal resistance. It requires balancing circuit requirements, component availability and design margin.

## 6. Arduino Code & Digital Output

Source file: [led_test.ino](./led_test.ino)

The program configures digital pin D13 as an output using `pinMode()`.

Inside the `loop()` function, the LED is switched on and off using `digitalWrite()` and `delay()`.

| State | Command | Duration |
|---|---|---|
| LED ON | `digitalWrite(LED, HIGH)` | 1000 ms |
| LED OFF | `digitalWrite(LED, LOW)` | 500 ms |

**Total cycle:** 1500 ms (1.5 seconds)  
**ON duty cycle:** Approximately 66.7%

## 7. Results & Observations

**Result: Successful**

The Arduino Leonardo successfully executed the uploaded sketch.

The external red LED blinked at the programmed intervals:

- ON for approximately 1 second.
- OFF for approximately 0.5 seconds.
- Repeated continuously.

This confirmed that the Arduino Leonardo was able to execute the uploaded program and control the D13 digital output.

The 220 Ω current-limiting resistor provided sufficient current for the LED to illuminate visibly.

The LED current was estimated theoretically rather than measured directly.

## 8. Reflection

This experiment refreshed my understanding of Ohm's Law and how it can be applied to practical electronic circuits.

The key learning outcome was recognising that component selection is not simply about calculating a resistor value based on a component's rated current.

**Engineering decisions also involve considering functionality, available components and design margin.**

Although a 150 Ω resistor matched the calculation based on the LED's rated current, selecting 220 Ω reduced the expected current while still meeting the objective of the experiment.

A 330 Ω resistor would provide additional margin, but was not necessary for this initial verification test.

This approach to component selection will be important in future experiments involving MOSFETs, pneumatic pumps, solenoid valves and power management.

## 9. Next Steps

- Document the circuit with a photograph or schematic.
- Explore digital input and output control.
- Investigate MOSFET switching for higher-current loads.
- Progress towards Arduino-controlled pneumatic actuation.

---

**Key Concepts:** Ohm's Law · Design Margin · Current Limiting · Digital Output · LED Forward Voltage
