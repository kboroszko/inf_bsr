# Hash function

### Kartkówka na początku lekcji

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