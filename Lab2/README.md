Zaliczenie:
zadania $(1 \vee 2)&(3 \vee 4)&(5 \vee 6)&(7 \vee 8)$ - obowiązkowe na zajęciach;
zadania 1--7 - obowiązkowe, z tym, że to co nie zostało wykonane w trakcie zajęć może być wykonane w domu (mniej punktów);
zadania 8 - opcjonalne, do wykonania w domu (na lepszą ocenę).

(2p.) Zapoznaj się z programem ps (man ps). Wypróbuj dwa formaty wyświetlania rozszerzonych informacji: -f i -l. Przeczytaj podręcznik polecenia ps aby zrozumieć wyświetlane parametry. Naucz się wybierać zestaw procesów do wyświetlania argumentami opcjonalnymi -u, -t, i -p.
Ile Twoich procesów istniało w systemie w chwili przykładowego wywołania ps?

Ile procesów sshd istniało w systemie (serwerze) w chwili wykonywania ćwiczenia (sprawdź polecenie pgrep)?

(2p.) W jednym okienku terminala uruchom hierarchię co najmniej trzech procesów, tzn. procesy A, który uruchomi proces potomny B, który uruchomi proces potomny C. Mogą to być kolejno uruchamiane interpretery poleceń, albo uruchamiające się kolejno skrypty lub programy. W innym oknie terminala sprawdź programem ps zależności potomków i rodziców w utworzonej hierarchii.
Poleceniem kill zabij proces w środku tej hierarchii (B). Sprawdź poleceniem ps co pozostało z pierwotnych procesów, i czy osierocony proces zostanie poprawnie adoptowany przez proces init.

W sprawozdaniu z wykonania zadania opisz tylko otrzymany wynik, nie wklejaj napisanych skryptów.

(2p.) Uruchom potok co najmniej trzech poleceń działających przez jakiś zauważalny czas. Mogą to być odpowiednio dobrane polecenia systemowe, lub samodzielnie napisane skrypty. Sprawdź poleceniem ps i odpowiedz jakie zachodzi pokrewieństwo między tymi procesami (jeśli w ogóle zachodzi).
Wskazówka: ponieważ potok służy do przesyłania danych od procesu do procesu, i synchronizuje pracę wszystkich procesów odpowiednio do pojawiających się danych, dobrą metodą generowania demonstracyjnego potoku jest umieszczenie na jego początku procesu, wysyłającego na swoje wyjście stały strumień danych, np. piszącego w pętli co sekundę jakiś krótki komunikat. Kolejne elementy potoku mogą być realizowane przez program cat.

(2p.) Poleceniem mknod utwórz potok nazwany (FIFO). W co najmniej czterech okienkach wywołaj równoczesne pisanie do, i równoczesne czytanie z tego potoku przez wiele procesów (polecenie cat).
Sprawdź (i podaj w raporcie) jak system rozdziela dane z pliku procesom o współdzielonym dostępie do tego potoku?

Zabijając na przemian procesy piszące/czytające, zaobserwuj, kiedy proces cat czytający z potoku czeka na więcej danych, a kiedy kończy pracę. Analogicznie, kiedy proces piszący czeka w gotowości do dalszego pisania na potoku, a kiedy samoistnie kończy pracę. Podsumuj w raporcie.

(2p.) Napisz skrypt, który w pętli będzie coś robił (np. co sekundę wypisywał bieżącą godzinę). Sprawdź wysyłanie do procesu różnych sygnałów poleceniem kill (SIGINT, SIGQUIT, ale także SIGFPE, SIGILL). Następnie rozbuduj skrypt o przechwytywanie tych sygnałów (trap) i sprawdź, że to działa, to znaczy, że tak napisanego procesu nie da się zabić tymi sygnałami. Sprawdź możliwość uśmiercenia sygnałem SIGKILL procesu, który przechwytuje wszystkie 15 podstawowych sygnałów.
Uwaga: trap jest wbudowanym poleceniem shella, i jego wywołanie trochę się różni pod różnymi shellami. Najłatwiej jest wykonać to ćwiczenie przy użyciu Bourne shella (/bin/sh), ponieważ bash wykonuje różne potajemne zabiegi z obsługą sygnałów. Jednak polecenie trap w Bourne shellu jest prymitywne - czytaj man sh.

(2p.) Sprawdź możliwość zawieszania procesu sygnałem SIGSTOP i wznawiania sygnałem SIGCONT. Sprawdź, że sygnał SIGSTOP daje taki sam efekt jak naciśnięcie klawisza Ctrl+Z na terminalu. Sprawdź, że sygnał SIGCONT daje taki sam efekt jak wykonanie polecenia fg lub bg (którego bardziej?).
(2p.) Sprawdź wartości priorytetów procesów i ich liczby nice, a następnie przećwicz obniżanie priorytetu pracującego w tle procesu (nice/renice). Czy potrafisz zademonstrować działanie obniżonego liczbą nice priorytetu?
Podsumuj wynik w raporcie i podaj polecenie obniżania priorytetu procesu.

(2p.) Zapoznaj się z poleceniem ulimit. Ustaw liczbę procesów na małą wartość i sprawdź, czy działanie jest respektowane. Następnie napisz skrypt, który w nieskończonej pętli uruchamia kolejne kopie samego siebie w tle. \textbf{Uruchom skrypt koniecznie w tej powłoce, w której ograniczyłeś/ograniczyłaś maksymalną liczbę procesów!} Następnie spróbuj opanować sytuację, czyli pozabijać wszystkie utworzone procesy i powrócić do normalnej pracy.
