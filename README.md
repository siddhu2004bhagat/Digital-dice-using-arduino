# 🎲 Arduino Digital Dice

> Roll the dice, but make it ✨microcontroller-powered✨.

This is a simple Arduino project that simulates a digital dice using a push button and a 7-segment display. When the button is pressed, a random number between 1 and 6 appears on the display – no physical dice needed!

---

## 🧠 Features

- Random number generation (1–6)
- Real-time display on 7-segment
- Button-triggered roll
- Compact and breadboard-friendly
- Great for beginners and classroom demos!

---

## 🛠️ Hardware Requirements

- Arduino Uno (or any compatible board)
- 1x Common Cathode 7-Segment Display
- 1x Push Button
- 1x 10kΩ Resistor (pull-down for the button)
- Jumper wires
- Breadboard
- USB Cable + Arduino IDE

---

## ⚡ Circuit Connections

| 7-Segment Pin | Segment | Arduino Pin |
|---------------|---------|-------------|
| a             | Top     | 2           |
| b             | Top-right | 3         |
| c             | Bottom-right | 4     |
| d             | Bottom | 5           |
| e             | Bottom-left | 6      |
| f             | Top-left | 7          |
| g             | Center  | 8           |
| COM (Common Cathode) | GND | GND       |

**Button Connection:**

- One side → Pin 9  
- Other side → GND  
- Pull-down resistor (10kΩ) between Pin 9 and GND

---

## 💻 Arduino Code

> Check the `code/digital_dice.ino` file in this repo for the full source code.

Basic logic:
1. Wait for button press.
2. Generate random number using `random(1, 7)`.
3. Light up segments to match the number.
4. Repeat on next press.

---

## 📂 Folder Structure

