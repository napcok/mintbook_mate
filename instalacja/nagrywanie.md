# Nagrywanie ISO na DVD
Teraz, kiedy sprawdziłeś plik ISO z jego sygnaturą MD5, jesteś gotowy na nagranie go na płytę DVD.

Weź czystą płytę DVD-R (DVD-RW powinna też być dobra, ale ten typ płyty jest znany jako sprawiający problemy) i Twój ulubiony mazak (marker) i nazwij płytę. Może to zabrzmieć trywialnie, ale powinieneś upewnić się, że to zrobiłeś. Łatwo skończyć z dwudziestoma nienazwanymi i niezidentyfikowanymi płytami na swoim biurku. :)

Włóż czystą płytę DVD-R do napędu i przygotuj się do wypalenia ISO.

Jeśli masz uruchomiony Linux z MATE, prawym klawiszem myszy kliknij na pliku ISO i wybierz **Write to Disc**.

Jeśli masz uruchomiony Linux z KDE, uruchom K3B i z menu wybierz **Tools** → **Write ISO Image**

Jeśli masz uruchomiony Linux i chciałbyś użyć terminala, w katalogu zawierającym plik ISO wykonaj:
```
cdrecord -v -dao dev=1,0,0 linuxmint.iso
```
Zamień cyfry po dev= wpisując numer swojego urządzenia.
Uruchom
```
cdrecord -scanbus
```
aby się przekonać. Być może potrzebujesz uprawnień root'a aby uruchomić to polecenie.

Jeśli używasz Windows, możesz wykorzystać program InfraRecorder:
http://infrarecorder.sourceforge.net/?page_id=5

**Uwaga:** *Upewnij się, że wypalasz obraz ISO na dysku, a nie zapisujesz obraz na DVD jako plik. Bardzo częstym błędem, zwłaszcza dla ludzi używających Nero, jest nagranie pliku ISO na płycie jako plik danych.
Plik ISO jest obrazem dysku i musi być nagrany nie jako plik na dysku tylko jako obraz, który zostanie rozkompresowany i cała jego zawartość trafi na płytę. Po wypaleniu płyty nie powinieneś widzieć na płycie pliku ISO, ale raczej foldery takie jak **casper** lub **isolinux**. Większość aplikacji do nagrywania ma taką opcję.*
