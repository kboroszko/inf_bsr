# Algorytmy i struktury danych

Zasady pisania pseudo-kodu:
1. Piszemy w prymitywnej wersji pythona. Składnia wygląda tak samo, kod który piszemy można bez problemu uruchomić jako zwykły pythonowy program.
2. Uzywamy tylko prymitywnych operacji 
    - przypisanie
    - operacje artmetyczne `+.-,*,/,%`
3. Jeśli zadanie *explicite* na to nie pozwala, nie używamy żadnych nie napisanych przez nas funkcji, bibliotek i zaawansowanych cech języka takich jak:
    - domyślna wartość argumentów funkcji
    - `sorted(...)`, `filter()`, `pow()`, potęgowanie: `**` itp.
4. Wyjatki to:
    - można sprawdzać długość tablicy/stringa `len(x)`
    - dla uproszczenia można używać pętli for po elementach tablicy: `for n in [1,2,3]:`
    - można też iterować po indexach w pętli for: `for n in range(len(list))`
    - dodawanie elementu na końcu tablicy `list.append(elem)`

.
--------------------

## 1. [złożoność obliczeniowa](/lekcja1.md)
## 2. [rekurencja](/lekcja2.md)
