# A pwd motor controller

# MotorController class
// Sets the pwd pin used by the controller.

void setPin(int pin);
                                                               
// Returns the current pwd pin.

int getPin();

// Sets the percent power output.

// -1.0 to 1.0

void setPower(double power);
                                                               
// Gets the percent power the motor is set to.

// -1.0 to 1.0

double getPower();
                                                               
// Sets power to 0.0

void stop();
                                                               
// The motor may not be perfect so there are dead zones.

// By default motorMinDeadZone is 0 and motorMaxDeadZone is 180

void setDeadZones(int motorMinDeadZone, int motorMaxDeadZone);

# Example code

\#include "MotorController.h"

// Controlls a motor with the motor controller library and a pot.

\#define POT_PIN A5

MotorController spx;

void setup() {

  spx.setPin(9);

  Serial.begin(9600);

}

void loop() {

  int input_value = analogRead(POT_PIN);

  double power = (input_value / 336.5) - 1;

  Serial.println(power);

  spx.setPower(power);

  delay(15);
}