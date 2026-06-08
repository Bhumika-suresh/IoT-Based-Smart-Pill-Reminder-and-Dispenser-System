# Smart Pill Reminder and Dispenser System

## Overview

The Smart Pill Reminder and Dispenser System is an IoT-based healthcare solution designed to help users manage their medication schedules effectively. The system automatically reminds users to take medicines, dispenses the correct pill at the scheduled time, and confirms medicine intake using a motion sensor.

This project is especially useful for elderly individuals, patients with memory disorders, visually impaired users, and people following complex medication schedules.

---

## Features

- Automated medication reminders
- RTC-based accurate scheduling
- Automatic pill dispensing using a servo motor
- Audio alerts using a buzzer
- Visual alerts using LED indicators
- Motion-based confirmation of medicine intake
- Logging of medication status (Taken/Missed)
- Affordable and user-friendly design
- Future support for IoT-based remote monitoring

---

## Problem Statement

Many patients forget to take their medication on time, leading to health complications. Traditional pillboxes and reminder applications only notify users and cannot verify whether medication was actually taken.

This project solves these problems by combining automated reminders, pill dispensing, and medicine intake confirmation in a single smart system.

---

## System Workflow

1. User sets medication schedules.
2. RTC module continuously monitors time.
3. At the scheduled time:
   - Buzzer sounds.
   - LED indicator turns ON.
   - Servo motor dispenses the medicine.
4. PIR sensor detects hand movement.
5. If motion is detected:
   - Medicine marked as **Taken**.
   - Alarm stops.
6. If motion is not detected:
   - Medicine marked as **Missed**.
   - Event is logged.

---

## Required Hardware Components

| Component | Purpose |
|------------|----------|
| Arduino UNO | Main controller |
| RTC DS3231 | Time tracking |
| PIR Motion Sensor | Detects hand movement |
| Servo Motor SG90 | Pill dispensing |
| Buzzer | Audio alert |
| LED Indicator | Visual alert |
| Push Button | Stop reminder |
| Pill Container | Stores medicines |
| Jumper Wires | Connections |
| Power Supply | Powers the system |

---

## Software Requirements

- Arduino IDE
- RTClib Library
- Servo Library
- Blynk IoT Platform (Future Enhancement)

---
## System architecture

<img width="1337" height="1458" alt="PILL 3" src="https://github.com/user-attachments/assets/e4db1b95-9e9d-4dc1-992c-e7401228e01b" />

---

## Circuit Diagram

<img width="1092" height="708" alt="PILL 4" src="https://github.com/user-attachments/assets/c777dc4c-24f9-4e3c-844f-d0c64cdefd73" />

---

## Circuit Connections

### RTC DS3231
- VCC → 5V
- GND → GND
- SDA → A4
- SCL → A5

### Servo Motor
- Signal → Pin 9
- VCC → 5V
- GND → GND

### Buzzer
- Positive → Pin 8
- Negative → GND

### LED
- Positive → Pin 10
- Negative → GND through resistor

### PIR Sensor
- OUT → Pin 5
- VCC → 5V
- GND → GND

### Push Button
- One terminal → Pin 7
- Other terminal → GND

---

## Installation

1. Install Arduino IDE.
2. Install required libraries:
   - RTClib
   - Servo
3. Connect hardware components.
4. Upload the Arduino code.
5. Configure RTC time.
6. Power ON the system.

---

## Working Principle

### Schedule Monitoring
The RTC module continuously compares the current time with predefined medication schedules.

### Reminder Activation
When the scheduled time arrives:
- Buzzer turns ON.
- LED glows.
- Servo motor dispenses medicine.

### Intake Confirmation
The PIR sensor detects user hand movement near the dispenser.

### Logging
- Motion detected → Medicine Taken
- Motion not detected → Medicine Missed

---

## Project Output

- Timely medication reminders
- Automatic pill dispensing
- Confirmation of medicine intake
- Logging of medication history
- Improved medication adherence

---

## Advantages

- Reduces missed doses
- Improves patient safety
- Cost-effective solution
- Easy to use
- Supports elderly and disabled users

---

## Future Enhancements

### IoT Integration
- Mobile application support
- Cloud-based monitoring

### Caregiver Notifications
- SMS alerts
- Push notifications

### Voice Assistance
- Audio announcements for medicines

### Smart Refill Alerts
- Low medicine stock detection

### AI-Based Scheduling
- Adaptive reminder timings

### Emergency Alerts
- Notifications for repeated missed doses

---

## Snapshort of working model

<img width="1600" height="1195" alt="PILL 2" src="https://github.com/user-attachments/assets/927f1350-6eb9-40a4-a979-566edd730d33" />

<img width="2252" height="2872" alt="PILL 1" src="https://github.com/user-attachments/assets/89f874d9-cf7b-4886-9224-7be2a5e2832b" />

## Video of working model
https://drive.google.com/file/d/1Gt5I5QhMVUiwumFShYgZ5iaJtmMIFOOB/view?usp=sharing

## Snapshort of implementation
 
 <img width="455" height="230" alt="image" src="https://github.com/user-attachments/assets/82424cf8-c0fa-4b35-9a5f-84c65b72d1ca" />
 <img width="452" height="268" alt="image" src="https://github.com/user-attachments/assets/f5e5b758-98a2-4f76-8286-31430562c44b" />
 <img width="452" height="275" alt="image" src="https://github.com/user-attachments/assets/245bcd1f-ca91-4397-9c43-4fcb8b134c91" />
 <img width="453" height="278" alt="image" src="https://github.com/user-attachments/assets/899ab36d-c949-4c18-ac16-f7f7c644ad07" />


---

## Conclusion

The Smart Pill Reminder and Dispenser System provides an efficient, automated, and affordable solution for medication management. By integrating automated reminders, pill dispensing, and motion-based confirmation, the system improves medication adherence and helps users maintain better health outcomes.

---
