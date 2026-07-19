# Serial-Controlled-LED-System-Using-Arduino-
#This project uses Arduino to control Red, Green, and Blue LEDs through the Serial Monitor. The user selects the LED color and enters the number of times it should #blink. The Arduino then blinks the selected LED according to the given input.
String name;
String msg1 = "Enter which LED you want to blink?";
String msg2 = "Enter how many times you want to blink?";

int j;
int number;

int redpin = 12;
int bluepin = 11;
int greenpin = 10;
int dt = 500;

void setup() {
  Serial.begin(9600);

  pinMode(redpin, OUTPUT);
  pinMode(bluepin, OUTPUT);
  pinMode(greenpin, OUTPUT);
}

void loop() {

  Serial.println(msg1);

  // Wait for color input
  while (Serial.available() == 0) {
  }

  name = Serial.readString();
  name.trim();  // Removes \n and \r

  if (name == "green") {

    Serial.println(msg2);

    // Wait for number input
    while (Serial.available() == 0) {
    }

    number = Serial.parseInt();

    for (j = 1; j <= number; j++) {
      digitalWrite(greenpin, HIGH);
      digitalWrite(redpin, LOW);
      digitalWrite(bluepin, LOW);
      delay(dt);

      digitalWrite(greenpin, LOW);
      delay(dt);
    }
  }

  else if (name == "red") {

    Serial.println(msg2);

    while (Serial.available() == 0) {
    }

    number = Serial.parseInt();

    for (j = 1; j <= number; j++) {
      digitalWrite(redpin, HIGH);
      digitalWrite(greenpin, LOW);
      digitalWrite(bluepin, LOW);
      delay(dt);

      digitalWrite(redpin, LOW);
      delay(dt);
    }
  }

  else if (name == "blue") {

    Serial.println(msg2);

    while (Serial.available() == 0) {
    }

    number = Serial.parseInt();

    for (j = 1; j <= number; j++) {
      digitalWrite(bluepin, HIGH);
      digitalWrite(greenpin, LOW);
      digitalWrite(redpin, LOW);
      delay(dt);

      digitalWrite(bluepin, LOW);
      delay(dt);
    }
  }

  else {
    Serial.println("Invalid color!");

    digitalWrite(redpin, LOW);
    digitalWrite(bluepin, LOW);
    digitalWrite(greenpin, LOW);
  }
}
