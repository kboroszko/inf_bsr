# Drzewa 馃尦

[kod](https://codecollab.io/@kajetan/binsearch)

### Kartk贸wka
**Cz臋艣膰 1:**
Tworzymy drzewo BST z nast臋puj膮cych element贸w:
```
[1,2,3,4,5,6,7,8,9,10]
```
1. Jak膮 minimaln膮 ma wysoko艣膰?
2. Jak膮 maksymaln膮?
3. Je艣li drzewo mia艂oby `n` element贸w i by艂oby *zbalansowane*, jaka jest z艂o偶ono艣膰 obliczeniowa operacji dodawania elementu?


**Cz臋艣膰 2:**
Tworzymy drzewo BST dodaj膮c do niego elementy w nast臋puj膮cej kolejno艣ci:
```
[35,28,31,59,23,55,67,50,56,30]
```
Narysuj je sobie w zeszycie dla u艂atwienia.


4. Jaka jest wysoko艣膰 tego drzewa?
5. Ile operacji por贸wnania zostanie wykonanych przy dodawaniu elementu o warto艣ci `70`?
6. Ile operacji por贸wnania zostanie wykonanych przy dodawaniu elementu o warto艣ci `29`?
7. Ile operacji por贸wnania zostanie wykonanych przy dodawaniu elementu o warto艣ci `23`? (uwaga: ten element ju偶 jest w drzewie)

*呕eby zaliczy膰 kartk贸wk臋, odpowiedz dobrze na 6/7 pyta艅.*

## Binary tree

Drzewem binarnym nazywamy tak膮 struktur臋 danych, wkt贸rej ka偶dy przechowywany element mo偶e mie膰 rodzica i dw贸jk臋 dzieci.

![drzewo](/lekcja7/binary_search_tree.png)


Taki spos贸b przedstawienia danych pozwala na zawarcie dodatkowych informacji o danych przez to jak s膮 u艂o偶one.

## Implementacja drzewa:

```python
class Tree:
  value = None
  left_child = None
  right_child = None

  def __init__(self, value):
    self.value = value  
```

## Przyk艂ady:

Stw贸rzmy takie drzewo kt贸re ma dwoje dzieci.
```
  鈹屸攢鈹?(6)
鈹?(5)
  鈹斺攢鈹?(4)
```
Tworzymy je w ten spos贸b:
```python
# korze艅
tr1 = Tree(5)

# prawe dziecko
tr2 = Tree(6)
tr1.right_child = tr2

# lewe dziecko
tr3 = Tree(4)
tr1.left_child = tr3
```

Spr贸buj stworzy膰 takie drzewa:
### 1.
```
      鈹屸攢鈹?(7)
  鈹屸攢鈹?(6)
鈹?(5)
```

### 2.
```
      鈹屸攢鈹?(8)
  鈹屸攢鈹?(6)
鈹?(5)
  鈹?   鈹屸攢鈹?(4)
  鈹斺攢鈹?(3)
```

### 3.
```
      鈹屸攢鈹?(7)
  鈹屸攢鈹?(6)
鈹?(5)
  鈹?   鈹屸攢鈹?(4.5)
  鈹斺攢鈹?(4)
      鈹?   鈹屸攢鈹?(3.5)
      鈹斺攢鈹?(3)
          鈹斺攢鈹?(2)
```

### Drukowanie drzewa

Poni偶ej jest funkcja kt贸ra wypisuje drzewo w konsoli. Skopiuj j膮 do swojego programu.

```python
def print_tree(tree, rec=False):
  if tree is None:
    return [],0
  right_subtree, idx_r = print_tree(tree.right_child, rec=True)
  left_subtree, idx_l = print_tree(tree.left_child, rec=True)
  ret = []
  for i,e in enumerate(right_subtree):
    if i == idx_r:
      ret.append("  鈹屸攢" + e)
    elif i < idx_r:
      ret.append("    " + e)
    else:
      ret.append("  鈹? " + e)
  ret_idx = len(ret)
  ret.append(f"鈹?({tree.value})")
  for i,e in enumerate(left_subtree):
    if i == idx_l:
      ret.append("  鈹斺攢" + e)
    elif i > idx_l:
      ret.append("    " + e)
    else:
      ret.append("  鈹? " + e)
  if rec:
    return ret, ret_idx
  else:
    print('\n'.join(ret))
    return None
```

## BST - Binary Search Tree

Binary Search Tree - to drzewo w kt贸rym ustawiamy elementy w nast臋puj膮cy spos贸b:
- Je艣li drzewo jest puste, nowy element staje si臋 **korzeniem**.
- Je艣li element jest wi臋kszy od korzenia, wstawiamy go jako prawe dziecko
- Je艣li jest mniejszy, jako lewe.

Przyk艂ad znajduje si臋 [tutaj](http://btv.melezinek.cz/binary-search-tree.html).

Teraz spr贸bujmy spawdzi膰 czy dany element ju偶 jest w drzewie.
Wykonujemy wszystko tak jakby艣my chcieli doda膰 ten element do drzewa **ale nie dodajemy go na ko艅cu**. Je艣li natrafimy na ten element po drodze, to wiemy 偶e by艂 w drzewie.

Postaraj si臋 odpowiedzie膰 na te pytania:

- Jak膮 minimaln膮 wysoko艣膰 ma drzewo kt贸re ma 10 element贸w?
- Jak膮 minimaln膮 wysoko艣膰 ma drzewo kt贸re ma `n` element贸w?
- Jaka jest wysoko艣膰 drzewa kt贸re ma `n` element贸w w najgorszym mo偶liwym wypadku?
- Ile krok贸w wzgl臋dem liczby element贸w w drzewie trzeba wykona膰 偶eby sprawdzi膰 czy dany element jest w drzewie?

# Zadanie:
Zaimplementuj funkcje kt贸re pozwol膮 na dodawanie element贸w do drzewa, usuwanie ich i przeszukiwanie drzewa.


## Znajdywanie elementu
Szukaj膮c elementu, musimy por贸wna膰 nasz szukany element z korzeniem drzewa.
- je艣li jest r贸wny - koniec, element znaleziony
- je艣li szukany element jest wi臋kszy, szukamy w prawym poddrzewie
- je艣li szukany element jest mniejszy, szukamy w lewym poddrzewie
- je艣li nie ma poddrzewa - koniec elementu nie ma w drzewie
Nast臋pnie je艣li wybrali艣my poddrzewo, wykonujemy t膮 sam膮 operacje rekurencyjnie.

```python
def find_elem(tree, elem):
    if elem == tree.value:
        return True
    if elem < tree.value and tree.left_child is not None:
        return find_elem(tree.left_child, elem)
    if elem > tree.value and tree.right_child is not None:
        return find_elem(tree.right_child, elem)
    return False
```


## Dodawanie elementu
Dodaj膮c element post臋pujemy analogicznie do szukania elementu.
Por贸wnujemy dodawany element z korzeniem.

- je艣li jest r贸wny - koniec, element ju偶 jest w drzewie
- je艣li dodawany element jest wi臋kszy, idziemy w prawo
- je艣li dodawany element jest mniejszy, idziemy w lewo
- je艣li nie ma poddrzewa - dodajemy element na to miejsce i ko艅czymy

```python
def add_elem(tree, elem):
    if elem == tree.value:
        return 
    if elem < tree.value and tree.left_child is not None:
        return add_elem(tree.left_child, elem)
    if elem > tree.value and tree.right_child is not None:
        return add_elem(tree.right_child, elem)
    if elem < tree.value and tree.left_child is None:
        new_tree = Tree(elem)
        tree.left_child = new_tree
        return
    if elem > tree.value and tree.right_child is None:
        new_tree = Tree(elem)
        tree.right_child = new_tree
        return 
```


## Usuwanie elementu
*Ta funkcja powinna zwraca膰 korze艅 nowego drzewa (po usuni臋ciu elementu).*

Usuwaj膮c element trzeba si臋 zastanowi膰 co w艂o偶ymy na jego miejsce. 
S膮 trzy mo偶liwo艣ci:
- element nie ma dzieci - jest *li艣ciem*
- element ma jedno dziecko
- element ma dwoje dzieci.

### element nie ma dzieci - jest *li艣ciem*
Ta sytuacja jest najprostrza. Je艣li znale藕li艣my element kt贸ry nie ma dzieci, trzeba go po prostu usun膮膰.
Musimy wi臋c w jego rodzicu, ustawi膰 odpowiedni膮 *referencj臋* (czyli `left_child` lub `right_child`) na `None`.

Je艣li dostali艣my jedno-elementowe drzewo i usuwamy ten element, zwr贸cimy `None`.

### element ma jedno dziecko:
Ta sytuacja te偶 jest prosta. Podmieniamy u rodzica odpowiedni膮 *referencj臋* (czyli `left_child` lub `right_child`) na dziecko tego w臋z艂膮.

### element ma dwoje dzieci.
No to problem. Kt贸re dziecko powinni艣my wstawi膰 na miejsce tego rodzica? Co zrobi膰 z jego dzie膰mi?

Zastan贸wmy si臋, jak znale藕膰 taki element drzewa, kt贸ry 艂atwo usun膮膰 (czyli np. jest *li艣ciem*) i po wstawieniu na miejsce usuwanego elementu,
nie zaburzy porz膮dku. Na potrzeby tego zadania taki element nazwiemy **dublerem**.

Za艂贸偶my 偶e mamy takie drzewo i chcemy usun膮膰 element nr. 35.
![tr_del1](/lekcja7/tree_delete1.png)

Je艣li na miejsce `35` wstawimy inny element kt贸ry dalej b臋dzie mniejszy od prawego dziecka, a wi臋kszy od lewego, to porz膮dek b臋dzie zachowany.

Jak znale藕膰 **najmniejszy** element **wi臋kszy** od korzenia?

Zatrzymaj si臋 na chwil臋 nad tym pytaniem i spr贸buj na nie odpowiedzie膰 samemu.

[Odpowied藕.](/lekcja7/tree_delete2.png)

Gdy ju偶 znajdziemy taki element - (*dublera*), musimy zamieni膰 usuwany element na ten kt贸ry znale藕li艣my. 

1. Usuni臋cie dublera jest proste, poniewa偶 to li艣膰.
2. Dublera wstawiamy na miejsce usuwanego elementu i dzieci usuwanego elementu staj膮 si臋 dzie膰mi dublera.
3. Rodzic usuwanego elementu teraz powinien mie膰 ustawionego dublera zamiast usuwanego dziecka.

[jamboard](https://jamboard.google.com/d/1bUr35tgEYEA-d3Mlp8TR2kBEWq_Z7_9MZ7ZekenFwrA/edit?usp=sharing)

```python

def delete_elem(tree, elem):
    parent = None
    current_node = tree
    while current_node.value != elem:
        if elem < current_node.value:
            parent = current_node
            current_node = current_node.left_child
        else:
            parent = current_node
            current_node = current_node.right_child

    # current_node jest li艣ciem (nie ma dzieci)
    if current_node.right_child is None and current_node.left_child is None:
        if parent is not None:
            if parent.left_child.value == current_node.value:
                parent.left_child = None
            else:
                parent.right_child = None
            return tree
        else:
            return None
    
    # current_node ma tylko prawe dziecko
    if current_node.right_child is not None and current_node.left_child is None:
        if parent is not None:
            if parent.left_child.value == current_node.value:
                parent.left_child = current_node.right_child
            else:
                parent.right_child = current_node.right_child
            return tree
        else:
            return current_node.right_child

    # current_node ma tylko lewe dziecko
    if current_node.right_child is None and current_node.left_child is not None:
        if parent is not None:
            if parent.left_child.value == current_node.value:
                parent.left_child = current_node.left_child
            else:
                parent.right_child = current_node.left_child
            return tree
        else:
            return current_node.left_child

    # current node ma oboje dzieci
    else:
        if current_node.right_child.left_child is not None:
            node = current_node.right_child.left_child
            while node.left_child is not None:
                node = node.left_child
            delete_elem(tree, node.value)
            current_node.value = node.value
            if parent is None:
                return current_node
            else:
                return tree
        else:
            current_node.right_child.left_child = current_node.left_child
            if parent is not None:
                if parent.value > current_node.value:
                    parent.left_child = current_node.right_child
                else:
                    parent.right_child = current_node.right_child
                return tree
            else:
                return current_node.right_child
```



# Praca domowa:
We藕 swoje imie i nazwisko. Zamie艅 litery na liczby wed艂ug tej tabeli:

| Lp. | Majusku艂a | Minusku艂a |                 Nazwa                 |
|:---:|:---------:|:---------:|:-------------------------------------:|
|   1 | A         | a         | a                                     |
|   2 | 膭         | 膮         | 膮; a z ogonkiem                       |
|   3 | B         | b         | be                                    |
|   4 | C         | c         | ce                                    |
|   5 | 膯         | 膰         | cie; ce z kresk膮                      |
|   6 | D         | d         | de                                    |
|   7 | E         | e         | e                                     |
|   8 | 臉         | 臋         | 臋; e z ogonkiem                       |
|   9 | F         | f         | ef                                    |
|  10 | G         | g         | gie                                   |
|  11 | H         | h         | ha                                    |
|  12 | I         | i         | i                                     |
|  13 | J         | j         | jot                                   |
|  14 | K         | k         | ka                                    |
|  15 | L         | l         | el                                    |
|  16 | 艁         | 艂         | e艂; el z kresk膮                       |
|  17 | M         | m         | em                                    |
|  18 | N         | n         | en                                    |
|  19 | 艃         | 艅         | e艅; en z kresk膮                       |
|  20 | O         | o         | o                                     |
|  21 | 脫         | 贸         | o z kresk膮; o kreskowane; u zamkni臋te |
|  22 | P         | p         | pe                                    |
|  23 | R         | r         | er                                    |
|  24 | S         | s         | es                                    |
|  25 | 艢         | 艣         | e艣; es z kresk膮                       |
|  26 | T         | t         | te                                    |
|  27 | U         | u         | u; u otwarte                          |
|  28 | W         | w         | wu                                    |
|  29 | Y         | y         | y; igrek                              |
|  30 | Z         | z         | zet                                   |
|  31 | 殴         | 藕         | ziet; zet z kresk膮                    |
|  32 | 呕         | 偶         | 偶et; zet z kropk膮                     |

*殴r贸d艂o [wikipedia](https://pl.wikipedia.org/wiki/Alfabet_polski)*

Napisz **program** kt贸ry stworzy drzewo BST z liczb z imienia,
nast臋pnie dla ka偶dej liczby z nazwiska wypisze czy znajduje si臋 w tym drzewie.

Pisz膮c prac臋 domow膮 skorzystaj z funkcji kt贸re pisali艣my na lekcji

Przyk艂ad dla 'Janek Kowalski':
```
Drzewo imienia:
  鈹屸攢鈹?(18)
  鈹?   鈹斺攢鈹?(14)
鈹?(13)
  鈹?   鈹屸攢鈹?(7)
  鈹斺攢鈹?(1)

Litery nazwiska:
'k':True
'o':False
'w':False
'a':True
'l':False
's':False
'k':True
'i':False
```

## *Zadanie dodatkowe:* Drzewa AVL
Co zrobi膰 偶eby drzewa zawsze by艂y *zbalansowane* tj. takie kt贸rych wysoko艣膰 jest zawsze nie wi臋ksza ni偶 `log(n)+1`?

Tworzymy drzewa kt贸re podczas dodawania zostaj膮 automatycznie zrebalansowane. W drzewie AVL operacje wyszukiwania, dodawania i usuwania wszystkie zajmuj膮 `log(n)`.
![drzewo_avl](https://upload.wikimedia.org/wikipedia/commons/f/fd/AVL_Tree_Example.gif)

Drzewa AVL opisane s膮 [tutaj](https://pl.wikipedia.org/wiki/Drzewo_AVL).

Spr贸buj je zaimplementowa膰!

