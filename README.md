# TEMPERATURE-MONITORING-SYSTEM

"COMPANY" : CODTECH IT SOLUTIONS

"NAME" : GANGAMBIKA BK

"INTERN ID" : CT08VCR

"DOMAIN" : EMBEDDED SYSTEMS

"DURATION" : 4 WEEKS

"MENTOR" : NEELA SANTHOSH

"DISCRIPTION" :

Introduction

This task focuses on designing a temperature monitoring system using an Arduino UNO, an LM35 analog temperature sensor, and a 16x2 LCD display. The system reads ambient temperature values, converts them from analog to digital form, and displays the result both on the Serial Monitor and the LCD screen in real time. This type of system is commonly used in weather stations, smart thermostats, greenhouses, and industrial applications where continuous temperature monitoring is crucial.

Tools and Components Used :
Component	Purpose
Arduino UNO R3	Microcontroller to read sensor and display data
LM35 Sensor	Analog temperature sensor (output in °C)
16x2 LCD Display	To show temperature values on-screen
10k Potentiometer	(Optional) For adjusting LCD contrast
Breadboard & Wires	For circuit connections
Arduino IDE	To upload code and view serial data
Working Principle :
The LM35 sensor outputs an analog voltage that is directly proportional to the temperature in degrees Celsius. This voltage is read through the analog pin A0 on the Arduino and converted into a temperature value using the formula:

cpp
Copy
Edit
float voltage = reading * 4.68 / 1024.0;
float temperatureC = (voltage - 0.5) * 100;
4.68 is used instead of 5.0 as a more accurate measured voltage from the Arduino's 5V line.

The resulting temperature is:

Printed to the Serial Monitor using Serial.print()
Displayed on a 16x2 LCD screen using the LiquidCrystal library
The LCD is initialized with the following pin connections:

LCD Pin	Arduino Pin
RS	8
E	7
D4	6
D5	5
D6	4
D7	3
On the LCD, the temperature value is shown in the second row under the label “Temperature Value”.

Code Summary :
cpp
Copy
Edit
#include <LiquidCrystal.h>
LiquidCrystal lcd(8, 7, 6, 5, 4, 3);
int sensorPin = 0;

void setup() {
  Serial.begin(9600);
  lcd.begin(16, 2);
}

void loop() {
  int reading = analogRead(sensorPin);
  float voltage = reading * 4.68 / 1024.0;
  float temperatureC = (voltage - 0.5) * 100;

  Serial.print(temperatureC);
  Serial.println(" degrees C");

  lcd.setCursor(0, 0);
  lcd.print("Temperature Value ");
  lcd.setCursor(0, 1);
  lcd.print(" degrees C");
  lcd.setCursor(11, 1);
  lcd.print(temperatureC);

  delay(100);
}
This code continuously reads the temperature and updates the LCD and Serial Monitor every 100 milliseconds.

Applications :

This project demonstrates the fundamental design of real-world systems including:
Smart home thermostats for temperature-based control
Greenhouse and agricultural monitoring
Server room/environment monitoring
Consumer electronics with temperature displays
Weather stations and environmental sensing systems
Conclusion :
This task successfully demonstrates real-time temperature monitoring using the LM35 analog temperature sensor and an LCD display. By integrating sensor input, analog-to-digital conversion, and visual display, this project provides a solid foundation for building more advanced IoT or embedded monitoring systems. The dual output on LCD and Serial Monitor also enhances usability and debugging, making it a reliable and informative embedded system project.

"OUTPUT" :

![Image](https://github.com/user-attachments/assets/9abc8a38-6e60-4b3d-afa8-8288bc5de9df)








