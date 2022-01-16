# Rekurencja ogonowa
Rodzaj rekurencji, w której ostatnia operacja wykonywana przez funkcję to rekurencyjne wywołanie samej siebie lub zwrócenie końcowego wyniku.

```python

def sumuj(lista, akumulator):
    if len(lista) == 0:
        return akumulator
    else:
        return sumuj(lista[1:], lista[0] + akumulator)

assert sumuj([1,2,3,4], 0) == 10
```


### Zadania

1. Napisz program który policzy potęgę liczby używając rekurencji ogonowej
2. Napisz program który sprawdzi stopień parzystości liczby
3. Napisz program który dostanie tablicę liczb całkowitych i policzy: 
    - sumę tych liczb
    - sumę kwadratów tych liczb
4. Napisz procedurę, która sprawdza, czy dana liczba jest podzielna przez 9 w następujący
sposób: jedyne liczby jednocyfrowe podzielne przez 9 to 9 i 0; reszta z dzielenia liczby
wielocyfrowej przez 9 jest taka sama, jak reszta z dzielenia sumy jej cyfr przez 9; jeśli
suma cyfr jest wielocyfrowa, to całość powtarzamy, aż do uzyskania liczby jednocyfrowej.

### Algorytm euklidesa NWD
`NWD(a,b) == NWD(a-b, b)`

15 25

121, 374

1122, 867

2584, 610



### Zadania domowe:
TBD.
