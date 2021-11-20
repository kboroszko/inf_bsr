<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.10.2/dist/katex.min.css" integrity="sha384-yFRtMMDnQtDRO8rLpMIKrtPCD5jdktao2TV19YiZYWMDkUR5GQZR/NOVTdquEx1j" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.10.2/dist/katex.min.js" integrity="sha384-9Nhn55MVVN0/4OFx7EE5kpFBPsEMZxKTCnA+4fqDmg12eCTqGi6+BB2LjY8brQxJ" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.10.2/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>

# Lekcja 1

Koncepcja komputera zaczęła się od przetważania wyrażeń logicznych.

Zacznijmy od najprostrzych wyrażeń:

* `OR` oznaczonego przez `$\lor$`
* `AND`oznaczonego przez `$\land$`
* `NOT` pznaczonego przez `$\neg$`

| `A` | `B` | `$A \lor B$` |
|---|---|-------|
| 0 | 0 | 0     |
| 0 | 1 | 1     |
| 1 | 0 | 1     |
| 1 | 1 | 1     |

| `A` | `B` | `$A \land B$` |
|---|---|-------|
| 0 | 0 | 0     |
| 0 | 1 | 0     |
| 1 | 0 | 0     |
| 1 | 1 | 1     |

Teraz zwróćmy uwagę na to że każde wyrażenie można przedstawić za pomocą dwóch
operatorów: AND i NOT.

Spróbuj przedstawić OR jako kombinację AND i NOT.

Teraz zastanówmy się w jaki sposób można dodawać liczby traktując je jako wyrażenia
logiczne.

Krótkie przypomnienie jak przedstawiać liczby w postaci binarnej:
Każdy bit oznacza kolejną potęgę 2.

Jaką liczbę przedstawiono na rysunku?
> ! `$2^0 + 2^3 + 2^4 + 2^6 = 89$`

![bity jako potęgi dwójki](https://miro.medium.com/max/804/1*O5DcmmXADTdQCNgYYw7Qpw.png)

Teraz weźmy dwie liczby w postaci binarnej i spróbujmy napisać wyrażenie logiczne które
będzie równe ich wynikowi. Pierwsza liczba `A` jest reprezentowana przez jeden
bit: `$A_1$`, druga `B` tak samo: `$B_1$`.

Dodajemy liczby pod kreską tak jak liczby dziesiętne w podstawówce. Jeśli obydwa bity
mają wartość 1, przenosimy 1 do kolejnej kolumny.

Wynik opiszemy w dwóch bitach `C` = `$C_2C_1$`.

```
$$C_1 = (A \lor B) \land \neg(A \land B) $$
$$C_2 = (A \land B)$$
```




