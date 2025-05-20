# Magic Wand Gesture Recognition System

This project implements a gesture recognition system using an **ESP32** microcontroller and the **MPU6050** accelerometer. The system enables real-time gesture recognition for controlling magic spells, with each gesture representing a different spell in the game. The recognition model is built using **Edge Impulse** and optimized for embedded devices.

  
## Introduction
This system captures gesture data using the **MPU6050** sensor, processes it with a machine learning model in **Edge Impulse**, and deploys it to the **ESP32** for real-time gesture recognition. The wand can recognize gestures associated with spells such as Fire Bolt, Reflect Shield, and Healing Spell.

## Hardware Requirements
- **ESP32 Development Board**
- **MPU6050 IMU Sensor**
- **LED** (for visual feedback of gestures)
- **Wires** (for connections)
- **PCB** (for prototyping)
- **Battery** (for mobile power)
- **Enclosure** (for assembling the wand)

### Hardware Connections
Connect the MPU6050 sensor to the ESP32 as follows:
- **VCC** → 3.3V
- **GND** → GND
- **SDA** → GPIO4
- **SCL** → GPIO5

## Software Requirements
- **Arduino IDE** with **ESP32** board support
- **Edge Impulse SDK** (for inference)
- **Python 3.8r**

## Getting Started

### 1. Data Collection
- Set up your hardware and connect the **MPU6050** sensor to the **ESP32** as described in the **Hardware Connections** section.
- Use the provided `gesture_capture.ino` Arduino sketch and `process_gesture_data.py` Python script to capture gesture data.
- Collect data for gestures associated with different spells:
  - **Fire Bolt** (Gesture "Z")
  - **Reflect Shield** (Gesture "O")
  - **Healing Spell** (Gesture "V")
- Ensure you collect at least 20 samples for each gesture. The collected data will be stored in the `data/` directory.

### 2. Model Development in Edge Impulse
- Create a new project in **Edge Impulse** and upload your collected gesture data.
- In the **Impulse Design** tab, create a new impulse and select appropriate **DSP blocks** for feature extraction (e.g., time-domain features, FFT) and **ML blocks** (e.g., neural network) for training the model.
- Experiment with different parameters like window size and stride for feature extraction, and tune hyperparameters (e.g., learning rate, epochs) for optimal performance.
- Test and validate your model using the **Live classification** feature in Edge Impulse.
- Once satisfied with the model, download the quantized version for deployment on the **ESP32**.

### 3. ESP32 Implementation
- Deploy the trained model to the **ESP32** using the **Edge Impulse SDK**.
- Upload the `wand_inference.ino` sketch to the **ESP32**.
- Test the real-time gesture recognition by sending a trigger signal (e.g., pressing a button or using serial communication).
- Modify the code to trigger gesture recognition when a button is pressed instead of serial input. This improves the user experience for real-time interaction.

### 4. Battery and Enclosure
- Power the **ESP32** using a battery instead of USB for portability.
- Design and 3D-print or source an enclosure that fits the **ESP32**, **MPU6050**, battery, and wires neatly. Ensure that the enclosure is stable, durable, and easy to handle.
- Include mounting holes or methods to secure the components in place within the enclosure.
