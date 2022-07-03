# arduino stuff


# Sketches

## Onboard LED - blink

````
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
````

## Stepper motor

### 28BYJ-48 Unipolar Stepper with ULN2003 driver

![image](https://user-images.githubusercontent.com/38451588/177039377-36fa5070-64d9-4e40-84fa-37c0d0485d5d.png)


### 



# ESP8266

- Add addiitonal board manager URL:
File, Preferences 
http://arduino.esp8266.com/stable/package_esp8266com_index.json

![image](https://user-images.githubusercontent.com/38451588/173273411-6ea5fdc3-ae61-475b-8269-7b0e4e7c96fe.png)

- Set board type

![image](https://user-images.githubusercontent.com/38451588/173273458-779e091e-7382-4fdb-ac6e-0c2eed6d9bbe.png)
