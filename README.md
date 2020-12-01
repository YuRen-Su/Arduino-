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
