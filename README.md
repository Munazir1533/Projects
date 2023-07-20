                **ABSTRACT**
This project report presents an automatic door-opening system with a visitor counter employing ARDUINO UNO.A PIR sensor in conjunction with the motor driver module 
L293D and Arduino microcontroller implement the door opening mechanism by detecting human movement near the door.The visitor counter shows the number of persons who entered the room.
The open-source Arduino Software Integrated Development Environment (IDE) software implements and uploads the code to the Arduino board.The microcontroller sends an active high signal to the motor driver which controls the door and its status is displayed on the LCD screen.
The visitor counter will show how many persons enter the room. The circuit is powered using two standard 9V PP3/6FF22 batteries. The software used to implement the code is ARDUINO Integrated Development Environment.

          **PROGRAMMING CODE.**
#include <LiquidCrystal.h>

 LiquidCrystal lcd(13, 12, 11, 10, 9, 8); 
#define PIR_sensor A0
#define counter 7
#define m11 0
#define m12 1
void setup()
{
lcd.begin(16, 2);
 lcd.clear ();
 pinMode(m11, OUTPUT);
 pinMode(m12, OUTPUT);
 pinMode(PIR_sensor, INPUT);
 pinMode(counter , OUTPUT);
 lcd.print("AUTOMATIC DOOR");
 lcd.setCursor(0,1);
 lcd.print("OPENING SYSTEM ");
 delay(1000);
 lcd.print("WITH VISITOR ");
 delay(1000);
lcd.setCursor(0,1);
 lcd.print(" COUNTER ");
delay(1000);
 //initialize visitor counter as int visitor =0
 }
 void loop()
{
 
 if(digitalRead(PIR_sensor))
{
 digitalWrite(counter,HIGH);
 digitalWrite(counter,LOW);
 lcd.setCursor(0,0);
 lcd.print("MovementDetected");
 lcd.setCursor(0,1);
 lcd.print(" Gate Opened ");
 digitalWrite(m11, HIGH); // gate opening
 delay(1000);
 digitalWrite(m12, LOW);
 delay(1000);
 digitalWrite(m11, LOW); // gate stop for a while
 digitalWrite(m12, LOW);
 delay(1000);
 lcd.clear();
 lcd.setCursor(0, 0);
 lcd.print(" Gate Closed ");
 digitalWrite(m11, LOW); // gate closing
 digitalWrite(m12, HIGH);
 delay(2000);
 digitalWrite(m11, LOW);
 digitalWrite(m12,LOW);
 delay(1000);
 //display visitor count to seven segment display
 //please increase visitor count ++
}
 else
{
 digitalWrite(counter,LOW);
 lcd.setCursor(0,0);
 lcd.print(" No Movement");
 delay(200);
 lcd.setCursor(0,1);
 lcd.print(" Gate Closed ");
 digitalWrite(m11, LOW);
 digitalWrite(m12, LOW); }
}

