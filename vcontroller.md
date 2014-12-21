---
title: Virtual Controller
---

<hr id="goals" class="featurette-divider">

<div class="row">
 
 <div class="col-md-8">
### Android application

For the platform to run the virtual controller on we chose Android. It was develped using <a href="http://www.scala-lang.org/">Scala</a> programming language. Scala is modern, staticially typed, multi-paradigm language. It mixes object-oriented paradigm with funcional paradigm. This allows programs written in Scala to be very concise. Another interesting property of Scala is that it is fully interoperable with Java, and Scala source code is intended to be compiled to Java bytecode. As a result of this we can develop apps in Scala for the Dalvik VM. There is a great <a href="https://github.com/yareally/android-scala-intellij-no-sbt-plugin">sample</a> application with detailed instruction how to start developing apps for Android in Scala using IntelliJ IDEA. <a href="https://github.com/Pa00k/pa00k-controller">Source</a> and installer oand installer of he application is available on GitHub. Minimal required version of Android is 2.3.3 (Gingerbread). 
 </div>

 <div class="col-md-4">
<img class="img-responsive img-rounded centre-img" src="/images/scaladroid.png" alt="scala droid" width="250px">
 </div>

</div>

<hr id="goals" class="featurette-divider">

<div class="row">
 
 <div class="col-md-6">
### User Interface
<p>The UI offers an easy and intuitive way of driving the robot. It consists of two surfaces and four buttons. The left surface enables the user to command the robot to translate in any direction. Right surface is used to rotate the robot.</p>
<p>The buttons allow some special movement pattern. They are described from left to right:
<ol>
 <li>rising the body</li>
 <li>lowering the body</li>
 <li>toogle the tilt mode - mode in which the robot mirrors the tilt of the smartphone</li>
 <li>toogle rotational and translational mode - it allows the robot to translate and rotates the body in the same time. During this mode the robot can't walk.</li>
</ol></p>
 </div>

 <div class="col-md-6">
<img class="img-responsive img-rounded centre-img" src="/images/app.jpg" alt="scala droid" >
 </div>

</div>

<hr id="goals" class="featurette-divider">

<div class="row">
 <div class="col-md-8">
### Driving 
<p>Driving the robot is really easy. It was largely inspired by the way popular <em>gamepads</em> are used to play video games. The user is driving the robot with his thumbs, using his left thumb to translate and his left thumb to rotate the robot. When the thumb is pressed down on the surface a circle is drawn around the finger. This circle represents the area of sensitivity of the surface. Further away the thumb is from the centre of the circle, the faster the robot moves. When the finger crosses over the edge of the circle, top speed is reached.</p>
 </div>

 <div class="col-md-4">
<img class="img-responsive img-rounded centre-img" src="/images/circles.jpg" alt="scala droid" >
 </div>

</div>

<hr id="goals" class="featurette-divider">

<div class="row">
 <div class="col-md-6">
### Connecting to the pa00k
<p>
When the app starts it will demad that Bluetooth must be turned on. Allowing this, we land on a screen from which we can choose a bluetooth device to connect to. Selecting the pa00k the app prompts us with the driving interface described above.
</p>
 </div>

 <div class="col-md-6">
<img class="img-responsive img-rounded centre-img" src="/images/bt_connect.jpg" alt="scala droid" >
 </div>

</div>

<hr id="goals" class="featurette-divider">

<div class="row">
 <div class="col-md-6">
### Bluetooth communication
<p>
Communication between the Android device and the robot is one way. Every 100 ms a packet is sent to the robot containig the current state of the UI. The Bluetooth connection to the robot is serial, so we created a simple way to synchronize the packets. We begin each packet with character 'P' and the rest of the cells represent:

<ol>
 <li>x1, y1, x2, y2 - thumbs' coordinates on the control surface (range [-100..100] </li>
 <li>hight of the body [1..3]</li>
 <li>level of stride [1..3]</li>
 <li>tilt and rot/trans mode toogle [0,1]</li>
 <li>acceleration of the phone in x and y axis, required for the tilting</li>

</ol>
</p>
 </div>

 <div class="col-md-6">
<img class="img-responsive img-rounded centre-img" src="/images/packet.jpg" alt="scala droid" >
 </div>

</div>

