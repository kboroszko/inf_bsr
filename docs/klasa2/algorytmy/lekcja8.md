# Przeszukiwanie drzewa

### Kartkówka na początek:
Liczbę nazwiemy doskonałą jeśli jest równa sumie swoich dzielników. Na przykład `28 = 14 + 7 + 4 + 2 + 1` , [WIKIPEDIA](https://pl.wikipedia.org/wiki/Liczba_doskona%C5%82a). Napisz funkcję która sprawdza czy dana liczba jest liczba doskonała.

*Rozwiązania prześlijcie na ten sam adres email co zawsze, z tytułem: "Kartkówka 28.02".*


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


**Zwróć uwagę**, że jeśli drzewo jest drzewem BST, to przeszukując je algorytmem DFS elementy będą znajdywane w kolejności rosnącej.


