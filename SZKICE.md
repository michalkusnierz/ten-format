# Szkice 10 Format: instrukcja dla agenta

Ten plik czyta zadanie, które co godzinę obsługuje zgłoszenia z formularza na stronie 10 Format.

## Skąd brać zgłoszenia

Zgłoszenia z Web3Forms trafiają na tenformat@gmail.com i są przekierowane na Gmaila Michała.
Szukaj w Gmailu: `subject:"Zgłoszenie 10 Format" -label:tf-szkic-gotowy -label:tf-pominiete newer_than:7d`.
Każde zgłoszenie ma pola: pakiet, firma, link, miasto, telefon, email, uwagi, branza, landing.

Etykiety Gmail (utwórz, jeśli ich nie ma):
- `tf-szkic-gotowy`: szkic zrobiony, szkic maila czeka na Michała
- `tf-pominiete`: spam, test, brak prawdziwej firmy

## Kiedy pominąć

Pomiń i oznacz `tf-pominiete`, gdy: nazwa firmy albo link wyglądają na test lub spam, linku nie da się otworzyć i nie da się znaleźć firmy w sieci po nazwie i mieście, albo zgłoszenie dotyczy czegoś nielegalnego. Nie odpisuj takim osobom.

Jeśli zgłoszeń w cenie Black Week jest więcej niż wolnych miejsc, i tak rób szkic. Limit 8 dotyczy wpłaconych zaliczek.

## Jak zrobić szkic

1. Zbierz informacje o firmie: otwórz link ze zgłoszenia (WebFetch), poszukaj firmy w sieci po nazwie i mieście (WebSearch): wizytówka Google, strona, Facebook, Instagram, Oferteo, Panorama Firm. Zanotuj: usługi, obszar działania, telefon i adres firmowy, ocenę Google i liczbę opinii, 2–3 krótkie opinie z imieniem autora, kolory logo, bezpośrednie adresy zdjęć z ich strony.
2. Skopiuj `szkic/_szablon/index.html` do `szkic/<kod>-<slug-firmy>/index.html`. `<kod>` to 6 losowych znaków [a-z0-9] (np. `python3 -c "import secrets;print(secrets.token_hex(3))"`), slug bez polskich znaków, małe litery, myślniki.
3. Podmień wszystko oznaczone `{{...}}` w komentarzach. Zasady:
   - Pisz po polsku, konkretnie, językiem właściciela firmy. Zero wymyślonych faktów: liczby, lata działalności, ocena, opinie i adres tylko z prawdziwych źródeł. Jeśli czegoś nie ma, usuń ten element.
   - Bez typowych zwrotów AI: bez „to nie X, to Y”, pytań z odpowiedzią („Efekt? …”), wymuszonych trójek, krótkich dramatycznych zdań, słów kluczowy, kompleksowy, holistyczny, przestrzeń. Bez pauz (—) w zdaniach. Nagłówki zwykłą wielkością liter w treści (CSS i tak robi wersaliki).
   - Paleta z logo lub zdjęć firmy. Zakaz: gradient fiolet→niebieski, tekst z gradientem, glassmorphism, kremowe tło z terakotą.
   - Fonty zostają: Big Shoulders Display + Libre Franklin.
   - Intro pod branżę: klimatyzacja/pompy ciepła zostaje szyba z szablonu (zmień tylko hasło pod temperaturą). Ogrodzenia, kuchnie, detailing: przenieś intro z `../../ogrodzenia/index.html`, `../../kuchnie/index.html`, `../../detailing/index.html` (HTML, CSS i JS intro) i dopasuj tekst do firmy. Inna branża: zostaw tło w kolorze firmy, wejście nazwy firmy literami i usuń canvas szyby.
   - Bonus branżowy: klimatyzacja kalkulator z szablonu; ogrodzenia prosty kalkulator metrów bieżących; kuchnie kalkulator długości zabudowy; detailing wybór pakietu. Inna branża: usuń sekcję.
   - Telefon i adres w szkicu tylko firmowe, publiczne. Nigdy dane osobowe ze zgłoszenia (prywatny mail, prywatny numer).
   - Pasek u góry z „Szkic strony przygotowany przez 10 Format dla firmy …” i przycisk „Chcę tę stronę” zostają. W mailto podmień nazwę firmy w temacie.
   - `<meta name="robots" content="noindex, nofollow">` zostaje.
4. Sprawdź plik: poprawny HTML, brak `{{`, brak pustych `url('')` (usuń puste zdjęcia albo całą sekcję), polskie znaki.
5. Commit i push do `main`: `git add szkic/<folder> && git commit -m "Szkic: <firma>" && git push`. Link: `https://michalkusnierz.github.io/ten-format/szkic/<folder>/` (GitHub Pages publikuje po ~1 minucie).
6. Zrób szkic maila w Gmailu (create_draft, NIE wysyłaj) do adresu ze zgłoszenia:
   - Temat: `Szkic strony dla <firma>`
   - Treść (dopasuj do firmy, krótko, bez zwrotów AI):

```
Dzień dobry,

przygotowaliśmy szkic strony dla <firma>:
<link>

Zrobiliśmy go z <skąd: wizytówki Google / Waszej strony / profilu na Facebooku>. <Jedno zdanie, co w nim jest najciekawszego dla tej firmy, np. kalkulator kosztu ogrzewania dla klientów.>

Jeśli Wam się podoba, odpiszcie „chcę” albo zadzwońcie. Wtedy wystawiamy fakturę zaliczkową na 990 zł netto i w 7 dni roboczych oddajemy gotową stronę pod Waszą domeną. Cena Black Week 1990 zł netto zostaje także po 30 listopada.

Jeśli coś zmienić, napiszcie co, zrobimy drugą wersję.

Zespół 10 Format
tenformat@gmail.com · 794 016 134
```

7. Oznacz wątek zgłoszenia etykietą `tf-szkic-gotowy`.
8. Na koniec przebiegu wyślij Michałowi powiadomienie z listą: firma, link do szkicu, czy coś było niepewne. Jeśli nie było nowych zgłoszeń, nic nie wysyłaj.

## Czego nie robić

- Nie wysyłaj maili do klientów. Tylko szkice maili.
- Nie zmieniaj plików poza `szkic/`.
- Nie używaj zdjęć stockowych udających realizacje firmy.
