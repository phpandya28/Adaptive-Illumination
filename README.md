# Adaptive Illumination: Smart Bulb with Dynamic Daylight Sensing

This Arduino project demonstrates a smart bulb system with dynamic daylight sensing, offering adaptive illumination based on ambient light conditions. By incorporating a light sensor made with the help of photo resistor, the project adjusts the brightness of an LED in response to changes in the surrounding light environment. The system is designed to turn off the LED when the light intensity falls below a certain threshold and gradually increase its brightness as the ambient light level rises.

## Introduction

Experience intelligent lighting with the Adaptive Illumination Arduino project. Transform a standard LED into a smart bulb that dynamically adapts to varying daylight conditions. This project utilizes a light sensor and Arduino board to create a responsive lighting system, offering a hands-on exploration of Light sensors which is made with the help of Photo Resistor and Analog control for LEDs.

Navigate through this README to set up the project, comprehend the code's functionality, and gain insights into its methodology. Whether you're a novice exploring Arduino projects or an enthusiast looking for an engaging experiment, this project provides an exciting opportunity to blend technology with the natural environment. Let's delve into the world of Adaptive Illumination and create a smart bulb that adjusts to the changing patterns of daylight

# Setup
Follow these steps to set up the Adaptive Illumination Arduino project:

## Components Required
- 1x Arduino board
- 1x Photoresistor
- 2x Resistor (for photoresistor and LED)
- 1x Red LED
- 1 x Breadboard
- 5x jumper wires

# Wiring Instructions
1) Connect the Photoresistor:

- Connect a resistor from the one end of the photoresistor to the 5V on the Arduino board.
- Connect the resistor end of the photoresistor to the analog input pin A1 on the Arduino board.
- Connect 2nd end of photoresistor to Ground (GND pin) on Arduino board.
  
2) Connect the LED:

- Connect the longer leg (anode) of the red LED to a current-limiting resistor followed by digital pin 8 on the Arduino board.
- Connect the other end of the resistor to the ground (GND Pin) on the Arduino board.

# Power Supply:

Ensure that your Arduino board is connected to a power source.

# Final Setup
Your setup should now resemble the following way :
![image](https://github.com/phpandya28/Adaptive-Illumination/assets/138100019/8213fae1-e5ab-480b-a0ac-9a0d68aeb3db)

# Uploading and Running the Code
- Connect your Arduino board to your computer using a USB cable.
- Open the Arduino IDE on your computer.
- Copy and paste the code from the provided Arduino project into a new sketch.
- Click the "Upload" button in the Arduino IDE to upload the code to your Arduino board.
- Open the Serial Monitor to view the analog readings from the photoresistor.
- With these steps completed, your Adaptive Illumination Arduino project is ready to respond to changes in ambient light and adjust the LED brightness accordingly. Experiment with different lighting conditions to observe the dynamic behavior of your smart bulb.

## Usage
The Adaptive Illumination Arduino project provides a straightforward and interactive way to experience dynamic daylight sensing with a smart bulb. Follow these instructions to make the most of your project:

# Power On:

Connect your Arduino board to a power source via USB.

# Upload Code:

- Open the Arduino IDE on your computer.
- Copy and paste the provided code into a new sketch.
- Upload the code to your Arduino board using the "Upload" button in the Arduino IDE.
- Monitor Serial Output:
- Open the Serial Monitor in the Arduino IDE to observe the analog readings from the photoresistor.
- The Serial Monitor will display the light intensity values, helping you understand how the system responds to changes in ambient light.
  
# Setup in Different Lighting Conditions:

- Place the photoresistor in various lighting environments, ranging from low light to bright light.
- Observe the behavior of the connected LED on digital pin 8.
- Note how the LED adjusts its brightness based on the detected light intensity.
  
# Experiment with Thresholds:

- Explore the code to understand how the LED brightness threshold is set (800 in the provided code).
- Adjust the threshold value in the code to experiment with different sensitivity levels.

# Modify Code (Optional):

If you're comfortable with coding, feel free to modify the code to implement additional features or customize the project to suit your preferences.

# Turn Off and Disconnect:

- When finished, turn off the Arduino board and disconnect it from the power source.
- This project allows you to engage with the concept of dynamic daylight sensing in a tangible way. Use the Serial Monitor to gain insights into the light intensity values and observe how the LED adapts to its surroundings. Enjoy experimenting with different lighting scenarios and discover the versatility of your Adaptive Illumination smart bulb.

## Methodology
The Adaptive Illumination Arduino project employs a simple yet effective methodology to create a smart bulb with dynamic daylight sensing. The following outlines the key steps and concepts involved in the development of this project:

# 1. Light Sensor Integration:
- A photoresistor is utilized as the light sensor, which exhibits changes in resistance based on ambient light intensity.
- The photoresistor is connected to analog pin A1 on the Arduino board, forming a voltage divider circuit with a resistor. This configuration allows the Arduino to measure the analog voltage corresponding to the light level.

# 2. LED Control with PWM:
- A red LED is employed as the output device, representing the illumination element of the smart bulb.
- The LED is connected to digital pin 8 on the Arduino board with a current-limiting resistor. This allows the Arduino to control the LED brightness using Pulse Width Modulation (PWM).

# 3. Threshold-Based Illumination Control:
- The project introduces a threshold value (800 in the provided code) that acts as a reference point for determining whether the ambient light requires a response from the smart bulb.
- If the light intensity falls below the threshold, the LED is turned off to conserve energy.
- As the light intensity surpasses the threshold, the LED brightness is adjusted proportionally using a linear mapping function, providing adaptive illumination.

# 4. Serial Monitoring for Insights:
The Arduino Serial Monitor is utilized to display real-time analog readings from the photoresistor. This feature enables users to observe and analyze the changes in light intensity as the project responds to different lighting conditions.

# 5. User Interaction and Experimentation:
- Users are encouraged to experiment with the project by placing it in various lighting environments.
- The project provides a tangible and interactive experience for users to witness how the smart bulb dynamically adjusts its brightness in response to changing daylight conditions.

# 6. Code Customization and Exploration:
- The project's code is structured to be accessible for customization.
- Users can explore the code to understand its logic and experiment with modifications, such as adjusting the threshold value or implementing additional features.

# 7. Educational Value:
- The project serves as an educational tool for individuals learning about analog sensors, PWM, and basic control systems in the context of Arduino programming.
- It encourages hands-on exploration and understanding of how hardware components can be integrated to create a responsive and adaptive system.

By following this methodology, the Adaptive Illumination Arduino project offers an engaging way to explore the intersection of technology and ambient light control, providing a foundation for further experimentation and learning in the realm of Arduino development.

## Code Explanation
The Adaptive Illumination Arduino project code is designed to create a smart bulb with dynamic daylight sensing using a photoresistor and an LED. 
Here's a breakdown of the key elements and functionality in the provided code:

# Variables Declaration : 
Code :
float lightval;
int voltageread = A1;
int ledpin = 8;
float y_op;
int dt = 1000;

Explanation :
- lightval: Float variable to store the analog reading from the photoresistor.
- voltageread: Integer variable representing the analog pin (A1) connected to the photoresistor.
- ledpin: Integer variable representing the digital pin (8) connected to the LED.
- y_op: Float variable to store the calculated LED brightness.
- dt: Integer variable representing the delay time in milliseconds.

  # Setup Function :
  Code :
  void setup() {
  Serial.begin(9600);
  pinMode(voltageread, INPUT);
  pinMode(ledpin, OUTPUT);
  }

Explanation :
- Serial.begin(9600): Initializes communication with the Serial Monitor at a baud rate of 9600.
- pinMode(voltageread, INPUT): Sets the pin mode for the photoresistor pin as INPUT.
- pinMode(ledpin, OUTPUT): Sets the pin mode for the LED pin as OUTPUT.

# Loop Function :
Code :
void loop() {
  lightval = analogRead(voltageread);
  Serial.println(lightval);
  delay(dt);

  if (lightval < 800) {
    analogWrite(ledpin, 0);
  } else if (lightval >= 800 && lightval <= 1023) {
    y_op = map(lightval, 800, 1023, 0, 255);
    analogWrite(ledpin, y_op);
  }
}

Explanation :
- analogRead(voltageread): Reads the analog voltage from the photoresistor and stores it in the lightval variable.
- Serial.println(lightval): Prints the light intensity reading to the Serial Monitor.
- delay(dt): Pauses the program for the specified delay time.

The code then checks if the light intensity is below 800. If true, it turns off the LED. If false, it uses the map function to scale the lightval from the range [800, 1023] to [0, 255] and adjusts the LED brightness accordingly.

This code continuously reads the light intensity, prints it to the Serial Monitor, and adjusts the LED brightness based on the ambient light conditions, providing a responsive and adaptive lighting system. Users can experiment with different lighting environments to observe the system in action.

## Components Used
The Adaptive Illumination Arduino project involves the integration of several components to create a smart bulb with dynamic daylight sensing. Here's an overview of the components used and how each one contributes to the functionality of the project:

# Photoresistor
Description:
- The photoresistor is a variable resistor that changes its resistance based on the intensity of ambient light.

Role in the Project:
- Acts as a light sensor to measure the surrounding light intensity.
- Connected in a voltage divider circuit with a resistor to provide a variable voltage to the Arduino analog pin.
  
# Resistor (Connected with Photoresistor)
Description:
- A fixed resistor used in conjunction with the photoresistor to create a voltage divider circuit.
Role in the Project:
- Helps create a stable voltage reference for the Arduino analog pin by forming a voltage divider with the photoresistor.
  
# Red LED
Description:
- A light-emitting diode (LED) that emits red light when powered.
  
Role in the Project:
- Represents the illumination element of the smart bulb.
- Adjusts its brightness based on the analog readings from the photoresistor.
  
# Current Limiting Resistor (Connected with LED)
Description:
A resistor placed in series with the LED to limit the current flowing through it.

Role in the Project:
- Prevents excessive current flow through the LED, protecting it from damage.
- Enables precise control of LED brightness using Pulse Width Modulation (PWM).
  
## How Each Component Works
# Photoresistor and Resistor (Voltage Divider Circuit)
- In a bright environment, the photoresistor's resistance decreases, causing the voltage at the analog pin to increase.
- In low-light conditions, the photoresistor's resistance increases, resulting in a decrease in voltage at the analog pin.
- The fixed resistor in the voltage divider circuit ensures a consistent reference voltage, allowing the Arduino to measure changes in light intensity based on the varying voltage at the analog pin.
  
# Red LED and Current Limiting Resistor
- The red LED is connected to a digital pin on the Arduino.
- The current limiting resistor controls the amount of current flowing through the LED, preventing it from drawing too much current and burning out.
- Pulse Width Modulation (PWM) is employed to adjust the LED's brightness by controlling the duty cycle of the PWM signal.
- By combining these components, the project creates an adaptive illumination system that adjusts the brightness of the LED based on the surrounding light conditions measured by the photoresistor. This interaction provides a tangible example of using analog sensors, resistors, and LEDs in an Arduino project to create a responsive and energy-efficient smart bulb.

## Limitations
While the Adaptive Illumination Arduino project provides an interactive and educational experience, it also comes with certain limitations that users should be aware of:

1. Limited Sensing Range:
The project's photoresistor may have a limited sensing range, affecting its ability to accurately measure light intensity in extremely bright or extremely dim environments.

2. Sensitivity to Ambient Light:
The system's sensitivity to ambient light changes might result in the LED flickering or adjusting rapidly in response to minor variations in light levels.

3. Single Light Source:
The project is designed to respond to overall ambient light levels. It may not differentiate between multiple light sources, potentially leading to unexpected behavior in environments with multiple light fixtures.

4. Fixed Threshold:
The threshold value (800 in the provided code) is fixed and might not be optimal for all scenarios. Users might need to adjust this value based on specific lighting conditions.

5. No External Power Management:
The project doesn't incorporate power management features to optimize energy consumption. It continuously operates and may drain the power source even when the LED is off.

6. Dependency on Serial Monitor:
The project relies on the Serial Monitor for displaying light intensity readings. In standalone applications, this dependency might not be practical.

7. Limited LED Control:
The project uses basic PWM control for LED brightness. Advanced features, such as color changes or pattern displays, are not implemented in this version.

8. Single Light Output:
The project uses a single LED for illumination. For applications requiring multiple light sources or different colors, additional modifications are necessary.

9. Hardware Limitations:
The effectiveness of the project is influenced by the quality and specifications of the hardware components used, including the photoresistor and LED.

10. Environmental Factors:
- External factors, such as changes in temperature or humidity, may influence the photoresistor's behavior and impact the project's responsiveness.

Understanding these limitations allows users to make informed decisions about the project's suitability for specific applications and consider potential areas for improvement or customization. This information serves as a guide for users to refine the project based on their requirements and explore further enhancements.

## Future Improvements
The Adaptive Illumination Arduino project provides a foundation for creating a dynamic smart bulb, and there are several opportunities for future improvements and enhancements:

1. Multi-Sensor Integration:
Incorporate multiple light sensors to improve accuracy and sensitivity across various directions or light sources.

2. Dynamic Threshold Adjustment:
Implement an algorithm to dynamically adjust the threshold value based on the ambient light conditions, providing a more adaptive response.

3. Power Management:
Integrate power management features to minimize energy consumption when the LED is not in use, extending the project's battery life for portable applications.

4. Advanced LED Control:
Explore advanced PWM techniques or external LED driver modules to enable features such as color changing, fading, or pattern displays.

5. User-Configurable Parameters:
Create user-friendly interfaces (physical or digital) to allow users to configure parameters such as threshold values or LED behavior without modifying the code.

6. Real-time Clock (RTC) Integration:
Incorporate a real-time clock module to enable time-dependent illumination changes, simulating natural lighting conditions throughout the day.

7. Machine Learning Algorithms:
Implement machine learning algorithms to predict and adapt to lighting patterns based on historical data, enhancing the system's intelligence.

8. Mobile Application Integration:
Develop a mobile application or web interface for remote monitoring and control of the smart bulb, providing users with more flexibility.

9. Multiple LED Outputs:
Extend the project to support multiple LEDs or different types of light sources, creating a more versatile lighting system.

10. Enclosure Design:
Design and create a protective enclosure for the components, making the project more aesthetically pleasing and suitable for different environments.

11. Integration with Home Automation Systems:
Connect the smart bulb to popular home automation platforms (e.g., IoT platforms, smart home ecosystems) for seamless integration with other devices.

12. Data Logging and Analytics:
Implement data logging capabilities to record and analyze light intensity trends over time, providing insights into environmental changes.

These future improvements aim to enhance the project's functionality, versatility, and user experience. Users are encouraged to explore these possibilities based on their specific needs and interests, further expanding the capabilities of the Adaptive Illumination system.
