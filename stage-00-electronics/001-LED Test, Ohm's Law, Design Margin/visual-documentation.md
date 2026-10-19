# EXP-001 — Visual Documentation

**Project:** Pneumatic Robotics 
**Experiment:** Arduino Leonardo Verification & LED Blink  
**Date:** 19 October 2026  
**Stage:** 00 — Electronics Fundamentals

**Keywords:** Ohm's Law, Design Margin, Digital Output, LED Current Limiting
---

## 1. Circuit Setup

Physical wiring of the Arduino Leonardo, 220 Ω resistor and 5 mm red LED.

<img width="987" height="1120" alt="visual" src="https://github.com/user-attachments/assets/f2767777-2e51-4309-8c5c-3a141053e51a" />

Circuit：
<img width="978" height="804" alt="circut" src="https://github.com/user-attachments/assets/d0805331-5ea9-4b8a-8960-59a65e501eb1" />

**Connection:** D13 → 220 Ω Resistor → Red LED → GND

## 2. Experiment in Motion

The LED blinks continuously, staying on for 1 second and off for 0.5 seconds.

The Arduino successfully controlled the LED through digital output pin D13.

## 3. Handwritten Notes & Calculations

Documentation of the resistor selection process using Ohm's Law.

<img width="522" height="809" alt="notes" src="https://github.com/user-attachments/assets/71551c2d-53fd-44d2-80a0-579d831ae67c" />

**Key Learning:** A 220 Ω resistor was selected instead of 150 Ω to reduce the expected LED current while maintaining sufficient brightness. According to the Design Margin
