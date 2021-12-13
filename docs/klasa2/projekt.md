# Projekt - <span style="color:red">do 22 Grudnia</span>

Waszym zadaniem będzie zrobienie jednego z wariantów projektu. Do zaliczenia tej części przedmiotu absolutnie niezbędne jest wykonanie przynajmniej wersji podstawowej. Oczywiście, im bardziej złożony projekt zrobisz, tym lepiej. Moment chwały, murowany. 

**Ale pamiętaj!** Wybranie trudniejszego projektu nie jest usprawiedliwieniem żeby go nie dokończyć! Zastanów się czy wolisz 100% pkt za prostszy projekt czy 30% za trudniejszy.

W razie pytań zawsze możesz napisać do mnie przez IDU/email/discord. Chętnie pomogę.

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