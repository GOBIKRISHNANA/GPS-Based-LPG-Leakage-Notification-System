# GPS Based LPG Leakage Notification System

## Project Title

**GPS Based LPG Leakage Notification System Using ESP32, MQ-6, GPS and GSM**

---

# 1. Introduction

Liquefied Petroleum Gas (LPG) is widely used in homes, hotels, industries, and commercial kitchens. Leakage of LPG can cause fire accidents, explosions, and loss of human life. To improve safety, a GPS Based LPG Leakage Notification System is developed to detect gas leakage and immediately send alerts with location information to emergency contacts.

The system continuously monitors LPG concentration using an MQ-6 gas sensor. When leakage is detected, the ESP32 activates a buzzer and sends an SMS containing the GPS location through the GSM module.

---

# 2. Problem Statement

LPG leakage is difficult to identify at an early stage. Existing systems only provide local alarms and do not notify users remotely.

**Problems:**

* Delay in detecting gas leakage.
* Risk of fire and explosion.
* No remote notification.
* Difficulty locating the leakage area during emergencies.

---

# 3. Objectives

* Detect LPG gas leakage instantly.
* Alert nearby people using a buzzer.
* Obtain real-time location using GPS.
* Send SMS alerts through GSM.
* Improve household and industrial safety.
* Reduce accidents caused by LPG leakage.

---

# 4. System Overview

The system consists of:

1. MQ-6 Gas Sensor detects LPG leakage.
2. ESP32 processes sensor data.
3. Buzzer generates local alarm.
4. GPS module obtains latitude and longitude.
5. GSM module sends SMS alerts.
6. LCD displays system status.

When gas concentration exceeds the threshold:

* Buzzer turns ON.
* GPS fetches location.
* GSM sends alert message.
* LCD displays warning.

---

# 5. Components Required

| Component               | Quantity    |
| ----------------------- | ----------- |
| ESP32 Development Board | 1           |
| MQ-6 LPG Gas Sensor     | 1           |
| SIM800L GSM Module      | 1           |
| NEO-6M GPS Module       | 1           |
| 16x2 LCD Display (I2C)  | 1           |
| Buzzer                  | 1           |
| Jumper Wires            | As Required |
| Breadboard              | 1           |
| Power Supply            | 1           |

---

# 6. Block Diagram

```
          +-------------+
          | MQ-6 Sensor |
          +------+------+
                 |
                 v
          +-------------+
          |   ESP32     |
          +------+------+
                 |
      -------------------------
      |           |           |
      v           v           v
  Buzzer       LCD        SIM800L
                              |
                              v
                        SMS Alert

                 ^
                 |
          +-------------+
          | NEO-6M GPS  |
          +-------------+
```

---

# 7. Working Principle

### Step 1

MQ-6 sensor continuously senses LPG concentration.

### Step 2

Sensor data is sent to ESP32.

### Step 3

If gas concentration exceeds the preset threshold:

* Leakage is confirmed.

### Step 4

ESP32 activates buzzer.

### Step 5

GPS module fetches current location.

### Step 6

GSM module sends SMS:

```
ALERT!
LPG Gas Leakage Detected.

Location:
Latitude: 11.12345
Longitude: 78.12345

Immediate Action Required.
```

### Step 7

LCD displays:

```
GAS LEAKAGE
ALERT SENT
```

---

# 8. Hardware Architecture

```
           MQ-6 Sensor
                |
                v
            ESP32
         /    |    \
        /     |     \
       v      v      v
   Buzzer   LCD   SIM800L
                     |
                     v
                SMS Alert

                ^
                |
             GPS
```

---

# 9. Circuit Connections

## MQ-6 to ESP32

| MQ-6 | ESP32  |
| ---- | ------ |
| VCC  | 5V     |
| GND  | GND    |
| AO   | GPIO34 |

---

## GPS (NEO-6M) to ESP32

| GPS | ESP32  |
| --- | ------ |
| VCC | 3.3V   |
| GND | GND    |
| TX  | GPIO16 |
| RX  | GPIO17 |

---

## SIM800L to ESP32

| SIM800L | ESP32       |
| ------- | ----------- |
| VCC     | External 4V |
| GND     | GND         |
| TX      | GPIO27      |
| RX      | GPIO26      |

---

## LCD I2C to ESP32

| LCD | ESP32  |
| --- | ------ |
| VCC | 5V     |
| GND | GND    |
| SDA | GPIO21 |
| SCL | GPIO22 |

---

## Buzzer

| Buzzer   | ESP32  |
| -------- | ------ |
| Positive | GPIO25 |
| Negative | GND    |

---

# 10. Software Requirements

* Arduino IDE
* ESP32 Board Package
* TinyGPS++ Library
* LiquidCrystal_I2C Library
* SoftwareSerial Library

---

# 11. Algorithm

### Start

1. Initialize ESP32.
2. Initialize MQ-6, GPS, GSM, LCD.
3. Read gas sensor value.
4. Compare with threshold.
5. If gas level normal:

   * Display Safe.
6. If gas leakage detected:

   * Activate buzzer.
   * Read GPS location.
   * Send SMS through GSM.
   * Display alert.
7. Repeat continuously.

---

# 12. Flowchart

```
START
   |
Initialize Modules
   |
Read MQ-6 Sensor
   |
Gas > Threshold ?
   |
  No -------------------
   |                   |
Display SAFE           |
   |                   |
   ---------------------
   |
  Yes
   |
Activate Buzzer
   |
Get GPS Location
   |
Send SMS Alert
   |
Display Warning
   |
Repeat
```

---

# 13. Advantages

* Early gas leakage detection.
* Real-time location tracking.
* Remote SMS notification.
* Low cost.
* Easy installation.
* Portable design.
* Improved safety.

---

# 14. Applications

* Houses
* Hotels
* Restaurants
* LPG Storage Units
* Industries
* Laboratories
* Commercial Kitchens

---

# 15. Future Enhancements

* Mobile application integration.
* Cloud monitoring.
* Automatic gas valve shutdown.
* Fire detection integration.
* Voice call alerts.
* IoT dashboard.

---

# 16. Expected Output

### Normal Condition

```
LCD:
SYSTEM SAFE
NO GAS LEAK
```

### Leakage Condition

```
LCD:
LPG LEAKAGE
ALERT SENT
```

SMS:

```
WARNING!

LPG Gas Leakage Detected.

Latitude: 11.12345
Longitude: 78.12345

Take Immediate Action.
```

---

# 17. Conclusion

The GPS Based LPG Leakage Notification System provides a reliable and low-cost solution for detecting LPG leaks and notifying users remotely. By combining the MQ-6 gas sensor, ESP32 controller, GPS module, GSM communication, buzzer, and LCD display, the system improves safety and helps prevent accidents, property damage, and loss of life. It is suitable for both domestic and industrial environments.
