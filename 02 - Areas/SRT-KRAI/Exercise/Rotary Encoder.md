---
tags: 
Links: "[[My Areas]]"
---
---
## Increment-Decrement Encoder
```cpp
// Rotary Encoder Inputs
#define inputCLK 5
#define inputDT 4

// LED Outputs
#define ledCW 8
#define ledCCW 9

int counter = 0;
int currentStateCLK;
int previousStateCLK;

String encdir = "";

void setup() {
	Serial.begin(9600);
	pinMode(inputCLK, INPUT);
	pinMode(inputDT, INPUT);
	pinMode(ledCW, OUTPUT);
	pinMode(ledCCW, OUTPUT);
	
	// Read the initial state of inputCLK
	// Assign to previousStateCLK variable
	previousStateCLK = digitalRead(inputCLK); // A
}

void loop() {
	// Read the current state of inputCLK
	currentStateCLK = digitalRead(inputCLK); // B
	
	// if the previous and the current state of the inputCLK are different then a pulse has occured
	if (currentStateCLK != previousStateCLK) {
		// if the inputDT state is different than inputCLK state then
		// the encoder is rotating counterclockwise
		if (digitalRead(inputDT) != currentStateCLK) {
		  counter--;
		  encdir = "CCW";
		  digitalWrite(ledCW, LOW);
		  digitalWrite(ledCCW, HIGH);
		}else {
		  // encoder is rotating clockwise
		  counter++;
		  encdir = "CW";
		  digitalWrite(ledCW, HIGH);
		  digitalWrite(ledCCW, LOW);
		}
		Serial.print("Direction: ");
		Serial.print(encdir);
		Serial.print(" -- value: ");
		Serial.println(counter);
	}
	// update previousStateCLK with the current state
	previousStateCLK = currentStateCLK;
	// delay(100);
}
```