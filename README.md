# Free-Thinker
americanspacedesignchallenge
// C++ code
//
int a = 0;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);  // Clear the trigger
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  // Sets the trigger pin to HIGH state for 10 microseconds
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  // Reads the echo pin, and returns the sound wave travel time in microseconds
  return pulseIn(echoPin, HIGH);
}

void setup()
{
  pinMode(11, OUTPUT);
  pinMode(10, OUTPUT);
}

void loop()
{
  a = 0.01723 * readUltrasonicDistance(13, 12);
  if (a < 20) {
    digitalWrite(11, HIGH);
    digitalWrite(10, HIGH);
  } else {
    digitalWrite(11, LOW);
    digitalWrite(10, LOW);
  }
  delay(10); // Delay a little bit to improve simulation performance
}
