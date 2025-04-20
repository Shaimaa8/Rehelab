# RehabLab - Wearable Rehabilitation Tracker

## Overview
RehabLab is an innovative wearable solution designed to track and analyze movements during rehabilitation or training activities. It utilizes 3D gyroscope technology to accurately measure limb and joint angles, providing real-time feedback and progress tracking to ensure correct form and reduce injury risk.

## Key Features
- **Precise Angle Measurement**: Tracks joint movements with high accuracy using gyroscopic sensors
- **Real-time Feedback**: Alerts users when movements deviate from prescribed ranges
- **Progress Tracking**: Logs and visualizes rehabilitation progress over time
- **Customizable Exercises**: Supports personalized rehabilitation programs
- **Cloud Integration**: Stores data securely in Firebase for remote monitoring
- **Portable Design**: Compact Arduino-based module that fits in a pocket

## Hardware Components
- ESP8266 WiFi module for connectivity
- MPU-6050 6-axis gyroscope/accelerometer
- Arduino-compatible microcontroller
- LCD display (I2C interface)

## Software Components
- Firebase Realtime Database for cloud storage
- NTP client for accurate timestamping
- Serial communication between devices
- Data visualization dashboard (future implementation)

## Installation & Setup

### Prerequisites
- Arduino IDE (v1.8.19 or later)
- ESP8266 board support package
- Required libraries:
  - FirebaseESP8266
  - NTPClient
  - WiFiUDP
  - Wire
  - LiquidCrystal_I2C

### Hardware Connections
1. Connect the MPU-6050 gyroscope to the Arduino via I2C (SDA/SCL)
2. Connect the ESP8266 module for WiFi connectivity
3. Connect the LCD display via I2C (address 0x27)

### Configuration
1. Update WiFi credentials in `ESP_.ino`:
   ```cpp
   #define WIFI_SSID "your_SSID"
   #define WIFI_PASSWORD "your_password"
   ```

2. Configure Firebase settings:
   ```cpp
   #define FIREBASE_HOST "your_firebase_url"
   #define FIREBASE_AUTH "your_firebase_auth_token"
   ```

3. Set your UTC offset for accurate timekeeping:
   ```cpp
   const long utcOffsetInSeconds = 7200; // Adjust for your timezone
   ```

## Usage
1. Power on the device
2. The system will automatically:
   - Connect to WiFi
   - Synchronize with NTP time server
   - Initialize the gyroscope sensors
3. Perform calibration movements when prompted
4. Begin your rehabilitation exercises
5. View real-time angle data on the LCD display
6. Data is automatically uploaded to Firebase for progress tracking

## Data Structure
The Firebase database is organized by date and time:
```
/DD-MM-YYYY/HH:MM:SS/
  - roll: [value]
  - pitch: [value]
  - yaw: [value]
```

## Troubleshooting
- **WiFi Connection Issues**: Ensure correct credentials and strong signal
- **Firebase Errors**: Verify authentication token and database rules
- **Sensor Inaccuracies**: Perform recalibration routine
- **Serial Communication**: Check baud rate (115200) and physical connections

## Future Enhancements
- Mobile app integration for enhanced visualization
- Gamification elements to improve user engagement
- Multi-language support
- AI-based movement prediction and correction suggestions

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
Special thanks to Dr. Riham Rasheed for guidance and support in developing this rehabilitation solution.
