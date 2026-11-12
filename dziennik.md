# Dziennik — notatnik-v2

Wpisy z lekcji 4d („Narzędzia SDD”), zadania 4.4–4.7. Każdy wpis ma datę
i numer zadania; tam, gdzie decyzja zmieniła plik w repozytorium, jest
podany plik i commit. Dziennik jest zapisem tego, co zostało zrobione,
a nie planem tego, co ma być zrobione.

## 2026-11-12 — 4.4 Cztery pliki, dwie kolumny, trzy poziomy

### Cztery pliki w Spec Kit i Kiro

| Mój plik | Spec Kit | Kiro |
| --- | --- | --- |
| `konstytucja.md` | `/speckit.constitution` → `constitution.md` | pliki sterujące: `product.md`, `tech.md`, `structure.md` |
| `spec.md` | `/speckit.specify` → `spec.md` | `requirements.md`, kryteria w notacji EARS |
| `plan.md` | `/speckit.plan` → `plan.md` | `design.md` |
| `tasks.md` | `/speckit.tasks` → `tasks.md` | `tasks.md`, przy każdym zadaniu przycisk **Start task** |

Poza czterema plikami jest jeszcze wykonanie i sprawdzenie: w Spec Kit
`/speckit.implement` i `/speckit.analyze`, w Kiro wykonywanie zadań
odhaczanych w edytorze. Sprawdzone z tabelą lekcji (stan 2026-09-02) po
zapisaniu — zgodne.

### Trzy poziomy Böckeler

- **Spec-first** — dobrze przemyślana specyfikacja powstaje najpierw,
  a potem jest używana w pracy z agentem nad danym zadaniem.
- **Spec-anchored** — specyfikacja zostaje po skończeniu zadania i służy
  dalej rozwojowi i utrzymaniu funkcji.
- **Spec-as-source** — specyfikacja staje się z czasem głównym plikiem
  źródłowym; człowiek edytuje tylko ją i nigdy nie dotyka kodu.

Notatnik jest na **pierwszym poziomie, z jednym nawykiem drugiego**:
`specs/001-notatnik/spec.md` zostaje w repozytorium i następna zmiana
notatnika ma zacząć się od zmiany specyfikacji, ale nic nie wymaga,
żeby ten plik nadążał za kodem, a kod nadal edytuje człowiek — więc to
jeszcze nie *spec-anchored* i nie *spec-as-source*.

## 2026-11-12 — 4.5 Szablon Spec Kit obok `spec.md`

Kopia szablonu leży w
`specs/001-notatnik/reference/spec-template-spec-kit.md` — pobrana
2026-11-12 z
`https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md`,
treść bez zmian, tylko nagłówek z adresem. Mój plik to
`specs/001-notatnik/spec.md`.

Szablon ma sekcje, których moja specyfikacja nie ma. Wybieram dwie
i przy każdej decyduję: dopisać albo nie.

### 1. Historie użytkownika z priorytetami P1–P3 i „Independent Test” — nie dopisuję

Co daje szablon: dzieli funkcję na historie, które da się zbudować,
sprawdzić i pokazać niezależnie, i każe każdej nadać priorytet oraz
uzasadnienie. To działa, kiedy z jednej specyfikacji pracuje kilka osób
albo kiedy zakres trzeba ciąć.

Dlaczego nie u mnie: notatnik ma jednego użytkownika i jeden tydzień,
a zakres zamyka „Czego nie robi”. Kolejność jest już w „Co robi”
(punkty 1–12) i w numerach K1–K16. Priorytety byłyby drugą, konkurencyjną
kolejnością i sugerowałyby, że K9–K12 można odłożyć — a konstytucja,
punkt 6, robi z utraty notatki rzecz, której nie wolno odkładać.
Dopisanie priorytetów nie rozstrzyga niczego nowego; tworzy tylko drugie
miejsce, które trzeba by synchronizować z kryteriami.

### 2. Mierzalne kryteria sukcesu (SC-001…) — dopisuję, jako K16

Co daje szablon: osobną sekcję z wynikami, które da się zmierzyć i które
nie zależą od technologii („technology-agnostic and measurable”), na
przykład czas albo odsetek udanych prób. Moja specyfikacja ma wyłącznie
kryteria zero-jedynkowe: każde mówi „tak albo nie”, żadne nie mówi
„jak szybko”.

Dlaczego dopisuję: „Cel” obiecuje, że program będzie szybszy niż
otwarcie pliku w edytorze, i to jedyne zdanie w specyfikacji, którego nie
da się obalić, bo nie ma liczby. Bez progu K1–K15 mogą przejść, a program
może być wolniejszy od edytora i nikt tego nie zauważy.

Gdzie: nie jako siódma sekcja — specyfikacja ma sześć części i tyle
zostaje — tylko jako K16 w „Kryteriach akceptacji”, bo to odpowiada na to
samo pytanie („po czym poznam, że jest dobrze”), tylko z progiem. Próg
2 s jest wyraźnie niższy niż otwarcie edytora i pliku, a jednocześnie nie
wymaga optymalizacji, której specyfikacja nie zamawia.

> K16. Kiedy zapiszę notatkę, to od kliknięcia „Zapisz” do pojawienia się
> jej na górze listy mija mniej niż 2 sekundy. Sprawdzenie: zmierzyć
> stoperem trzy zapisy pod rząd i wziąć najdłuższy czas.

Skutek: `spec.md` zmieniony (K1–K16), `README.md` zaktualizowany
(K1–K16 i trzeci commit), commit
`4.5: K16 — mierzalne kryterium sukcesu po porównaniu z szablonem Spec Kit`.

## 2026-11-12 — 4.6 Plan z dwóch plików

### Jak powstał

Plan Mode nie był dostępny na moim koncie, więc zadanie poszło wariantem
zapasowym: przeczytałem dokumentację. Cursor Plan Mode tworzy plan jako
edytowalny plik Markdown i domyślnie zapisuje go w katalogu domowym;
„Save to workspace” przenosi go do projektu. Antigravity tworzy artefakty
**Task List** i **Implementation Plan** (opisany jako przeznaczony do
przeczytania przez użytkownika) i czeka na **Proceed**, chyba że
ustawienie każe iść dalej („Always Proceed”). Z czterech plików oba
wytwarzają więc **`plan.md` i `tasks.md`**; **`spec.md` i
`konstytucja.md`** muszą już leżeć w projekcie, bo edytor nie wymyśla
celu, zakresu ani konstytucji.

Żeby mieć co porównać, ten sam plan wygenerowałem metodą z lekcji 4c:
świeża sesja, dołączone wyłącznie `konstytucja.md` i
`specs/001-notatnik/spec.md`, polecenie o pliki, kolejność, „poza planem”
i zagrożone punkty konstytucji. Wynik:
`specs/001-notatnik/plan.md`.

### Czy są trzy części

| Część | Plan z lekcji 4c | Plan z 4.6 |
| --- | --- | --- |
| Sprawdzenie z konstytucją | jest — punkty 2, 3 i 5 | jest — wszystkie 8 punktów |
| Pliki | jest — 5 pozycji (7 plików) | jest — te same 5 pozycji (7 plików) |
| Kolejność z kryteriami | jest — 5 kroków | jest — 7 kroków, każdy z K w nawiasie |
| Poza planem | jest | jest |

### Co dodał

- **Blokadę na dwóch `[DO USTALENIA]`.** W specyfikacji zostały dwa
  otwarte pytania (odświeżanie listy po zmianie pliku poza programem;
  kopia zapasowa i ponawianie przy zapisie). Plan jest oznaczony jako
  roboczy, a kroki, które od nich zależą, są wstrzymane. Plan z lekcji
  tego nie zrobił, choć jego specyfikacja też miała jedno otwarte pytanie
  — czyli lekcja złamała własną zasadę „plan nie powstaje, zanim pytanie
  zniknie”.
- **Sprawdzenie konstytucji dla punktów 4, 6 i 8** (polskie znaki;
  notatka nie ginie; Windows, C#/.NET, Avalonia). W planie z lekcji
  sprawdzane były tylko punkty 2, 3 i 5, a właśnie 4, 6 i 8 dotyczą K3,
  K9–K12 i nazw plików.
- **Kryteria K8–K16**: odświeżenie listy bez restartu, komunikat przy
  nieudanym zapisie, ręczna edycja pliku, plik nieczytelny, nieznany
  fragment pliku, praca bez sieci, dwie notatki w tej samej minucie,
  linia `##` w treści, czas zapisu. Plan z lekcji ich nie miał, bo jego
  specyfikacja kończyła się na K7.
- **Zapis przez plik tymczasowy i podmianę** — to sposób na punkt 6
  konstytucji i K9/K11, a nie nowe wymaganie.

### Co pominął

- Nic z pięciu kroków planu z lekcji. Kolejność jest ta sama, tylko krok
  „`Note.cs` i `NoteFile.cs`” jest rozdzielony na odczyt i zapis, a na
  końcu doszedł przebieg przez wszystkie K.
- Nie powtórzył uzasadnienia z „Celu” („notatnik jest potrzebny, bo…”).
  To dobrze: uzasadnienie należy do specyfikacji, a plan, który na nowo
  przekonuje do funkcji, nie ma stałego celu.

### Czy wszedł na teren specyfikacji albo konstytucji

- Nie dopisał nowego zachowania. Nazwy plików, kolejność i sposób zapisu
  to „jak”, czyli plan.
- Nie zmienił konstytucji ani jej nie osłabił; sprawdzenie jest
  interpretacją punktów, nie ich poprawianiem.
- Nie osłabił kryteriów: K9 i K11 nie są odłożone „na później”, tylko
  wstrzymane do decyzji, bo pytania są w specyfikacji.
- Jedno miejsce graniczne: „Poza planem” powtarza „Czego nie robi” ze
  specyfikacji. To wskazanie, a nie nowa decyzja — ale gdyby plan zaczął
  rozstrzygać, co jest poza zakresem, byłby to wyciek w drugą stronę.
  W tym planie nie rozstrzyga.

### Wniosek

Plan z dwóch plików ma te same trzy części co plan z lekcji. Różnica nie
polega na tym, że edytor planuje lepiej, tylko na tym, że dostał
ostrzejszy wkład: 8 punktów konstytucji i 16 kryteriów zamiast 3 i 7.
Największa różnica jest jednak w zachowaniu wobec otwartych pytań: plan
z 4.6 ich nie przemilcza. Przed lekcją 4e trzeba odpowiedzieć na oba
`[DO USTALENIA]`, inaczej budowa zacznie się od zgadywania.

## 2026-11-12 — 4.7 Poziom drugi

Część „Definition” artykułu Böckeler mówi, że *spec-anchored* to
specyfikacja zachowana po skończeniu zadania i używana dalej do rozwoju
i utrzymania funkcji. Jedno zdanie o notatniku:

**Żeby notatnik był *spec-anchored*, a nie tylko *spec-first*, każda
późniejsza zmiana musiałaby zaczynać się od poprawienia `spec.md`
i kończyć jego aktualizacją, a konstytucja musiałaby wymagać, że
specyfikacja 001 opisuje notatnik taki, jaki jest teraz — dziś jest
zapisem pierwszego tygodnia i nic nie wymaga, żeby nadążała za kodem.**
