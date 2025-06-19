#include <Arduino.h>
#include <DFRobotDFPlayerMini.h>
// Distance threshold (cm)
const int threshold = 25;
// DFPlayer & Serial
HardwareSerial dfSerial(2);
DFRobotDFPlayerMini player;
#define Trig 22
#define Echo 23
void setup() {
  // put your setup code here, to run once:
  Serial.begin(115200);
  pinMode(Trig,OUTPUT);
  pinMode(Echo,INPUT);
  
  dfSerial.begin(9600, SERIAL_8N1, 18, 19);//Rx,Tx pins for DFDminPlayer
   if (!player.begin(dfSerial)) {
    Serial.println("DFPlayer init failed!");
    while (1);
  }
  player.volume(25); // set volume (0–30)
  Serial.println("Setup complete");
}

void loop() {
  // main code here, to run repeatedly:
  digitalWrite(Trig, LOW);
  delayMicroseconds(2);
  digitalWrite(Trig, HIGH);
    delayMicroseconds(10);
  digitalWrite(Trig, LOW);
 unsigned long duration = pulseIn(Echo, HIGH);
  float distance=duration*0.034/2;
  Serial.print("Distance: ");
  Serial.println(distance);
Serial.print("cm");
  if(distance > 0 && distance < threshold){
     Serial.printf("Detected @ %.1f cm → PLAY\n", distance);
      player.play(3);
  }
  else{
  Serial.println("Object left range — stopping");
    player.stop();
    }
  delay(200);
}




