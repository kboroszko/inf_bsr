<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

# Temat 1 - Bramki logiczne

Koncepcja komputera zaczęła się od przetważania wyrażeń logicznych.

Zacznijmy od najprostrzych wyrażeń:

* `OR` oznaczonego przez $$\lor$$
* `AND`oznaczonego przez $$\land$$
* `NOT` pznaczonego przez $$\neg$$

| A   | B   | $$A \lor B$$ |
| --- | --- | ------------ |
| 0   | 0   | 0            |
| 0   | 1   | 1            |
| 1   | 0   | 1            |
| 1   | 1   | 1            |

| A   | B   | $$A \land B$$ |
| --- | --- | ------------- |
| 0   | 0   | 0             |
| 0   | 1   | 0             |
| 1   | 0   | 0             |
| 1   | 1   | 1             |

Teraz zwróćmy uwagę na to że każde wyrażenie można przedstawić za pomocą dwóch
operatorów: AND i NOT.

Spróbuj przedstawić `OR, NAND, XOR, XNOR` jako kombinację `AND` i `NOT`.

Teraz zastanówmy się w jaki sposób można dodawać liczby traktując je jako wyrażenia
logiczne.

## Liczby binarne

Krótkie przypomnienie jak przedstawiać liczby w postaci binarnej:
Każdy bit oznacza kolejną potęgę 2.

Jaką liczbę przedstawiono na rysunku?
<details>
        <summary>Odpowiedź</summary>
         $$2^0 + 2^3 + 2^4 + 2^6 = 89$$
</details> 

![bity jako potęgi dwójki](https://miro.medium.com/max/804/1*O5DcmmXADTdQCNgYYw7Qpw.png)

## Dodawanie liczb binarnych

Teraz weźmy dwie liczby w postaci binarnej i spróbujmy napisać wyrażenie logiczne które
będzie równe ich wynikowi. Pierwsza liczba A jest reprezentowana przez jeden bit:
$$A_1$$, druga B tak samo: $$B_1$$.

Dodajemy liczby pod kreską tak jak liczby dziesiętne w podstawówce. Jeśli obydwa bity
mają wartość 1, przenosimy 1 do kolejnej kolumny.

Wynik opiszemy w dwóch bitach C = $$C_2C_1$$.

$$C_1 = (A \lor B) \land \neg(A \land B) $$. $$C_2 = (A \land B)$$.

----------------------------

## Symulator

Użyjemy programu do symulowania bramek logicznych.

[LINK](https://sebastian.itch.io/digital-logic-sim)

## Symulator online

[LINK](https://www.falstad.com/circuit/circuitjs.html)

---------------------------

Dodawanie liczb jest realizowane za pomocą bramki która ma 3 wejścia i 2 wyjścia które
omawialiśmy na lekcji.
`A, B, C` oraz wyjścia `W, C'`

Napisaliśmy sobie wyrażenia które reprezentują `W` i `C'`

$$ W = (\neg A \land XOR(B,C)) \lor (A \land \neg XOR(B,C)) $$ 

$$ C' = (\neg A \land (B \lor C)) \lor (A \land (B \lor C)) $$

# Praca domowa:
Ściągnąć symulator i zrobić dwie bramki o nazwie WYN, CPR które mają po 3 wejścia i
jedno wyjście i realizują te dwie operacje.

### Oddawanie pracy domowej:
Przynieść na pendrivie/wysłać mi mailem zzipowany folder z projektem.

Na windowsie projekty zapisywane są w folderze:

`AppData\LocalLow\Sebastian Lague\Digital Logic Sim\SaveData`

Mój adres mailowy wyślę Wam na discordzie.

## Zadania dodatkowe:

> 1. Operacje logiczne:

### Zadanie 1.1
Spróbuj zapisać za pomocą wyrażeń logicznych $$\land, \lor, \neg$$ następujące wyrażenia:

a. Implikacja: $$ \implies $$
| A   | B   | $$A \implies B$$ |
| --- | --- | ---------------- |
| 0   | 0   | 1                |
| 0   | 1   | 1                |
| 1   | 0   | 0                |
| 1   | 1   | 1                |

b. XOR
| A   | B   | XOR(A,B) |
| --- | --- | -------- |
| 0   | 0   | 0        |
| 0   | 1   | 1        |
| 1   | 0   | 1        |
| 1   | 1   | 0        |

### Zadanie 1.2
Spróbuj zapisać za pomocą **tylko** wyrażeń logicznych $$\lor, \neg$$ następujące wyrażenia:



a. AND

| A   | B   | $$A \land B$$ |
| --- | --- | ------------- |
| 0   | 0   | 0             |
| 0   | 1   | 0             |
| 1   | 0   | 0             |
| 1   | 1   | 1             |


b. Implikacja: $$ \implies $$

| A   | B   | $$A \implies B$$ |
| --- | --- | ---------------- |
| 0   | 0   | 1                |
| 0   | 1   | 1                |
| 1   | 0   | 0                |
| 1   | 1   | 1                |

c. XOR

| A   | B   | XOR(A,B) |
| --- | --- | -------- |
| 0   | 0   | 0        |
| 0   | 1   | 1        |
| 1   | 0   | 1        |
| 1   | 1   | 0        |


> 2. Liczby binarne

### Zadanie 2.1
Zapisz następujące liczby w postaci binarnej:

| dziesiętne | Binarne   |
| ---------- | --------- |
| 1          | 0000 0001 |
| 3          | 0000 0011 |
| 4          | 0000 0100 |
| 7          | ?         |
| 12         | ?         |
| 44         | ?         |
| 56         | ?         |
| 17         | ?         |
| 342        | ?         |

### Zadanie 2.2
Dodaj liczby w postaci binarnej (pod kreską) i sprawdź wynik:


| działania |
| --------- |
| 1  + 4    |
| 3   + 2   |
| 7   + 12  |
| 15   +7   |