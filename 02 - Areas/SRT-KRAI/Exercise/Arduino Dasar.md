---
tags: 
Links: "[[My Areas]]"
---
---
## 1. Untuk Mengetahui Apakah Tombol Ditekan atau Tidak

```cpp
#include <Arduino.h>
#include <Servo.h>

const int pb = 3;

void setup(){
	 Serial.begin(9600);
	 pinMode(pb, INPUT);
} 

void loop(){
	 Serial.println(digitalRead(pb));
	 delay(1000);
}
```
## 2. Apakah tombol ditekan dengan tambahan LED (if statement)

```cpp
#include <Arduino.h>
#include <Servo.h>

const int pb = 3;
const int led = 4;
boolean result;

void setup(){
	 Serial.begin(9600);
	 pinMode(pb, INPUT);
	 pinMode(led, OUTPUT);
} 

void loop(){
	result = digitalRead(pb);
	if(result){
		digitalWrite(led, HIGH);
	}else{
		digitalWrite(led, LOW);
	}
	delay(1000);
}
```
## 3. Logic AND & OR

![[schematic1.png#center|400]]
source : fritzing
```cpp
conts int ledR = 11;
const int ledB = 10;
const int ledP = 12;

const int pbR = 5;
const int pbB = 6;

void setup(){
	pinMode(ledR, OUTPUT);
	pinMode(ledB, OUTPUT);
	pinMode(ledP, OUTPUT);
	pinMOde(pbR, INPUT);
	pinMOde(pbB, INPUT);
}
void loop(){
	if(digitalRead(pbR) == 1 && digitalRead(pbB) == 0){
		digitalWrite(ledR, HIGH);
	}else{
		digitalWrite(ledR, LOW);
	}
	
	if(digitalRead(pbR) == 0 && digitalRead(pbB) == 1){
		digitalWrite(ledB, HIGH);
	}else{
		digitalWrite(ledB, LOW);
	}
	
	if(digitalRead(pbR) == 1 && digitalRead(pbB) == 1){
		digitalWrite(ledP, HIGH);
	}else{
		digitalWrite(ledP, LOW);
	}
}
```

> [!NOTE] TASK
> Kondisi awal nyala semua
> 1. pbR ditekan, led merah dan led ungu akan mati
> 2. pbB ditekan, led biru dan led ungu akan mati
> 3. pbR dan pbB ditekan maka led ungu akan mati
## 4. switch case

```cpp
void loop(){
	resultLeft = digitalRead(pbLeft);
	if(resultLeft == 1){
		i++;
		delay(300);
	}
	
	resultRight = digitalRead(pbRight);
	if(resultRight == 1){
		i--;
		delay(300);
	}
	
	switch(i){
	case 1:
		digitalWrite(ledR, HIGH);
		digitalWrite(ledB, LOW);
		digitalWrite(ledP, LOW);
	case 2;
		digitalWrite(ledR, LOW);
		digitalWrite(ledB, LOW);
		digitalWrite(ledP, HIGH);
	case 3;
		digitalWrite(ledR, LOW);
		digitalWrite(ledB, HIGH);
		digitalWrite(ledP, LOW);
		break;
	default:
		break;
	}
}
```
## EEPROM Internal
```cpp
#include<EEPROM.h> // harus memakai library
byte value;

void setup(){
	// parameter pertama merupakan address dari 0 sampai 1023 (1 kb)
	// parameter kedua merupakan jumlah data dari 0 sampai 255 (1 byte = 8 bit)
	EEPROM.write(0,123);
}
void loop(){
	value = EEPROM.read(0); //alamat ke 0
	// Serial.println(EEPROM.read(0));
	Serial.println(value);
	delay(1000);
}
```
## Sensor Jarak (HCSR04)
```cpp
#include<NewPing.h>
NewPing sensor(10, 11, 30); // pinTrig, pinEcho, JarakMaksimal

void setup(){
	Serial.begin(9600);
}

void loop(){
	jarak = sensor.ping_cm();
	Serial.println(jarak);
	delay(1000);
}
```
## Interrupt
Mengintrupsi fungsi yang sedang berjalan dengan fungsi lain. Interrupt berguna untuk menjalankan fungsi lain saat suatu fungsi sedang berjalan.
```cpp
#include<TimerOne.h>
const int merah = 12, hijau = 11, pb = 2;

void setup(){
	pinMode(pb, INPUT);
	pinMode(merah, OUTPUT);
	pinMode(hijau, OUTPUT);
	Timer1.initialize(10000); // dalam microsecond
	Timer1.attachInterrupt(blinkMerah);
}

void loop(){
	for(int i = 1; i <= 5; i++){
		digitalWrite(hijau, HIGH);
		delay(1000);
		digitalWrite(hijau, LOW);
		delay(1000);
	}
	if(digitalRead(pb) == HIGH){
		digitalWrite(merah, HIGH);
	}else{
		digitalWrite(merah, LOW);
	}
}

void blinkMerah(){
	if(digitalRead(pb) == HIGH){
		digitalWrite(merah, HIGH);
	}else{
		digitalWrite(merah, LOW);
	}
}
```