# Hackathon Repository

## Institution: Siddaganga Institute of Technology  
**Innovation Council & Siddaganga TBI**

Welcome to the repository for the hackathon organized by **Innovation Council** and **Siddaganga TBI**. This repository is a central hub for storing and collaborating on data related to our hackathon project.

### Problem Statement

Small-scale farmers and merchants in developing regions suffer significant financial 
losses due to the lack of affordable cold storage facilities for their perishable produce. 
Conventional cold storage solutions are too expensive and require reliable electricity, 
making them inaccessible to rural farmers. With high post-harvest losses impacting both 
farmer income and food security, there is an urgent need for a low-cost cold storage 
solution that can operate with minimal electricity, be built from locally available 
materials, and effectively maintain lower temperatures to extend produce shelf life. 
Additionally, incorporating IoT technology for real-time monitoring and control of 
temperature and humidity can further enhance the efficiency and reliability of these 
storage facilities.

---

## Team Details

**Team Name:** [Your Team Name]

### Team Members

Team Member 1: 
● Name: Akshaykumar Prabhayya Lutimath 
● USN:1si22ec002 
Team Member 2: 
● Name: Arvind Shankrappa yakkundi 
● USN:1si22ec009 
Team Member 3: 
● Name:Kowshik P 
● USN:1si22ec048 
Team Member 4: 
● Name: Mahesha H G  
● USN:1si22ec055 


---

## Project Description

 • To develop a low cost and a portable cold storage unit using a compressor AC for 
maximizing the profit of farmers from their produce. 
• To integrate IoT based sensor network for remote monitoring and controlling of 
temperature and humidity. 
• To use LCD interface to display the internal temperature and humidity and automated 
controlling  
• Using easily available low-cost materials and combining to make a single material that 
must retain the heat for longer time.

## Technologies Used

Cold storage unit development 
Combination of multiple material with less R value.
 Hardware components.
 • Temperature and humidity sensors(DHT11)
 • AURDINO microcontroller
 • LCDdisplay 
• Battery 
• Cooling system (mini air compressor)
 Software implementation
 •Microcontroller Programming: Sensor data reading and 
processing
 • LCD display interface
 • Control algorithms for cooling system
 Control logic 
• If temperature>threshold                                              
❖Activate cooling system
 ❖Increase fanspeed
 • If temperature = threshold
 ❖Automatic Switch off compressor 

---

## Getting Started

To get started with this repository, follow these steps:

1. Clone the repository:

   ```bash
#include <DHT.h>
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#define DHTPIN 2
#define DHTTYPE DHT11
DHT dht(DHTPIN, DHTTYPE);
const int potPin = A0;
const int fanPin = 3; // Connect the fan to this pin
LiquidCrystal_I2C lcd(0x3F, 16, 2); // Set the LCD address and dimensions
void setup() {
dht.begin();
pinMode(fanPin, OUTPUT);
lcd.init(); // Initialize the LCD
lcd.backlight(); // Turn on the backlight
lcd.setCursor(0, 0);
lcd.print("Temp Fan Control");
lcd.setCursor(0, 1);
lcd.print("SMART FROST");
delay(2000);
lcd.clear();
}
void loop() {
int threshold = map(analogRead(potPin), 0, 1023, 20, 40); // Map potentiometer value to
  
float temperature = dht.readTemperature();
if (temperature > threshold) {
digitalWrite(fanPin, HIGH); // Turn on the fan
} else {
digitalWrite(fanPin, LOW); // Turn off the fan
}
lcd.clear();
lcd.setCursor(0, 0);
lcd.print("Temp: ");
lcd.print(temperature);
lcd.print("C");

lcd.setCursor(0, 1);
lcd.print("Threshold: ");
lcd.print(threshold);
lcd.print("C");
delay(1000);
}
