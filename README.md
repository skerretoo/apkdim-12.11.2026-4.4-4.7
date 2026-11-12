# notatnik-v2 — zadania 4.3–4.7

Repozytorium zawiera konstytucję i pierwszą decyzję z zadania 4.2,
specyfikację notatnika z zadania 4.3 oraz dziennik i plan z zadań 4.4–4.7.
Kodu jeszcze nie ma: zgodnie z lekcją specyfikacja jest budowana dopiero
za dwie lekcje.

## Co jest w repozytorium

- `konstytucja.md` — osiem zdań, które mają zostać prawdziwe niezależnie
  od tego, jaką funkcję dopiszemy.
- `decyzje/0001-format-pliku-notatek.md` — format pliku `notatki.md`:
  kontekst, decyzja, odrzucone możliwości i skutki.
- `specs/001-notatnik/spec.md` — specyfikacja w sześciu częściach: cel,
  dla kogo, co robi, czego nie robi, kryteria akceptacji (K1–K16),
  do ustalenia.
- `specs/001-notatnik/przeglad.md` — zapis dwóch niezależnych przeglądów
  specyfikacji i lista zmian wprowadzonych po pierwszym z nich.
- `dziennik.md` — wpisy z zadań 4.4–4.7: odpowiedzi, decyzje i porównanie
  planów.
- `specs/001-notatnik/plan.md` — plan budowy z dwóch plików (zadanie 4.6).
- `specs/001-notatnik/spec-template-spec-kit.md` — kopia szablonu Spec
  Kit do porównania (zadanie 4.5), położona obok `spec.md`.

## Pięć zdań przepisanych na kryteria

1. **Program obsługuje polskie znaki.**

   Kryterium: Kiedy zapiszę notatkę z tytułem „Żółć” i treścią
   „Łódź — ąćęłńóśźż”, to tytuł na liście oraz tytuł i treść w pliku
   zawierają dokładnie te same znaki, bez znaków zapytania ani krzaczków
   (K3).

   Sprawdzenie: otworzyć `notatki.md` w edytorze tekstu ustawionym na
   UTF-8 i porównać oba miejsca z listą w programie.

2. **Lista notatek jest zawsze aktualna.**

   Kryterium: Kiedy zapiszę notatkę w programie, to pojawia się ona na
   górze listy od razu, a po ponownym uruchomieniu lista pokazuje te same
   notatki w tej samej kolejności co plik (K8, K4).

   Sprawdzenie: zapisać notatkę, sprawdzić pierwszy element listy,
   zamknąć i uruchomić program ponownie, a potem porównać listę z plikiem.

   Decyzja: słowo „zawsze” nie da się przepisać w całości bez
   rozstrzygnięcia, czy lista ma reagować także na zmiany pliku zrobione
   poza programem, gdy program jest otwarty. To pytanie jest w części
   „Do ustalenia” w specyfikacji (pierwszy punkt); bez tej decyzji
   kryterium obejmuje tylko zapis w programie i ponowne uruchomienie.

3. **Zapis jest bezpieczny.**

   Kryterium: Kiedy zapis się nie powiedzie, na przykład gdy plik nie
   pozwala na zapis, to program pokazuje po polsku komunikat, a zawartość
   pliku pozostaje taka sama (K9, K11).

   Sprawdzenie: wykonać kopię pliku, uniemożliwić zapis (np. ustawić plik
   jako tylko do odczytu), spróbować zapisać, sprawdzić, czy komunikat jest
   po polsku, i porównać plik z kopią.

   Decyzja: słowo „bezpieczny” wymaga rozstrzygnięcia, czy wystarczy
   komunikat i plik bez zmian, czy przed każdym zapisem ma dodatkowo
   powstawać kopia zapasowa, a plik zablokowany ma być ponawiany. To
   pytanie jest w części „Do ustalenia” w specyfikacji (drugi punkt).

4. **Pusta notatka nie jest zapisywana.**

   Kryterium: Kiedy tytuł jest pusty albo składa się tylko z białych
   znaków, to przycisk zapisu jest nieaktywny, nie da się zapisać notatki,
   a plik i lista się nie zmieniają (K5).

   Sprawdzenie: wykonać kopię pliku, sprawdzić, że przycisk jest
   nieaktywny, spróbować go użyć, porównać plik z kopią i sprawdzić, czy
   lista się nie zmieniła.

5. **Program działa po ponownym uruchomieniu.**

   Kryterium: Kiedy zamknę i uruchomię program ponownie, to lista pokazuje
   te same notatki w tej samej kolejności co plik (K4).

   Sprawdzenie: porównać tytuły i kolejność na liście z kolejnością wpisów
   w pliku.

## Prompt z pokazu rozsortowany do czterech plików

Prompt z pokazu w module 2 budował aplikację „Fiszki”. Poniżej te same
fragmenty, rozdzielone według tego, na jakie pytanie odpowiada każdy plik.

| Plik | Co z promptu tam trafia |
| --- | --- |
| `konstytucja.md` | Stały stos, nazwa projektu, zakaz bibliotek zewnętrznych i polski interfejs — rzeczy wspólne dla całego programu. |
| `spec.md` | Osiem wymagań funkcjonalnych: zestawy, fiszki, tryb powtórki, zapis danych, licznik powtórek, dane startowe, instrukcja, polski interfejs. |
| `plan.md` | Nic. Prompt nie wymienia plików, kolejności ani sprawdzenia z konstytucją. |
| `tasks.md` | Jedno zadanie na koniec („write README.md in Polish”) i jedno globalne kryterium zakończenia (`dotnet build`, `dotnet run`). |

### `konstytucja.md`

- „C# on .NET 8, WPF, Windows.” oraz „The project name is Fiszki.” —
  nie zmienia się przy żadnej funkcji.
- „No external NuGet packages unless you decide one is truly necessary.
  If you add one, record why in DECISIONS.md.” — zasada dla całego
  projektu; wyjątek wymaga zapisanej decyzji.
- „All UI text is in Polish, with correct diacritics (ą ć ę ł ń ó ś ź ż)
  …” — stała zasada interfejsu, niezależna od funkcji.

### `spec.md`

- Wymagania 1–8: tworzenie i usuwanie zestawów, dodawanie, edycja
  i usuwanie fiszek, tryb powtórki z przyciskiem „Sprawdź” i ocenami
  „Umiem” / „Nie umiem”, trwały zapis, licznik fiszek do powtórki, trzy
  zestawy startowe, przycisk „Instrukcja” i polskie znaki.
- Zdanie „The task is done when `dotnet build` finishes with no errors and
  `dotnet run` starts the application” jest kryterium akceptacji, ale
  jedynym i technicznym — nie mówi, co użytkownik ma zobaczyć.
- Brakuje „dla kogo”, „czego nie robi” i kryteriów w formie
  sytuacja–wynik–sprawdzenie. Zdanie „when something is unspecified,
  decide yourself” oddaje właśnie tę brakującą część agentowi.

### `plan.md`

- Nic. Prompt nie nazywa plików, nie ustala kolejności i nie każe
  sprawdzić planu z konstytucją. Najbliżej planu jest zdanie „Create the
  project in the current directory (it is already created and empty)”,
  ale to pojedynczy krok przygotowania, nie plan.

### `tasks.md`

- „At the end, write README.md in Polish: how to run the application, and
  what you did not manage to do.” — jedno zadanie z warunkiem końca.
- „The task is done when `dotnet build` … verify this yourself” —
  globalny warunek zakończenia, nie „gotowe, gdy” dla każdego kroku.
- Brak zadań wielkości jednego commita i brak numerów, które dałoby się
  odhaczać po kolei.

### Poza czterema plikami

- „Do not ask questions. When something is unspecified, decide yourself
  and record the decision in `DECISIONS.md` in the project directory —
  one line per decision, each naming the alternative you rejected.” —
  to reguła procesu, która w pętli czterech plików należy do specyfikacji
  (pytania i decyzje), a nie do osobnego pliku. To ona zastępowała
  brakującą specyfikację.

**Czego prompt nie miał wcale:** specyfikacji — a także planu i zadań, ale
najdroższy był brak `spec.md`: osiem „wymagań funkcjonalnych” to lista
życzeń bez „dla kogo”, „czego nie robi” i kryteriów akceptacji, a zdanie
„when something is unspecified, decide yourself” oddaje brakującą
specyfikację agentowi; trzy `DECISIONS.md` pokazują rachunek, bo te same
pytania — format zapisu, algorytm powtórek i porównanie odpowiedzi —
dostały trzy różne odpowiedzi, więc trzy aplikacje są trzema produktami,
a nie jednym zbudowanym trzy razy.

## Weryfikacja warunków zadania

- [x] `spec.md` ma sześć części: cel, dla kogo, co robi, czego nie robi,
      kryteria akceptacji, do ustalenia.
- [x] Każde kryterium ma sytuację („Kiedy…”), wynik („to…”) i sposób
      sprawdzenia („Sprawdzenie:…”).
- [x] W specyfikacji nie ma nazw plików z kodem, klas ani bibliotek.
      `notatki.md` to plik użytkownika, nie plik programu.
- [x] Są dwa commity specyfikacji z zadania 4.3: pierwszy z wersją
      własną, drugi po przeglądzie. Przegląd jest zapisany w
      `przeglad.md`; trzeci commit (K16) doszedł w zadaniu 4.5.
- [x] Pięć zdań z listy jest przepisanych na kryteria; przy dwóch
      zapisano, jaka decyzja jest potrzebna, i przeniesiono ją do
      „Do ustalenia”.
- [x] Prompt z pokazu jest rozsortowany do czterech plików, z jednym
      zdaniem o brakującej specyfikacji i jej koszcie.

## Commity specyfikacji

1. `konstytucja, decyzja 0001 i pierwsza wersja specyfikacji 001`
2. `spec 001-notatnik po przeglądzie: poprawki, przegląd i README`
3. `4.5: K16 — mierzalne kryterium sukcesu po porównaniu z szablonem Spec Kit`
