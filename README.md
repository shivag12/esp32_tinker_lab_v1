# IoT Temperature Monitoring and Alert System

## Overview

This project uses an ESP32 WROOM32 microcontroller board to read temperature and humidity data from a DHT11 sensor and control an LED. The data is then sent to the Blynk IoT platform, allowing for remote monitoring and control through the Blynk app.

## Components

### ESP32 WROOM32

The ESP32 WROOM32 is a powerful microcontroller with built-in WiFi and Bluetooth capabilities. It is commonly used in IoT projects due to its versatility and low power consumption. It features multiple GPIO pins, allowing it to interface with various sensors and actuators.

### DHT11 Sensor

The DHT11 is a basic, low-cost digital temperature and humidity sensor. It uses a capacitive humidity sensor and a thermistor to measure the surrounding air, and spits out a digital signal on the data pin (no analog input pins needed). It’s simple to use but requires careful timing to grab data.

### Pin Descriptions

- **DHT11 Sensor**
  - Data Pin: Connected to GPIO 4 on the ESP32 (DHTPIN)
- **LED**
  - LED Pin: Connected to GPIO 2 on the ESP32 (LED_PIN)

## Setup and Configuration

1. **Hardware Connections:**
   - Connect the DHT11 sensor to the ESP32:
     - VCC to 3.3V
     - GND to GND
     - Data pin to GPIO 4 (DHTPIN)
   - Connect the LED to GPIO 2 (LED_PIN) and GND.

2. **Software Requirements:**
   - Install the following libraries in the Arduino IDE:
     - `DHT` library
     - `Blynk` library
     - `WiFi` library

3. **Code Configuration:**
   - Define your Blynk credentials in the code:
     ```cpp
     #define BLYNK_TEMPLATE_ID "" // Type your Blynk template ID
     #define BLYNK_TEMPLATE_NAME "" // Type your Blynk template Name
     #define BLYNK_AUTH_TOKEN "" // Type your Blynk auth Token
     ```
   - Define your WiFi credentials:
     ```cpp
     char ssid[] = "";     // Type your WiFi name
     char pass[] = "";   // Type your WiFi password
     ```

4. **Upload the Code:**
   - Upload the provided code to your ESP32 using the Arduino IDE.

## Code Explanation

### Setup Function

- Initializes serial communication at a baud rate of 115200.
- Connects to the Blynk cloud using the provided credentials.
- Initializes the DHT11 sensor.
- Configures the LED pin as an output and ensures it is initially off.

### Loop Function

- Continuously runs the Blynk process.
- Reads temperature and humidity data from the DHT11 sensor.
- Computes the heat index.
- Sends temperature and humidity data to Blynk virtual pins V5 and V6.
- Contains placeholders for additional tasks such as pushing heat index data to the cloud and triggering events based on thresholds.

### Blynk Write Function

- Controls the LED based on the state of a button widget in the Blynk app.
- Turns the LED on or off depending on the button state.

## Tasks to Implement

1. **Push Heat Index Data to IoT Cloud**
   - Implement functionality to send the computed heat index to the Blynk IoT cloud.

2. **Trigger Events Based on Thresholds**
   - Implement functionality to trigger alerts based on temperature, humidity, or heat index thresholds. For example, if the temperature exceeds 25 degrees Celsius, raise an alert.

## Conclusion

This project demonstrates how to use the ESP32 WROOM32 microcontroller with a DHT11 sensor and Blynk platform to create an IoT-enabled environment monitoring system. By following the setup instructions and code configuration, you can monitor and control the system remotely via the Blynk app.
