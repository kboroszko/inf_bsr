# Timery

<!-- https://www.instructables.com/Arduino-Timer-Interrupts/ -->

```c++

#include <Arduino.h>


bool b_val = false;


void setup() {
  // put your setup code here, to run once:
  pinMode(8, OUTPUT);
  pinMode(9, OUTPUT);

  
  cli();//stop interrupts

  //set timer0 interrupt at 2kHz
  TCCR0A = 0;// set entire TCCR0A register to 0
  TCCR0B = 0;// same for TCCR0B
  TCNT0  = 0;//initialize counter value to 0
  // set compare match register for 2khz increments
  OCR0A = 124;// = (16*10^6) / (2000*64) - 1 (must be <256)

  // turn on CTC mode
  TCCR0A |= (1 << WGM01);
  // Set CS01 and CS00 bits for 64 prescaler
  TCCR0B |= (1 << CS01) | (1 << CS00);   
  // enable timer compare interrupt
  TIMSK0 |= (1 << OCIE0A);


  
  sei();//allow interrupts
}


void toggle(){
  b_val = !b_val;
}

void display(){
  if(b_val){
    digitalWrite(8, HIGH);
    digitalWrite(9, LOW);
  } else {
    digitalWrite(8, LOW);
    digitalWrite(9, HIGH);
  }
}


ISR(TIMER0_COMPA_vect){//timer0 interrupt 2kHz toggles pin 8
//generates pulse wave of frequency 2kHz/2 = 1kHz (takes two cycles for full wave- toggle high then toggle low)
  toggle();
  display();
}


void loop() {
}


```