//question:Build a reaction time tester

#click here to view tinkercadlink(KINDLY USE SERIAL MONITOR TO SEE THE REACTION TIME)

https://www.tinkercad.com/things/g5u5ws7NlLZ-reaction-time-?sharecode=1mujftISSzpl2IM0_QIeowuaJNz-AmlTWPyN0rbLRpA

#Code

unsigned long int starttime;

unsigned long int stoptime;

void setup(){

    pinMode(2,INPUT);
    
    pinMode(5,OUTPUT);
    
    Serial.begin(9600);
    
    randomSeed(analogRead(0));
    
}

void loop(){

  delay(random(1000,4000));
  
  digitalWrite(5,HIGH);
  
  starttime=millis();
  
  while(digitalRead(2)==LOW){
  
  }
  
  stoptime=millis();
  
  digitalWrite(5,LOW);
  
  Serial.println(stoptime-starttime);
  
  delay(5000);
  
}

#Componenets

1.2 LED

2.Resistors

3.Arduino uno

4.Button

#LOGIC

For building a reaction time tester this is my logic is to keep a timer and we notice two timing.
One is to calculate when the LED is ON and another when button is pressed. Now subtracting both we get reaction time 

#EXPLANATION

Firstly we need to generate a random number to make the led blink at random time . 
For that we use randomseed function to generate different numbers which gives us the starting point. 
analogread function we use to pick a number where arduino reads the voltage on a pin. then the voltage is converted to required numbers from binary to decimal . 
Then we start delay of random function to generate random delay through which the led start blink . now once the led blink we note down the current time using the millis . 
Now we run a loop till the button is on (once the button is on the pin gets voltage and using digital read we can check if it is HIGH then it on) we come out of loop and note down the time now. 
Then we print the subtracted time in serial monitor. 
