<!-- # Cele kształcenia: -->
[symulator online](https://www.falstad.com/circuit/circuitjs.html)

[symulator do pobrania](https://sebastian.itch.io/digital-logic-sim)

<!-- Chcemy zrozumieć jaka jest zasada działania komputera na najprostrzym, najniższym poziomie.
Jak możemy przejść od prostych sygnałów do zaawansowanych urządzeń których
używamy na codzień. 

Chcemy zrozumieć jak działa procesor, pamięć, peryferia.

Następnie jak wygląda architektura najprostrzych mikrokontrolerów.

Wreszcie jak mogą nam pomóc w prostych zadaniach na codzień i jakie
rozwiązania zostały stworzone żeby ułatwić to zadanie.



# Program

* TOC
{:toc}


-----



# 1. Wprowadzenie - Analog vs Cyfrowy

Co to znaczy że coś jest cyfrowe? Jak przejść od napięcia do 0 i 1?

### krótkie powtórzenie

Co to jest napięcie i dzielnik napięcia. Jak działa kondensator, dioda, tranzystor.


### Jak zrobić z napięcia 0 i 1

Można użyć MOSFETa albo tranzystora bipolarnego. Tworzymy proste układy.
Chcemy żeby dla konkretnego napięcia na wejściu 
powstawało napięcie na wyjściu itd. zamienić sygnał np. sinusa na prostokąt

*Tutaj fanie by było mieś generator i oscyloskop i pokazać 
to na "żywym organiźmie"*


Teraz jakie są analogowe rzeczy? Przede wszystkim **dźwięk**. ale nie tylko.
Dużo aparatury pomiarowej działa tak że im większe napięcie, tym większa wartość
pomiaru. Np. termometr gdzie temperatura będzie proporcionalna do napięcia.

Dźwięk np. w mikrofonie działa dokładnie w ten sposób - mamy drgania,
które przekładają się na to jak dobrze przylegają do siebie drobinki węgla
im większe drgania -> tym mniejszy spadek napięcia na mikrofonie

No to jak zamienić jakieś napięcie na odczyt cyfrowy, lepiej niż 0 i 1?
**Komparator**

No a jak wytworzyć konkretne napięcie?
**DAC**

Słabe i mocne strony takiego podejścia? Czas włączania i wyłączania.

# 2. interpretacja sygnału, bramki logiczne

No dobra, a teraz część cyfrowa: mamy te zera i jedynki co można z tym dalej zrobić?
Chcemy opisywać proste zależności i relacje logiczne za pomocą poziomów napięcia.

Do tego tworzymy bramki logiczne. Tworzymy maszynę która wnioskuje. Jak coś, to coś.
(Maszynę Turinga)
Jakie są podstawowe bramki logiczne?

`bramka logiczna przy użyciu mosfetów - np. negacja i and i or`


Każde zdanie logiczne da się zapisać za pomocą 2 operatorów logicznych np. negacja i or

`Zapisanie and za pomocą negacji i or`

No dobra, to teraz jak zapisać dodawanie 2 liczb używając bramek logicznych?

`dodawanie przy użyciu bramek`

Hmm... mamy te bramki, no ale komputer działa dynamicznie a bramki wykonują statyczne ruchy

`counter`

Zauważmy że nasz licznik liczy tak szybko, jak szybki mamy zegar...

Jak przejść od licznika do procesora?

To przejście powinno być już dość łatwe, 
mamy licznik który zaczyna w pewnym miejscu i 
odczytuje operacje co ma się zadziać

# 3. jak działa procesor <- To jest gruby temat, można go rozbić na 2 lekcje
Mamy rejestry, mamy instrukcje, mamy pamięć
zapisując bardzo proste instrukcje możemy mówić procesorowi co ma robić.

`pytanie jak ten "pseudo" assembler byłby trudny i 
jak miałby się do prawdziwego asemblera?`

Tutaj możnaby spróbować zrobić ten symulator procesora.

tylko integery, mogą być ujemne, mamy kilka rejestrów, podstawowe operacje mat,
jump, conditional jump, write i read do pamięci

```
READ mem reg
WRITE reg mem
ADD/SUB/MUL/DIV reg reg
JMP mem
CJMP reg mem
```

Może coś prostrzego i co już istnieje :)\

[TOYSIM](https://www.cs.princeton.edu/courses/archive/fall14/cos109/toysim.html) <br>
[TOY DOC](https://www.csie.ntu.edu.tw/~cyy/courses/introCS/20fall/lectures/handouts/lec06_TOYprogramming_4up.pdf)

[VONNEUMAN SIM](https://github.com/jpdante/VonNeumannSimulator/wiki)

[little man computer - LMC](https://www.101computing.net/lmc-simulator/)


Piszemy prosty program i zapisujemy go w naszym asemblerze
w konkretnym miejscu w pamięci (które znamy) mamy zapisane 10 liczb
1. policz ich sumę
2. policz ich średnią
3. \* w pamięci jest zapisana liczba N oznaczająca 
ile jest tych liczb a potem kolejno te liczby
4. \* ciąg liczb jest dowolnie długi i kończy się 0

Zastanawiamy się jak można zrobić funkcje?
Co to jest stos funkcji? 

A jak dynamicznie alokować pamięć?
Co to jest sterta? (Stack vs Heap)

Patrzymy na zdekompilowany kod C - 
[dekompilator](https://godbolt.org/)

# 4. Jak działa mikroprocesor?

Architektura mikroprocesora:

Komponenty: CPU, FLASH, [EEPROM](https://www.electronicwings.com/avr-atmega/atmega16-eeprom), RAM, Porty I/O, Serial Port, 
Bus, Timer, Oscylator, przerwania o których powiemy potem

Schemat budowy:

Jak działa bus? Dlaczego używamy Bus'a a nie łączymy wszystko bezpośrednio?

von Neuman vs Harvard Architecture

Jak działają porty I/O?

W jaki sposób programuje się mikrokontroler przez serial port?

Jak działają Timery? Jak działają przerwania?

# 5. Programowanie na atmegach :) arduino nano czy coś

Czas na trochę praktyki. łatwo jest zrobić taki program, 
ale warto się zapoznać z programowaniem atmegi itp.

Każdy dostaje: płytkę stykową, atmegę, 
dodatki - oscylator, diody, rezystory, programator, kabelki

Robimy program miganie 1 diodą co 1 sek.

Teraz chcemy mignąć 2 jeśli będzie wciśnięty przycisk. (przerwania)

Teraz migamy 1. diodą co 3 sek a drugą co 5. Jak to zrobić?
(timery vs software)

# 6. Architektura Maliny
Architektura maliny:

System operacyjny, usb, pamięć ram, wielowątkowość, czas, peryferia.

Maliny to fundamentalnie inny sprzęt, nie mamy tak niskopoziomowej kontroli.
To może być plus ale też minus:

| Malina                                                 | AVR (Atmega)                                                            |
|--------------------------------------------------------|-------------------------------------------------------------------------|
| + wysoki poziom abstrakcji (system operacyjny, python) | + mały koszt                                                            |
| + łatwość obsługi peryferiów (przez software)          | + rozmiar                                                               |
| + dużo pamięci                                         | + mały pobór prądu                                                      |
| + szybki procesor                                      | + nie skomplikowana architektura                                        |
| + 64 bit                                               | + 100% kontroli nad pracą procesora (assembler), chodzi o wydajność |
| + wielowątkowość                                       |                                                                         |
| + łatwa komunikacja z innymi użądzeniami               |                                                                         |
|                                                        |                                                                         |
| - pobór prądu                                          | - niskopoziomowa (trzeba pisać w C)                                     |
| - mała kontrola działania procesora                    | - powolna (zazwyczaj kilkanaście MHz)                                   |
| - rozmiar                                              | - mało bitów (zazwyczaj architektura 16bit)                             |
| - koszt                                                | - komunikacja z innymi użądzeniami to ból (np. USB)                     |



Kiedy używamy maliny a kiedy AVR?

W ogromnej większości zastosowań, malina będzie lepszym wyborem.
Jeśli tylko mamy wystarczająco miejsca, mocy, pieniędzy.

Nawiązując do programowania na AVR, 
piszemy program w pythonie do migania jedną lub dwiema diodami.

Różnice?
+ łatwość z jaką można obsługiwać I/O
+ software'owy timer 
+ łatwa obsługa przerwań
+ wielowątkowość


# 7. Komunikacja
Sposoby na komunikację między urządzeniami i z peryferiami:
Niskopoziomowe:
UART, SPI i IC2

Wysokopoziomowe:
Bluetooth, Wifi, Ethernet, GSM, USB

USB jest dość wyjątkowym przykładem. Dlaczego nie jest łatwo tworzyć urządzeń które
łączą się z komputerem przez USB? I dlaczego jest to praktycznie nie do zrobienia
na jakimś AVR bez specialnego modułu USB? Jak używa się biblioteki V-USB?

Tu natychmiast widać ogromną przewagę maliny. Mamy łatwość w łączeniu się
z czym tylko dusza zapragnie używając kilku linijek kodu i bibliotek które
ktoś już napisał.

Na początek spróbujmy skomunikować się z peryferiami,
połączyć się z termometrem czy z ekranem. 

mini-projekt:
Program który wyświetla na ekranie 7 segmentowym temperaturę.

Komunikacja z innym komputerem itd. jest na raspi w zasadzie
załatwiona bo mamy połączenie przez wifi i możemy wystawić jakieś api webowe.

A jak skomunikować się z czymś co nie ma połączenia z wifi?
Dlaczego korzystanie z USART jest 1000 razy prostrze?
Na czym polega standard USB?

Możemy to omówić, albo zrobić jakiś mini-projekt komunikacji dwóch mikrokontrolerów przez usart.


# 8. PWM

PWM - Pulse Width Modulation:
Do sterowania komponentami które mają dużo wolniejszą odpowiedź 
niż długość cyklu zegara, możemy użyć PWM.
Żeby wysterować silnik, bardzo szybko włączamy i wyłączamy go. 
Sterując *wypełnieniem* cyklu, możemy regulować ilość mocy dostarczanej do silnika.

Tak samo możemy sterować napięciem. Multimetr podłączony do
wyjścia PWM. Sterowanie jasnością diody, silnikiem, serwo-motorem. -->



