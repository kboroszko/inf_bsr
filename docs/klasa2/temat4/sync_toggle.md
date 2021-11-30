# Synchroniczne wyłączanie licznika

```c++

#include <Arduino.h>

#define PinA 7
#define PinB 6
#define PinC 5
#define PinD 4
#define PinE 3
#define PinF 8
#define PinG 10

#define NOTHING 10

#define BUTTON 2


void display(uint8_t x)
{
  if (x == 0)
  {
    //display 0
    digitalWrite(PinA, LOW);
    digitalWrite(PinB, LOW);
    digitalWrite(PinC, LOW);
    digitalWrite(PinD, LOW);
    digitalWrite(PinE, LOW);
    digitalWrite(PinF, LOW);
    digitalWrite(PinG, HIGH);
    return;
  }
  if (x == 1)
  {
    //display 1
    digitalWrite(PinA, HIGH);
    digitalWrite(PinB, LOW);
    digitalWrite(PinC, LOW);
    digitalWrite(PinD, HIGH);
    digitalWrite(PinE, HIGH);
    digitalWrite(PinF, HIGH);
    digitalWrite(PinG, HIGH);
    return;
  }
  if (x == 2)
  {
    //display 2
    digitalWrite(PinA, LOW);
    digitalWrite(PinB, LOW);
    digitalWrite(PinC, HIGH);
    digitalWrite(PinD, LOW);
    digitalWrite(PinE, LOW);
    digitalWrite(PinF, HIGH);
    digitalWrite(PinG, LOW);
    return;
  }
  if (x == 3)
  {
    //display 3
    digitalWrite(PinA, LOW);
    digitalWrite(PinB, LOW);
    digitalWrite(PinC, LOW);
    digitalWrite(PinD, LOW);
    digitalWrite(PinE, HIGH);
    digitalWrite(PinF, HIGH);
    digitalWrite(PinG, LOW);
    return;
  }
  if (x == 4)
  {
    //display 4
    digitalWrite(PinA, HIGH);
    digitalWrite(PinB, LOW);
    digitalWrite(PinC, LOW);
    digitalWrite(PinD, HIGH);
    digitalWrite(PinE, HIGH);
    digitalWrite(PinF, LOW);
    digitalWrite(PinG, LOW);
    return;
  }
  if (x == 5)
  {
    //display 5
    digitalWrite(PinA, LOW);
    digitalWrite(PinB, HIGH);
    digitalWrite(PinC, LOW);
    digitalWrite(PinD, LOW);
    digitalWrite(PinE, HIGH);
    digitalWrite(PinF, LOW);
    digitalWrite(PinG, LOW);
    return;
  }
  if (x == 6)
  {
    //display 6
    digitalWrite(PinA, LOW);
    digitalWrite(PinB, HIGH);
    digitalWrite(PinC, LOW);
    digitalWrite(PinD, LOW);
    digitalWrite(PinE, LOW);
    digitalWrite(PinF, LOW);
    digitalWrite(PinG, LOW);
    return;
  }
  if (x == 7)
  {
    //display 7
    digitalWrite(PinA, LOW);
    digitalWrite(PinB, LOW);
    digitalWrite(PinC, LOW);
    digitalWrite(PinD, HIGH);
    digitalWrite(PinE, HIGH);
    digitalWrite(PinF, HIGH);
    digitalWrite(PinG, HIGH);
    return;
  }
  if (x == 8)
  {
    //display 8
    digitalWrite(PinA, LOW);
    digitalWrite(PinB, LOW);
    digitalWrite(PinC, LOW);
    digitalWrite(PinD, LOW);
    digitalWrite(PinE, LOW);
    digitalWrite(PinF, LOW);
    digitalWrite(PinG, LOW);
    return;
  }
  if (x == 9)
  {
    //display 9
    digitalWrite(PinA, LOW);
    digitalWrite(PinB, LOW);
    digitalWrite(PinC, LOW);
    digitalWrite(PinD, LOW);
    digitalWrite(PinE, HIGH);
    digitalWrite(PinF, LOW);
    digitalWrite(PinG, LOW);
    return;
  }
  // display nothing
  digitalWrite(PinA, HIGH);
  digitalWrite(PinB, HIGH);
  digitalWrite(PinC, HIGH);
  digitalWrite(PinD, HIGH);
  digitalWrite(PinE, HIGH);
  digitalWrite(PinF, HIGH);
  digitalWrite(PinG, HIGH);
  return;
}

uint8_t counter;
bool display_on;

void setup()
{
  // put your setup code here, to run once:
  pinMode(PinA, OUTPUT);
  pinMode(PinB, OUTPUT);
  pinMode(PinC, OUTPUT);
  pinMode(PinD, OUTPUT);
  pinMode(PinE, OUTPUT);
  pinMode(PinF, OUTPUT);
  pinMode(PinG, OUTPUT);

  
  pinMode(BUTTON, INPUT_PULLUP);

  display(10);
  counter = 0;
  display_on = true;
}


void toggleDisplay(){
  display_on = !display_on;
}

void loop()
{
  if(!digitalRead(BUTTON)){ // button pressed
    toggleDisplay();
  }
  counter = (counter + 1) % 10;
  if(display_on){
    display(counter);
  } else {
    display(NOTHING); // display nothing
  }
  delay(1000);
}
```