# Counter

Efektem pracy po poprzednim temacie powinien być program pozwalający wyświetlać cyfry na wyświetlaczu 7-segmentowym.


Teraz spróbujmy zrobić program który będzie działał następująco:
- Będzie wyświetlał liczby od 0 do 9, co 0.1 sekundy.
- Będzie zatrzymywał licznik po wciśnięciu guzika.

Żeby to zrobić podłączymy guzik do pinu nr. 2. (To ważne żeby to był dokładnie ten pin)
Jeśli używasz tego pinu do wyświetlania liczb, zmodyfikuj swój program tak żeby używał innego pinu, a do 2 podłącz guzik.

Do drugiego końca guzika podłączamy GND. Ustawimy pin 2 tak żeby był do niego podłączony rezystor pull-up.
Dzięki temu, jeśli guzik pozostaje nie wciśnięty, pin 2 ma zawsze wartość 1, natomiast po wciśnięciu będzie miał wartość 0.

```c++
#include <Arduino.h>

#define BUTTON 2

void setup()
{
  Serial.begin(9600);

  pinMode(BUTTON, INPUT_PULLUP);
}


void loop()
{
  Serial.println(digitalRead(BUTTON));
  delay(10);
}
```

Teraz spróbuj napisać program który po wciśnięciu guzika wyłącza licznik, a po ponownym naciśnięciu włącza spowrotem.

[Rozwiązanie](temat4/sync_togle.md)

Jaki jest z tym problem?

# Przerwania

Przerwań używamy żeby zatrzymać kod który właśnie się wykonuje żeby wykonać inną operację.

```c++
#include <Arduino.h>

#define BUTTON 2

uint8_t counter;
volatile bool counter_on;


void toggleCounter(){
  counter_on = !counter_on;
}

void setup(){
  counter = 0;
  counter_on = true;
  Serial.begin(9600);

  pinMode(BUTTON, INPUT_PULLUP);

  attachInterrupt(digitalPinToInterrupt(BUTTON), toggleCounter, FALLING);
}


void loop(){
  
  Serial.println(counter);
  
  if(counter_on){
    counter += 1;
  }
  delay(50);
}

```


# Debouncing

Zauważyłeś że czasem licznik się nie wyłącza mimo że klikasz? Jak myślisz, dlaczego?

```c++
#include <Arduino.h>

#define BUTTON 2
#define DEBOUNCE_TIME_MS 5

uint8_t counter;
volatile bool counter_on;
volatile long last_interrupt_time;


void toggleCounter(){
  long current_time = millis();
  if(current_time - last_interrupt_time > DEBOUNCE_TIME_MS){
    last_interrupt_time = current_time;
    counter_on = !counter_on;
  }
}

void setup(){
  counter = 0;
  counter_on = true;
  Serial.begin(9600);
  last_interrupt_time = 0;

  pinMode(BUTTON, INPUT_PULLUP);

  attachInterrupt(digitalPinToInterrupt(BUTTON), toggleCounter, FALLING);
}


void loop(){
  
  Serial.println(counter);
  
  if(counter_on){
    counter += 1;
  }
  delay(50);
}
```






















