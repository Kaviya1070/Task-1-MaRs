
//question:Build a circuit with 3 led , where leds blink at time interval of 500,1000,1500

##click here to view my tinkercad link:

https://www.tinkercad.com/things/2nPODYCnBaw-blinking-led?sharecode=1yry42pHJckaeXGdID359HLpOObyECxOelCqVf-8mJI

##code 

`cpp
int state1=LOW;

int state2=LOW;

int state3=LOW;


unsigned long int past1=0;

unsigned long int past2=0;

unsigned long int past3=0;

void setup(){

  pinMode(2,OUTPUT);
  
  pinMode(3,OUTPUT);
  
  pinMode(4,OUTPUT);
  
}

void loop(){

  unsigned long int current=millis();
  
  if(current-past1>=500){
  
    state1=!state1;
    
    digitalWrite(2,state1);
    
    past1=current;
    
  }
  
  if(current-past2>=1000){
  
    state2=!state2;
    
    digitalWrite(3,state2);
    
    past2=current;
    
  }
  
  if(current-past3>=1500){
  
    state3=!state3;
    
    digitalWrite(4,state3);
    
    past3=current;
    
  }
  
}

`

##COMPONENETS:
1.3 LED

2.3 resistors

3.Arduino uno

4.wires

#LOGIC:

Logic is to make the 3 led blink at different time interval by subtracting the present and past time if it crosses the given time then led should change the current state

##Explanations:

First make the 3 led in off condition. Then set the past time as 0 initially for all 3. Now we will use the function millis which calculate the current time since we start our simulation. Our main condition is to make 3 led blink independently so we cannot use the delay option as when it is used the whole circuit will stop working in the time mentioned in delay. Now we write a loop in which the subtraction between the present time and past time reaches the given interval then we change the present state of led and finnally make the past time as current time
