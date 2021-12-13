# Projekt - <span style="color:red">do 22 Grudnia</span>

Waszym zadaniem będzie zrobienie jednego z wariantów projektu. Do zaliczenia tej części przedmiotu absolutnie niezbędne jest wykonanie przynajmniej wersji podstawowej. Oczywiście, im bardziej złożony projekt zrobisz, tym lepiej. Moment chwały, murowany. 

**Ale pamiętaj!** Wybranie trudniejszego projektu nie jest usprawiedliwieniem żeby go nie dokończyć! Zastanów się czy wolisz 100% pkt za prostszy projekt czy 30% za trudniejszy.

W razie pytań zawsze możesz napisać do mnie przez IDU/email/discord. Chętnie pomogę.

> Przypominam Wam że do zrobienia jest projekt. Na stronie jest opisane dokładnie co jest do zrobienia. 
Wszystkim polecam zrobić wersję podstawową jak najszybciej i potem dopiero robić rozszerzenia.

>Jeśli nie macie w domu komponentów to weźcie je ze szkoły po wcześniejszym ustaleniu z Jankiem lub Mną. 

> Jeśli jesteście uwięzieni w domu koniecznie napiszcie do mnie tu lub na maila i wymyślimy jak macie zaliczyć ten przedmiot.

> Do wersji podstawowej nie musicie używać LCD ani przerwań, tylko napisać trochę kodu i podłączyć 3 guziki.
Proszę Was nie zostawiajcie tego na ostatnią chwilę. W razie problemów piszcie do mnie tu lub na maila.

> Jeśli chodzi o przerwania: Arduino ma tylko dwa piny na których obsługuje przerwania (PIN2 i PIN3), zatem jeśli chcecie ich użyć (co nie jest obowiązkowe!):
> 1. Albo nie używajcie przerwań
> 2. Albo użyjcie tylko 2 guzików. Trzeba wtedy wymyślić co zrobić zamiast 3 guzika. (Np. wciśnięcie 2 na raz może odpalać timer)
> 3. Albo zróbcie to co jest opisane w nowym temacie na [stronie o przerwaniach](/interrupts.md). To jest trudniejsze i nie obowiązkowe. Nie robiliśmy tego na lekcji więc nie będę tego wymagał.


## Timer (wersja podstawowa) `10 pkt`:
Zrób timer, który ma 3 guziki: `+`, `-` i `start`.
używając `+` i `-` możemy ustawić czas. 
Po wciśnięciu `start` zaczynamy odliczanie w dół, a gdy dojdziemy do `0`, timer miga (diodami).
Jako ekranu możesz użyć ekranu komputera i wysyłać czas przez serial port.

**WAŻNE**: Pamiętaj że dobry timer to taki którego nie da się zepsuć ustawiając ujemny czas lub klikając start gdy na wyświetlaczu znajduje się już 0. Ponad to, raczej nie powinno się dać zmieniać czasu gdy timer odlicza.

### Rozszerzenia do timera :
1. zrób debouncing na guzikach. `2 pkt`
2. przy naciśnięciu *długo* guzika `start` timer przestaje odliczać i resetuje się do jakiegoś ustalonego czasu np. 1 min. `3 pkt`
3. użyj ekranu LCD do wyświetlania czasu `5 pkt`
4. użyj przerwań `5 pkt`

### Jak zrobić jedno przerwanie dla wielu guzików?
Wyjaśnienie [tutaj](/interrupts.md).

## Budzik (wersja rozszerzona) `18 pkt`
Zrób zegarek który pozwala ustawić godzinę i wyświetla czas. Powinien posiadać guziki do ustawiania czasu i  rozszerzenia 1 i 3 z wersji podstawowej. Przemyśl jak powinno wyglądać menu do ustawiania czasu i ile powinien mieć guzików.

### Rozszerzenia do budzika:
1. niech pokazuje również temperaturę w pomieszczeniu. `5 pkt`
2. dodaj możliwość ustawienia budzika. Wymyśli jak stworzyć wygodne w użyciu menu `10 pkt` 
3. Coś ekstra co nie zostało tu opisane! `? pkt`


# Zaliczanie projektu:

Opisane dokładnie na [poprzedniej stronie](/plan.md). Trzeba **wysłać kod do 8:00 22.12.2021** na mojego maila i zaprezentować działający projekt online o wcześniej umówionej godzinie.


![warning_sign](https://media3.giphy.com/media/Y5wlazC8lSVuU/giphy.gif?cid=ecf05e47a5es3ktuo49tolvdd7pftefap3rl7013lxp53vrj&rid=giphy.gif&ct=g)