# Złożoność obliczeniowa (3 pkt.) GRUPA B

Jaka jest złożoność podanych funkcji:

```python
def silnia(n):
    wyn = 1
    for i in range(1, n + 1):
        wyn = wyn * i
    return wyn
```

```python
def is_in(tab, target):
    for elem in tab:
        if elem == tab:
            return True
    return False
```

```python
def repeated(tab):
    ret = []
    for i in range(1, len(tab)):
        for j in range(0, i):
            if tab[i] == tab[j]:
                ret.append(tab[i])
    return True
```

# rekurencja ogonowa (3 pkt.)

- Z jakiego powodu należy jej uzywać?

```python
.
.
.
.
.
.
```

Które z podanych funkcji używają poprawnie rekurencji ogonowej:

```python
def silnia_rec(n):
    if n <= 1:
        return 1
    else:
        return n * silnia_rec(n - 1)
```

```python
def sum(tab, acc):
    if len(tab) == 0:
        return acc
    else:
        return sum(tab[1:], acc + tab[0])
```

```python
def pow(a, n, acc):
    if n == 0:
        return acc
    else:
        return pow(a, n - 1, acc * a)
```

```python
def max(tab, best):
    if len(tab) == 0:
        return best
    else:
        if best > tab[0]:
            return max(tab[1:], best)
        else:
            return max(tab[1:], tab[0])
```

# sortowanie (1 pkt.)

Jakie znasz algorymty sortowania? Jaką mają złożoność?
(podaj conajmniej te 3 które omawialiśmy na zajęciach)

```python
.
.
.
.
.
.
```


# binary search (2 pkt.)

Poniżej zamieszczono jedną z możliwych implemetacji binary-search'a:

```python
def binary_search(arr, x):
    if len(arr) == 0:
        return False
    if x > arr[-1] or x < arr[0]:
        return False
    mid_idx = len(arr) // 2
    if x == arr[mid_idx]:
        return True
    elif arr[mid_idx] > x:
        return binary_search(arr[:mid_idx], x)
    else:
        return binary_search(arr[mid_idx:], x)
```
\
\

Ile **najwięcej** wywołań funkcji `binary_search` wykona poniższy program dla listy która ma
100 elementów? (odpowiedź uzasadnij)

```python
binary_search([1, 2, 3, ..., 98, 99, 100], x)
```

Dla przykładu pierwsze dwa to:

```python
binary_search([1, 2, 3, ..., 98, 99, 100], x)
binary_search([1, 2, 3, ..., 48, 48, 50], x)
...
```

Twoja odpowiedź:
```python
.
.
.
.
.
.
```
# stos (3 pkt.)

- Jake są podstawowe trzy funkcje do obsługi stosu? (co robią?)
```python
.
.
.
.
.
```
- Opisz własnymi słowami (lub napisz implementację) jak działa algorytm sprawdzający
  poprawność wyrażenia złożonego z nawiasów?
```python
.
.
.
.
.
```
- Policz wartość tego wyrażenia: `4 2 - 3 5 + *`

```python
.
.
```
# drzewo BST (3 pkt.)

- Jaki warunek musi spełniać drzewo BST?

```python
.
.
```
- jaką minimalną wysokość ma drzewo które ma `7` węzłów/node'ów?

```python
.
.
```
- jaką minimalną wysokość ma drzewo które ma `n` węzłów/node'ów?

```python
.
.
```
- Narysuj drzewo które jest zrobione z elementów dodawanych w takiej kolejnosci: \\
`[81, 58, 69, 60, 25,33, 14, 40, 80, 28, 43]` następnie usunięto z niego `[33, 81]`

```python
.
.
.
.
.
.
.
.
.
```

# przeszukiwanie drzew (2 pkt.)

Napisz kolejność w której przejdziesz po drzewie algorytmem **DFS**.
Przypomnienie:
- (DFS - z ang. Depth First Search)
- (BFS - z ang. Breadth First Search)


```python
DFS:
.
```

# hashowanie (1 pkt.)

1. jakie są cechy dobrej funkcji hashującej?
2. Co to jest kolizja?
3. Dlaczego to jest słaba funkcja hash'ująca? Podaj conajmniej 2 przyczyny

```python
def hash(x):
    return x % 11
```
