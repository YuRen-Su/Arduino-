# Arduino-Classroom-learning-content
## Topic One - LED blinking
### 功能-LED閃爍 0.2S亮 0.2S滅
#### ＊電路圖＆功能如下：
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
### 功能-LED由左至右逐一亮滅
### 初始狀態○○○○
### STEP1 ●○○○
### STEP2 ○●○○
### STEP3 ○○●○
### STEP4 ○○○●
#### ＊電路圖＆功能如下：
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
### 功能-LED呼吸燈，每80ms改變亮度
### ☆此功能需將LED接在有"~"符號的腳位
#### ＊電路圖＆功能如下：
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
### 功能-用雙按鈕控制繼電器讓LED亮滅
#### ＊電路圖＆功能如下：
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
### 功能-單顆按鈕透過繼電器控制LED亮滅
#### ＊電路圖＆功能如下：
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
### 功能-透過按鈕控制伺服馬達轉速
#### ＊電路圖＆功能如下：
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
### 功能-使用Arduino控制HT6751 IC發出PWM控制風扇轉速
#### ＊電路圖＆功能如下：
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
### 使用按鈕控制PWM來控制風扇轉速
#### ＊電路圖＆功能如下：
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
### 模擬一般市售直流風扇之功能
#### ＊電路圖＆功能如下：
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
##  Topic Ten - LiquidCrystal Library - Hello World
### 功能-使用LCD顯示出"Hello World"字樣與正數計時
### ☆使用LiquidCrystal Library程式庫
#### ＊電路圖＆功能如下：
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/LiquidCrystal%20Library%20-%20Hello%20World%20GIF.gif)
```c++
/*
   The circuit:
 * LCD RS pin to digital pin 12
 * LCD Enable pin to digital pin 11
 * LCD D4 pin to digital pin 5
 * LCD D5 pin to digital pin 4
 * LCD D6 pin to digital pin 3
 * LCD D7 pin to digital pin 2
 * LCD R/W pin to ground
 * LCD VSS pin to ground
 * LCD VCC pin to 5V
 * 10K resistor:
 * ends to +5V and ground
 * wiper to LCD VO pin (pin 3)
 * 
 */
#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup() {
  lcd.begin(16, 2);
  lcd.print("hello, world!");
}

void loop() {
  lcd.setCursor(0, 1);
  lcd.print(millis() / 1000);
}
```
##  Topic Eleven - LCD Display Basic Personal Information
### 功能-使用LCD顯示出班級＆座號＆姓名
### ☆使用LiquidCrystal Library程式庫
#### ＊電路圖＆功能如下：
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/LCD%20display%20personal%20information%20GIF.jpg)
```C++
#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup() {
  lcd.begin(16, 2);
  lcd.print("SuYuRen");
  lcd.setCursor(0, 1);
  lcd.print("25 I3A");
}
```
##  Topic Twelve - Button scroll LCD text
### 功能-使用LCD顯示可捲動的英文字母清單
### ☆使用LiquidCrystal Library程式庫
#### ＊電路圖＆功能如下：
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/Button%20scroll%20LCD%20text%20GIF.gif)
```C++
#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
String LCD[]{"A","B","C","D"};

int tmp=0,tmpd=1;
bool b=false;

void setup() {
  pinMode(7,INPUT);
  pinMode(6,INPUT);
  lcd.begin(16, 2);
  lcd.print("Welcome!!"); 
}

void loop() {
    
   if (digitalRead(7) == 0) {
      while (digitalRead(7) == 0)
      delay(20);
      if(b==true){
        tmp++;
        tmpd++;
        lcd.clear();
        if (tmp>=4){
          tmp=0;
        }
        if (tmpd>=4){
          tmpd=0;
        }
      }
      if(b==false){
        b=!b;
        lcd.clear();
      }
  }
   if (digitalRead(6) == 0) {
      while (digitalRead(6) == 0){
        delay(100);
      }
      if(b==true){
        tmp--;
        tmpd--;
        lcd.clear();
        if (tmp<=-1){
          tmp=3;
        }
        if (tmpd<=-1){
          tmpd=3;
        }
      }
      if(b==false){
        b=!b;
        lcd.clear();
      }
  }
   if(b==true){
      
      lcd.setCursor(0, 0);
      lcd.print(LCD[tmp]);
      lcd.setCursor(0, 1);
      lcd.print(LCD[tmpd]);
   }
}
```
