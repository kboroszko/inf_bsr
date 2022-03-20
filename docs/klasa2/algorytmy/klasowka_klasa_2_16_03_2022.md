<!-- Transformed to PDF using dillinger.io-->
# Złożoność obliczeniowa
Jaka jest złożoność podanych funkcji:
```python
def find_max(tab):
    best = tab[0]
    for elem in tab:
        if elem > best:
            best = elem
    return elem
```

```python
def silnia(n):
    wyn = 1
    for i in range(1,n+1):
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
def is_prime(n):
    for divisor in range(2, n):
        if n % divisor == 0:
            return False
    return True
```

```python
def repeated(tab):
    ret = []
    for i in range(1, len(tab)):
        for j in range(0,i):
            if tab[i] == tab[j]:
              ret.append(tab[i])
    return True
```

# rekurencja ogonowa
Czym jest? Z jakiego powodu należy jej uzywać?

Które z podanych funkcji używają poprawnie rekurencji ogonowej:
```python
def silnia_rec(n):
    if n <= 1:
      return 1
    else:
      return n * silnia_rec(n-1)
```
```python
def pow(a, n, acc):
    if n == 0:
      return acc
    else:
      return pow(a, n-1, acc*a)
```
```python
def fib(n):
    if n <= 2:
      return 1
    else:
      return fib(n-1) + fib(n-1)
```
```python
def sum(tab,acc):
    if len(tab) == 0:
      return acc
    else:
      return sum(tab[1:], acc + tab[0])
```
```python
def max(tab,best):
    if len(tab) == 0:
        return best
    else:
        if best > tab[0]:
            return max(tab[1:], best)
        else:
            return max(tab[1:], tab[0])
```


# sortowanie
Jakie znasz algorymty sortowania? Jaką mają złożoność?
(podaj conajmniej te 3 które omawialiśmy na zajęciach)

# binary search
  - Do czego służy?

Poniżej zamieszczono jedną z możliwych implemetacji binary-search'a:
```python
def binary_search(arr, x):
    if len(arr) == 0:
        return False
    if x > arr[-1] or x < arr[0]:
        return False
    mid_idx =  len(arr) // 2
    if x == arr[mid_idx]:
        return True
    elif arr[mid_idx] > x:
        return binary_search(arr[:mid_idx], x)
    else:
        return binary_search(arr[mid_idx:], x)
```
Ile wywołań funkcji `binary_search` wykona program poniżej?
```python
binary_search([1,2,3,...,98,99,100], 35)
```

Wypisz te wywołania.

Dla przykładu pierwsze trzy to:
```python
binary_search([1,2,3,...,98,99,100], 35)
binary_search([1,2,3,...,48,48,50], 35)
binary_search([25,26,...,48,48,50], 35)
...
```


# stos
  - Jake są podstawowe metody do obsługi stosu?
  - Opisz jak działa algorytm sprawdzający poprawność wyrażenia złożonego z nawiasów?
  - Policz wartość tego wyrażenia: `4 5 + 7 2 - *`
  - Policz wartość tego wyrażenia: `4 2 - 3 5 + *`




# drzewo BST
  - Jaki warunek musi spełniać drzewo BST?
  - jaką minimalną wysokość ma drzewo które ma `10` węzłów/node'ów?
  - jaką minimalną wysokość ma drzewo które ma `n` węzłów/node'ów?
  - Narysuj drzewo które jest zrobione z elementów dodawanych w takiej kolejnosci:
    - `[26, 91, 97, 89, 49, 4, 97, 54, 96, 12]`
    - `[81, 58, 69, 60, 25, 14, 40, 80, 28, 43]`
<!--
      ┌──(97)
      │   └──(96)
  ┌──(91)
  │   └──(89)
  │       └──(54)
─(50)
  │   ┌──(49)
  └──(26)
      │   ┌──(12)
      └──(4)

  ┌──(81)
  │   │       ┌──(80)
  │   │   ┌──(69)
  │   │   │   └──(60)
  │   └──(58)
─(50)
  │       ┌──(43)
  │   ┌──(40)
  │   │   └──(28)
  └──(25)
      └──(14)
-->
# przeszukiwanie drzew
Napisz kolejność w której przejdziesz po drzewie algorytmem BFS/DFS.

# hashowanie
  - jakie są cechy dobrej funkcji hashującej?
  - Co to jest kolizja?
  - Dlaczego to jest słaba funkcja hash'ująca?
```python
def hash(x):
    return x % 7
```
