# Arduino-Classroom-learning-content
## LED blinking
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
