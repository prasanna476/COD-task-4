# COD-task-4#include <SoftwareSerial.h>

SoftwareSerial BT(10, 11); // RX, TX for Bluetooth

const int ledPin = 8; 

void setup() {
  Serial.begin(9600);
  BT.begin(9600);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  if (BT.available()) {
    String command = BT.readStringUntil('\n');
    command.trim(); // Remove any trailing characters

    Serial.println("Received: " + command);

    if (command == "ON") {
      digitalWrite(ledPin, HIGH);
      Serial.println("LED ON");
    }
    else if (command == "OFF") {
      digitalWrite(ledPin, LOW);
      Serial.println("LED OFF");
    }
  }
}
