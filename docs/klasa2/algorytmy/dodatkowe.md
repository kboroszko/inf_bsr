# Zadania dodatkowe


1. Napisz funkcję `jak_duzo(lista, elem)` która wczyta listę i element i policzy ile razy ten element występuje na liście.
2. Napisz funkcję `brakujace(lista)` która wczyta posortowaną listę i sprawdzi jakich elementów brakuje do tego żeby na tej liscie były wszystkie liczby od 0 do 10. Na przykład `brakujace([0,1,2,5,6,7,8,10]) == [3, 4, 9]`. 
3. Napisz funkcję `para(lista, n)` która przyjmuje listę i liczbę `n` i sprawdza czy na liście jest taka para elementów która sumuje się do n. Na przykład: `para([1,2,3,4,3,0,7,2], 7) == True`
4. Napisz funkcję `powielone(lista)` która liczy ile jest elementów na liście które powtarzają się conajmniej raz. Na przykład: `powielone([1,2,3,2,4,1,2]) == 2`.
5. Napisz funkcję `wzrost(lista)`, która dla danej listy liczb całkowitych znajduje w niej najdłuższy spójny fragment ściśle rosnący i zwraca go. Na przykład:
`wzrost([3, 4, 0, -1, 2, 3, 7, 6, 7, 8] = [-1, 2, 3, 7]`
Ściśle rosnący tj. taki w którym każdy element jest większy od poprzedniego o conajmniej 1.
6. Listę nazwiemy ciekawą jeśli żadne dwa kolejne jej elementy nie są sobie równe. Napisz funkcję `podzial(lista)` , która daną listę podzieli na minimalną liczbę spójnych fragmentów (zachowując ich kolejność), z których każdy jest ciekawy.
Na przykład, `podzial([3, 2, 2, 5, 7, 5, 4, 4, 3, 1]) = [[3, 2], [2, 5, 7, 5, 4], [4, 3, 1]]`

7. Liczbę nazwiemy doskonałą jeśli jest równa sumie swoich dzielników. Na przykład `28 = 14 + 7 + 4 + 2 + 1` , [WIKIPEDIA](https://pl.wikipedia.org/wiki/Liczba_doskona%C5%82a). Napisz funkcję która sprawdza czy dana liczba jest liczba doskonała.
    - Napisz funkcję która znajduje wszystkie liczby doskonałe mniejsze od n


8. napisz funkcje `flatten(lista)` która wczytuję listę list i zwraca listę elementów. Na przykład: `flatten([[1,2], [3], [4,5]]) = [1,2,3,4,5]`
    - `*` Uogólnij funkcję flatten tak żeby listy mogły być dowolnie zagnieżdżone, tzn. elementem listy może być liczba, lista liczb, lista list liczb, lista list list liczb... itd.. Na przykład `flatten([1,[2], [3,[4,5]]]) = [1,2,3,4,5]`


9. Masz za zadanie zaplanować nową stację kolejową. Masz listę godzin o których przyjeżdżają i odjeżdżają pociągi. (pociągi odjeżdżają tylko o pełnych godzinach i stoją na stacji conajmniej godzinę.) Musisz policzyć ile conajmniej torów będzie potrzebnych do obsłużenia pociągów. Napisz funkcję `ile_torow(lista)` która wczyta listę par. Każda para oznacza godzinę przyjazdu i odjazdu. Funkcja ma zwrócić minimalną listę torów potrzebnych do obsłużenia pociągów. Jeśli na danym torze stoi pociąg, to kolejny potrzebuje nowego wolnego toru. Jeśli jeden pociąg dojeżdża dokładnie wtedy kiedy drugi odjeżdża to także potrzebują dwóch różnych torów.

Przykład:
```
lista = [(1,2), (1,7), (3, 4), (7,9)]

`(1,2)` oznacza że pociąg przyjeżdża o 1 i odjeżdża o 2.

ile_torow(lista) == 2
```