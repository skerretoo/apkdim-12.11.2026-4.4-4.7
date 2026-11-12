# 0001 — Format pliku z notatkami

Kontekst: konstytucja, punkt 2, wymaga, żeby notatki dały się otworzyć
w każdym edytorze. W Budowie 2 porównałem cztery sposoby zapisu: JSON,
jeden plik na notatkę, zwykły tekst bez nagłówków i Markdown z nagłówkiem
na każdą notatkę. Najłatwiej czytało się ostatni z nich, także po tygodniu
i przy kilkunastu notatkach.

Decyzja: jeden plik `notatki.md` w folderze programu. Każda notatka to
nagłówek `## RRRR-MM-DD GG:MM — Tytuł`, a pod nim treść, która może mieć
kilka linii. Wpisy oddziela jedna pusta linia. Najnowsza notatka jest na
górze pliku. Plik jest zapisywany w UTF-8. Tytuł może zawierać myślniki;
granicą nagłówka jest pierwsze ` — ` występujące po godzinie.

Odrzucone: JSON — czytelny dla programu, nie dla człowieka w edytorze;
osobny plik na notatkę — folder zamienia się w nieporządek i trudno
policzyć notatki; tekst bez nagłówków — nie da się odróżnić tytułu od
treści ani sprawdzić, gdzie kończy się jedna notatka.

Skutki: format da się sprawdzić gołym okiem, bez uruchamiania programu.
„Najnowsza na górze” wymaga jednak przy każdym zapisie przeczytania całego
pliku i zapisania go od nowa, więc łatwo zgubić ostatni wpis — to miejsce
musi mieć własne kryterium akceptacji. Kolejność wynika wyłącznie
z położenia wpisu w pliku, bo data w nazwie pliku nie występuje.
