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
    return '\n'.join(ret)
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

## Zadanie:
Zaimplementuj funkcje które pozwolą na dodawanie elementów do drzewa, usuwanie ich i przeszukiwanie drzewa.

### Dodawanie elementu
```python
def add_elem(tree, elem):
  """funkcja która doda `elem` do drzewa BST"""
  # TODO: Twoja implementacja
  pass
```

### Znajdywanie elementu
```python
def find_elem(tree, elem):
  """funkcja sprawdza czy `elem` należy do drzewa BST"""
  # TODO: Twoja implementacja
  pass
```

### Usuwanie elementu
```python
def delete_elem(tree, elem)
  """funkcja która usunie `elem` do drzewa BST, jeśli taki istnieje."""
  # TODO: Twoja implementacja
  pass
```

## Drzewa ADL