---
tags: 
Links: "[[My Areas]]"
---
---
## 1. Two Servo with One analog module

```cpp
#include <Arduino.h>
#include <Servo.h>

int pinx = A0;
int piny = A1;
int sw = A2;

void setup() {
  Serial.begin(9600);
  pinMode(pinx, INPUT);
  pinMode(piny, INPUT);
  pinMode(sw, INPUT);
} 

void loop() {
  int x = analogRead(pinx);
  int y = analogRead(piny);
  int swtc = analogRead(sw);

  Serial.print("X : ");
  Serial.println(x);
  Serial.print("Y : ");
  Serial.println(y);
  Serial.print("Switch : ");
  Serial.println(swtc);
  delay(1000);
}
```

