# Plan — 001 Notatnik

Wejście: `konstytucja.md`, `specs/001-notatnik/spec.md`. Nic więcej.
Status: roboczy. Dwa pytania `[DO USTALENIA]` w specyfikacji nie mają
odpowiedzi, więc plan obejmuje tylko to, co od nich nie zależy; kroki
wstrzymane są na końcu.

## Sprawdzenie z konstytucją

- pkt 1 (jedna osoba, jeden komputer): spełnia — jedno okno, bez kont,
  profili i synchronizacji.
- pkt 2 (zwykły plik tekstowy): spełnia — `notatki.md` w Markdownie,
  format z decyzji 0001 i z „Co robi”; plik da się otworzyć i poprawić
  bez programu.
- pkt 3 (nic poza komputer): spełnia — program nie używa sieci; w
  projekcie nie ma klienta HTTP ani zależności sieciowej (K13).
- pkt 4 (interfejs po polsku, polskie znaki): spełnia — teksty interfejsu
  po polsku, odczyt i zapis w UTF-8 (K3).
- pkt 5 (tylko szablon, bez bibliotek): spełnia — szablon
  `avalonia.app`, bez dodatkowych pakietów.
- pkt 6 (notatka zostaje w pliku w całości): spełnia — odczyt całego
  pliku, wstawienie nowego wpisu na początek, zapis całości; fragmenty
  nierozpoznane zostają bez zmian (K12); zapis przez plik tymczasowy
  i podmianę, żeby nieudany zapis nie zostawił połowy pliku (K1, K2, K9,
  K10, K11).
- pkt 7 (specyfikacja nie zaprzecza konstytucji): spełnia — plan nie
  zmienia specyfikacji ani konstytucji; otwarte pytania zostają pytaniami.
- pkt 8 (Windows, C#/.NET, Avalonia, aplikacja okienkowa): spełnia —
  szablon `avalonia.app` na .NET, jedno okno; nie konsola i nie web.

## Pliki

- `Notatnik.csproj`, `Program.cs`, `App.axaml(.cs)` — z szablonu, bez
  zmian.
- `Note.cs` — tytuł, data i godzina, treść; jedna notatka.
- `NoteFile.cs` — odczyt i zapis `notatki.md`: podział na nagłówki
  `## RRRR-MM-DD GG:MM — Tytuł`; linia od `##`, która nie pasuje do
  pełnego wzorca, zostaje w treści (K15); fragmenty nierozpoznane są
  zachowywane dosłownie (K12); UTF-8; zapis całości do pliku tymczasowego
  i podmiana.
- `MainWindow.axaml` — pole tytułu, pole treści, przycisk „Zapisz”,
  lista notatek (tytuł oraz data i godzina), podgląd treści.
- `MainWindow.axaml.cs` — obsługa przycisku, wybór na liście, polskie
  komunikaty przy nieudanym zapisie i nieczytelnym pliku.

## Kolejność

1. Szablon `dotnet new avalonia.app` i pierwszy commit projektu.
2. `Note.cs` oraz odczyt w `NoteFile.cs` — plik z wpisami wczytuje się do
   listy, także wpis wielolinijkowy i linia `##` w treści; wykrycie
   nieczytelnego pliku (K4, K6, K7, K10, K11, K12, K15 — strona odczytu).
3. Zapis w `NoteFile.cs` — nowy wpis na początek, UTF-8, plik tymczasowy
   i podmiana, zachowanie nieznanych fragmentów (K1, K2, K3, K6, K10,
   K12, K14, K15 — strona zapisu).
4. `MainWindow.axaml` — układ, lista i podgląd; przycisk nieaktywny przy
   pustym tytule albo tytule z białych znaków (K5, K7).
5. Połączenie okna z plikiem: zapis z przycisku, odświeżenie listy bez
   restartu, komunikat przy nieudanym zapisie i przy nieczytelnym pliku
   (K1, K2, K4, K8, K9, K11, K16).
6. Podgląd treści po kliknięciu na liście (K7).
7. Przejście przez K1–K16 na gotowym programie i wpis w `dziennik.md`.

## Poza planem

- Wyszukiwanie, filtrowanie i zmiana kolejności — specyfikacja, „Czego
  nie robi”.
- Edycja i usuwanie notatek, ustawienia, motywy, kategorie, załączniki,
  synchronizacja i sieć — specyfikacja, „Czego nie robi”.
- Odświeżanie listy na bieżąco, kiedy plik zmieni się poza programem —
  zależy od pierwszego `[DO USTALENIA]`; nie wchodzi do planu przed
  decyzją.
- Kopia zapasowa przed każdym zapisem i ponowienie zapisu przy pliku
  zablokowanym — zależą od drugiego `[DO USTALENIA]`; nie wchodzą do
  planu przed decyzją.

## Czego ten plan nie rozstrzyga

1. Czy lista ma odświeżać się na bieżąco, kiedy `notatki.md` zmieni się
   poza programem, czy wystarczy odświeżenie po zapisie w programie i po
   ponownym uruchomieniu?
2. Czy „zapis jest bezpieczny” wymaga kopii zapasowej przed każdym
   zapisem i ponawiania przy pliku zablokowanym, czy wystarcza K9 i K11
   (komunikat i plik bez zmian)?

Skutek: kroki 2, 3 i 5 są kompletne tylko w wariancie bez bieżącego
odświeżania i bez kopii zapasowej. Jeśli decyzja doda któreś z nich,
dochodzi osobny krok i osobne kryterium; plan trzeba wtedy poprawić,
a nie dopisywać tego po cichu.
