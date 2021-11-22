<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

# Temat 1 - Bramki logiczne

Koncepcja komputera zaczęła się od przetważania wyrażeń logicznych.

Zacznijmy od najprostrzych wyrażeń:

* `OR` oznaczonego przez $$\lor$$
* `AND`oznaczonego przez $$\land$$
* `NOT` pznaczonego przez $$\neg$$

| A | B | $$A \lor B$$ |
|---|---|-------|
| 0 | 0 | 0     |
| 0 | 1 | 1     |
| 1 | 0 | 1     |
| 1 | 1 | 1     |

| A | B | $$A \land B$$ |
|---|---|-------|
| 0 | 0 | 0     |
| 0 | 1 | 0     |
| 1 | 0 | 0     |
| 1 | 1 | 1     |

Teraz zwróćmy uwagę na to że każde wyrażenie można przedstawić za pomocą dwóch
operatorów: AND i NOT.

Spróbuj przedstawić `OR, NAND, XOR, XNOR` jako kombinację `AND` i `NOT`.

Teraz zastanówmy się w jaki sposób można dodawać liczby traktując je jako wyrażenia
logiczne.

##Liczby binarne
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
będzie równe ich wynikowi. Pierwsza liczba A jest reprezentowana przez jeden
bit: $$A_1$$, druga B tak samo: $$B_1$$.

Dodajemy liczby pod kreską tak jak liczby dziesiętne w podstawówce. Jeśli obydwa bity
mają wartość 1, przenosimy 1 do kolejnej kolumny.

Wynik opiszemy w dwóch bitach C = $$C_2C_1$$.


 $$C_1 = (A \lor B) \land \neg(A \land B) $$.
 $$C_2 = (A \land B)$$.

----------------------------

## Symulator
Użyjemy programu do symulowania bramek logicznych. 

[LINK](https://sebastian.itch.io/digital-logic-sim)

## Symulator online
[LINK](https://www.falstad.com/circuit/circuitjs.html)





