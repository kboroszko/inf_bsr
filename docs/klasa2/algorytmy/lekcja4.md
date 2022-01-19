### kartkówka
napisz funkcję która liczy silnię używając rekurencji ogonowej.

# Sortowanie

Omawialiśmy i implementowaliśmy:
- bubble sort
- insertion sort
- selection sort

**Każdy po tych zajęciach powinien mieć zapisaną i rozumieć implementacje tych trzech algorytmów.**

*W razie pytań piszcie*

### Zadanie domowe:
Sortowanie indexów.
Napisz funkcję która przyjmuje tablicę o długości `n` wypełnoną różnymi liczbami naturalnymi i zwraca tablicę indexów posortowanych elementów. Innymi słowy, jeśli ustawilibyśmy wartości w tablicy w takiej kolejności to byłby posortowane.

Przykład:
```python

def index_sort(lista)
    # TODO: Twój kod
    pass

lista = [2,4,6,7,1,3]
         0,1,2,3,4,5
wynik = index_sort(lista)

assert wynik == [4,0,5,1,2,3]
```




<!-- Bajtek ma cały garaż zawalony pudłami i potrzebuje pomocy w porządkach. W tej chwili wszystkie pudła leżą na ziemi. Bajtek próbował ustawiać je jedne na drugim ale gdy ustawia z nich wierze, pudła spadają mu na głowę. Żeby temu zapobiec, trzeba zawsze się upewnić że pudło które stawiamy na górze jest mniejsze na którym je stawiamy.

Przykładowe pudło:

![pudło](https://szaloneliczby.pl/wp-content/uploads/2016/09/wysokosc-szerokosc-dlugosc-prostopadloscianu-rys.png)

np. Gdy mamy pudło o wymiarach: `5 x 6 x 4` (długość x szerokość x wysokość)

to możemy je postawić na pudle o wymiarach `6 x 6 x 3`. 

Ale nie wolno nam ustawić go na pudle o wymiarach `5 x 5 x 10` ponieważ ma mniejszą szerokość.


Napisz program który przeczyta  -->