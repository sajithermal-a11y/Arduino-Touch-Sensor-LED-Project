# Arduino-Touch-Sensor-LED-Project
int touchPin = 7;

int led1 = 13;
int led2 = 12;
int led3 = 11;

int state = 0;
bool lastTouch = LOW;

void setup() {
  pinMode(touchPin, INPUT);
  
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
}

void loop() {

  bool touch = digitalRead(touchPin);

  if (touch == HIGH && lastTouch == LOW) {
    state++;
    if (state > 5) state = 1;

    if (state == 1) {
      digitalWrite(led1, HIGH);
      digitalWrite(led2, LOW);
      digitalWrite(led3, LOW);
    }

    if (state == 2) {
      digitalWrite(led1, LOW);
      digitalWrite(led2, HIGH);
      digitalWrite(led3, LOW);
    }

    if (state == 3) {
      digitalWrite(led1, LOW);
      digitalWrite(led2, LOW);
      digitalWrite(led3, HIGH);
    }

    if (state == 4) {
      digitalWrite(led1, HIGH);
      digitalWrite(led2, HIGH);
      digitalWrite(led3, HIGH);
    }

    if (state == 5) {
      digitalWrite(led1, LOW);
      digitalWrite(led2, LOW);
      digitalWrite(led3, LOW);
    }

    delay(200); // debounce
  }

  lastTouch = touch;
}
