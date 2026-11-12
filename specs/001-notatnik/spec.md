# 001 — Notatnik: zapis i przegląd notatek

## Cel

Jedna osoba zapisuje krótkie notatki i wraca do nich później. Program ma
być szybszy niż otwarcie pliku w edytorze, a plik z notatkami ma pozostać
czytelny także bez programu.

## Dla kogo

Dla jednej osoby, która pisze po polsku kilka krótkich notatek dziennie na
jednym komputerze. Nie dzieli notatek z innymi i nie potrzebuje do nich
dostępu z drugiego urządzenia.

## Co robi

1. Pokazuje pole tytułu, pole treści i przycisk zapisu.
2. Pokazuje listę zapisanych notatek, najnowszą na górze. Każda pozycja
   listy pokazuje tytuł oraz datę i godzinę zapisu.
3. Po zapisie umieszcza notatkę w pliku `notatki.md` w folderze programu
   (tam, gdzie leży plik programu), w formacie opisanym poniżej i zgodnym
   z decyzją 0001:
   - każda notatka zaczyna się linią `## RRRR-MM-DD GG:MM — Tytuł`;
     tytuł to tekst po pierwszym ` — ` i może zawierać kolejne myślniki;
   - pod nagłówkiem znajduje się treść, która może mieć wiele linii;
     linia zaczynająca się od `##` należy do treści tylko wtedy, gdy nie
     pasuje do pełnego wzorca nagłówka; linia pasująca do wzorca zawsze
     rozpoczyna nową notatkę;
   - wpisy oddziela jedna pusta linia; notatka z pustą treścią składa się
     tylko z nagłówka;
   - nowa notatka trafia na początek pliku, a pozostałe wpisy zachowują
     swoją kolejność;
   - przy dwóch notatkach zapisanych w tej samej minucie nowsza jest
     wyżej, bo trafia na początek pliku;
   - data i godzina to czas lokalny komputera;
   - plik jest zapisywany w UTF-8.
4. Po ponownym uruchomieniu pokazuje wszystkie notatki z pliku,
   w kolejności z pliku.
5. Kliknięcie notatki na liście pokazuje jej pełną treść i datę zapisu.
6. Nie pozwala zapisać notatki bez tytułu; tytuł złożony wyłącznie
   z białych znaków jest traktowany jak pusty. Tytuł jest zapisywany bez
   białych znaków na początku i końcu, a tytuły mogą się powtarzać.
   Treść może być pusta.
7. Zachowuje polskie znaki zarówno w pliku, jak i na liście.
8. Po udanym zapisie czyści pole tytułu i pole treści.
9. Kiedy zapis się nie powiedzie, pokazuje po polsku komunikat, że zapis
   się nie udał, i pozostawia zawartość pliku bez zmian.
10. Kiedy plik istnieje, ale nie da się go odczytać, pokazuje komunikat
    przy uruchomieniu, a przy próbie zapisu nie zmienia jego zawartości.
11. Zachowuje fragmenty pliku, których nie rozpoznaje jako notatkę; przy
    zapisie nie usuwa ich.
12. Działa bez połączenia z siecią.

## Czego nie robi

- Nie wyszukuje, nie filtruje i nie zmienia kolejności notatek inaczej niż
  „najnowsza na górze”.
- Nie edytuje ani nie usuwa zapisanych notatek — robi się to w edytorze
  tekstu.
- Nie ma ustawień, motywów, kategorii, załączników ani synchronizacji.
- Nie wysyła niczego do sieci i nie wymaga połączenia z internetem.
- Nie zmienia ani nie poprawia ręcznie dopisanych fragmentów pliku.
- Nie ostrzega o niezapisanym tekście przy zamykaniu programu.

## Kryteria akceptacji

K1. Kiedy zapiszę notatkę z tytułem „Zakupy” i treścią „mleko”, to
    w `notatki.md` pojawia się nagłówek `## RRRR-MM-DD GG:MM — Zakupy`
    z bieżącą datą i godziną, a pod nim linia `mleko`.
    Sprawdzenie: otworzyć `notatki.md` w edytorze tekstu; porównać wzorzec
    nagłówka, datę i godzinę z zegarem (z dokładnością do minuty) oraz
    treść.

K2. Kiedy zapiszę pięć notatek jedna po drugiej, to plik ma pięć wpisów
    oddzielonych dokładnie jedną pustą linią, a czytane od góry tytuły
    tworzą odwrotność kolejności zapisu: ostatnio zapisana notatka jest
    pierwsza.
    Sprawdzenie: zapisać notatki o różnych tytułach, odczytać tytuły od
    góry, porównać z kolejnością zapisu i sprawdzić odstępy między wpisami.

K3. Kiedy zapiszę notatkę z tytułem „Żółć” i treścią „Łódź — ąćęłńóśźż”,
    to tytuł na liście oraz tytuł i treść w pliku zawierają dokładnie te
    znaki.
    Sprawdzenie: otworzyć plik w edytorze tekstu ustawionym na UTF-8
    i porównać oba miejsca z wpisanym tekstem.

K4. Kiedy zamknę i uruchomię program ponownie, to lista pokazuje te same
    notatki w tej samej kolejności co plik.
    Sprawdzenie: porównać tytuły i kolejność na liście z kolejnością
    wpisów w pliku.

K5. Kiedy tytuł jest pusty albo składa się tylko z białych znaków, to
    przycisk zapisu jest nieaktywny, nie da się zapisać notatki, a plik
    i lista się nie zmieniają.
    Sprawdzenie: wykonać kopię pliku, sprawdzić, że przycisk jest
    nieaktywny, spróbować użyć przycisku, porównać plik z kopią
    i sprawdzić, czy lista się nie zmieniła.

K6. Kiedy `notatki.md` nie istnieje, to program uruchamia się z pustą
    listą i nie tworzy pliku przy samym uruchomieniu; plik powstaje przy
    pierwszym zapisie.
    Sprawdzenie: usunąć plik, uruchomić program, sprawdzić listę i brak
    pliku, zapisać notatkę i sprawdzić, czy plik powstał.

K7. Kiedy kliknę notatkę na liście, to widzę jej pełną, wielolinijkową
    treść oraz datę i godzinę zapisu.
    Sprawdzenie: zapisać notatkę o znanej treści, kliknąć ją, porównać
    wyświetlony tekst z tym, co zostało wpisane, i porównać datę oraz
    godzinę z nagłówkiem w pliku.

K8. Kiedy zapiszę notatkę przy kilku istniejących, to nowa notatka
    pojawia się na górze listy od razu, plik zawiera nowy wpis, a pola
    tytułu i treści są puste.
    Sprawdzenie: zapisać notatkę, sprawdzić pierwszy element listy, nowy
    wpis w pliku i oba pola.

K9. Kiedy zapis się nie powiedzie, na przykład gdy plik nie pozwala na
    zapis, to program pokazuje po polsku komunikat o nieudanym zapisie,
    a zawartość pliku pozostaje taka sama.
    Sprawdzenie: wykonać kopię pliku, uniemożliwić zapis (np. ustawić plik
    jako tylko do odczytu), spróbować zapisać, sprawdzić, czy komunikat
    jest po polsku, i porównać plik z kopią.

K10. Kiedy dopiszę notatkę do `notatki.md` w edytorze tekstu i uruchomię
     program, to lista pokazuje także tę notatkę, czyli jej tytuł oraz
     datę i godzinę, a po kliknięciu widać jej treść; zapis nowej notatki
     z programu nie usuwa jej ani nie zmienia.
     Sprawdzenie: dopisać wpis na końcu pliku, uruchomić program,
     sprawdzić tytuł i datę na liście, kliknąć wpis i sprawdzić treść,
     zapisać nową notatkę i porównać ręcznie dopisany fragment z kopią.

K11. Kiedy plik istnieje, ale nie da się go odczytać, to program pokazuje
     przy uruchomieniu komunikat po polsku, a zapis nowej notatki nie
     zmienia zawartości pliku.
     Sprawdzenie: zablokować plik w innym programie lub odebrać prawo
     odczytu, uruchomić program i sprawdzić komunikat, spróbować zapisać
     notatkę, sprawdzić komunikat po polsku i porównać plik z kopią.

K12. Kiedy w pliku znajduje się fragment, którego program nie rozpoznaje
     jako notatkę, to zapis nowej notatki nie usuwa tego fragmentu.
     Sprawdzenie: dopisać na końcu pliku dowolny tekst bez nagłówka, na
     przykład `to jest ręcznie dopisany fragment`, zapisać notatkę
     w programie i sprawdzić, czy tekst nadal jest w pliku.

K13. Kiedy komputer nie ma połączenia z siecią, to program uruchamia się,
     pokazuje listę i zapisuje notatkę tak samo jak z połączeniem.
     Sprawdzenie: wyłączyć sieć, uruchomić program, zapisać notatkę
     i sprawdzić plik.

K14. Kiedy zapiszę dwie notatki w tej samej minucie, to nowsza jest
     wyżej.
     Sprawdzenie: zapisać dwie notatki jedna po drugiej w tej samej
     minucie i porównać ich kolejność od góry pliku.

K15. Kiedy treść notatki zawiera linię zaczynającą się od `##`, ale
     niepasującą do pełnego wzorca nagłówka, to linia pozostaje częścią
     treści.
     Sprawdzenie: zapisać notatkę z taką linią i sprawdzić, czy program
     pokazuje ją jako treść, a nie jako osobną notatkę.

## Do ustalenia

- [DO USTALENIA] Czy lista ma odświeżać się na bieżąco, kiedy
  `notatki.md` zmieni się poza programem (np. w edytorze), czy wystarczy
  odświeżenie po zapisie w programie i po ponownym uruchomieniu?
  (dotyczy zdania „Lista notatek jest zawsze aktualna”)
- [DO USTALENIA] Co dokładnie ma znaczyć „zapis jest bezpieczny”: czy
  wystarczy zachowanie z K9 i K11 (komunikat i plik bez zmian), czy przed
  każdym zapisem ma dodatkowo powstawać kopia zapasowa pliku, a plik
  zablokowany ma być ponawiany? (dotyczy zdania „Zapis jest bezpieczny”)
