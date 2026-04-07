// project :
OBSTACLE FINDING ROBOT
//click here to view my tinkercad link
https://www.tinkercad.com/things/5ZTogBTE3OS-grand-hango/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard%2Fdesigns%2Fcircuits&sharecode=ey8G7Pf0PNvMl9qgiXZxgbakthKLdXDJdOqJk37-aiw
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
