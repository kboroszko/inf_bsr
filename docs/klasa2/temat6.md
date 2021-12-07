# I2C

Protokół I2C służy do komunikacji między mikrokontrolerem a peryferiami.

Jest to protokół komunikacji w której jest ustalona hierarchia: master - slave.

Master może być podłączony na raz do wielu peryferiów które zachowują się jak slave.
![jeden_master](https://www.circuitbasics.com/wp-content/uploads/2016/01/Introduction-to-I2C-Data-Transmission-Diagram-START-CONDITION-3-768x695.png)

Master decyduje kiedy rozpoczyna się transmisja i zaczyna wysyłać dane do slave'a.

Dane są wysyłane w formie pakietu który wygląda w ten sposób:
![pakiet I2C](https://www.circuitbasics.com/wp-content/uploads/2016/01/Introduction-to-I2C-Message-Frame-and-Bit-2-1024x258.png)

- Master najpierw wysyła 7-bitowy adres urządzenia z którym chciałby się komunikować. 
- Następnie wysyła jeden bit który oznacza że będzie wysyłał lub odbierał dane.
- Następnie czeka na slave'a który powinien odpowiedzieć sygnałem który nazywamy `ACK` lub `NACK` od słowa ACKNOWLEDGE. Ten bit oznacza czy slave otrzymał wiadomość bez zakłóceń.
- Następnie master wysyła/odbiera 8 bitów wiadomości po których znów czeka na `ACK/NACK`.
- Master wysyła/odbiera dane w 8 bitowych pakietach aż stwierdzi że to koniec. Wtedy wysyła znak końca komunikacji.

### Rozumiesz dlaczego ta komunikacja nazywa się master/slave?

<br>

# Praktyka

Program do skanowania urządzęń I2C z tej [strony](https://www.makerguides.com/character-i2c-lcd-arduino-tutorial/).
```c++
#include <Arduino.h>
#include <Wire.h>
void setup() {
  Wire.begin();
  Serial.begin(9600);
  while (!Serial);
  Serial.println("\nI2C Scanner");
}
void loop() {
  byte error, address;
  int nDevices;
  Serial.println("Scanning...");
  nDevices = 0;
  for (address = 1; address < 127; address++ ) {
    Wire.beginTransmission(address);
    error = Wire.endTransmission();
    if (error == 0) {
      Serial.print("I2C device found at address 0x");
      if (address < 16)
        Serial.print("0");
      Serial.print(address, HEX);
      Serial.println("  !");
      nDevices++;
    }
    else if (error == 4) {
      Serial.print("Unknown error at address 0x");
      if (address < 16)
        Serial.print("0");
      Serial.println(address, HEX);
    }
  }
  if (nDevices == 0)
    Serial.println("No I2C devices found\n");
  else
    Serial.println("done\n");
  delay(5000);
}
```

To pozwala nam na komunikację z peryferiami.

# Termometr

Spróbujmy podłączyć termometr. Do tego potrzebujemy biblioteki która pozwoli nam na komunikację z nim.
Na szczęście w internecie jest już mnóstwo gotowych rozwiązań, także do naszego termometru, takich jak ta biblioteka: [LINK](https://platformio.org/lib/show/532/BMP180/examples).


Żeby ją zainstalować, trzeba otworzyć terminal PlatformIO klikając na kwadracik ze strzałką na dolnym pasku vscode.
![ikonka](temat6/ikonka.png)

Tam wpisujemy komendę do zainstalowania nowej biblioteki:
```bash
pio lib install "lowpowerlab/BMP180"
```

Teraz możemy używać tej biblioteki wpisując umieszczając odpowiednie include'y na początku programu:

```c++
#include <SFE_BMP180.h>
```

Żeby dowiedzieć się jak jej używać warto spojrzeć na przykład który jest na stronie do której link podałem powyżej. Dla ułatwienia poniżej też jest instrukcja.

Żeby używać termometru musimy stwożyć instancję klasy `SFE_BMP180` który dostarcza nam biblioteka. Robimy to jedną linijką na początku programu, poza funkcjami `loop` i `setup`. W ten sposób powstanie zmienna globalna którą możemy używać wszędzie w naszym programie.

```c++
SFE_BMP180 probe;
```

Trzeba jeszcze pamiętać o zainicjowaniu komunikacji z peryferium przy starcie mikrokontrolera.
Gdzie umieścić tą linijkę?
```c++
probe.begin();
```

Teraz żeby zmierzyć temperaturę musimy rozpocząć pomiar.
```c++
probe.startTemperature();
```
Będzie tym dokładniejszy im dłużej trwa. Sekunda wystarczy.
```c++
delay(1000);
```
Na koniec odczytujemy wartość. Żeby to zrobić, podajemy zmienną typu `double` jako argument funkcji `probe.getTemperature(temp)`. Ta funkcja, podczas wykonywania, sprawdzi temperaturę i zapisze ją w tej zmiennej.
```c++
double temp;
probe.getTemperature(temp);
```

Teraz zrób to sam w swoim programie i spróbuj sprawdzić temperaturę w pokoju w którym jesteś.
Czy umiesz zmierzyć ciśnienie?

# LCD

Nauczymy się używać LCD. Skożystamy z tego że ktoś napisał już bibliotekę do obsługi takiego ekranu.

Żeby ją zainstalować, trzeba otworzyć terminal PlatformIO klikając na kwadracik ze strzałką na dolnym pasku vscode.
![ikonka](temat6/ikonka.png)

Tam wpisujemy komendę do zainstalowania nowej biblioteki:
```bash
pio lib install "marcoschwartz/LiquidCrystal_I2C"
```

Teraz możemy używać tej biblioteki wpisując umieszczając odpowiednie include'y na początku programu:

```c++
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
```

żeby używać tej biblioteki najpierw musimy zadeklarować jakiego ekranu używamy i pod jakim adresem się znajduje. W tym celu umieszczamy następującą linijkę na samym początku programu:
```c++
// set the LCD address to 0x27 for a 16 chars and 2 line display
LiquidCrystal_I2C lcd(0x27, 20, 2);
```

Przy starcie mikrokontrolera musimy wykonać kilka instrukcji żeby uruchomić ekran:
```c++
  lcd.init(); // initialize the lcd
  lcd.backlight();
  lcd.begin(20, 2);
```

Następnie żeby wypisać coś na ekranie ustawiamy kursor w pozycji od której chcemy zacząć i wyświetlamy napis:
```c++
  lcd.setCursor(0, 0);
  lcd.print("Hello world!");
```

Mam nadzieję że wszystko działa tak jak powinno i właśnie zobaczyłeś napis na ekranie swojego wyświetlacza.

