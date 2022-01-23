# Trudne zadania dodatkowe


1. Napisz funkcję trójkąt, która dla danej listy `[x1; x2; . . . ; xn]` dodatnich liczb całkowitych sprawdzi, czy lista zawiera trójkę elementów `xi`, `xj` i `xk` spełniających nierówność trójkąta, tzn.: `2 · max(xi, xj, xk) ≤ xi + xj + xk`. **UWAGA** Zakładając że na liscie są liczby naturalne mniejsze od 10, spróbuj napisać funkcję której złożoność wynosi O(1) - jest stała i nie zależnie od długości listy.


2. Ciąg różnicowy ciągu [x1; x2; . . . ; xn], to ciąg postaci [x2 − x1; x3 − x2; . . . ; xn − xn−1].
    - Oblicz ciąg różnicowy zadanej listy liczb całkowitych

3.  Oblicz listę złożoną z pierwszych elementów kolejnych ciągów różnicowych danej listy, tzn.: głowy danej listy, gowy jej ciągu różnicowego, głowy ciągu różnicowego jej ciągu różnicowego itd.


4. prefixo-suffix słowa to taki ciąg znaków który znajduje się na początku i na końcu tego słowa. Przykłady:

```
"aabababaaab" ma prefixo-suffix "aab"
"abbababb" ma prefixo-suffix "abb"
"abbabba" ma prefixo-suffix "abba"
```

Napisz funkcje `pref_suf(slowo)` która znajduje najdłuższy prefixo-suffix (który nie jest tym słowem).


5. Liczbę naturalną nazwiemy rzadką, jeżeli w jej zapisie binarnym żadne dwie jedynki nie stoją obok siebie. Napisz funkcję `rzadkie(n)` która sprawdzi czy dana liczba n jest liczbą rzadką. Na przykład liczba `n = 10 = 1010` jest rzadka, a liczba `n = 12 = 1100` nie jest rzadka.
    - `*` napisz funkcję `ile_rzadkich(n)` która dla danej liczby naturalnej n wyznaczy liczbę dodatnich liczb rzadkich, które nie przekraczają n. Na przykład, dla `n = 42 = 1010102` mamy rzadkie 42 = 20.


6. Bajtek ma zabawkę, z której wystają drewniane słupki różnej wysokości. Jednym uderzeniem młotka może wbić lub wysunąć wybrany słupek o 1.
Napisz procedurę słupki, która dla danej listy początkowych wysokości słupków obliczy minimalną liczbę uderzeń młotka potrzebnych do wyrównania wysokości słupków.

7. Napisz funkcje `pary(lista, target)` która wypisze wszystkie pary elementów sumujące się do podanej liczby `target`. przykład: 
`pary([1,2,3,4,3,2,0], 4)` →  `(1, 3), (2,2), (4, 0)`

8. Napisz funkcje `trojki(lista, target)` która sprawdzi czy trójka o podanej sumie istnieje na liście.

```
Input:
 
lista = [ 2, 7, 4, 0, 9, 5, 1, 3 ]
target = 6
 
Output: True
 
Na przykład {1, 2, 3} 
```

9. Twój plecak ma pewną pojemność. Masz do spakowania pewne przedmioty, każdy z nich ma określoną wartość i zajmuje pewną ilość miejsca. Napisz funkcję `knapsack(items, cap)` która przyjmuję listę par wartości i pojemność plecaka. każda para na liście oznacza odpowiednio rozmiar i wartość danej rzeczy. Wynikiem działania tej funkcji powinna być lista rzeczy które spakujesz do plecaka tak żeby się  zmieściły i żeby wartość była jak największa.
