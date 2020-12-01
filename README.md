# Arduino-Classroom-learning-content
## Topic One - LED blinking
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/LED%20blink%20GIF.gif)
<pre style="word-wrap: break-word; white-space: pre-wrap;">void setup() {
  // put your setup code here, to run once:
   pinMode(2,OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  digitalWrite(2,HIGH);
  delay(200);
  digitalWrite(2,LOW);
  delay(200);
}
</pre>
##  Topic Two - LED turn on and off one by one from left to right
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/LED%20turn%20on%20and%20off%20one%20by%20one%20from%20left%20to%20right%20GIF.gif)
<pre style="word-wrap: break-word; white-space: pre-wrap;">int LED=5;
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
</pre>
##  Topic Three - LED breathing light
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/LED%20breathing%20light%20GIF.gif)
<pre style="word-wrap: break-word; white-space: pre-wrap;">int value=255; int x=-15;
void setup() {
  // put your setup code here, to run once:
pinMode(3,OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
if (value&lt;=0 || value&gt;=255) x=-x;
analogWrite(3,value);
delay(80);
value=value-x;
}
</pre>
