# 💧 Purification of Drinking Water using Pulsed Electric Field (PEF)

> A pre-final-year Electrical & Electronics Engineering (EEE) project designed to **purify water without chemicals** using **high-voltage electric pulses**, powered by **Arduino**.

---

## 🖼️ Live Project Setup



<p align="center">
  <img src="https://github.com/user-attachments/assets/5d081c75-95c3-45c6-9313-a18a915edb18" width="500" alt="PEF Water Purification Setup"/>
</p>


---

## 📄 Project Overview

This project demonstrates a **Pulsed Electric Field (PEF)** system for **chemical-free water purification**. Instead of boiling or chlorination, we use **short high-voltage pulses** to disrupt microbial cell membranes — making the water safe to drink.

⚡ Technology Stack:
- High-voltage pulse generation (Boost Converter + Voltage Multiplier)
- IGBT/MOSFET controlled switching
- Arduino Uno for automation
- MATLAB simulation & hardware prototype

---

## 🧪 Key Features

- ✅ Kills bacteria using **irreversible electroporation**
- ⚡ Generates ~3kV pulses using DC-DC boost and CDVM
- 🔄 Arduino controls timing and pulse duration
- 🔋 Runs on 12V adapter or 9V battery
- 🧠 Energy-efficient, modular, and IoT-ready

---

## 📚 Table of Contents

- [📄 Project Report (PDF)](./docs/PEF_Water_Purification_Project_Report.pdf)
- [🛠️ Circuit Design](#-hardware-schematic)
- [🔍 Working Principle](#-working-principle)
- [📷 Hardware Image](#-live-project-setup)
- [💻 Arduino Code](#-arduino-code)
- [🧪 Results & Output](#-results--discussion)
- [🚀 Future Scope](#-future-improvements)

---

## ⚙️ Hardware Schematic

Main Components:
- Arduino Uno
- IRF540N N-Channel MOSFET
- DC-DC Boost Converter
- Capacitor-Diode Voltage Multiplier
- Water Pump (12V)
- Relay Module
- High-voltage electrodes
- LEDs, resistors, jumpers

---

## 🔬 Working Principle

1. Boost converter increases low DC voltage to ~400V.
2. Voltage multiplier amplifies it to ~3kV.
3. Arduino sends pulses to switch the high voltage via MOSFET.
4. Pulses pass through water using electrodes, disrupting bacteria membranes.
5. Relay turns on water pump to transfer purified water.

---

## 💻 Arduino Code (Simplified)
```cpp
#define pulsePin 8
#define pumpPin 3
#define redLED 6
#define greenLED 5

void setup() {
  pinMode(pulsePin, OUTPUT);
  pinMode(pumpPin, OUTPUT);
  pinMode(redLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
}

void loop() {
  digitalWrite(redLED, HIGH);
  for (unsigned long t = millis(); millis() - t < 10000;) {
    digitalWrite(pulsePin, HIGH);
    delayMicroseconds(20);
    digitalWrite(pulsePin, LOW);
    delay(1);
  }
  digitalWrite(redLED, LOW);
  
  digitalWrite(greenLED, HIGH);
  digitalWrite(pumpPin, HIGH);
  delay(10000);
  digitalWrite(pumpPin, LOW);
  digitalWrite(greenLED, LOW);
  
  while (true); // Stops here
}
