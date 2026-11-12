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
2. Pokazuje listę zapisanych notatek, najnowszą na górze.
3. Po zapisie umieszcza notatkę w pliku `notatki.md` w folderze programu,
   w formacie z decyzji 0001, tak żeby najnowsza była na górze.
4. Po ponownym uruchomieniu pokazuje wszystkie notatki z pliku,
   w kolejności z pliku.
5. Kliknięcie notatki na liście pokazuje jej pełną treść.
6. Nie pozwala zapisać notatki bez tytułu; treść może być pusta.
7. Zachowuje polskie znaki zarówno w pliku, jak i na liście.
8. Kiedy zapis się nie powiedzie, pokazuje komunikat i pozostawia plik bez
   zmian.

## Czego nie robi

- Nie wyszukuje, nie filtruje i nie zmienia kolejności notatek inaczej niż
  „najnowsza na górze”.
- Nie edytuje ani nie usuwa zapisanych notatek — robi się to w edytorze
  tekstu.
- Nie odświeża listy na bieżąco, kiedy plik zmieni się poza programem;
  taką zmianę widać po ponownym uruchomieniu.
- Nie ma ustawień, motywów, kategorii, załączników ani synchronizacji.
- Nie wysyła niczego do sieci i nie wymaga połączenia z internetem.

## Kryteria akceptacji

K1. Kiedy zapiszę notatkę z tytułem „Zakupy” i treścią „mleko”, to
    w `notatki.md` pojawia się nagłówek `## RRRR-MM-DD GG:MM — Zakupy`,
    a pod nim linia `mleko`.
    Sprawdzenie: otworzyć `notatki.md` w edytorze tekstu i porównać
    nagłówek oraz treść.

K2. Kiedy zapiszę pięć notatek jedna po drugiej, to plik ma pięć wpisów
    rozpoczynających się nagłówkiem `##`, a pierwszy od góry należy do
    notatki zapisanej jako ostatnia.
    Sprawdzenie: policzyć nagłówki rozpoczynające notatki i porównać tytuł
    pierwszego wpisu z tytułem ostatnio zapisanej notatki.

K3. Kiedy zapiszę notatkę z tytułem „Żółć” i treścią „Łódź — ąćęłńóśźż”,
    to w pliku i na liście widać dokładnie te znaki.
    Sprawdzenie: otworzyć plik w edytorze tekstu i porównać oba miejsca
    z wpisanym tekstem.

K4. Kiedy zamknę i uruchomię program ponownie, to lista pokazuje tyle
    samo notatek, ile jest wpisów rozpoczynających się nagłówkiem `##`
    w pliku.
    Sprawdzenie: policzyć wpisy w pliku i pozycje na liście.

K5. Kiedy tytuł jest pusty, to przycisk zapisu jest nieaktywny, a plik się
    nie zmienia.
    Sprawdzenie: spróbować kliknąć przycisk i porównać datę modyfikacji
    pliku przed próbą i po niej.

K6. Kiedy `notatki.md` nie istnieje, to program uruchamia się z pustą listą
    i tworzy plik przy pierwszym zapisie.
    Sprawdzenie: usunąć plik, uruchomić program, sprawdzić listę, zapisać
    notatkę i sprawdzić, czy plik powstał.

K7. Kiedy kliknę notatkę na liście, to widzę jej pełną treść, także wtedy,
    gdy ma kilka linii.
    Sprawdzenie: zapisać notatkę wielolinijkową, kliknąć ją na liście
    i porównać z treścią w pliku.

K8. Kiedy zapiszę notatkę przy kilku istniejących, to nowa notatka pojawia
    się na górze listy od razu, bez ponownego uruchamiania.
    Sprawdzenie: zapisać notatkę i spojrzeć na pierwszy element listy.

K9. Kiedy zapis się nie powiedzie, na przykład dlatego że plik jest tylko
    do odczytu, to program pokazuje komunikat, a zawartość pliku pozostaje
    bez zmian.
    Sprawdzenie: ustawić plikowi atrybut „tylko do odczytu”, spróbować
    zapisać notatkę i porównać plik z wcześniejszą kopią.

K10. Kiedy dopiszę notatkę do `notatki.md` w edytorze tekstu i uruchomię
     program, to lista pokazuje także tę notatkę, a zapis nowej notatki
     z programu nie usuwa jej z pliku.
     Sprawdzenie: dopisać wpis ręcznie, uruchomić program, zapisać nową
     notatkę i policzyć wpisy w pliku.

## Do ustalenia

- [DO USTALENIA] Co dokładnie ma znaczyć „zapis jest bezpieczny”: czy
  wystarczy zachowanie z K9 (komunikat i plik bez zmian), czy przed każdym
  zapisem ma dodatkowo powstawać kopia zapasowa pliku?
- [DO USTALENIA] Czy program ma obsługiwać przypadek, w którym
  `notatki.md` jest w chwili zapisu otwarty w innym programie
  i zablokowany, inaczej niż przez komunikat z K9 — na przykład przez
  ponowienie zapisu?
