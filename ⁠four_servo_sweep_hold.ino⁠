#include <Servo.h>

// Instantiate 4 servo motor controllers
Servo servo1;
Servo servo2;
Servo servo3;
Servo servo4;

unsigned long startTime; // Variable to store the start time of the simulation
const unsigned long sweepDuration = 2000; // Duration for the sweep phase (2000 ms = 2 seconds)

int angle = 0;      // Initial starting angle for the motors
int direction = 1;  // Movement direction multiplier (1 for increment, -1 for decrement)

void setup() {
  // Attach the 4 servo motors to their respective PWM-capable digital pins
  servo1.attach(3);
  servo2.attach(5);
  servo3.attach(6);
  servo4.attach(9);

  // Record the starting time when the program begins
  startTime = millis();
}

void loop() {
  // Calculate the elapsed time since the start
  unsigned long currentTime = millis() - startTime;

  // Phase 1: Run the sweep motion for the first 2 seconds
  if (currentTime < sweepDuration) {
    servo1.write(angle);
    servo2.write(angle);
    servo3.write(angle);
    servo4.write(angle);

    angle += direction * 5; // Step size for smooth movement

    // Reverse direction if boundaries (0 or 180 degrees) are reached
    if (angle >= 180 || angle <= 0) {
      direction = -direction;
    }
    delay(15); // Small delay for smooth transition steps

  } else {
    // Phase 2: After 2 seconds, stop sweeping and hold firmly at 90 degrees
    servo1.write(90);
    servo2.write(90);
    servo3.write(90);
    servo4.write(90);

    // Infinite loop to safely halt further code execution and keep motors holding position
    while (true) {
      // Do nothing, maintaining the 90-degree hold state
    }
  }
}
