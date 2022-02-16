### Kartkówka:

Dana jest funkcja: 
```python
def binsearch(array, elem) -> int:
    pass
```
Która dla posortowanej listy i elementu zwraca index tego elementu jeśli
występuje na liście. Jeśli element nie występuje zwraca `-1`.
Jeśli element występuje więcej niż raz, zwraca index losowego z tych elementów.

przykład:
```python
arr = [1,4,5,6,7,8,9,10]
binsearch(arr, 5) == 2
```

Mając do dyspozycji funkcję `binsearch` napisz funkcję `last(arr, elem)` która
znajdzie index ostatniego wystąpienia danego elementu na posortowanej liście.

przykład:
```python
arr = [1,4,5,5,7,8,8,8,9,10]
last(arr, 5) == 3
last(arr, 7) == 4
last(arr, 8) == 7
```

# Stos [ang. Stack]

Stos to struktura danych która dostarcza trzy podstawowe operacje:
`pop`, `push`, `peek` 

Stos jest jak lista na której można patrzeć tylko na ostatni element.
Możemy dodać coś na koniec tej listy instrukcją `push`, tak samo możemy *zdjąć element ze stosu* czyli usunąć ostatni element listy robiąć `pop`
oraz możemy zajrzeć co jest na szczycie stosu wykonując `peek`.


Będziemy traktować stos jako listę specialnego rodzaju. W liście można podejrzeć każdy element robiąc `lista[i]`. W stosie wolno będzie nam podjerzeć tylko ostatni element, robiąc `peek()`. 

Dodatkowo do listy możemy dodać coś na koniec robiąc `lista.append(e)`. W
stosie robimy `push(e)`.

Z listy możemy usunąć ostatni element, tak samo ze stosu - robiąc `pop()`

## implementacja:
Do implementacji będziemy używać zwykłej listy, ale będziemy się z nią obchodzić w specjalny sposób:

- Nie wolno nam zmieniać żadnego elementu z listy 
    - czyli używać operatora przypisania do elementu: ~~`lista[0] = 10`~~
- Uzywamy tylko: 
    - `lista.append()` do dodawania elementów
    - `lista.pop()` do usuwania ostatniego elementu


Wyobraźmy sobie prawdziwy stos w którym układamy elementy jeden na drugim:
```
4
3
2
1
###
```
Dół stosu oznaczyłem `###`

Na naszym stosie są 4 elementy. Takiemu stosowi w pythonie odpowiada lista:
```
stos = [1,2,3,4]
```

Możemy sprawdzić ostatni element:
```
print(stos[-1])
```

Możemy wrzucić element na koniec:
```
stos.append(5)
```
Wtedy nasz stos będzie wyglądał tak:
```
5
4
3
2
1
###
```
Możemy też usunąć kilka ostatnich elementów:
```
stos.pop()
stos.pop()
stos.pop()
```
Wtedy nasz stos będzie wyglądał tak:
```
2
1
###
```
-----------------
# Zadanie 1.

Napisz funkcję `parse` która sprawdza czy wyrażenie z nawiasów jest
poprawnie napisane, tj. Czy wszystkie otwarte nawiasy są później zamknięte.

```python

def parse(line):
    """funkcja która sprawdza czy nawiasy są poprawnie postawione"""
    stack = []
    for c in line:
        pass
        # TODO - Twoja implementacja
    return False

line = input("podaj wyrażenie składające się z nawiasów:\n")

print("wyrażenie prawidłowe?", parse(line))
```


Przykłady  wyrażeń poprawnych:
```
()
(()())
((()()(())))
```

Przykłady  wyrażeń **nie** poprawnych:
```
()(
((())
())()()()()))()
```
----------------

## Zadanie 1*
Rozszerz funckję `parse` tak żeby sprawdzała wyrażenie składające się z 2 rodzajów nawiasów: `()`, `[]`.

Przykłady  wyrażeń poprawnych:
```
([])
([()()])
[(([()()](([]))))]
```


Przykłady  wyrażeń **nie** poprawnych:
```
(([])
([)]
[((]
([([)()]])
[(([()()(](([]))))])
```
-----------------------
# Notacja `in-fix`

Litery `a,b,c` oznaczają dowolne **liczby**.

Operacje matematyczne wykonujemy zapisując znak operacji między argumentami.
Na przykład `add(a,b)` zapiszemy tak:
```
a + b
```

Operacje można też zagnieżdżać.
`add(a,multiply(b,c))` zapiszemy tak:
```
a + (b * c)
```
**Note:**  pisząc działania matematyczne często pomijamy niepotrzebne nawiasy, ale tutaj dla jasności zawsze będę je pisał.

# Notacja `post-fix`
Napisanie programu który będzie czytał w ten sposób konstrułowane wyrażenia matematyczne jest dość skomplikowane, nawet jeśli używamy nawiasów. Żeby było łatwiej, możemy zapisywać najpierw argumenty działania, a potem znak działania:



Operacje matematyczne wykonujemy zapisując znak operacji za argumentami.
Na przykład `add(a,b)` zapiszemy tak:
```
a b +
```

`multiply(a,b)`:
```
a b *
```

`subtract(a, b):
```
a b -
```
etc.

### Uwaga:
Operacje można też zagnieżdżać.
`add(a,multiply(b,c))` zapiszemy tak:
```
b c * a +
```

Zwróć uwagę co się dzieje. Wyrażenie czytamy od lewej. Najpierw wykonujemy mnożenie b i c. 

Następnie otrzymujemy wynik, bierzemy drugi argument `a` i wykonujemy dodawanie.

## Implementacja:
Taki kalkulator łatwo zaimplementować używając stosu.
Wrzucamy na stos argumenty, po czym jeśli natrafimy na operację matematyczną:
`*`,`+`,`-`,`/`, to zdejmujemy dwie ostatnie liczby ze stosu, wykonujemy operację i wrzucamy wynik na stos.

Jak będzie wyglądało przetwarzanie tego wyrażenia:
```
3 5 * 4 +
```


znakiem `^` oznaczam ostatni przeczytany znak.

### Krok 1
```
3 5 * 4 +
^
```

Wrzuć na stos `3`.
Stos:
```
3
###
```

### Krok 2
```
3 5 * 4 +
  ^
```

Wrzuć na stos `5`.
Stos:
```
5
3
###
```

### Krok 3
```
3 5 * 4 +
    ^
```
Zdejmij ze stosu dwie ostatnie liczby i wykonaj mnożenie.
Wynik wrzuć na stos
Stos:
```
15
###
```

### Krok 4
```
3 5 * 4 +
      ^
```

Wrzuć na stos `4`.
Stos:
```
4
15
###
```

### Krok 5
```
3 5 * 4 +
        ^
```

Zdejmij ze stosu dwie ostatnie liczby i wykonaj dodawanie.
Stos:
```
19
###
```

### Krok 6
```
3 5 * 4 +
          ^
```

Koniec, zdejmij wynik ze stosu
Stos:
```
19
###
```


# Zadanie 2:
Uzupełnij `TODO` w implementacji kalkulatora który działa w notacji post-fix:

Możesz założyć że podane przez użytkownika wyrażenie będzie poprawne.
```python
def parse(line):
    operators = ['*', '+', '-', '/']
    stack = []
    for c in line.split():
        if c in operators:
            # TODO wykonaj operację matematyczną
            pass
        else:
            number = float(c)
            # TODO wczytaj liczbę
            pass
    return stack.pop()

line = input("podaj wyrażenie matematyczne:\n")

print(parse(line))
```