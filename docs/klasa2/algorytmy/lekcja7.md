# Drzewa 🌳

### Kartkówka
<!-- jakieś zadanie na stosy -->


## Binary tree

Drzewem binarnym nazywamy taką strukturę danych, wktórej każdy przechowywany element może mieć rodzica i dwójkę dzieci.

![drzewo](/lekcja7/binary_search_tree.png)


Taki sposób przedstawienia danych pozwala na zawarcie dodatkowych informacji o danych przez to jak są ułożone.

## Implementacja drzewa:

```python
class Tree:
  value = None
  left_child = None
  right_child = None

  def __init__(self, value):
    self.value = value  
```

## Przykłady:

Stwórzmy takie drzewo które ma dwoje dzieci.
```
  ┌──(6)
─(5)
  └──(4)
```
Tworzymy je w ten sposób:
```python
# korzeń
tr1 = Tree(5)

# prawe dziecko
tr2 = Tree(6)
tr1.right_child = tr2

# lewe dziecko
tr3 = Tree(4)
tr1.left_child = tr3
```

Spróbuj stworzyć takie drzewa:
### 1.
```
      ┌──(7)
  ┌──(6)
─(5)
```

### 2.
```
      ┌──(8)
  ┌──(6)
─(5)
  │   ┌──(4)
  └──(3)
```

### 3.
```
      ┌──(7)
  ┌──(6)
─(5)
  │   ┌──(4.5)
  └──(4)
      │   ┌──(3.5)
      └──(3)
          └──(2)
```

### Drukowanie drzewa

Poniżej jest funkcja która wypisuje drzewo w konsoli. Skopiuj ją do swojego programu.

```python
def print_tree(tree, rec=False):
  if tree is None:
    return [],0
  right_subtree, idx_r = print_tree(tree.right_child, rec=True)
  left_subtree, idx_l = print_tree(tree.left_child, rec=True)
  ret = []
  for i,e in enumerate(right_subtree):
    if i == idx_r:
      ret.append("  ┌─" + e)
    elif i < idx_r:
      ret.append("    " + e)
    else:
      ret.append("  │ " + e)
  ret_idx = len(ret)
  ret.append(f"─({tree.value})")
  for i,e in enumerate(left_subtree):
    if i == idx_l:
      ret.append("  └─" + e)
    elif i > idx_l:
      ret.append("    " + e)
    else:
      ret.append("  │ " + e)
  if rec:
    return ret, ret_idx
  else:
    print('\n'.join(ret))
    return None
```

## BST - Binary Search Tree

Binary Search Tree - to drzewo w którym ustawiamy elementy w następujący sposób:
- Jeśli drzewo jest puste, nowy element staje się **korzeniem**.
- Jeśli element jest większy od korzenia, wstawiamy go jako prawe dziecko
- Jeśli jest mniejszy, jako lewe.

Przykład znajduje się [tutaj](http://btv.melezinek.cz/binary-search-tree.html).

Teraz spróbujmy spawdzić czy dany element już jest w drzewie.
Wykonujemy wszystko tak jakbyśmy chcieli dodać ten element do drzewa **ale nie dodajemy go na końcu**. Jeśli natrafimy na ten element po drodze, to wiemy że był w drzewie.

Postaraj się odpowiedzieć na te pytania:

- Jaką minimalną wysokość ma drzewo które ma 10 elementów?
- Jaką minimalną wysokość ma drzewo które ma `n` elementów?
- Jaka jest wysokość drzewa które ma `n` elementów w najgorszym możliwym wypadku?
- Ile kroków względem liczby elementów w drzewie trzeba wykonać żeby sprawdzić czy dany element jest w drzewie?

# Zadanie:
Zaimplementuj funkcje które pozwolą na dodawanie elementów do drzewa, usuwanie ich i przeszukiwanie drzewa.


## Znajdywanie elementu
Szukając elementu, musimy porównać nasz szukany element z korzeniem drzewa.
- jeśli jest równy - koniec, element znaleziony
- jeśli szukany element jest większy, szukamy w prawym poddrzewie
- jeśli szukany element jest mniejszy, szukamy w lewym poddrzewie
- jeśli nie ma poddrzewa - koniec elementu nie ma w drzewie
Następnie jeśli wybraliśmy poddrzewo, wykonujemy tą samą operacje rekurencyjnie.

```python
def find_elem(tree, elem):
  """funkcja sprawdza czy `elem` należy do drzewa BST i zwraca True lub False"""
  # TODO: Twoja implementacja
  pass
```


## Dodawanie elementu
Dodając element postępujemy analogicznie do szukania elementu.
Porównujemy dodawany element z korzeniem.

- jeśli jest równy - koniec, element już jest w drzewie
- jeśli dodawany element jest większy, idziemy w prawo
- jeśli dodawany element jest mniejszy, idziemy w lewo
- jeśli nie ma poddrzewa - dodajemy element na to miejsce i kończymy

```python
def add_elem(tree, elem):
  """funkcja która doda `elem` do drzewa BST"""
  # TODO: Twoja implementacja
  pass
```


## Usuwanie elementu
*Ta funkcja powinna zwracać korzeń nowego drzewa (po usunięciu elementu).*

Usuwając element trzeba się zastanowić co włożymy na jego miejsce. 
Są trzy możliwości:
- element nie ma dzieci - jest *liściem*
- element ma jedno dziecko
- element ma dwoje dzieci.

### element nie ma dzieci - jest *liściem*
Ta sytuacja jest najprostrza. Jeśli znaleźliśmy element który nie ma dzieci, trzeba go po prostu usunąć.
Musimy więc w jego rodzicu, ustawić odpowiednią *referencję* (czyli `left_child` lub `right_child`) na `None`.

Jeśli dostaliśmy jedno-elementowe drzewo i usuwamy ten element, zwrócimy `None`.

### element ma jedno dziecko:
Ta sytuacja też jest prosta. Podmieniamy u rodzica odpowiednią *referencję* (czyli `left_child` lub `right_child`) na dziecko tego węzłą.

### element ma dwoje dzieci.
No to problem. Które dziecko powinniśmy wstawić na miejsce tego rodzica? Co zrobić z jego dziećmi?

Zastanówmy się, jak znaleźć taki element drzewa, który łatwo usunąć (czyli np. jest *liściem*) i po wstawieniu na miejsce usuwanego elementu,
nie zaburzy porządku. Na potrzeby tego zadania taki element nazwiemy **dublerem**.

Załóżmy że mamy takie drzewo i chcemy usunąć element nr. 35.
![tr_del1](/lekcja7/tree_delete1.png)

Jeśli na miejsce `35` wstawimy inny element który dalej będzie mniejszy od prawego dziecka, a większy od lewego, to porządek będzie zachowany.

Jak znaleźć **najmniejszy** element **większy** od korzenia?

Zatrzymaj się na chwilę nad tym pytaniem i spróbuj na nie odpowiedzieć samemu.

[Odpowiedź.](/lekcja7/tree_delete2.png)

Gdy już znajdziemy taki element - (*dublera*), musimy zamienić usuwany element na ten który znaleźliśmy. 

1. Usunięcie dublera jest proste, ponieważ to liść.
2. Dublera wstawiamy na miejsce usuwanego elementu i dzieci usuwanego elementu stają się dziećmi dublera.
3. Rodzic usuwanego elementu teraz powinien mieć ustawionego dublera zamiast usuwanego dziecka.

[jamboard](https://jamboard.google.com/d/1bUr35tgEYEA-d3Mlp8TR2kBEWq_Z7_9MZ7ZekenFwrA/edit?usp=sharing)

```python
def delete_elem(tree, elem)
  """funkcja która usunie `elem` do drzewa BST, jeśli taki istnieje.
  Funkcja powinna zwracać korzeń nowego drzewa (po usunięciu elementu)."""
  # TODO: Twoja implementacja
  pass
```

# Przeszukiwanie drzewa (nie koniecznie BST):
Może się tak zdarzyć, że będziemy chcieli przejsć przez całe drzewo, tak żeby mieć pewność, że odwiedziliśmy każdy węzęł.

Można to zrobić na dwa sposoby: BFS, DFS

![dfs_bfs](https://res.cloudinary.com/practicaldev/image/fetch/s---f65OlYQ--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/i/e2ru41fjhqs4ombbcedf.png)

## BFS - Breadth First Search
Pierwszym sposobem jest przeszukiwanie warstwa po warstwie. Przechodzimy drzewo od góry i sprawdzamy najpierw każdy element na wysokości 0, potem na wysokości 1, etc.

![bfs_gif](https://upload.wikimedia.org/wikipedia/commons/5/5d/Breadth-First-Search-Algorithm.gif?20100504223639)


Postaraj się zaimplementować algorytm BFS samemu. Napisz funkcję BFS, która przejdzie po drzewie i zapisze wartość każdego elementu do wynikowej tablicy i po przejściu całego drzewa zwróci ją:
```python
# bfs

def bfs(tree):
  #TODO: Twoja implementacja
  return []

```

### Przykład:
```
      ┌──(14)
  ┌──(12)
─(10)
  │   ┌──(16)
  └──(15)
BFS: [10, 15, 12, 16, 14]
```

## DFS - Depth First Search

Drugim sposobem, jest najpierw wchodzenie najgłębiej jak się da. Następnie cofanie się i wchodzenie w kolejną "gałąź" drzewa, znów najgłębiej jak się da.

![dfs_gif](https://upload.wikimedia.org/wikipedia/commons/7/7f/Depth-First-Search.gif)

```python
# bfs

def dfs(tree):
  #TODO: Twoja implementacja
  return []

```

### Przykład
```
      ┌──(14)
  ┌──(12)
─(10)
  │   ┌──(16)
  └──(15)
DFS: [10, 15, 16, 12, 14]
```






## *Zadanie dodatkowe:* Drzewa AVL
Co zrobić żeby drzewa zawsze były *zbalansowane* tj. takie których wysokość jest zawsze nie większa niż `log(n)+1`?

Tworzymy drzewa które podczas dodawania zostają automatycznie zrebalansowane. W drzewie AVL operacje wyszukiwania, dodawania i usuwania wszystkie zajmują `log(n)`.
![drzewo_avl](https://upload.wikimedia.org/wikipedia/commons/f/fd/AVL_Tree_Example.gif)

Drzewa AVL opisane są [tutaj](https://pl.wikipedia.org/wiki/Drzewo_AVL).

Spróbuj je zaimplementować!

