# Hash function

### Kartkówka na początku lekcji
Napisz funkcję która dostanie jako argument drzewo i sprawdzi czy to drzewo jest drzewem BST.

## Cechy funkcji hashującej:
- łatwa do policzenia
- daje wartości ze stałego zakresu
- nieodwracalna (mając hash *trudno* znaleźć klucz)
- mało kolizji (minimalna szansa na to że dwa klucze dadzą ten sam wynik *[pigeon hole](https://en.wikipedia.org/wiki/Pigeonhole_principle)*) 
- mała zmiana klucza powoduje dużą zmianę hash'a (efekt lawiny)

## przykłady:
- kod pocztowy
- ostatnie 2 cyfry numeru telefonu
- modulo

**prawidzwy przykład:**
```python
def hash(key):
    m = 100
    c = 0.152372912706488
    h = (m * (key * c % 1))
    return int(h)
```

# Przykład użycia - HashTable
Robimy długą tablicę o długości `m` która bardzo przewyższa długością ilość spodziewanych elementów.

Dodając element, najpierw liczymy jego hash → tym sposobem otrzymujemy liczbę od 1 do m. Następnie
używamy hasha jako indexu w tej tablicy. Możemy tam coś włożyć. Albo ten element albo coś innego.

![hash_table](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7d/Hash_table_3_1_1_0_1_0_0_SP.svg/1200px-Hash_table_3_1_1_0_1_0_0_SP.svg.png)

Jakie właściwości ma taka tablica?
- element który hashujemy nazywamy **kluczem** (ang. key) bo służy do wkładania i wyciągania wartości.
- jeśli tablica jest dużo większa niż ilość elementów która w niej jest, prawdopodobieństwo kolizji jest bardzo małe.
- jeśli do środka tablicy wrzucimy element który zhashowaliśmy do indexu, to mamy `hash-set`.
    - taki zbiór ma tylko jedną wartość każdego rodzaju
    - złożoność dodawania elementu do takiego zbioru jest stała
    - złożoność wyciągania elementu również

- jeśli do środka tablicy wrzucimy coś innego, to mamy słownik do którego wrzucamy parę `<klucz, wartość>`.
    - taki słownik ma tylko jeden klucz każdego rodzaju
    - złożoność dodawania elementu do takiego zbioru jest stała
    - złożoność wyciągania elementu również


Co jeśli mamy pecha i wystąpi kolizja?
![hash_table_colisions](https://www.jsmount.com/wp-content/uploads/2021/02/hash-table-structure.png)




# Praca domowa
Napisać program który sprawdzi dla każdego indexu od 1 do `m = 100` jaki jest jego hash
oraz sprawdzi czy dany hash nie wystąpił już wcześniej. Następnie wypisze listę kolizji
tj. takich indexów które mają taki sam hash.

przykład:
```
i:1     h:28
i:2     h:56
i:3     h:84
i:4     h:12
i:5     h:40
.
.
.
i:96    h:93
i:97    h:21
i:98    h:49
i:99    h:77
i:100   h:5

Colisions:
1,77 hash to 28
14,56,99 hash to 77
.
.
.
```