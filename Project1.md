// project :
OBSTACLE DETECTING ROBOT

//click here to view my tinkercad link

https://www.tinkercad.com/things/b7rSJbpgh8P-obstacle-detecting-robot-?sharecode=TcRuIBeyhn1_yVGvoiJFzYTQo3ObYNBynyuKkVZQyEU

#Code

#include<Servo.h>

Servo s;

const int trig=9;

const int echo=10;

int l1=2;

int l2=3;

int l3=4;

signed long int d;

float dist;

void setup(){

  pinMode(l1,OUTPUT);
  
  pinMode(l2,OUTPUT);
  
  pinMode(l3,OUTPUT);
  
  pinMode(trig,OUTPUT);
  
  pinMode(echo,INPUT);
  
  s.attach(5);
  
  Serial.begin(9600);
  
}

void loop(){

  digitalWrite(trig,LOW);
  
  delayMicroseconds(2);
  
  digitalWrite(trig,HIGH);
  
  delayMicroseconds(10);
  
  digitalWrite(trig,LOW);
  
  d=pulseIn(echo,HIGH);
  
  dist=d*0.034/2;
  
  Serial.println(dist);
  
  if(dist>30){
  
    digitalWrite(l1,HIGH);
    
    digitalWrite(l2,LOW);
    
    digitalWrite(l3,LOW);
    
    s.write(90);
    
  }
  
  else if(dist>=15&&dist<30){
  
    digitalWrite(l1,LOW);
    
    digitalWrite(l2,HIGH);
    
    digitalWrite(l3,LOW);
    
    s.write(45);
    
  }
  
  else if(dist<15&&dist>0){
  
    digitalWrite(l1,LOW);
    
    digitalWrite(l2,LOW);
    
    digitalWrite(l3,HIGH);
    
    s.write(0);
    
  }
  
  delay(200);
  
}

#LOGIC

Logic of obstacles finding robot is first we use a ultrasonic sensor to detect object distance if the distance comes under the specific conditions the colour of led will blink according to it . Then the bot will work based on the condition under which colour it is blinking

#EXPLANATION

Explain would be , Connecting the ultrasonic pins that is trig and echo to Arduino pins and  fix 3 leds , connect servo motor also and initialise it. After ensuring clean signal we send pulse to trigger. Using the variable d to calculate the time using pulIn function. Now d will be converted to distance in cm through dist variable. After ensuring clean signal we send pulse to trigger. Based on the distance range first the green light would blink , as it reaches close yellow light blinks(bot slows it's speed)when reaches the max point red light blinks(bot stops or uturn). This is how it is done
