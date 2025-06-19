# Distance_measureAlarm

ESP32 + HC‑SR04 ultrasonic alarm: continuous MP3 playback via DFPlayer Mini when object is within 40 cm.

## ✨ Features
- Distance detection from 2 cm to ~400 cm  
- Triggers continuous playback when object is nearby  
- Stops playback when the object moves away  
- Adjustable threshold and audio track  
==========================================================================================================================
## 📋 Hardware Setup
- ESP32 Dev Board  
- HC-SR04 Ultrasonic Sensor  
- DFPlayer Mini MP3 Module  
- Micro SD card (with cat sound file)  
- Speaker  
- Jumper wires, Breadboard, Power supply
=======================================================================================================================================
## 🏁 Quick Start
1. Clone the repo  
2. Copy `0003.mp3` to `/mp3/` on the SD card  
3. Wire ESP32 + HC-SR04 + DFPlayer as described above  
4. Upload the sketch, open Serial Monitor at 115200 baud  
5. Move an object close (<25 cm) to trigger audio  
