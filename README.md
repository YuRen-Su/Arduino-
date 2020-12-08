# Arduino-Classroom-learning-content
## Topic One - LED blinking
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/LED%20blink%20GIF.gif)
```C++
void setup() {
   pinMode(2,OUTPUT);
}

void loop() {
  digitalWrite(2,HIGH);
  delay(200);
  digitalWrite(2,LOW);
  delay(200);
}
```
##  Topic Two - LED turn on and off one by one from left to right
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/LED%20turn%20on%20and%20off%20one%20by%20one%20from%20left%20to%20right%20%20GIF.gif)
```C++
int LED=5;
void setup() {
  for (int i=2 ;i&lt;6;i++){
    pinMode(i,OUTPUT);
  }
}

void loop() {
  for(int i=5; i&gt;1; i--)
    digitalWrite(i,HIGH);
    if (LED&gt;=2){
      digitalWrite(LED,LOW);
    }
    else{
      LED=6;
    }   
    LED--;
 delay(500);
}
```
##  Topic Three - LED breathing light
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/LED%20breathing%20light%20GIF.gif)
```C++
int value=255; int x=-15;
void setup() {
  pinMode(3,OUTPUT);
}

void loop() {
  if (value&lt;=0 || value&gt;=255) x=-x;
  analogWrite(3,value);
  delay(80);
  value=value-x;
}
```
##  Topic Four - Two Button + Relay Switch
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/Button%20%2B%20Relay%20Switch%20GIF.gif)
```C++
void setup() {
  pinMode(2,OUTPUT);
  pinMode(13,OUTPUT);
  for (int i=3 ;i&lt;5;i++){
    pinMode(i,INPUT);
  }  
}

void loop() {
  while (digitalRead(3) == 0) {
     while (digitalRead(3) == 0) {
       delay(30);
     }
     digitalWrite(2,HIGH);
  }
  while (digitalRead(4) == 0) {
     while (digitalRead(4) == 0) {
       delay(30);
     }
     digitalWrite(2,LOW);
  }
  delay(20);
}
```
##  Topic Five - One Button + Relay Switch
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/One%20Button%20%2B%20Relay%20Switch%20GIF.gif)
```C++
void setup() {
  pinMode(2,OUTPUT);
  pinMode(13,OUTPUT);
  for (int i=3 ;i<5;i++){
    pinMode(i,INPUT);
  }  
}

void loop() {
  while (digitalRead(3) == 0) {
     while (digitalRead(3) == 0) ;
     digitalWrite(2,!digitalRead(2));
  }
  delay(20);
}
```
##  Topic Six - Servo Motor Speed Control
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/Servo%20motor%20speed%20control%20GIF.gif)
```C++
#include <Servo.h>
Servo myservo;
int data= 0 ;
void setup() {
 myservo.attach(7);
for (int i=2 ;i<6;i++){
    pinMode(i,INPUT);
    myservo.write(0);
  } 
}

void loop() {
    while (digitalRead(2) == 0) {
      while (digitalRead(2) == 0) ;
      
      if (data>180) {
        data = 0;
      }
      else{
        data+=30;
      }
      myservo.write(data);
    }
}
```
##  Topic Seven - Motor PWM Control
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/Motor%20PWM%20Control%20GIF.gif)
```C++
void setup() {
  pinMode(2,OUTPUT);//IN3
  pinMode(9,OUTPUT);//IN1
  pinMode(10,OUTPUT);//IN2
  digitalWrite(2,LOW);
}

void loop() {
  fr(200);
  delay(2000);
  br();
  delay(2000);
  rev(200);
  delay(2000);
  br();
  delay(2000);
  
}

void fr(int f){
  analogWrite(9,f);
  analogWrite(10,LOW);
}
void rev (int r){
  analogWrite(9,LOW);
  analogWrite(10,r);
}
void br(){
  analogWrite(9,HIGH);
  analogWrite(10,HIGH);
}
```
##  Topic Eight - Motor PWM Button Control
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/Motor%20PWM%20Button%20Control%20GIF.gif)
```C++
int i=110;
void setup() {
  pinMode(2,OUTPUT);//IN3
  pinMode(9,OUTPUT);//IN1
  pinMode(10,OUTPUT);//IN2
  pinMode(3,INPUT);
  digitalWrite(2,LOW);
}

void loop() {
  while (digitalRead(3) == 0) {
      while (digitalRead(3) == 0) ;
      delay(50);
      if (i==255){
        i=110;
      }
      else
      {
        i+=29;
      }
  }
  fr(i);
  delay(50);
}

void fr(int f){
  analogWrite(9,f);
  analogWrite(10,LOW);
}
void rev (int r){
  analogWrite(9,LOW);
  analogWrite(10,r);
}
void br(){
  analogWrite(9,HIGH);
  analogWrite(10,HIGH);
}
```
##  Topic Nine - Motor PWM Button Control + LED +ON/OFF Button
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/Motor%20PWM%20Button%20Control%20%2B%20LED%20%2BONOFF%20Button%20GIF.gif)
```C++
int i=110;
int z=8;
bool b = false;
void setup() {
  pinMode(2,OUTPUT);//IN3
  pinMode(5,OUTPUT);//IN1
  pinMode(6,OUTPUT);//IN2
  pinMode(3,INPUT);
  pinMode(4,INPUT);
  digitalWrite(2,LOW);
    for(int i=7;i<13;i++){
    pinMode(i,OUTPUT);
  }
  for(int i=7;i<13;i++){
    digitalWrite(i,HIGH);
  }
  Serial.begin(9600);
}

void loop() {
  while (digitalRead(4) == 0) {
      while (digitalRead(4) == 0) ;
      delay(40);
      b=!b;
  }
  if (b==false){
    fr(0);
    led(7);
    i=110;
    z=8;
  }
  else{
    lo();
  }
  delay(50);
}

void lo() {
  while (digitalRead(3) == 0) {
      while (digitalRead(3) == 0) ;
      delay(50);
      if (i==255){
        i=110;
        z=8;
      }
      else
      {
        i+=29;
        z++;
      }
  }
  led(z);
  fr(i);
}

void fr(int f){
  analogWrite(5,f);
  analogWrite(6,LOW);
}

void led(int l){
  for(int i=7;i<13;i++){
    digitalWrite(i,HIGH);
  }
  for(int i=7;i<l;i++){
    digitalWrite(i,LOW);
  }
}
```
