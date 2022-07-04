# arduino stuff


# General

- May have to set a different processor option per board

![image](https://user-images.githubusercontent.com/38451588/177109781-351e07e1-6ddf-4814-a038-fe658b443032.png)

- Setting COM port to a faster speed increases upload speed

![image](https://user-images.githubusercontent.com/38451588/177109891-7473963c-98fe-4bf2-9dec-22a12a80e93d.png)


# Sketches

## Onboard LED - blink

```cpp
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for a second
}
```

## Stepper motor

### 28BYJ-48 Unipolar Stepper with ULN2003 driver

- Driver accepts 12V BUT 5V motor doesn't like it, so use 5V

![image](https://user-images.githubusercontent.com/38451588/177039377-36fa5070-64d9-4e40-84fa-37c0d0485d5d.png)

```cpp
/*
  Stepper Motor Demonstration 1
  Stepper-Demo1.ino
  Demonstrates 28BYJ-48 Unipolar Stepper with ULN2003 Driver
  Uses Arduino Stepper Library

  DroneBot Workshop 2018
  https://dronebotworkshop.com
*/

//Include the Arduino Stepper Library
#include <Stepper.h>

// Define Constants

// Number of steps per internal motor revolution 
const float STEPS_PER_REV = 32; 

//  Amount of Gear Reduction
const float GEAR_RED = 64;

// Number of steps per geared output rotation
const float STEPS_PER_OUT_REV = STEPS_PER_REV * GEAR_RED;

// Define Variables

// Number of Steps Required
int StepsRequired;

// Create Instance of Stepper Class
// Specify Pins used for motor coils
// The pins used are 8,9,10,11 
// Connected to ULN2003 Motor Driver In1, In2, In3, In4 
// Pins entered in sequence 1-3-2-4 for proper step sequencing

Stepper steppermotor(STEPS_PER_REV, 8, 10, 9, 11);

void setup()
{
// Nothing  (Stepper Library sets pins as outputs)
pinMode(LED_BUILTIN, OUTPUT);
}

void loop()
{
  // Slow - 4-step CW sequence to observe lights on driver board
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
 delay(100);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
 delay(100);                       // wait for a second
 digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
 delay(100);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
 
  //steppermotor.setSpeed(1);    
  StepsRequired  =  4;
  //steppermotor.step(StepsRequired);
  //delay(2000);

   // Rotate CW 1/2 turn slowly

//  StepsRequired  =  STEPS_PER_OUT_REV / 2; 
//  steppermotor.setSpeed(100);   
//  steppermotor.step(StepsRequired);
//  delay(1000);


   // Rotate CW full turn medium speed

  StepsRequired  =  STEPS_PER_OUT_REV; 
  steppermotor.setSpeed(1000);   // 1000 may be max??
  steppermotor.step(StepsRequired);
  delay(1000);


  // Rotate CCW full turn quickly

  StepsRequired  =  - STEPS_PER_OUT_REV; // 2;   
  steppermotor.setSpeed(1000);  
  steppermotor.step(StepsRequired);
  delay(1000);

}
```



### 



# ESP8266


![image](https://user-images.githubusercontent.com/38451588/177111280-908840dd-53ae-4d20-b13a-3d0ed423ef69.png)
  

- Add addiitonal board manager URL:
File, Preferences 
http://arduino.esp8266.com/stable/package_esp8266com_index.json

![image](https://user-images.githubusercontent.com/38451588/173273411-6ea5fdc3-ae61-475b-8269-7b0e4e7c96fe.png)

- Set board type

![image](https://user-images.githubusercontent.com/38451588/173273458-779e091e-7382-4fdb-ac6e-0c2eed6d9bbe.png)


## LED Blink

- Note, onboard LED is inverted - LOW turns it on!
- Onboard LED is connected to GPIO2

```cpp
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  #define LED_BUILTIN 2
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for a second
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
}
```

## Stepper motor

- use AccelStepper.h for stepper motors

## WIFI

```cpp

#include "ESP8266WiFi.h"

char ssid[]           = "MyWifiNetwork SSID";
const char* password  = "MyP@ssword"; 

void setup() {
Serial.begin(115200);
Serial.print("Connecting to ");
Serial.println(ssid);
WiFi.begin(ssid, password);
while (WiFi.status() != WL_CONNECTED) {
delay(500);
Serial.print(".");
}
Serial.println("WiFi connected.");
}
```
