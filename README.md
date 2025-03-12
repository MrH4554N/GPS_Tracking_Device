# GPS Tracking Device  

## Overview  
This project is a **GPS tracking device** designed for high-value equipment monitoring. It continuously tracks the location of assets and transmits position data to a remote server. The device is designed for **low power consumption**, allowing it to operate for **2-3 months** on two **18650 3500mAh rechargeable batteries**.  

## Features  
- **Real-time GPS Tracking** – Uses the **Waveshare LC76G GPS module** to determine location with large distance.
- **ESP32 Bluetooth** - Uses the Bluetooth to  determine location with small distance.
- **Data Transmission** – Utilizes the **A7680 module** for communication to server.  
- **Power Efficiency** – Operates in low-power mode and wakes up only when movement is detected.  
- **Motion Detection** – **MPU6050** detects tilt, triggering the device to wake up and operate.  
- **ESP32-based** – Handles processing, communication, and power management.  

## Hardware Components  
| Component       | Description |
|----------------|------------|
| **ESP32**      | For processing, communication and tracking location |
| **A7680**      | For remote data transmission |
| **LC76G GPS**  | For location tracking |
| **MPU6050**    | For motion detection |
| **18650 Battery (x2)** | Powersource for devices |

## System Architecture  
1. **Normal Mode**: If there is no trigger signal from **MPU6050**, the device remains in low-power mode and only send data once every 11h about battery capacity. 
2. **Wake-Up Trigger**: If **MPU6050** detects movement, the **ESP32** wakes up and perform operations. It will receive location data and then send this data along with battery capacity to server. 
3. **Return to Sleep Mode**: If the device is stop in a place for at least 5 minute without trigger from **MPU6050**, the device will go back to **Normal mode**.  
