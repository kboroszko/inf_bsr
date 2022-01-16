# Lekcja 2.
### kartkówka na początku
napisz funkcję która znajduje różnicę między największym i najmniejszym elementem w tablicy. Jaką złożoność ma Twoje rozwiązanie?

### zagadnienia:
- Reszta zadań z lekcji 1.
- Rekurencja ogonowa.
- Liczby fibonacciego.
    - Wersja oczywista z rekurencją
    - Wersja z loopem
    - Wersja z rekurencją ogonową

### Wizualizacja:
```python
from matplotlib import pyplot as plt
import numpy as np
import time

########################################
#  TWOJA FUNKCJA KTÓREJ CZAS MIERZYSZ  #
########################################

def foo(n):
  ret = []
  for i in range(n*1000):
    ret.append(i)
  return ret

########################################


def time_it(fun, *args):
    start_time = time.time()
    fun(*args)
    end_time = time.time()
    return end_time - start_time

points = np.arange(30)
times = np.array([time_it(foo, x) for x in points])

plt.figure()
plt.title("time complexity")
plt.xlabel("number of steps - n")
plt.ylabel("execution time [sec]")
plt.plot(points, times)
plt.show()
```




## Zadanie domowe:
Przy rozwiązywaniu zadań zastanów się również jaką złożoność ma Twoje rozwiązanie.

Napisz procedurę, która przekształca daną liczbę naturalną w taką, w której cyfry wy-
stępują w odwrotnej kolejności, np. 1234 jest przekształcane na 4321. Postaraj się użyć rekurencji ogonowej.


`*` Liczbę naturalną nazwiemy rzadką, jeżeli w jej zapisie binarnym żadne dwie jedynki
nie stoją obok siebie. Napisz funkcję która sprawdzi czy dana liczba jest liczbą żadką używając rekurencji ogonowej.


`**` Napisz procedurę zera_silni : int → int, która dla danej dodatniej liczby całkowitej
n obliczy ile zer znajduje się na końcu zapisu dziesiętnego liczby n!. Użyj rekurencji ogonowej.


![xkcd](https://imgs.xkcd.com/comics/functional.png)
