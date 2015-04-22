# Sprawdź MD5
Przeczytałeś ReleaseNotes i pewnie nie możesz się doczekać aby wypróbować nowe funkcje lub pobawić się Linux Mint. Jeśli pobieranie pliku ISO się zakończyło, jesteś gotowy do wypalenia płyty DVD i uruchomienia komputera... ale hej! Zaczekaj chwilkę!

Jeśli ten DVD jest uszkodzony, doświadczysz dziwnych błędów i będziesz miał problemy ze znalezieniem pomocy. Dwie najczęstsze  przyczyny wadliwego DVD to:
* Błędy w pliku ISO spowodowane problemami podczas pobierania
* Błędy podczas procesu nagrywania

Sygnatura MD5, która jest obecna na stronie pobierania, pozwala szybko upewnić się, że Twoje ISO jest dokładnie takie jakie powinno być. Zatem aby zaoszczędzić sobie potencjalnych problemów jeszcze przed wypaleniem krążka DVD, sprawdźmy plik ISO, który właśnie pobrałeś.

Jeśli uruchomisz jakąkolwiek dystrybucję Linuxa, zapewne znajdziesz tam zainstalowany program o nazwie md5sum. Otwórz terminal i przejdź  do katalogu, gdzie zapisałeś plik ISO (np. Jeśli plik **linuxmint.iso** zapisałeś w katalogu Pobrane), otwórz terminal i wpisz:
```
cd ~/Pobrane
md5sum linuxmint.iso
```
Komenda powinna zwrócić ciąg cyfr i liter, który składa się na sumę kontrolną MD5 lub sygnaturę (podpis) Twojego ISO. Zgodnie z projektem, każda nawet mała zmiana w pliku ISO, spowoduje, że sygnatura będzie znacząco się różnić. To pozwala nam sprawdzić czy plik jest dokładnie taki jaki powinien być.

Porównaj zatem sygnatury, jeśli są takie same, to wiesz, że Twój plik jest dokładnie taki sam jak oryginał i można teraz przygotować się do nagrania go na DVD.

W przypadku Windows, istnieje ryzyko, że nie będziesz miał zainstalowanej aplikacji md5sum. Możesz ją pobrać stąd: http://www.etree.org/md5com.html
Umieść plik ISO i md5sum.exe w tym samym miejscu (powiedzmy na C:\) i uruchom **cmd.exe**. W linii komend wpisz polecenia:
```
C:
cd \
md5sum linuxmint.iso
```
Potem porównaj sygnaturę z tą obecną na stronie.
