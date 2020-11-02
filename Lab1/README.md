Zaliczenie:
zadania 1+2 lub 1+3 - dostateczny (sprawdzane w trakcie zajęć)
zadania 1+2+3 - dobry (sprawdzane w trakcie zajęć)
zadania 1+2+3+4 - bardzo dobry (istnieje możliwość dokończenia po zajęciach; do końca dnia)
(2p.) Wykorzystaj 'date' do wyswietlania różnych komunikatów powitalnych w zależności czy aktualnie jest dzień roboczy czy świąteczny (dla uproszczenia: dzień tygodnia czy weekend).
Uwaga: Porównywanie napisów wyświetlanych przez program 'date' (i inne programy) jest zależne od języka i lokalizacji. Sprawdź możliwość ustawienia zmiennych lokalizacji LC_* (np. LC_ALL=C) i ich wpływ na postać komunikatu. Która/które z nich sterują postacią wyświetlanej daty? Ustawiając tę zmienną w skrypcie na wartość C (lub POSIX), wymuszamy lokalizację kanoniczną, co ułatwia sprawdzanie wartśoci daty, i uniezależnia działanie skryptu od lokalizacji (będzie on poprawnie sprawdzał warunek również np. w Japonii).

(3p.) W pliku tekstowym adresy.txt istnieje wiele adresów email firm świadczących pewne usługi (np. instalacji okien PCV). W pliku tresc.txt wpisana została treść maila zawierającego zapytanie ofertowe do takiej firmy. W plikach spec*.pdf mamy szereg dokumentów zawierających dokładną specyfikację, rysunki, itp. dotyczące zamawianej usługi. Chcemy automatycznie rozesłać kompletne zapytanie ofertowe (treść+załączniki) do wszystkich firm.
Znajdź program klienta poczty elektronicznej pozwalającego wysyłać maile z wiersza poleceń w trybie nieinterakcyjnym (np. mail/mailx, pine/alpine, mutt, itp). Przeczytaj jego opis i opracuj wyrażenie shella pozwalającego automatycznie rozesłać zapytanie ofertowe do wszystkich adresów w pliku.

Ważne: emaile muszą być rozesłane indywidualnie do wszystkich adresatów. Niedopuszczalne jest wysłanie jednego emaila do listy zawierającej wszystkie adresy.

Wskazówka: istotą tego zadania nie jest wysyłanie emaili, ale czytanie w pętli kolejnych wierszy z pliku. Najprościej to wykonać ustawiając dla polecenia pętli while skierowanie wejścia stdin z pliku, dzięki czemu w kolejnych przebiegach pętli czytanie z pliku/stdin będzie kontynuowane.

(3p.) Ćwiczenia z programem find: napisz skrypt znajdujący programem find wszystkie pliki o zadanym rozszerzeniu lub masce, które były modyfikowane w ciągu ostatnich N dni i tworzący z nich archiwum tar o zadanej nazwie. Mamy tu trzy parametry: maskę nazwy pliku, liczbę N i nazwę archiwum. Parametry są zadawane przez argumenty, to znaczy skrypt zawsze będzie wywołany z trzema parametrami.
(5p.) Zmodyfikuj skrypt napisany w poprzednim punkcie tak, aby miał rozbudowany i wygodny interfejs użytkownika. Po pierwsze, pozycyjne parametry wywołania zamień na opcjonalne z jednoliterowymi słowami kluczowymi (poprzedzonymi znakiem minus), według wzoru:
  find_and_tar.sh -n 5 -m '*.c' -a progarch.tar
Każdy z parametrów -n, -m, i -a może wystąpić lub nie, i mogą one być zadane w dowolnej kolejności (ale w parach ze słowem kluczowym). Jest to ogólnie przyjęta konwencja pisania skryptów i programów w systemie Unix.
Następnie dodaj mechanizm pobierania wartości parametru w przypadku, gdyby nie wystąpił jako argument wywołania. Jeśli dany parametr nie wystąpił, a istnieje zmienna środowiskowa zadająca wartość danego parametru (wymyśl dobre nazwy dla tych zmiennych), to będzie użyta wartość tej zmiennej. Jeśli nie ma ani argumentu wywołania ani zmiennej środowiskowej, to skrypt powinien zapytać się użytkownika o wartość danego parametru, i wykorzystać tę wartość. Do zadania pytania użytkownikowi wykorzystaj polecenie echo, a do odczytania odpowiedzi użytkownika polecenia read lub programu line.

Wskazówka: można usprawnić czytanie i analizę (parsing) wektora argumentów z parametrami opcjonalnymi za pomocą programu getopt. Jego użycie jest proste, a daje przenośność i odporność na błędy. Dobry jest przykład w dokumentacji man getopt (na niektórych wersjach Linuksa man nie ma tego przykładu, patrz man getopt na systemie Solaris).
