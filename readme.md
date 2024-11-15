

# RFID-Based Intruder Alert and Access Control System  (SECURITY LIGHTING SYSTEM)

## Overview  
This project is an **RFID-Based Intruder Alert and Access Control System** designed to:  
- Grant access to authorized users via RFID tags.  
- Detect and alert on unauthorized access attempts.  
- Activate a buzzer and flashing LED in case of intruder alerts.  
- Use a servo motor to control the opening and closing of a door.  
- Send alerts to a Python script to capture pictures of intruders using a connected camera.  

The system also provides a gradual servo motor operation for smoother movement of the door.  

---

## Features  
- **RFID Access Control**: Grants access to authorized RFID tags while denying others.  
- **Intruder Detection**: Detects unauthorized access using an IR sensor and RFID scanning.  
- **Intruder Alert**: Activates a buzzer with a "cop car" siren pattern and flashing LED for unauthorized access.  
- **Camera Integration**: Sends alerts to a Python script to capture images of the intruder.  
- **Smooth Servo Motion**: Gradual movement of the servo motor for realistic door operation.  

---

## Hardware Components  
1. **Arduino Uno**  
2. **RFID Reader (MFRC522)**  
3. **IR Sensor**  
4. **Servo Motor**  
5. **HW487 LED Module**  
   - Red, Green, and Blue LEDs  
6. **Buzzer**  
7. **Breadboard and Jumper Wires**  

---

## Circuit Diagram  
The circuit includes:  
- **RFID Reader** connected to SPI pins.  
- **Servo Motor** attached to pin `7`.  
- **Buzzer and LEDs** connected to digital pins for visual and sound alerts.  
- **IR Sensor** connected to pin `2` for motion detection.  

---

## Software Components  
1. **Arduino IDE**  
   - Libraries:  
     - `MFRC522` for RFID functionality.  
     - `Servo` for servo motor control.  
2. **Python Script**  
   - Receives Serial alerts for intruders.  
   - Captures pictures using a connected camera (e.g., OpenCV).  

---

## How It Works  
### Authorized Access  
1. An RFID tag is scanned.  
2. If the tag matches the authorized UID, the door opens for 5 seconds.  
3. A green LED indicates access approval.  

### Unauthorized Access  
1. If an unauthorized RFID tag is scanned or the IR sensor detects motion:  
   - A buzzer and a flashing blue LED are activated.  
   - An alert is sent to a Python script to capture the intruder's picture.  

### Door Operation  
The servo motor operates gradually for smooth opening and closing.  

---

## Installation  
### Arduino Code  
1. Install the required libraries:  
   - `MFRC522`  
   - `Servo`  
2. Upload the provided Arduino sketch to the Arduino Uno.  

### Python Script  
1. Install the required Python libraries:  
   ```bash  
   pip install pyserial opencv-python  
   ```  
2. Connect your camera to the system.  

---

## How to Run the Python Script  
1. Save the Python script (e.g., `camera.py`) to your computer.  
2. Open a terminal or command prompt.  
3. Run the script by providing the appropriate serial port for your Arduino:  
   ```bash  
   python intruder_alert.py COM3  
   ```  
   Replace `COM5` with the correct serial port of your Arduino (use the Arduino IDE to check this).  
4. The script will:  
   - Continuously listen for "Intruder detected!" messages from the Arduino.  
   - Capture and save images using the connected camera when an alert is received.  

---

## Usage  
1. Power up the system.  
2. Scan an RFID tag:  
   - **Authorized**: Green LED lights up, and the door opens.  
   - **Unauthorized**: Blue LED flashes, the buzzer sounds, and the camera takes a picture.  
3. Observe Serial Monitor for logs.  
4. Run the Python script to capture intruder images.  

---

## Troubleshooting  
- Ensure RFID reader connections are correct.  
- Verify the authorized UID in the Arduino code matches your RFID tag.  
- Check Serial communication for Python integration.  
- If the servo motor doesn’t move smoothly, adjust the delay in the `slowMoveServo` function.  
- If the Python script fails to capture images, ensure the camera is correctly connected and accessible.  

---

## Future Improvements  
- Integrate a database for managing multiple authorized RFID tags.  
- Implement wireless alerts (e.g., via Wi-Fi or Bluetooth).  
- Add a timestamp to captured images.  

---

