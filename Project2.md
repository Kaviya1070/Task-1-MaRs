//project2:
Drinking water remainder system 
#Click here to view the tinkercad link
https://www.tinkercad.com/things/eEOyDvtZGID-water-remainder-system-?sharecode=J0kLkWEWNsUiYH1CWGw4ADRUITrgZ5qqZMo_hBRl49I
#Code
const int button=2;
const int buzzer=8;
const int led=13;
unsigned long int starttime=0;
unsigned long int previousblink=0;
unsigned long int blinkinterval=500;
bool ledstate=LOW;
bool running=false;

void setup(){
  pinMode(button,INPUT_PULLUP);
  pinMode(buzzer,OUTPUT);
  pinMode(led,OUTPUT);
  digitalWrite(led,LOW);
  digitalWrite(buzzer,LOW);
}
 void loop(){
  unsigned long int current=millis();
  if (digitalRead(button) == LOW) {
    delay(200); 
    starttime = current;
    running = true;
    ledstate = LOW;
    digitalWrite(led, LOW);
    digitalWrite(buzzer, LOW);
    previousblink = current;
  }
  if (!running) return; 
  unsigned long int elapsed = current - starttime;
  if (elapsed < 10000) {
    digitalWrite(led,LOW);
    digitalWrite(buzzer, LOW);
  }
  else {
      if (current - previousblink >= blinkinterval) {
      ledstate = !ledstate;
      digitalWrite(led, ledstate);
      previousblink = current;
    }
  if (elapsed >= 20000) {
      digitalWrite(buzzer, HIGH);
    } else {
      digitalWrite(buzzer, LOW);
    }
  }
}
#LOGIC
For the water drinking remainding system the logic is simply using the calcuted time interval make the led blink first and later make buzzer 
sounds once the button is pressed everything restart from first
#EXPLANATION
Explanation for water remainder system is we use starttime to record when timer start previous blink to check previoused state , 
blink interval to control speed. Set both buzzer and led both at off state. Next check whether the button is on using digitalRead if it off then make all
state low but make sure to change the running as true as timer starts. If 0 to 10sec means both at off condition.
More than 10 means check led state and reverse the state account to blink interval. If button not pressed still(time more than 20 sec means make buzzer on till the condition satisfy.
Then restart the process again
