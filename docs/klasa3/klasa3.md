<style>
 /* The alert message box */
.alert {
  padding: 20px;
  background-color: #f44336; /* Red */
  color: white;
  margin-bottom: 15px;
}

/* The close button */
.closebtn {
  margin-left: 15px;
  color: white;
  font-weight: bold;
  float: right;
  font-size: 22px;
  line-height: 20px;
  cursor: pointer;
  transition: 0.3s;
}

/* When moving the mouse over the close button */
.closebtn:hover {
  color: black;
} 
</style>

# Projekty


* TOC
{:toc}

## MVP - Minimum Viable Product
Każdy projekt składa się z szeregu wymagań które trzeba na koniec spełnić. Żeby nie czekać aż wszystkie funkcjonalności będą zaimplementowane, 
zanim będzie można  korzystać z efektu końcowego wprowadzono koncepcję [MVP](https://en.wikipedia.org/wiki/Minimum_viable_product) czyli minimalnej 
wersji projektu która jest w najmniejszym stopniu używalna dla końcowego użytkownika.
 
 <div class="alert">
  <span class="closebtn" onclick="this.parentElement.style.display='none';">&times;</span>
 <b>UWAGA</b> Stworzenie wersji MVP projektu jest <b>absolutnie najważniejszą częścią Waszego zadania</b>. Macie ustalić minimalną wersję Waszego projektu na początku i ta minimalna wersja musi powstać.
</div> 
 

# Lewitacja akustyczna
![lewitacja akustyczna](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9d/Acoustic_Levitation.ogv/1200px--Acoustic_Levitation.ogv.jpg)
Prezentacja fenomenu lewitacji akustycznej, stojące fale dźwiękowe tworzą "poduszki" z wyższym ciśnieniem, co powoduje że leciutki przedmiot może zawisnąć w powietrzu.

Pytania na które będziecie musieli odpowiedzieć:
*  Jak się generuje fale sinusa za pomocą mikrokontrolera?
*  Jak wytworzyć falę stojącą?
*  Czy da się sterować tą falą? (Zmieniać częstotliwość? Zmieniać położenia strzałek i węzłow?
*  Jakie źródło zasilania będzie potrzebne?
*  Jakie komponenty będziecie potrzebować?
*  Na jakie części można podzielić ten projekt?
*  Jaki mikrokontroler użyć?
     *  Na co należy zwrócić uwagę przy wyborze?

# Dron - autonomiczny samolot
![dron](https://i.pinimg.com/originals/8c/b7/62/8cb762f52f6815b53cb3820d19ce20c5.jpg)
Celem projektu jest stwożenie pewnego rodzaju *autopilota* który pozwoliłby na utrzymywanie kursu po utracie kontaktu z kontrolerem. Jest wiele sposobów określania kierunku (GPS, Żyroskop, kompas), chodzi o to żeby wykorzystać je do stworzenia ukladu który pozwoli na sterowanie samolotem.

Pytania:
*  Co sprawia że samolot lata?
     *  To może trywialne, ale jakie podstawowe warunki muszą być spełnione żeby samolot utrzymywał się w powietrzu?
     *  Skąd biorą się opory ruchu?
     *  Co nadaje mu sterowność? Ile jest stopni swobody (parametrów które można zmieniać żeby wpłynąć na trajektorię lotu)?
*  Jakie jest źródło zasilania?
*  Ile energii potrzeba dla takiego układu sterowania?
*  Jaki mikrokontroler użyć?
     *  Na co należy zwrócić uwagę przy wyborze?


#  E-Karmnik dla ptaków
![bird buddy](https://mobirank.pl/wp-content/uploads/2021/07/birdbuddy-inteligentny-karmnik-dla-ptakow.jpg)
Karmnik dla ptaków który pozwala na obserwowanie ich z bliska i oglądanie ich przez kamerkę internetową. Tak jak [tutaj](https://www.youtube.com/watch?v=VPCGr5xcVtY). Potem można ustawić w szkole ekran z live-feedem z kamery, tak żeby na przerwie można było na korytarzu zobaczyć co się dzieje na zewnątrz przy karmniku.

Pytania:
*  Jak przesyła się obraz na odległość?
*  Jakie są zalety robienia tego przewodowo/bezprzewodowo?
     *  Jaki jest zasięg i zalety i wady popularnych protokołów przesyłania danych (wifi/bluetooth/ethernet)
*  Co jest najważniejsze w karmniku? Co sprawia ze karmnik jest dobry albo zły?
     *  Czy są jakieś dodatkowe cechy których ten karmnik z linku nie posiada?
*  Jakie jest źródło zasilania?
*  Jaki mikrokontroler użyć?
     *  Na co należy zwrócić uwagę przy wyborze?


# Monitoring do warsztatu
![monitoring](https://img.directindustry.com/images_di/photo-m2/7945-16452376.jpg)
System monitoringu do warsztatu który pozwoli na określenie kto i w jakich godzinach z niego korzysta i czy ktoś nieproszony korzysta z niego poza godzinami? Można do tego dodać wykrywanie ruchu lub uruchamianie kamery przy otwarciu drzwi. Tak samo, można go rozszerzyć o system uwieżytelniania żeby tylko osoby do tego uprawnione mogły swobodnie włączać/wyłączać ten system.  Do tego jeszcze powiadamianie o niespodziewanych zdarzeniach (np. mail do Janka że ktoś właśnie kradnie kabel USB-C!)

Pytania:
*  Jakie są najważniejsze elementy systemu zabezpieczeń? 
     *  Na czym można oprzeć uwierzytelnianie użytkowników?
     *  Co zrobić żeby szansa na oszóstwo była jak najmniejsza?
*  Co taki system powinien zgłaszać? (I co jest w stanie zgłaszać? Czy aby napewno wynoszenie kabla?)
*  Po co ktoś zazwyczaj zagląda do starych nagrań? 
*  W jaki sposób i gdzie należy je przechowywać?


# Trackowanie tagów RFID
![rfid tag](https://ae01.alicdn.com/kf/Hcee3370309b5497397e3111aedc41384Y/anti-theft-uhf-rfid-tag-EAS-58khz-UHF-840-960mhz-waterproof-epc-gen2-tag-EAS-for.jpg_220x220xz.jpg_.webp)
Sklepy z ubraniami już rozwiąząły ten problem. Może można przyczepić do kabli takie tagi RFID jak w sklepach z odzieżą i postawić przy wyjściu bramkę która będzie piszczeć kiedy ktoś wynosi to czego nie powinien?

*  Jak działają tagi RFID?
*  Jakie są słabe i mocne strony tego systemu i czy faktycznie rozwiązuje ten problem?
*  Czy każda rzecz może mieć swoje id? Czy jesteśmy w stanie wykryć tylko że ktoś wyniósł "coś"?

#  Naprowadzany nerf-gun
![portal sentry turret](https://static.turbosquid.com/Preview/001221/567/X9/sentry-turret-portal-model_D.jpg)
Coś takiego jak robicie na zajęciach, ale jako projekt semestralny można się nie ograniczać i zrobić działo które nie tylko używa jakichś skuteczniejszych naboi, np z [nerf-gun'a](https://m.media-amazon.com/images/I/81x6sRmCF8L._AC_SL1500_.jpg), ale też lepiej celuje i super wygląda np. jak to z portala.

*  Jak celować i sterować działem w dwóch wymiarach?
     *  Jakich silników użyć?
*  Jakie są sposoby wykrywania poruszających się obiektów?
*  Jaki mikrokontroler użyć?
     *  Na co należy zwrócić uwagę przy wyborze?


#  automatyczne podlewanie
![podlewanie](https://ae01.alicdn.com/kf/H0d84fc5b1a9c4bda9b5b4fd1d461ac48e/DIY-automatyczny-System-nawadniania-z-mikrootworami-nawadnianie-ogrodu-zestawy-do-samodzielnego-podlewania-z-regulowanym-kroplomierzem.jpg_Q90.jpg_.webp)
Wcale nie proste zadanie stworzenia systemu automatycznego podlewania. Taki system powinien pozwalać na ustawienie ilości zużywanej wody i czas kiedy takie podlewanie powinno zostać wykonane. Do tego, warto żeby sprawdzał wilgotność gleby żeby określić czy potrzeba podlewania, raportował błędy jeśli wilgotność nie rośnie po podlewaniu i nie podlewał kiedy pada.

*  Jak sterować zaworami?
*  Jak mieżyć zużycie wody?
*  Jak mierzyć wilgotność?
*  Jaki interfejs może mieć taki system podlewania?

#  autonomiczna kosiarka
![husqvarna automover](https://grupa-narzedziowa.pl/16246-large_default/zabawka-robot-kosiarka-automatyczna-husqvarna-automower-597809601.jpg)
Czy odkurzacz czy kosiarka, chodzi o coś co jeździ po zadanym terenie i wykonuje pewną pracę. Trzeba zrobić autonomiczny pojazd, który sam się włącza w ustalonych porach, sam się ładuje i porusza się po ograniczonym w jakiś sposób terenie.

*  W jaki sposób można rozpoznawać granice obszaru roboczego?
*  Jaki interfejs może mieć taka kosiarka?
*  Co jest trudnego w skutecznym koszeniu trawy?
*  Kto zbierze skoszoną trawę/wymieni pojemnik?
*  Czy warto w ogóle zbierać tą skoszoną trawę?
*  Jakie jest źródło zasilania?
*  Jaki mikrokontroler użyć?
     *  Na co należy zwrócić uwagę przy wyborze?

#  wiecOS
![urządzenie do głosowanie](https://wizualizer.pl/pic/Bezprzewodowy-system-do-glosowania-Taiden-HCS-4395N-bp22777.jpg)
Rozbudowa systemu głosowania podczas wieców albo o aplikację mobilną albo użądzenia do głosowania albo coś jeszcze.

*  Jakie są najważniejsze warunki które powinien spełniać system głosowania?
     *  Jakie są niebezpieczeństwa?
     *  Jak można go oszukać?
     *  Jakie informacje powinien dostarczać użytkownikom?
*  Jakie ograniczenia/wymagania dodatkowe są nałożone na projekt z tego powodu że ma być do użytku przez wiele osób?
*  W jaki sposób uwierzytelniać użytkowników?
*  W przypadku urządzeń do głosowania, jakie protokoły komunikacji są najlepsze dla takiego zastosowania? (wifi/bluetooth/radio/kabel)

# Apka
Może jest jakaś inna aplikacja na którą macie pomysł którą chcecie zrobić w ramach tego projektu?


--------------------------------------------------------------------------------------------

<br>

# Pytania pomocnicze:
Wiele z tych projektów natrafia na podobne problemy. To są pytania wspólne dla większości z nich które mogą Wam pomóc w pracy nad nimi.

*  Jaki problem ten projekt rozwiązuje?
*  Czy podobne rozwiązania już istnieją?
     *  Jeśli tak, to jakie?
     *  W jaki sposób takie rzeczy są najczęściej robione?
     *  Co można zrobić lepiej?
     *  Jeśli nie, to jak myślicie, dlaczego?
*  Jakich technologi zamierzasz użyć?
    *  mikrokontrolery? (arduino? ESP32? STM32? rasPi?)
    *  języki programowania? (C, C++, python?)
    *  framework'i (django, flutter?)
*  Jaka jest najtrudniejsza część tego projektu?


# Mam swój pomysł na projekt!
Super. Opisz w mailu swój pomysł. Postaraj się w nim zawrzeć plan jak widziałbyś wykonanie tego projektu i odpowiedzi na następujące pytania (tak wiem że duża część z nich to to samo co "pytania pomocnicze"):


*  **Jaki problem rozwiązujesz?**
*  **Jakie są główne funkcjonalności które musisz dostarczyć?**
*  Jakich technologi zamierzasz użyć?
    *  mikrokontrolery? (arduino? ESP32? STM32? rasPi?)
    *  języki programowania? (C, C++, python?)
    *  framework'i (django, flutter?)
*  Co jest potrzebne do zrealizowania tego projektu? (trzeba coś dokupić? Głośniki? Silniki krokowe? Kamerę?)
*  Ile z tego da się zrobić w jeden semestr? (jak wyglądałaby wersja MVP?)
*  Jaka jest najtrudniejsza część tego projektu?
*  Czy jest coś czego na razie nie umiesz zrobić? Problem na który nie masz rozwiązania? (To jest ok.)


## Przykład:
Mój pomysł to autonomiczna kosiarka. Koszenie trawy to proste i mechaniczne zadanie, które może zostać wykonane przez robota. Chciałbym zrobić moją własną wersję takiej kosiarki. 

Wyobrażam to sobie tak:
Trzeba zrobić pojazd który będzie jeździł po terenie ograniczonym przez kabel wkopany w ziemie. Kosiarka będzie bezprzewodowo wykrywać że jest nad kablem i wtedy zawracać. Nie będzie zbierać skoszonej trawy, tylko zostawiać to co zkosi. Po wyczerpaniu baterii będzie podjeżdżać do stacji ładowania i się ładować. Nie wiem jeszcze jak rozwiązać problem z gałęziami które mogą się pojawić na drodze. Może kosiarka powinna je wykrywać i omijać albo ignorować?

Lista funkcjonalności:

*  jeżdżący pojazd
*  wykrywanie granic obszaru koszenia
*  narzędzie do koszenia (wirujące noże, czy coś)
*  stacja dokująca która sama się podłącza i ładuje baterie
*  znajdowanie stacji dokującej
*  zapewnienie 100% pokrycia obszaru koszenia (kosiarka musi napewno skosić 100% trawnika)
*  wykrywanie gałęzi?
*  Ekran i guziki potrzebne do konfiguracji kosiarki.

Wersja MVP:

jeżdżący pojazd który potrafi skręcać i cofać i jeździć po zadanej trasie wysyłanej do kosiarki przez wifi. np. jeździć po kwadracie. (Ekran i GUI do obsługi kosiarki nie znajduje się w wersji MVP)

Użyłbym do tego:

Raspberry pi w kosiarce i silników bezszczotkowych do jeżdżenia. Każde koło będzie na oddzielnym silniku żeby kosiarka mogła zawracać w miejscu.
Kod będzie w pythonie.

------------------------------------

Pomysły wysyłajcie na:
kajetan.boroszko@...
wiecie jaka jest domena szkolna
