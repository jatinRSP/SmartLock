# License and Author

This project is open-source; modify and use it freely.

Developed by jatinRSP

# Smart Door Lock System

This project demonstrates an RFID-based smart lock system using an Arduino UNO, MFRC522 RFID reader, LEDs, a solenoid lock controlled by a relay, and a buzzer. The system checks an RFID card's UID to grant or deny access. Authorized cards activate the solenoid lock, while unauthorized cards trigger a buzzer and a red LED.

## Components

- **Arduino UNO**
- **MFRC522 RFID Reader**
- **Green LED** - Indicates access granted
- **Red LED** - Indicates access denied
- **Solenoid Lock** - Unlocks on authorized access
- **Relay Module** - Controls the solenoid lock
- **Buzzer** - Sounds on access denial

## Wiring Connections

### RFID MFRC522 Module to Arduino UNO

| RFID Pin | Arduino UNO Pin | Description         |
|----------|------------------|---------------------|
| SDA      | Pin 10          | Chip select (SS)    |
| SCK      | Pin 13          | Serial clock        |
| MOSI     | Pin 11          | Master out, slave in|
| MISO     | Pin 12          | Master in, slave out|
| GND      | GND             | Ground              |
| RST      | Pin 9           | Reset               |
| 3.3V     | 3.3V            | Power supply        |

### Additional Components

| Component     | Arduino UNO Pin | Description               |
|---------------|-----------------|---------------------------|
| Green LED     | Pin 5           | Access Granted Indicator  |
| Red LED       | Pin 4           | Access Denied Indicator   |
| Relay (Solenoid Lock) | Pin 3    | Controls Solenoid Lock    |
| Buzzer        | Pin 2           | Sounds on Access Denial   |

> **Note**: Make sure the MFRC522 module is connected to the 3.3V pin of the Arduino UNO to avoid damage.

## Library Installation

Install the **MFRC522** library for RFID functionality:

1. Open Arduino IDE.
2. Go to **Sketch > Include Library > Manage Libraries**.
3. Search for **MFRC522** and install it.

## Usage

1. **Upload the Code**: Load the Arduino code onto your UNO.
2. **Place RFID Card**: Present an RFID card to the reader.
   - **Authorized Card**: Activates the relay, unlocking the solenoid lock and lighting the green LED.
   - **Unauthorized Card**: Triggers the red LED and buzzer to signal access denial.

## Troubleshooting

### 1. RFID Reader Not Detecting Card
   - Verify connections to the MFRC522 module.
   - Ensure the RFID card is close to the reader.

### 2. Compilation Errors with MFRC522 Library

If you see errors like:

ordered comparison of pointer with integer zero

Resolve this by:
- Updating the **MFRC522** library via Arduino Library Manager.
- Alternatively, modify `MFRC522Extended.cpp` within the library folder:
  ```cpp
  if (backData && backLen && (*backLen > 0)) {
