Smart Drive: A Revolutionary Anti-Drunk Driving Lock 
System


// Include the necessary libraries
#include <AFMotor.h>
// Define motor connections
AF_DCMotor motor1(1);
AF_DCMotor motor2(2);
AF_DCMotor motor3(3);
AF_DCMotor motor4(4);
const int alcoholSensorPin = A1;
int buzzer=A2;
void setup() {
  // Set motor speed (0-255)
  motor1.setSpeed(200);
  motor2.setSpeed(200);
  motor3.setSpeed(200);
  motor4.setSpeed(200);
  Serial.begin(9600);
}
 void loop() {
  // Read alcohol sensor value
  int alcoholValue = analogRead(alcoholSensorPin);

  // Print alcohol sensor value to serial monitor
  Serial.print("Alcohol Value: ");
  Serial.println(alcoholValue);
   if (alcoholValue > threshold) {
    // Alcohol detected, take action here
    Serial.println("Alcohol detected!");
     motor1.run(RELEASE);
     motor2.run(RELEASE);
    motor3.run(RELEASE);
    motor4.run(RELEASE);
    noTone(buzzer);
  } 
else {
    // No alcohol detected
    Serial.println("No alcohol detected.");
    motor1.run(FORWARD);
    motor2.run(FORWARD);
    motor3.run(FORWARD);
    motor4.run(FORWARD);
   Tone(buzzer,1000);
}
}
