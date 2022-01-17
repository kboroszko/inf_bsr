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


### Kartkówka na początku
znajdź element środkowy tablicy - taki dla którego suma elementów po prawej i po lewej jest taka sama.

### Zadania

1. Napisz program który policzy potęgę liczby używając rekurencji ogonowej
2. Napisz program który sprawdzi stopień parzystości liczby
3. Napisz program który dostanie tablicę liczb całkowitych i policzy: 
    - sumę tych liczb
    - sumę kwadratów tych liczb


### Algorytm euklidesa NWD
`NWD(a,b) == NWD(a-b, b)`

15 25

121, 374

1122, 867

2584, 610



### Zadania domowe:
Napisz funkcję która bierze dwie posortowane rosnąco tablice i zwraca jedną posortowaną tablicę która jest sumą argumentów.

przykład:
```python
lista_1 = [1,4,6,7,8]
lista_2 = [3,3,4,6,11]

lista_3 = merge(lista_1, lista_2)
lista_3 == [1,3,3,4,4,6,6,7,8,11]
```

`*` Napisz funkcję, która sprawdza, czy dana liczba jest podzielna przez 9 w następujący
sposób: jedyne liczby jednocyfrowe podzielne przez 9 to 9 i 0; reszta z dzielenia liczby
wielocyfrowej przez 9 jest taka sama, jak reszta z dzielenia sumy jej cyfr przez 9; jeśli
suma cyfr jest wielocyfrowa, to całość powtarzamy, aż do uzyskania liczby jednocyfrowej.

`**` Napisz funkcję która liczy liczby fibonacciego używając rekurencji ogonowej.
![xkcd](https://imgs.xkcd.com/comics/code_quality.png)