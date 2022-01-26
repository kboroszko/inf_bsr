# Treść


Bajtek ma cały garaż zawalony pudłami i potrzebuje pomocy w porządkach. W tej chwili wszystkie pudła leżą na ziemi i zajmują strasznie dużo miejsca. Bajtek próbował ustawiać je jedne na drugim, ale gdy układa je w stosy, pudła spadają mu na głowę. Żeby stos pudeł był stabilny, trzeba zawsze się upewnić że pudło które stawiamy na górze jest **ściśle** mniejsze w obydwu wymiarach od pudła na którym je stawiamy.

Przykładowe pudło:

![pudło](https://szaloneliczby.pl/wp-content/uploads/2016/09/wysokosc-szerokosc-dlugosc-prostopadloscianu-rys.png)

np. Gdy mamy pudło o wymiarach: `5 x 6 x 4` (długość x szerokość x wysokość)

to możemy je postawić na pudle o wymiarach `7 x 8 x 4`. 

Ale nie wolno nam ustawić go na pudle o wymiarach `5 x 7 x 4` ponieważ ma za małą długość.

Pudła można też obracać, ale tak żeby dalej stały na tym samym boku! tzn. pudło o wymiarach `5 x 6 x 4` można obrócić i wtedy będzie miało wymiary `6 x 5 x 4`, ale jego wysokość zawsze będzie taka sama.

Wobec tego pudło `6 x 3 x 4` można ustawić na pudle `5 x 10 x 4`.


Bajtek już dawno zapomniał po co układa te pudła, ale chciałby wiedzieć jaki najwyższy stos może ustawić ze swoich pudeł.

Napisz program który w pierwszej lini wczyta jedną liczbę `N` oznaczającą liczbę pudeł, a następnie w kolejnych `N` liniach wczyta po 3 liczby oddzielone spacjami, oznaczające kolejno długość, szerokość, wysokość każdego pudła.

Twój program powinien wypisać jedną liczbę oznaczającą maksymalną wysokość stabilnej wierzy jaką może ułożyć Bajtek.

### Przykłady:

| Przykładowe wejście | Przkładowe wyjście |
| ------------------- | ------------------ |
| `3`                 | `9   `             |
| `3 4 2`             |                    |
| `5 5 3`             |                    |
| `7 9 4`             |                    |

| Przykładowe wejście | Przkładowe wyjście |
| ------------------- | ------------------ |
| `3`                 | `8   `             |
| `3 4 5`             |                    |
| `4 5 2`             |                    |
| `3 3 6`             |                    |

| Przykładowe wejście | Przkładowe wyjście |
| ------------------- | ------------------ |
| `2`                 | `9   `             |
| `3 3 5`             |                    |
| `3 3 9`             |                    |

| Przykładowe wejście | Przkładowe wyjście |
| ------------------- | ------------------ |
| `3`                 | `7`                |
| `3 5 5`             |                    |
| `6 4 2`             |                    |
| `3 5 3`             |                    |


# Wczytywanie pudełek

Żeby wczytać wejście od użytkownika używamy instrukcji `input()`. Ta instrukcja wczytuje całą linijkę
podaną przez uzytkownika jako string. 

W naszym programie najpierw wczytujemy ile linijek z pudełkami będzie. Pamiętajmy o tym że to co wczytamy
to będzie `string` więc trzeba go jeszcze zamienić na liczbę instrukcją `int(str)`

Następnie wczytujemy tyle linijek z pudełkami ile potrzeba.

```python
N = int(input())

pudelka = []

for i in range(N):
    pudelka.append(input())

print("pudełka:")
print(pudelka)
```

Spróbuj uruchomić ten kod wpisać jakieś liczby i zobacz co się stanie.

.
---------------------

Każde pudełko jest opisane przez 3 liczby w jednej linijce.
Niestety python wczytuje każdą linijkę na raz, nie da się mu powiedzieć żeby przeczytał jedną liczbę do spacji. Trzeba więc podzielić je ręcznie. Jeśli mamy string który zawiera spacje, to możemy go podzielić wywołując na nim instrukcję `split()`.

na przykład:
```python
x = "Ala ma kota"
print(x.split())
x.split() == ["Ala", "ma", "kota"]
```

Więc jeśli wczytami linijkę w której jest pudełko np: "2 3 5"
to musimy ją podzielić:

```python
linijka = "2 3 5"
podzielona = linijka.split()

print(podzielona)
```

otrzymujemy listę stringów, trzeba jeszcze zamienić je na liczby, tak żebyśmy mogli operować na liczbach

```python
linijka = "2 3 5"
podzielona = linijka.split()

x_pudelka = int(podzielona[0])
y_pudelka = int(podzielona[1])
z_pudelka = int(podzielona[2])
```

### wszystko razem:

```python
N = int(input())

pudelka = []

for i in range(N):
    linijka = input()
    podzielona = linijka.split()

    x = int(podzielona[0])
    y = int(podzielona[1])
    z = int(podzielona[2])

    pudelko = [x,y,z]

    pudelka.append(pudelko)

print("pudełka:")
print(pudelka)
```

# Uruchamianie programu w konsoli (Przypomnienie)

Żeby uruchomić program który nazywa się `main.py` napisany w pythonie piszemy w konsoli:
```bash
python3 main.py
```

Po uruchomieniu, program zapyta nas o dane wejściowe.

Bash pozwala nam przekierować zawartość pliku zamiast wpisywania. Robimy to znaczkiem `>` (shift + kropka). Jeśli stworzymy plik `in.txt` i wpiszemy do niego dane wejściowe, np:

**in.txt:**
```
2
3 4 5
2 1 4
```

Możemy uruchomić program tak żeby komputer odrazu podał mu te dane z pliku

```bash
python3 main.py < in.txt
```

Tak samo, możemy zapisać wyjście do pliku:

```bash
echo "Hello" > test.txt
```
Ta instrukcja stwoży plik `test.txt` o zawartości "Hello".

### Wszystko razem:
```
python main.py < in.txt > out.txt
```
Ta instrukcja uruchomi `main.py`, wpisze dane z pliku `in.txt` i zapisze w `out.txt`

# Testy

Pierwsza paczka testów znajduje się tutaj:
- [testy](/zadanie_domowe/testy.zip)

Po pobraniu należy ją rozpakować. Są tam dwie rzeczy, folder `tests` i skrypt w bashu `run_tests.sh` który uruchamia testy po koleji. **Nie uruchomisz go na windowsie!** Jeśli nie masz linuxa to zaloguj się na serwer którego używałeś w pierwszym semestrze z Konradem.

dla przyponienia, IP napisałem na discordzie.

W katalogu `tests` znajdują się pliki ponumerowane kolejno od 1 do 10.
Każdy plik ma dwa warianty `1.in` i `1.out` w których znajduje się odpowiednio: dane wejściowe i spodziewany wynik.

Skrypt uruchamia program `main.py` i sprawdza czy to co wypisał jest takie samo jak w pliku z wynikiem.

Testów będzie więcej wkrótce.