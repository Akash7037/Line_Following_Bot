- 👋 Hi, I’m @Akash7037
# Line Following IOT 
A line-following robot is an autonomous machine that can follow a predefined path, typically marked by a black or white line on the ground. Using an Arduino Uno and 2 IR (infrared) sensors, you can build a simple and effective line-following robot.
# Components 
- Arduino Uno
- 2 Ir sensor (obstacles avoid sensor)
- Driver module (L298N)
- 2 Dc motors
- chassis
- Batteries
# Connection 
## IR sensor 
- Ir gnd = Arudino gnd
- Ir vcc = arudino 5v
- Ir out (left) = Arudino 2
- Ir out (right) = Arduino 3
## Driver Module 
- In1 = d 4
- In2 = d 5
- In4 = d 6
- In5 = d 7
- ENA = 9
- ENB = 10
- 12v or 5v = battery +ve
- gnd = -ve of battery
- Out 1,2 = motor left
- Out 3,4 = Motor right
  # CoDE
  ```
  #define leftSensor 2     // Left IR sensor
   #define rightSensor 3    // Right IR sensor
  #define leftMotor1 4     // IN1 on motor driver (Left Motor)
  #define leftMotor2 5     // IN2 on motor driver (Left Motor)
  #define rightMotor1 6    // IN3 on motor driver (Right Motor)
  #define rightMotor2 7    // IN4 on motor driver (Right Motor)
  #define enA 9            // ENA pin for speed control (Left Motor)
  #define enB 10           // ENB pin for speed control (Right Motor)
  int motorSpeed = 150;

  void setup() {
  pinMode(leftSensor, INPUT);
  pinMode(rightSensor, INPUT);
  pinMode(leftMotor1, OUTPUT);
  pinMode(leftMotor2, OUTPUT);
  pinMode(rightMotor1, OUTPUT);
  pinMode(rightMotor2, OUTPUT);
  pinMode(enA, OUTPUT);
  pinMode(enB, OUTPUT);

  // Set initial speed
  analogWrite(enA, motorSpeed);
  analogWrite(enB, motorSpeed);
  }

  void loop() {
  int left = digitalRead(leftSensor);
  int right = digitalRead(rightSensor);

  if (left == LOW && right == LOW) { // Both sensors on the line
    moveForward();
  } else if (left == HIGH && right == LOW) { // Left sensor off the line
    turnRight();
  } else if (left == LOW && right == HIGH) { // Right sensor off the line
    turnLeft();
  } else { // Both sensors off the line
    stopMotors();
  }
  }

  // Function to move forward
  void moveForward() {
  digitalWrite(leftMotor1, HIGH);
  digitalWrite(leftMotor2, LOW);
  digitalWrite(rightMotor1, HIGH);
  digitalWrite(rightMotor2, LOW);
  }

  // Function to turn left
  void turnLeft() {
  digitalWrite(leftMotor1, LOW);
  digitalWrite(leftMotor2, HIGH);
  digitalWrite(rightMotor1, HIGH);
  digitalWrite(rightMotor2, LOW);
  }

  // Function to turn right
  void turnRight() {
  digitalWrite(leftMotor1, HIGH);
  digitalWrite(leftMotor2, LOW);
  digitalWrite(rightMotor1, LOW);
  digitalWrite(rightMotor2, HIGH);
  }

   // Function to stop motors
  void stopMotors() {
  digitalWrite(leftMotor1, LOW);
  digitalWrite(leftMotor2, LOW);
  digitalWrite(rightMotor1, LOW);
  digitalWrite(rightMotor2, LOW);
  }
![](IMG_20241115_162842231_HDR.jpg)
<!---
Akash7037/Akash7037 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
