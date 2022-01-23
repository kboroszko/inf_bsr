<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

### Kartkówka
TODO

# Binary search i duże zadanie domowe

Przypomnienie:

Wyobraźmy sobie teleturiniej w którym trzeba zgadnąć liczbę między 0 a 100. Uczestnik zgaduje liczbę i dowiaduje się, że podana przez niego liczba jest za mała lub za duża, chyba że trafił, wtedy wygrywa.

Zastanówmy się według jakiej zasady powinniśmy zgadywać, żeby odgadnąć liczbę w jak najmniejszej liczbie kroków.

Jeśli będziemy zgadywać numer po numerze, zaczynająć od 1, w najgoryszym wypadku zadamy 100 pytań. Trzeba więc wymyślić lepszy sposób. 

Załóżmy że najpierw zapytamy o 50. Dowiemy się, że szukana liczba jest większa. Jaki powinien być następny strzał? (podpowiedź: nie 51)

Teraz szukamy liczby z przedziału 51 - 100. Oczywiście kolejnym strzałem powinno być 75. Wtedy niezależnie od tego czy szukana liczba jest większa czy mniejsza, ograniczymy możliwy przedział o połowę.

Skoro w każdym kroku ograniczymy przedział o połowę, ile takich kroków możemy wykonać? Ile razy można podzielić 100 na pół?

Jeśli natrafimy na liczbę nieparzystą, wynik zaokrąglajmy zawsze w górę.

```
100 / 2 = 50
50 / 2 = 25
25 / 2 = 13
13 / 2 = 7
7 / 2 = 4
4 / 2 = 2 
2 / 2 = 1
```

Wykonaliśmy 7 kroków. Jak policzyć ile takich kroków wykonamy dla dowolnej liczby?

Zobaczmy, ile razy możemy podzielić 64?

$$ 64 = 2^6 $$
Odp: 6 razy

Ile razy możemy podzielić 128?
$$ 128 = 2^7 $$
Odp: 7 razy

W takim razie każdą liczbę większą od 64 możemy podzielić conajmniej 6 razy na 2, a każdą mniejszą od 128 maksymalnie 7. Stąd wiemy że możemy podzielić liczbę `100` na pół między 6 a 7 razy. 

Dokładnie tak działa logarytm o podstawie 2. Mówi nam ile razy możemy podzielić daną liczbę na 2. 
$$ log_2(100) = 6.643... $$
Otrzymaliśmy wartość między 6 a 7.

Dzięki temu, wiemy że żeby zgadnąć liczbę od 0 do 100 musimy zadać maksymalnie 7 pytań. Żeby zgadnąć liczbę od 0 do `n` musimy zadać:
$$ log_2(n) $$
pytań. Więc to jest złożoność naszego algorytmu.


### Zadania (zastanów się nad złożonością):
1. Napisz funkcję która sprawdza czy dany element znajduje się na **posortowanej** liście w jak najmniejszej liczbie kroków. 

```python
def binsearch(lista, elem):
    """Funkcja zwracająca True jeśli element `elem` znajduje się na liście
    lista musi być posortowana"""
    ########################
    # TODO Twój kod tutaj  #
    ########################
    return False

l = []
for i in range(100):
    l.append(i)

print(binsearch(l, 54))
```

<!-- 
```python
def binsearch(lista, elem):
    print("lista:" + repr(lista))
    n = len(lista)
    if n == 0:
        return False
    if n == 1:
        return lista[0] == elem
    n_half = n//2
    if lista[n_half] == elem:
        return True
    if lista[n_half] > elem:
        return binsearch(lista[:n_half], elem)
    else:
        return binsearch(lista[n_half:], elem)

l = []
for i in range(10):
    l.append(i)

print(binsearch(l, 4))
``` -->
2. Napisz funckję `sqrt(n)` która znajduje pierwiastek liczby `n` zaokrąglony w dół do liczb całkowitych.
3. Napisz funkcję `find_index(lista, elem)` która zwraca index elementu z posorowanej listy. Jeśli elementu nie ma na liście, zwraca `-1`.
4. Napisz funkcję która zwraca *zapętloną* listę `n` razy, tj. przesuwa wszystkie elementy w prawo, a ostatni wstawia na początek.
```python
# przykład
tab = [1,2,3,4,5,6,7]
cycle(tab, 1) == [7,1,2,3,4,5,6]
cycle(tab, 3) == [5,6,7,1,2,3,4]
```
5. Napisz funkcję która sprawdza czy dany element znajduje się na liście która została posortowana, następnie *zapętlona* pewną liczbę razy, tj. ostatni element wstawiamy na początek, i tak kilka razy.

```python
def find_cycled(lista, elem):
    ########################
    # TODO Twój kod tutaj  #
    ########################
    return False

print(find_cycled([5,6,7,1,2,3,4], 3))
```


### Zadanie domowe do <span style="color: red">14 Lutego</span>

Bajtek ma cały garaż zawalony pudłami i potrzebuje pomocy w porządkach. W tej chwili wszystkie pudła leżą na ziemi i zajmują strasznie dużo miejsca. Bajtek próbował ustawiać je jedne na drugim, ale gdy układa je w stosy, pudła spadają mu na głowę. Żeby stos pudeł był stabilny, trzeba zawsze się upewnić że pudło które stawiamy na górze jest **ściśle** mniejsze w obydwu wymiarach od pudła na którym je stawiamy.

Przykładowe pudło:

![pudło](https://szaloneliczby.pl/wp-content/uploads/2016/09/wysokosc-szerokosc-dlugosc-prostopadloscianu-rys.png)

np. Gdy mamy pudło o wymiarach: `5 x 6 x 4` (długość x szerokość x wysokość)

to możemy je postawić na pudle o wymiarach `6 x 7 x 4`. 

Ale nie wolno nam ustawić go na pudle o wymiarach `5 x 7 x 4` ponieważ ma za małą podstawę.

Pudła można też obracać, ale tak żeby dalej stały na tym samym boku! tzn. pudło o wymiarach `5 x 6 x 4` można obrócić i wtedy będzie miało wymiary `6 x 5 x 4`, ale jego wysokość zawsze będzie taka sama.

Wobec tego pudło `6 x 3 x 4` można ustawić na pudle `5 x 10 x 4`.


Bajtek już dawno zapomniał po co układa te pudła, ale chciałby wiedzieć jaki najwyższy stos może ustawić ze swoich pudeł.

Napisz program który w pierwszej lini wczyta jedną liczbę `N` oznaczającą liczbę pudeł, a następnie w kolejnych `N` liniach wczyta po 3 liczby oddzielone spacjami, oznaczające kolejno długość, szerokość, wysokość każdego pudła.

Twój program powinien wypisać jedną liczbę oznaczającą maksymalną wysokość stabilnej wierzy jaką może ułożyć Bajtek.

### Przykłady:

| Przykładowe wejście | Przkładowe wyjście |
| ------------------- | ------------------ |
| `3`                 | `9   `             |
| `3 4 2`             |                    |
| `5 5 3`             |                    |
| `7 9 4`             |                    |

| Przykładowe wejście | Przkładowe wyjście |
| ------------------- | ------------------ |
| `3`                 | `8   `             |
| `3 4 5`             |                    |
| `4 5 2`             |                    |
| `3 3 6`             |                    |

| Przykładowe wejście | Przkładowe wyjście |
| ------------------- | ------------------ |
| `2`                 | `9   `             |
| `3 3 5`             |                    |
| `3 3 9`             |                    |

| Przykładowe wejście | Przkładowe wyjście |
| ------------------- | ------------------ |
| `3`                 | `7`                |
| `3 5 5`             |                    |
| `6 4 2`             |                    |
| `3 5 3`             |                    |


### xkcd

![xkcd](https://imgs.xkcd.com/comics/ineffective_sorts.png)