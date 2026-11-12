# Przegląd specyfikacji 001 — notatnik

Data: 2026-11-12.

Przegląd robiła świeża sesja agenta, która nie widziała rozmowy, w której
powstała specyfikacja, ani reszty repozytorium. Dostała wyłącznie dwa
dokumenty: `konstytucja.md` i `specs/001-notatnik/spec.md`. Jej zadaniem
było wypisać pliki, które utworzyłaby, zaznaczyć każdy wyciek (zdanie
o „jak” zamiast „co”) i wypisać każde pytanie, na które w dokumentach nie
ma odpowiedzi.

## Przegląd 1 — wersja pierwsza

### Raport recenzenta

#### 1. Pliki do utworzenia

**Nie umiem podać nazw plików bez zgadywania.** Brakuje mi dwóch rzeczy,
bez których każda nazwa pliku byłaby wymyślona:

- **stosu technologicznego i zawartości szablonu projektu** — konstytucja
  pkt 5 mówi „wyłącznie to, co daje szablon projektu”, ale żaden
  z dokumentów nie mówi, jaki to szablon (język, framework, czy jest GUI,
  jakie katalogi już istnieją);
- **treści decyzji 0001** — specyfikacja dwukrotnie się na nią powołuje
  („format z decyzji 0001”), a samej decyzji nie ma w materiałach; bez
  niej nie wiadomo nawet, jak nazwać moduł zapisu/parsowania, bo nie
  wiadomo, co dokładnie parsuje.

Gdyby pominąć nazwy i mówić tylko o odpowiedzialnościach, funkcja wymaga:
odczytu pliku przy starcie, zapisu nowej notatki z zachowaniem istniejących
wpisów, walidacji tytułu, widoku listy, widoku pojedynczej notatki
i obsługi błędu zapisu. Przypisanie tego do konkretnych plików jest możliwe
dopiero po ustaleniu szablonu.

#### 2. Wycieki (JAK zamiast CO)

Wycieków technologicznych (biblioteka, klasa, nazwa pliku z kodem)
**brak**. Graniczne przypadki:

- „…umieszcza notatkę w pliku `notatki.md` w folderze programu…” — nazwa
  pliku danych, nie kodu, więc dopuszczalna (konstytucja pkt 2 wymaga
  czytelnego pliku), ale **„folder programu” jest niedoprecyzowany** i pełni
  rolę ukrytego szczegółu implementacji.
- „…przycisk zapisu jest nieaktywny…” (K5) — przesądza mechanizm UI
  (wyłączona kontrolka) zamiast zachowania „nie da się zapisać”. To JAK
  interfejsu.
- „…na przykład dlatego że plik jest tylko do odczytu…” oraz „ustawić
  plikowi atrybut «tylko do odczytu»” (K9) — szczegół zależny od systemu
  plików (atrybut Windows), a nie ogólna sytuacja „brak prawa zapisu”.
- „…w formacie z decyzji 0001…” — nie wyciek, ale odesłanie do
  niezałączonego dokumentu (patrz pkt 3).
- „Sprawdzenie: … porównać datę modyfikacji pliku…” (K5) — metoda
  weryfikacji oparta na artefakcie implementacji, nie na obserwowalnym
  wyniku.

#### 3. Brakujące odpowiedzi

**Blokujące budowę:**

- **B1. Jak wygląda format z decyzji 0001?** Separator wpisów, sposób
  zapisu treści wielolinijkowej, puste linie, co z linią zaczynającą się
  od `##` w treści notatki. Oczekiwane: osobna sekcja „Format pliku”
  w specyfikacji lub załączona decyzja 0001.
- **B2. Jaki jest stos technologiczny i co daje szablon projektu?**
  Oczekiwane: wskazanie platformy/technologii albo odniesienie do opisu
  szablonu (konstytucja pkt 5).
- **B3. Co znaczy „folder programu”?** Katalog pliku wykonywalnego czy
  katalog danych użytkownika. Oczekiwane: „Co robi” pkt 3.
- **B4. Co pokazuje pozycja listy** — tylko tytuł, tytuł z datą, fragment
  treści? Od tego zależy sens K3 i K7. Oczekiwane: „Co robi” pkt 2.
- **B5. Co się dzieje, gdy plik przy starcie jest nieczytelny lub ma wpisy
  niezgodne z formatem** (np. dopisane ręcznie)? Czy program je
  zachowuje dosłownie, pomija, blokuje zapis? Oczekiwane: „Co robi”
  pkt 3–4 oraz K10; wiąże się z konstytucją pkt 6.
- **B6. Czy zapis wolno wykonać, jeśli nie udało się wiarygodnie odczytać
  istniejącej zawartości?** Bez tego nie da się zapewnić „program nie może
  po cichu nadpisać ani utracić” (konstytucja pkt 6). Oczekiwane:
  „Co robi” pkt 3 i 8.

**Doprecyzowujące:**

- **D1.** Strefa czasowa i zerowanie w `RRRR-MM-DD GG:MM` (czas lokalny?).
- **D2.** Kolejność dwóch notatek zapisanych w tej samej minucie.
- **D3.** Czy tytuł złożony z samych spacji jest „pusty” (K5).
- **D4.** Kodowanie pliku i końce linii (UTF-8, CRLF/LF) — istotne dla K3
  i „dowolnego edytora”.
- **D5.** Limity długości tytułu i treści („krótkie notatki”).
- **D6.** Treść i forma komunikatu o błędzie zapisu (K9).
- **D7.** Czy po zapisie pola formularza się czyszczą (K8 dotyczy tylko
  listy).
- **D8.** Co znaczy „plik bez zmian” w K9 — w ogóle nie dotknięty, czy
  przywrócony do poprzedniej treści.
- **D9.** Czy puste wpisy (nagłówek bez treści) i pusty plik to poprawny
  stan.
- **D10.** Czy kliknięta notatka pokazuje też datę zapisu.
- **D11.** Kwestie już jawnie otwarte w „Do ustalenia”: kopia zapasowa
  przed zapisem oraz plik zablokowany przez inny program.

#### 4. Kryteria akceptacji — kompletność

Wszystkie mają trzy elementy, ale w wielu są one nieprecyzyjne:

- **K1** — wynik nie podaje konkretnej daty i godziny, więc wzorzec
  `RRRR-MM-DD GG:MM` nie da się porównać dosłownie; brak zdefiniowanego
  separatora między wpisami.
- **K2** — sprawdzenie liczy nagłówki i porównuje tylko pierwszy wpis; nie
  weryfikuje pozostałych czterech ani ich kolejności; „nagłówki
  rozpoczynające notatki” jest niejednoznaczne, jeśli treść zawiera linię
  `##`.
- **K3** — wynik mówi „na liście widać dokładnie te znaki”, ale nie
  wiadomo, co lista pokazuje; brak wskazania kodowania pliku.
- **K4** — sprawdzana jest tylko liczba wpisów, nie ich treść ani
  kolejność; to samo zastrzeżenie o `##`.
- **K5** — sprzeczność: jeśli przycisk jest nieaktywny, nie da się
  „kliknąć”; sprawdzenie przez datę modyfikacji jest zawodne; brak
  sprawdzenia, że notatka nie pojawiła się na liście; brak przypadku
  tytułu z białych znaków.
- **K6** — sprawdzenie nie weryfikuje, że plik nie powstaje przy samym
  uruchomieniu, choć wynik właśnie to sugeruje.
- **K7** — sprawdzenie „porównać z treścią w pliku” zależy od nieznanego
  formatu; brak sprawdzenia zachowania treści dłuższej niż dwie linie
  (czy nie jest ucinana/scalana).
- **K8** — sprawdzenie dotyczy tylko listy; brak równoległego sprawdzenia
  pliku i stanu formularza po zapisie.
- **K9** — „tylko do odczytu” jest zależne od systemu; brak oczekiwanej
  treści komunikatu; nakłada się na otwarte pytanie o kopię zapasową.
- **K10** — sprawdzenie tylko liczy wpisy; nie sprawdza, czy wpis
  dopisany ręcznie zachował treść i format.

Poza kryteriami: **brak jakiegokolwiek kryterium dla konstytucji pkt 3**
(brak wysyłania danych do sieci); pkt 6 jest pokryty tylko częściowo
(K9, K10).

## Przegląd 2 — po poprawkach

Drugi przegląd dostał poprawioną konstytucję i specyfikację, znowu bez
reszty repozytorium. Wynik:

- **Pliki, które recenzent by utworzył:** `MainWindow.axaml`,
  `MainWindow.axaml.cs`, `Note.cs`, `NotesFileStore.cs`, `NoteFormat.cs`,
  plik z polskimi komunikatami, testy formatu i zapisu oraz listę
  kontrolną K1–K15. `App.axaml` i `Program.cs` pochodzą z szablonu.
- **Wycieki:** brak. Recenzent uznał `notatki.md`, UTF-8 i „folder
  programu” za kontrakt danych, nie implementację; technologię w
  konstytucji pkt 8 uznał za postanowienie ustrojowe, nie wyciek
  w specyfikacji.
- **Pytania blokujące:** format z decyzji 0001, znaczenie „folderu
  programu”, odróżnianie nagłówka od linii `##` w treści, kolejność
  w tej samej minucie, częściowy zapis, notatka z pustą treścią.
- **Kryteria:** wszystkie mają sytuację, wynik i sprawdzenie. Recenzent
  wskazał K9, K10 i K11 jako niekompletne oraz K2, K3, K5, K7 jako
  częściowo niekompletne; osobno zauważył sprzeczność K10 z pkt 2
  (lista miała pokazywać treść, choć pokazuje tytuł i datę).

## Co zmieniłem po przeglądach

1. Wpisałem cały format pliku do specyfikacji, żeby nie zależeć od
   niezałączonej decyzji 0001: nagłówek, separator, kolejność, czas
   lokalny, UTF-8, myślniki w tytule i linie `##` w treści (B1).
2. Dodałem do konstytucji punkt 8 o platformie (Windows, C#/.NET,
   Avalonia), bo bez niego recenzent nie umiał nazwać plików (B2). To fakt
   o programie, nie o pojedynczej funkcji.
3. Wyjaśniłem „folder programu”: tam, gdzie leży plik programu (B3).
4. Napisałem, co pokazuje pozycja listy: tytuł oraz datę i godzinę
   zapisu (B4).
5. Dodałem zachowanie dla nieczytelnego pliku i dla nieznanych
   fragmentów pliku (B5, B6) oraz kryteria K11 i K12.
6. Zmieniłem sprawdzenie K5 z daty modyfikacji pliku na porównanie
   z kopią, uogólniłem K9 poza atrybut „tylko do odczytu” i dopisałem
   sprawdzanie polskiego komunikatu w K9 i K11.
7. Doprecyzowałem K1, K2, K3, K4, K7, K8 i K10; dodałem K13 (praca bez
   sieci), K14 (dwie notatki w tej samej minucie) i K15 (linia `##`
   w treści).
8. Zostawiłem w „Do ustalenia” dwie decyzje produktowe, których nie
   powinien zgadywać ani recenzent, ani agent: czy lista ma reagować na
   zmiany spoza programu i co dokładnie znaczy „bezpieczny zapis”
   (kopia zapasowa, ponawianie). Obie są powiązane z pięcioma zdaniami
   w `README.md`.
9. Nie zmieniłem zasady: w specyfikacji nie ma nazw plików z kodem, klas
   ani bibliotek. Drugi przegląd potwierdził brak wycieków.
