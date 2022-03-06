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
    return h - int(h)
```

