# Arduino-Classroom-learning-content
## Topic One - LED blinking
![](https://github.com/YuRen-Su/Arduino-Classroom-learning-content/blob/main/LED%20blink%20GIF.gif)
<pre><span class="pl-k">void</span> <span class="pl-en">setup</span>() {
  <span class="pl-c"><span class="pl-c">//</span> put your setup code here, to run once:</span>
   <span class="pl-c1">pinMode</span>(<span class="pl-c1">2</span>,OUTPUT);
}

<span class="pl-k">void</span> <span class="pl-en">loop</span>() {
  <span class="pl-c"><span class="pl-c">//</span> put your main code here, to run repeatedly:</span>
 <span class="pl-c1">digitalWrite</span>(<span class="pl-c1">2</span>,HIGH);<span class="pl-c"><span class="pl-c">//</span>滅</span>
 <span class="pl-c1">delay</span>(<span class="pl-c1">200</span>);
<span class="pl-c1">digitalWrite</span>(<span class="pl-c1">2</span>,LOW);<span class="pl-c"><span class="pl-c">//</span>亮</span>
 <span class="pl-c1">delay</span>(<span class="pl-c1">200</span>);
｝</pre>
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
