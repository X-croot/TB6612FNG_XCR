# TB6612FNG-XCR

An **advanced Arduino motor driver library** for the **TB6612FNG** dual H-Bridge module, designed with robotics in mind.

---
<img width="474" height="474" alt="resim" src="https://github.com/user-attachments/assets/e95805ed-e5d3-499c-ba24-f7f5ab32134b" />

## 🚀 Features

* **Simple servo-style API** (like `write(speed)`)
* **Sumo mode** for dual motor coordination
* **Manual mode** for direct low-level pin control
* **Support for motor inversion** (e.g., if wired backwards)
* **Standby pin control** (STBY)
* **Adjustable min/max PWM speed**
* **Debug output option** via Serial

---

## 🤖 Perfect For

* Mini sumo robots
* Line follower robots
* Arduino-based mobile platforms
* Any dual DC motor project with TB6612FNG

---
<img width="405" height="338" alt="resim" src="https://github.com/user-attachments/assets/66654356-7125-45c8-bd78-759301f629bf" />

## 📦 Installation

1. Download the ZIP from [GitHub](https://github.com/X-croot/TB6612FNG-XCR)
2. Open Arduino IDE
3. Go to **Sketch > Include Library > Add .ZIP Library...**

---

## 🧠 Basic Usage

```cpp
#include "TB6612FNG_XCR.h"

TB6612FNG_XCR leftMotor;
TB6612FNG_XCR rightMotor;

void setup() {
  leftMotor.attach(5, A1, A2, "Left");
  rightMotor.attach(6, A3, A4, "Right");

  leftMotor.setStandbyPin(7);
  rightMotor.setStandbyPin(7);

  rightMotor.invert(true);

  leftMotor.enableSumoMode(&leftMotor, &rightMotor);
  rightMotor.enableSumoMode(&leftMotor, &rightMotor);

  leftMotor.sumoControl(255, 255); // Move forward
}
```

---

## ⚙️ Motor Driver Pinout (TB6612FNG)

Here is how to connect the TB6612FNG motor driver to Arduino:

| TB6612FNG Pin | Description     | Connect to Arduino             |
| ------------- | --------------- | ------------------------------ |
| AIN1          | Motor A input 1 | Digital Pin (e.g., A1)         |
| AIN2          | Motor A input 2 | Digital Pin (e.g., A2)         |
| PWMA          | Motor A PWM     | PWM Pin (e.g., 5)              |
| BIN1          | Motor B input 1 | Digital Pin (e.g., A3)         |
| BIN2          | Motor B input 2 | Digital Pin (e.g., A4)         |
| PWMB          | Motor B PWM     | PWM Pin (e.g., 6)              |
| STBY          | Standby control | Digital Pin (e.g., 7)          |
| VCC           | Motor voltage   | +5V or motor power supply      |
| GND           | Ground          | GND                            |
| VM            | Motor power     | External 6–12V (e.g., battery) |

Ensure STBY is connected and set HIGH in code using `setStandbyPin(pin)`.

---

## 🧰 Methods Overview

### Setup

* `attach(enPin, in1Pin, in2Pin, name)`
* `setStandbyPin(pin)`
* `invert(bool)`

### Movement

* `write(speed)`
* `stop()`
* `brake()`
* `read()`

### Limits

* `setMaxSpeed(pwm)`
* `setMinSpeed(pwm)`

### Manual Control

* `manual(in1, in2, pwm, duration)`

### Sumo Mode

* `enableSumoMode(&left, &right)`
* `disableSumoMode()`
* `sumoControl(leftSpeed, rightSpeed)`

### Debug

* `debugOn()` / `debugOff()`

---

## 🧪 Examples

* `/examples/LineFollower`
* `/examples/MiniSumo`

---

## 🛠️ Hardware Requirements

* TB6612FNG dual motor driver module
* 2x DC motors
* Arduino (Uno, Nano, Mega, etc.)
* STBY pin connection (optional but recommended)

---

