# Refundator – instrukcja

Refundator pokazuje, czy lek jest na liście leków refundowanych (obwieszczenie Ministra Zdrowia) i w jakich zakresach. Program ma charakter informacyjny – wiążąca jest treść obwieszczenia.

## Spis treści
1. [Instalacja](#1-instalacja)
2. [Pierwsze uruchomienie – pobranie danych](#2-pierwsze-uruchomienie--pobranie-danych)
3. [Wyszukiwanie](#3-wyszukiwanie)
4. [Karta leku](#4-karta-leku)
5. [Programy lekowe, chemioterapia i kody ICD-10](#5-programy-lekowe-chemioterapia-i-kody-icd-10)
6. [Leki spoza listy, ChPL, ulotki i zamienniki](#6-leki-spoza-listy-chpl-ulotki-i-zamienniki)
7. [Nowe obwieszczenia](#7-nowe-obwieszczenia)
8. [Korekty – sprostowania i obwieszczenia zmieniające](#8-korekty--sprostowania-i-obwieszczenia-zmieniające)
9. [Kody uprawnień](#9-kody-uprawnień)
10. [Wygląd – motywy i rozmiar czcionki](#10-wygląd--motywy-i-rozmiar-czcionki)
11. [Praca bez internetu](#11-praca-bez-internetu)
12. [Dane, aktualizacja programu i odinstalowanie](#12-dane-aktualizacja-programu-i-odinstalowanie)
13. [Skróty klawiszowe](#13-skróty-klawiszowe)

---

## 1. Instalacja
1. Pobierz `Refundator-…-instalator.exe` z [Wydania](../../releases/latest).
2. Uruchom instalator. Jeśli Windows pokaże „System Windows ochronił ten komputer”, kliknij **„Więcej informacji” → „Uruchom mimo to”** (program nie ma płatnego podpisu cyfrowego).
3. Zaakceptuj licencję i wskaż folder (domyślnie `%LOCALAPPDATA%\Programs\Refundator`). Uprawnienia administratora nie są potrzebne.

Instalator tworzy skróty na pulpicie i w menu Start (tam również „Licencje i składniki”). Przy uruchamianiu programu widać ekran startowy z postępem.

## 2. Pierwsze uruchomienie – pobranie danych
Przy pierwszym uruchomieniu baza jest pusta. Wybierz **Plik → Aktualizuj ze strony MZ** (Ctrl+U):

- okno pokazuje listę obwieszczeń ze strony Ministerstwa Zdrowia – na jaki dzień, z jakiego dnia, czy obowiązuje, czy jest już w programie i ile ma korekt,
- zaznaczone jest obwieszczenie **obowiązujące dziś** – kliknij **„Pobierz i ustaw jako bieżące”**.

Program pobiera załącznik xlsx z wykazem, archiwa załączników programów lekowych (B) i chemioterapii (C) oraz korekty PDF, a następnie je importuje (kilkanaście sekund). Pliki zapisuje w `%LOCALAPPDATA%\Refundator\pobrane`.

Pasek stanu na dole pokazuje, na jaki dzień jest bieżące obwieszczenie (szczegóły w dymku).

## 3. Wyszukiwanie
Wpisz w pole wyszukiwania:

| Co wpisać | Przykład | Co program znajdzie |
|---|---|---|
| nazwę handlową | `Xarelto`, `metformax 500` | leki o tej nazwie (wystarczy początek, wielkość liter i polskie znaki bez znaczenia) |
| substancję czynną | `rivaroxabanum`, `metformina` | substancja po łacinie; polską nazwę program znajdzie przez grupę limitową |
| numer GTIN | `05909990893423` | konkretne opakowanie |
| kod ICD-10 | `M31.3`, `m 31,3`, `C50.9`, `F33` | leki z programów lekowych i chemioterapii, których załącznik obejmuje kod (dokładnie, całą kategorią, podkodem albo zakresem), oraz leki apteczne, w których treści wskazania kod jest wpisany wprost |
| kod ATC | `C10AA05`, `b01af` | leki z danej grupy ATC (wymaga Rejestru Produktów Leczniczych – rozdział 6) |
| nazwę choroby | `łuszczyca stawowa`, `miastenia` | leki z programów, których kody ICD-10 mają taką nazwę w urzędowym słowniku, oraz leki apteczne, w których treści wskazania pada to słowo |

Wyniki wyszukiwania po chorobie pojawiają się w osobnej grupie **„Według choroby”**, a przy każdym leku widać, skąd pochodzi dopasowanie (np. „B.35. L40.5 Łuszczyca stawowa” albo „wskazanie: …”). Szukane słowa i kody są podświetlone na karcie leku.

Gdy nic nie pasuje, program wyraźnie pokazuje **„NIE MA NA LIŚCIE”**.

Uwaga: wskazania leków aptecznych opisane w obwieszczeniu słowami (np. „Cukrzyca”) nie mają kodów ICD-10 – program ich nie dopisuje. Takie leki znajdziesz po nazwie choroby (treść wskazania).

## 4. Karta leku
Po wybraniu leku z listy po prawej stronie pojawia się jego karta:

- **Nagłówek** – nazwa, substancja, moc, postać, kod ATC i podmiot odpowiedzialny oraz przyciski **Charakterystyka (ChPL)**, **Ulotka** i **Zamienniki** (po pobraniu Rejestru Produktów Leczniczych – rozdział 6).
- **Zakres refundacji** – część wykazu (A1 apteka, A2 środki spożywcze, A3 wyroby medyczne, B program lekowy, C chemioterapia) i grupa limitowa. Opakowania o identycznym zakresie (np. oryginał i jego importy równoległe) są zebrane razem – zakres widać raz. Jeśli opakowania mają w tej samej części kilka zakresów z różną odpłatnością, każdy jest osobno („zakres refundacji 1 z 2”).
- **Tabela opakowań** pod zakresem – opakowanie i GTIN, podmiot (oryginał albo import równoległy, z linkiem do ulotki importu), poziom odpłatności, dopłata pacjenta, cena detaliczna, kategoria dostępności i oznaczenia **S**, **DZ**, **C**, F2 (technologia o wysokim poziomie innowacyjności), G1/G2 (lek wytwarzany w Polsce). Opakowania są ułożone od najniższej dopłaty, najniższa jest wyróżniona na zielono.
- **▸ Szczegóły decyzji** – po kliknięciu: numer LP, limit finansowania, termin wejścia w życie i okres obowiązywania decyzji dla każdego opakowania. **▸ Opakowania spoza listy refundacyjnej** – pozostałe opakowania tego leku z rejestru (także importy, których nie ma w obwieszczeniu).
- **Zakres wskazań** – każde wskazanie osobno (oznaczenia &lt;1&gt;, &lt;2&gt;… jak w obwieszczeniu), także wskazania pozarejestracyjne. Przy każdym wskazaniu znaczki **S / DZ / C** – uprawnienie obejmuje to wskazanie. Kliknięcie znaczka otwiera opis uprawnienia.

### Uwagi listy DZ
Lista DZ (bezpłatne leki do 18 lat) potrafi zawęzić uprawnienie do części wskazań („dotyczy wyłącznie wskazania…”). Przy znaczku DZ opakowania pojawia się wtedy:
- **ⓘ** – uwagi zawężają DZ do części wskazań (zgodnie z treścią wskazań),
- **⚠** – uwagi zawierają fragmenty, których nie ma we wskazaniach.

Najedź na ikonę, żeby zobaczyć opis; kliknij, żeby porównać uwagi i wskazania obok siebie (z podświetlonymi różnicami).

## 5. Programy lekowe, chemioterapia i kody ICD-10
Dla leków z części B i C karta pokazuje załączniki, do których odwołuje się obwieszczenie, każdy z własnym terminem i okresem decyzji:

- **Programy lekowe (B):** tytuł programu i jego części z kodami ICD-10 oraz **nazwami chorób** z urzędowego słownika ICD-10. Kody spoza polskiej ICD-10 (np. E78.01) mają nazwę kategorii nadrzędnej z adnotacją.
- **Chemioterapia (C):** rozpoznania z kodem, nazwą i dodatkowymi warunkami („w przypadku: …”). Przy długich listach – link „pokaż wszystkie rozpoznania” z filtrem.
- Najedź na kod, żeby zobaczyć jego nazwę; **kliknij kod**, żeby wyszukać wszystkie leki z tym kodem.
- Link **„pełny opis programu”** (B) albo **„pełna treść załącznika”** (C) otwiera treść załącznika: kryteria kwalifikacji i wyłączenia, dawkowanie, badania – z wyszukiwaniem w tekście (Enter – następne wystąpienie) i przyciskiem **„Otwórz oryginał (Word)”**. Automatyczna numeracja punktów z Worda może nie być odwzorowana – w razie wątpliwości otwórz oryginał.

## 6. Leki spoza listy, ChPL, ulotki i zamienniki
Program korzysta też z **Rejestru Produktów Leczniczych** (Centrum e-Zdrowia) – wykazu wszystkich leków dopuszczonych do obrotu w Polsce. Pobierz go raz: **Plik → Pobierz Rejestr Produktów Leczniczych** (ok. 17 MB) albo link na pasku nad wyszukiwarką. Później program odświeża go razem z obwieszczeniem, gdy dane mają co najmniej 7 dni (stan rejestru widać w oknie aktualizacji i w dymku na pasku stanu).

- **Leki spoza listy refundacyjnej** pojawiają się w wynikach w osobnej grupie **„Spoza listy refundacyjnej”** – z mocą, postacią i kategorią dostępności (Rp – na receptę, OTC – bez recepty, Rpz, Rpw, Lz). Ich karta pokazuje **„NIE MA NA LIŚCIE REFUNDACYJNEJ”** (żadne opakowanie – numer GTIN – nie występuje w obwieszczeniu), dane z rejestru i opakowania.
- **Kod ATC:** wpisz np. `C10AA05` albo `B01AF`, żeby znaleźć leki z danej grupy – z listy i spoza niej.
- Na karcie **leku refundowanego** dane z rejestru są wplecione w kartę (rozdział 4): kod ATC i podmiot w nagłówku, podmiot i kategoria dostępności w tabeli opakowań, pozostałe opakowania w sekcji „Opakowania spoza listy refundacyjnej”.
- **Charakterystyka (ChPL)** i **Ulotka** – kliknij, program pobierze dokument i otworzy go w przeglądarce PDF (kopia jest przechowywana 30 dni). Dla leków dopuszczonych centralnie w Unii Europejskiej dokument pochodzi z Europejskiej Agencji Leków – jeden plik z ChPL i ulotką dla wszystkich mocy; jeśli go nie ma, program zaproponuje wyszukiwarkę EMA. Dla leków z importu równoległego rejestr udostępnia tylko ulotkę.
- **Zamienniki** – leki o tej samej substancji (nazwie powszechnie stosowanej) i mocy, najpierw o tej samej postaci; przy refundowanych – część wykazu, poziom odpłatności i dopłata dla każdego opakowania. Kliknięcie nazwy otwiera kartę leku. O zamianie w aptece decyduje farmaceuta – lista jest pomocnicza.

## 7. Nowe obwieszczenia
Obwieszczenia ukazują się co kwartał (na 1 stycznia, kwietnia, lipca i października), zwykle kilka tygodni wcześniej.

- Przy uruchomieniu program **sprawdza stronę MZ w tle** (można to wyłączyć: Plik → Sprawdzaj aktualizacje przy uruchomieniu). Pasek nad wyszukiwarką informuje o nowym obowiązującym obwieszczeniu, o obwieszczeniu ogłoszonym na kolejny kwartał i o nowych korektach.
- Ogłoszone obwieszczenie można **pobrać wcześniej** – gdy wejdzie w życie, program **sam ustawi je jako bieżące** i o tym poinformuje.
- W oknie aktualizacji (Ctrl+U) możesz też wrócić do innego pobranego obwieszczenia („Ustaw jako bieżące”).

## 8. Korekty – sprostowania i obwieszczenia zmieniające
Ministerstwo publikuje korekty obwieszczeń tylko w PDF. Program pobiera je razem z obwieszczeniem i – dopóki ich nie przejrzysz – **ostrzega na pasku**, że dane ich nie uwzględniają.

Otwórz **Plik → Korekty obwieszczenia** (Ctrl+K) albo link „Przejrzyj i zatwierdź…”:

1. Wybierz korektę z listy. Program odczytuje PDF i pokazuje proponowane zmiany pogrupowane według operacji: skreślenie, dodanie, nowe brzmienie, poprawka pola, nowe brzmienie załącznika.
2. Przy każdej zmianie widać stan: **✓ gotowe**, **⚠ wymaga uwagi**, **✖ nie można zastosować**, **= już uwzględnione**, **ⓘ informacja**. Po prawej – szczegóły: zdanie z PDF oraz porównanie „jest w programie / według korekty”.
3. Każda zmiana jest sprawdzana numerem LP i GTIN. Gdy numeracja LP w PDF różni się od wykazu, program dopasowuje opakowanie po GTIN i to zaznacza. W „poprawia się <pole>” zmieniane jest tylko to pole.
4. Zaznacz zmiany i kliknij **„Zastosuj zaznaczone”** (przy ⚠ sprawdź ze źródłem – **„Otwórz PDF”**). Korektę bez zmian do wprowadzenia oznacz **„Oznacz jako przejrzaną bez zmian”**.
5. Zastosowane zmiany widać na karcie leku: **✖ Skreślono**, **＋ Dodano**, **✎ Zmieniono** (pole: było → jest) z linkiem do PDF korekty; skreślone leki są na liście wyników oznaczone na czerwono.
6. Każdą zastosowaną zmianę można **cofnąć** (lista na dole okna korekt → „Cofnij zaznaczoną zmianę”).

Dokumenty spoza danych programu (np. „Podstawy limitu”, ceny zbytu netto) są pokazywane tylko informacyjnie.

## 9. Kody uprawnień
Zakładka **„Kody uprawnień”** opisuje 10 kodów uprawnień dodatkowych pacjenta (S, DZ, C, IB, WE, IW, ZK, PO, AZ, WP): kogo dotyczą, zakres, wymagany dokument, podstawę prawną i to, czy farmaceuta może uzupełnić kod na recepcie. Kody S, DZ i C zależą od konkretnego leku i są widoczne na karcie leku; pozostałe wynikają z ustaw.

## 10. Wygląd – motywy i rozmiar czcionki
- **Widok → Motyw jasny / Motyw ciemny / Wysoki kontrast.** Wysoki kontrast (czarne tło, biały tekst, żółte wyróżnienia, grubsze ramki) jest przeznaczony dla osób słabowidzących.
- **Rozmiar czcionki:** Widok → Powiększ / Pomniejsz / Domyślny rozmiar, skróty Ctrl+= / Ctrl+− / Ctrl+0, Ctrl+kółko myszy na karcie leku albo przyciski **A− / A+** na pasku stanu (9–24 pt, domyślnie 12 pt).

Wybór motywu i rozmiaru jest zapamiętywany.

## 11. Praca bez internetu
Bez dostępu do sieci można zaimportować pliki pobrane wcześniej ze strony MZ:
- **Plik → Importuj obwieszczenie z pliku (xlsx)** – plik `…_zalacznik_do_obwieszczenia.xlsx`,
- **Plik → Importuj załączniki B/C z pliku (7z/zip)** – archiwa `Programy_lekowe_RRRR-MM` i `Chemioterapia_RRRR-MM`,
- **Plik → Importuj Rejestr Produktów Leczniczych z pliku (csv)** – plik CSV rejestru (rejestry.ezdrowie.gov.pl → Rejestr Produktów Leczniczych → eksport CSV albo dane.gov.pl, zbiór 397).

Import jest ścisły: jeśli układ pliku różni się od oczekiwanego, program przerywa import i nic nie zapisuje. Uwagi z importu: **Plik → Raport importu**.

## 12. Dane, aktualizacja programu i odinstalowanie
- Baza danych i pobrane pliki: `%LOCALAPPDATA%\Refundator`. Ustawienia (motyw, czcionka): rejestr użytkownika.
- **Nowa wersja programu (od 1.2.0) instaluje się sama:** przy uruchomieniu program sprawdza wydania na GitHubie; gdy jest nowsza wersja, pobiera instalator (postęp na ekranie startowym), sprawdza jego sumę kontrolną, informuje o aktualizacji (szczegóły – „Pokaż szczegóły”: co nowego), instaluje ją i uruchamia się ponownie. Dane i ustawienia zostają. Bez internetu program uruchamia się normalnie. Automatyczną aktualizację można wyłączyć: **Plik → Aktualizuj program automatycznie**; ręcznie: **Pomoc → Sprawdź aktualizacje programu**.
- Wersje 1.0.0 i 1.1.0 nie aktualizują się same – pobierz instalator z [Wydania](../../releases/latest) i uruchom; zainstaluje się w miejsce poprzedniej, dane zostaną.
- **Odinstalowanie:** Ustawienia Windows → Aplikacje → Refundator albo menu Start → Refundator → „Odinstaluj Refundator”. Dane w `%LOCALAPPDATA%\Refundator` zostają – można je usunąć ręcznie.

## 13. Skróty klawiszowe
| Skrót | Działanie |
|---|---|
| Ctrl+U | Aktualizuj ze strony MZ |
| Ctrl+K | Korekty obwieszczenia |
| Ctrl+O | Importuj obwieszczenie z pliku |
| Ctrl+Shift+O | Importuj załączniki B/C z pliku |
| Ctrl+= / Ctrl+− / Ctrl+0 | Powiększ / pomniejsz / domyślny rozmiar czcionki |
| Ctrl+kółko myszy | Rozmiar czcionki (na karcie leku i w zakładce uprawnień) |
