# Zarządzanie pakietami w Linux Mint
Jeśli zainstalowałeś Linuxa po raz pierwszy, być może nie jesteś zaznajomiony z koncepcją organizacji oprogramowania w tzw. pakiety. Wkrótce zapoznasz się z menedżerem pakietów i docenisz zalety jakie oferuje w zakresie  bezpieczeństwa, kontroli i łatwości użytkowania.

Staraliśmy się, aby większość sprzętu została wykryta a sterowniki zostały zainstalowane automatycznie, tak aby komputer działał sprawnie od razu po instalacji systemu. Postaraliśmy się też, abyś mógł robić różne rzeczy bez szukania oprogramowania  w Internecie. Zauważ, że po instalacji komputer posiada pełny pakiet biurowy, profesjonalnej jakości rozwiązanie do edycji obrazów, komunikator internetowy (IM), klienta IRC, nagrywarkę dysków i kilka odtwarzaczy multimedialnych (jak i wiele innych podstawowych programów). Spokojnie, wszystko w porządku! To nie kradzione.
To jest wolne oprogramowanie. Naprawdę świetną rzeczą jest fakt, że nigdy nie trzeba szukać daleko dodatkowego oprogramowania aby  dodać więcej funkcji do systemu.

Ten rozdział ma na celu wyjaśnić, jak to działa i jakie osiągniesz z tego korzyści. To trochę potrwa,ale mamy nadzieję, że zrozumiesz filozofię zarządzania pakietami. Jeśli się śpieszysz, możesz przejść do następnego rozdziału, który powie Ci jak właściwie korzystać z systemu pakietów.

Jest wiele problemów z przeglądaniem oprogramowania na stronach WWW i instalowaniem ich:
* Jest trudnym, o ile nie niemożliwym, przekonanie się, że program został przetestowany do pracy z Twoim systemem operacyjnym.
* Jest trudnym, o ile nie niemożliwym, przekonanie się czy program potrafi współdziałać z innymi zainstalowanymi programami w systemie.
* Jest trudnym, o ile nie niemożliwym, przekonanie się, że można zaufać oprogramowaniu od nieznanego dewelopera, że program nie spowoduje żadnej szkody dla systemu. Nawet jeśli znasz ten program i jego twórcę, nie możesz być pewny, że pobierasz prawidłowy plik, który nie został podmieniony przez osoby trzecie lub przez jakieś złośliwe oprogramowanie.

Co więcej, problem z pobieraniem i instalacją wielu różnych programów, od wielu różnych deweloperów, jest taki, że nie ma infrastruktury zarządczej. Zanim powiesz *Nic wielkiego*, zastanów się, jak masz zamiar sprawić, aby  te wszystkie różne części oprogramowania były  na bieżąco aktualizowane. Jeśli znudzi Ci się jakiś program i chcesz go usunąć, jak sądzisz, jak to osiągnąć? Program, o którym mowa, nie musi posiadać opcji usuwania, a nawet gdyby tak było, nie zawsze uda się usunąć oprogramowanie czysto i całkowicie.
Kiedy uruchamiasz instalator, to w pewnym sensie powierzasz kontrolę instalatorowi napisanemu przez kogoś kompletnie obcego.

Ostatecznie, program w ten sposób dostarczany, jest często, ze względu na konieczność, **statyczny**(w informatyce rodzaj biblioteki funkcji i podprogramów, która łączona jest z programem w czasie budowania). Oznacza to, że nie tylko trzeba pobrać program, ale też wszystkie biblioteki, niezbędne do jego uruchomienia. Producent oprogramowania innej firmy nie może wiedzieć, jakie biblioteki masz już w systemie, więc aby zagwarantować działanie aplikacji, biblioteki są dołączane razem z programem. Oznacza to większy rozmiar aplikacji do pobrania, a w przypadku pojawienia się aktualizacji pojedynczej biblioteki, należy zrobić aktualizację wszystkich tych programów. Podsumowując - dystrybucja statycznych aplikacji powoduje niepotrzebnie dużo pracy.

Zarządzanie pakietami w Linux Mint  i systemach operacyjnych GNU/Linux w ogóle, stabilizowało się jakiś czas i stało się zalecaną metodą zarządzania aplikacjami, ponieważ pozwala uniknąć wszystkich tych problemów.

Jak się domyślasz, system jest na początku pisany przez dewelopera i koniec tego łańcucha produkcji zwany jest jako **upstream**. Będąc użytkownikiem dystrybucji Linuksa jesteś określany jako najdalszy punkt czyli **downstream**. Kiedy developer  jest zadowolony z programu lub jego aktualizacji, wówczas wypuszcza kod źródłowy do niego. Będzie również informować w dokumentacji, które biblioteki danych lub innych programów były wykorzystywane w głównej mierze podczas pisania programu. Trwa to przez jakiś czas i są to ustandaryzowane i określone metody. Należy zauważyć, że z nielicznymi wyjątkami (zazwyczaj albo producenci sprzętu, którzy uwalniają sterowniki dla Linuksa, jak nVidia lub ATI, czy też niektóre duże firmy, takie jak Adobe, którym można zaufać) udostępniany jest rzeczywisty kod źródłowy programu, który jest listą instrukcji zawartą w programie, zrozumiałą dla przeciętnego użytkownika. Ma to wiele implikacji, ale najważniejszą dla tej dyskusji jest to, że developerzy są gotowi na to, aby ich oprogramowanie było recenzowane przez każdego użytkownika z dostępem do internetu. Jest niewiarygodnie trudne, aby przemycić program szpiegujący do systemu, kiedy udostępniasz wgląd do tego co napisałeś.

Oprogramowanie trafia do opiekunów pakietów, którzy są zarówno wolontariuszami jak i pracownikami najemnymi pracującymi dla dystrybucji Linuxa. Ich obowiązkiem jest  kompilować kod, testować, rozwiązywać problemy i wreszcie zbudować pakiet. Pakiet ten zawiera pliki wykonawcze, ich konfigurację oraz dokumentację. Należy zauważyć, że nie będzie zwykle zawierać bibliotek statycznych, ponieważ nie ma takiej potrzeby. Biblioteki są dostarczane przez inne pakiety i noszą nazwę bibliotek współdzielonych. Menedżer pakietów będzie wiedział, że ten pojedynczy pakiet wymaga innego pakietu, który powinien być zainstalowany jako pierwszy, bo jak pamiętamy, biblioteki oraz pakiety powiązane potrzebne programowi do pracy zostały wcześniej zgłoszone. Gotowy pakiet wysyłany jest do specjalnego serwera plików, zwanego **repozytorium oprogramowania**.

To właśnie z tego miejsca będziesz w stanie pobrać i zainstalować aplikacje. Będziesz wiedział, że ta lokalizacja jest prawidłowa, ponieważ będzie podpisana prawidłowym certyfikatem sprawdzonym przez menedżera pakietów. Będzie również wiedzieć, że pakiet jest prawidłowy, gdyż będzie podpisany kluczem PGP opiekuna. Menedżer sprawdzi też sumy kontrolne MD5 dla każdego pakietu, aby się upewnić, że nic nie poszło źle podczas pobierania (tak jak to robiłeś wcześniej po pobraniu ISO liveDVD). Zauważ, że wszystko się robi za Ciebie. Menedżer pakietów pobierze wybrane pakiety, będzie śledził instrukcję pakietu podczas instalacji i spełni wszystkie zależności w odpowiedniej kolejności. Nie ma miejsca na błąd człowieka, jeśli pakiet pracował na komputerze opiekuna, to powinien pracować także u Ciebie, ponieważ zostanie wykonana ta sama procedura.

Kiedy przyjdzie czas, aby sprawdzić dostępność aktualizacji oprogramowania, Menedżer Pakietów automatycznie porówna wersję oprogramowania, którą posiadasz z tą która jest dostępna w repozytorium i wykona wszystkie potrzebne prace w sposób sprawny i bezpieczny.

Brzmi nieźle? Będzie jeszcze lepiej!

Czasami coś może pójść źle w tym procesie z powodu ludzkich błędów. Możliwe, że przez przypadek zainstalujesz sterowniki dla nie tego sprzętu i to spowoduje problemy.
Może pojawić się błąd lub jakaś funkcja zostanie usunięta przez dewelopera z jakiegoś powodu. Problemy te, paradoksalnie, pokazują siłę i bezpieczeństwo zarządzania pakietami. Menedżer Pakietów zapisuje wszystko co kiedykolwiek robi i jest w  stanie odwrócić instalację, czysto i całkowicie. Upewni się, że usunięcie któregoś pakietu nie uszkodzi innych, a nawet pozwoli robić takie rzeczy jak nie-automatyczne aktualizacje pojedynczych pakietów lub powrót do wcześniejszych wersji. Cały proces podlega wzajemnej weryfikacji.

Jesteś częścią dużej społeczności Linuxa, wszyscy korzystają z tych samych repozytoriów i jeśli coś jest nie tak, możesz być absolutnie pewny, że powstanie duże zamieszanie z tym związane i problem szybko zostanie rozwiązany.

Dystrybucja oprogramowania w świecie Linuxa mocno opiera się na zaufaniu, od chwili kiedy deweloper udostępnia swój kod dla wszystkich, aż do dyskusji na stronach internetowych danej dystrybucji. Możesz mieć pewność, nie tylko ze względu na wspomniane protokoły bezpieczeństwa, że jeśli coś pójdzie nie tak, wszyscy będą o tym mówić.

Spójrzmy zatem jeszcze raz na listę problemów i zobacz co udało nam się rozwiązać:

* *Jest trudnym, o ile nie niemożliwym, przekonanie się, że program został przetestowany do pracy z Twoim systemem operacyjnym.*

Oprogramowanie dostępne przez repozytorium zostało dokładnie sprawdzone przez opiekuna i zespół testowy, do pracy z Twoim systemem operacyjnym.

* *Jest trudnym, o ile nie niemożliwym, przekonanie się czy program potrafi współdziałać z innymi zainstalowanymi programami w systemie*

Podobnie, opiekunowie pakietów starają się aby pakiety nie konfliktowały z innymi pakietami oferowanymi w ich dystrybucji. Oczywiście nie mają zainstalowanego każdego pakietu na ich testowych maszynach (w rzeczywistości, opiekunowie, budują swoje pakiety na czystych instalacjach w celu upewnienia się, że bazowy zestaw pakietów jest standardowy), ale jeśli jakiś członek społeczności znajdzie jakiś problem, bez wątpienia powiadomi zespół a problem zostanie szybko rozwiązany. Jeśli nie jesteś beta testerem to mało prawdopodobne jest abyś napotkał taki konflikt.

* *Jest trudnym, o ile nie niemożliwym, przekonanie się, że można zaufać oprogramowaniu od nieznanego dewelopera, że program nie spowoduje żadnej szkody dla systemu.*

Jest mało prawdopodobne aby pojawił się pakiet, o którym opiekunowie wiedzą, że sprawi kłopoty na komputerze (w tym na ich własnych!). Tylko oprogramowanie, które jest znane i zaufane ma szanse trafić do repozytorium.

* *Nawet jeśli znasz ten program i jego twórcę, nie możesz być pewny, że pobierasz prawidłowy plik, który nie został podmieniony przez osoby trzecie lub przez jakieś złośliwe oprogramowanie.*

Oprócz zwykłych środków bezpieczeństwa wprowadzonych przez instytucje, które są właścicielami serwerów (zwykle prestiżowych instytucji naukowych lub badawczych lub dużych przedsiębiorstw), repozytoriów i samych pakietów, są zabezpieczone certyfikatami i kluczami GPG. Jeśli coś poszło nie tak, twój Menedżer Pakietów powie Ci o tym.
* *Trudno jest usunąć zainstalowane aplikacje (oraz wszystkie ślady)*

Ponieważ oprogramowanie do zarządzania prowadzi pełny rejestr wszystkich swoich działań, to może także odwrócić wszelkie kroki, które miały miejsce w przeszłości, przy jednoczesnym zapewnieniu, ze usunięcie pakietu nie będzie miało wpływu na inne.

* *Pakiety statyczne są duże i niezgrabne*

Menedżer pakietów pobierze statyczne biblioteki tylko wtedy gdy nie będzie istniała alternatywa w postaci bibliotek współdzielonych.

* *Nadal nie jestem przekonany*

Dobrze! Napisz do nas o tym na forum lub zapytaj innych o doświadczenia w tym temacie. Warto powtórzyć, że metoda pakietowania w dystrybucji w dużej mierze opiera się na zaufaniu, więc jeśli jest jakiś problem, chcemy o tym wiedzieć!

Ostatnie słowo. Być może słyszałeś pogłoski o tym, że Linux, nie jest jeszcze ukończony, że użytkownicy Linuxa to beta testerzy lub, że oprogramowanie na Linuxa jest niestabilne. Są to wszystko pół-prawdy. Linux nigdy nie będzie bardziej gotowy, podobnie jak to jest w innych systemach. Począwszy od jądra Linuxa, skończywszy na grafikach na ekranie, wszystkie elementy systemu, zawsze będą w trakcie rozwoju. To dlatego, że programiści ciężko pracują, aby utrzymać nas  na bieżąco z najnowszymi osiągnięciami w programowaniu i technologiami sprzętowymi. Nie oznacza to, że oprogramowanie jest złej jakości. System bazowy Linux Mint jest w ciągłym rozwoju od około 20 lat i jest bardzo dojrzały, stabilny i sprawdzony. Oczywiście, są niestabilne wersje programów, ale nie będziesz ich używał bo nie jesteś beta-testerem. Wiesz, że nie jesteś beta-testerem, ponieważ właśnie czytasz ten przewodnik. Oprogramowanie dostępne dla Ciebie w repozytoriach, zawsze będzie stabilne i dobrze przetestowane, chyba, ze zmienisz repozytoria na te używane przez testerów.

Tak więc, aby podsumować przykładem: po zainstalowaniu Opery, RealPlayer czy Google Earth, aplikacje te nie przychodzą od ich oryginalnych twórców. Oczywiście same aplikacje od nich pochodzą, ale tu zostały odpowiednio opakowane i przetestowane i w ten sposób udostępnione Tobie. Innymi słowy, nie trzeba przeszukiwać Internetu w poszukiwaniu oprogramowania, gdyż wszystko co potrzebne jest przygotowane i przetestowane dla Ciebie przez zespoły Linux Mint i Ubuntu.

Linux Mint aktualizuje się przez narzędzie zwane Menedżer Aktualizacji, który będzie aktualizował nie tylko podstawowy system operacyjny, ale również oprogramowanie.

To takie proste! Uff!

Niektóre z bardziej popularnych aplikacji, które domyślnie nie są instalowane w Linux Mint to:  Opera, Skype, Acrobat Reader, Google Earth oraz Real Player.

#### Menedżer oprogramowania
Najprostszym sposobem instalacji oprogramowania jest użycie **Menedżera Oprogramowania**. Wykorzystuje on technologię pakietów, które omówiliśmy wcześniej, lecz sprawia, że instalacja staje się łatwiejsza, gdyż pozwala instalować programy zamiast pakietów (choć należy pamiętać, że korzysta z systemu pakietów w tle, więc nadal ma same korzyści)

Otwórz zatem Menu i wybierz **Menedżer Oprogramowania**.

Menedżer Oprogramowania pozwoli przeglądać aplikacje stworzone dla Linux Mint. Możesz przeglądać jej poprzez kategorie, wyszukiwać po słowie lub sortować aplikacje wg ich popularności.

#### Menu

Jeśli wiesz czego szukasz, nie musisz niczego uruchamiać. Po prostu zacznij pisać nazwę aplikacji w menu i zainstaluj ją stąd.

Na przykład, aby zainstalować pakiet **gftp**:
* Wciśnij CTRL+Super_L aby otworzyć Menu
* Wpisz **gftp**
* Naciśnij strzałkę **W górę** aby podświetlić przycisk **Instaluj gftp**
* Naciśnij Enter

#### Synaptic & APT
eśli chcesz zainstalować więcej niż jedną aplikację lub chciałbyś zainstalować coś czego nie ma w Menedżerze Oprogramowania, Linux Mint oferuje także inne sposoby instalacji oprogramowania. Jednym z nich jest graficzne narzędzie o nazwie **Synaptic**, a drugi to narzędzie wiersza polecenia o nazwie **APT**.

Zobaczmy, jak możemy zainstalować  przeglądarkę internetową Opera  używając tych narzędzi.

Najpierw przyjrzyjmy się poleceniu **apt**.

Otwórz Menu i kliknij **Terminal**. Potem wpisz poniższe polecenie:

```
apt install opera
```
**Uwaga:** *Upewnij się, że synaptic nie jest uruchomiony przed użyciem APT. Synaptic używa **pod spodem** APT, więc nie mogą być uruchomione razem w tym samym czasie. To samo dotyczy Menedżera Oprogramowania.*

Jak widać, APT jest bardzo łatwy w użyciu, ale nie jest graficzny. Zaczynając pracę z Linuxem, będziesz bardziej preferował graficzne narzędzia, ale z czasem zaczniesz   korzystać z szybszych  i efektywniejszych, a jak widać to najszybszy sposób na instalację Opery, po prostu `apt install opera`. Nic prostszego!

Jest jeszcze jedna ważna różnica pomiędzy Menedżerem Oprogramowania a Synaptic/APT. W przypadku tych ostatnich masz w zasadzie do czynienia z pakietami. W naszym przykładzie aplikacja Opera była bardzo prosta, bo składała się tylko z jednego pakietu, którego nazwa była także **opera**.

Menedżer Oprogramowania jest inny, ponieważ pozwala instalować **Aplikacje** poprzez pozyskanie **pakietów** dla Ciebie, nie tylko z repozytoriów, Synaptic i APT mają dostęp do różnych miejsc w Internecie.

Tak więc, możesz użyć Menedżera Oprogramowania z dwóch powodów:
* Nie jesteś przyzwyczajony do używania Synaptic/APT
* Bo zainstalowałeś aplikacje do których dostępu inne narzędzia nie maja.
