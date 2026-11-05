<img src="zrzuty/ikona.png" width="72" align="right" alt="">

# Refundator

*Lista leków refundowanych – szybko i dokładnie.*

Refundator to program dla Windows, który odpowiada na pytanie: **czy lek jest na liście refundacyjnej Ministra Zdrowia, a jeśli tak – w jakich wskazaniach, z jaką odpłatnością i z jakimi uprawnieniami.** Dane pobiera prosto z obwieszczeń publikowanych na [gov.pl](https://www.gov.pl/web/zdrowie/obwieszczenia-ministra-zdrowia-lista-lekow-refundowanych), razem z załącznikami programów lekowych i chemioterapii oraz korektami (sprostowaniami i obwieszczeniami zmieniającymi).

![Karta leku](zrzuty/karta-leku.png)

## Co potrafi
- **Wyszukiwanie** po nazwie handlowej, substancji czynnej (także po polsku), numerze GTIN, **kodzie ICD-10** (np. `M31.3`) i **nazwie choroby** (np. „łuszczyca stawowa”).
- **Karta leku:** każdy zakres refundacji osobno – poziom odpłatności, dopłata pacjenta, cena, limit, grupa limitowa, termin i okres decyzji.
- **Uprawnienia S, DZ i C** (65+, do 18 lat, ciąża) przy każdym wskazaniu, którego dotyczą – z dopasowaniem „Uwag” listy DZ i ostrzeżeniem, gdy uwagi nie zgadzają się z treścią wskazań.
- **Programy lekowe i chemioterapia:** kody ICD-10 z załączników wraz z nazwami chorób, warunkami i pełnym opisem programu (kryteria kwalifikacji, dawkowanie, badania).
- **Korekty obwieszczeń** odczytywane z PDF i pokazywane **do zatwierdzenia** – każdą zmianę można sprawdzić ze źródłem i cofnąć.
- **Aktualizacja jednym kliknięciem** ze strony Ministerstwa Zdrowia; nowe obwieszczenie program sam ustawia jako bieżące, gdy wchodzi w życie.
- **Kody uprawnień dodatkowych** (S, DZ, C, IB, WE, IW, ZK, PO, AZ, WP) – kogo dotyczą, zakres, podstawa prawna.
- **Czytelność:** motyw jasny, ciemny i **wysoki kontrast**, regulowany rozmiar czcionki.

| Szukanie po chorobie | Korekty do zatwierdzenia |
|---|---|
| ![Szukanie po chorobie](zrzuty/szukanie-po-chorobie.png) | ![Korekty](zrzuty/korekty.png) |

## Pobierz
Najnowsza wersja: **[Wydania → Latest](../../releases/latest)** – plik `Refundator-…-instalator.exe`.

Przy pierwszym uruchomieniu instalatora Windows może pokazać okno „System Windows ochronił ten komputer” (program nie ma płatnego podpisu cyfrowego) – kliknij **„Więcej informacji” → „Uruchom mimo to”**. Instalacja nie wymaga uprawnień administratora. Sumy kontrolne SHA-256 są podane przy każdym wydaniu.

## Instrukcja
[INSTRUKCJA.md](INSTRUKCJA.md) – instalacja, pobranie danych, wyszukiwanie, karta leku, korekty, kody uprawnień, ustawienia widoku.

## Ważne
Program ma charakter **wyłącznie informacyjny**. Wiążąca jest treść obwieszczeń Ministra Zdrowia oraz przepisów prawa. Program nie przypisuje kodów ICD-10 do wskazań, których obwieszczenie nie opisuje kodami – pokazuje urzędowe brzmienie, a wszystko, czego nie da się odczytać jednoznacznie, wyraźnie oznacza.

## Prywatność
Program nie zbiera i nie wysyła żadnych danych. Łączy się wyłącznie ze stroną **www.gov.pl**, żeby sprawdzić i pobrać obwieszczenia (sprawdzanie przy uruchomieniu można wyłączyć w menu Plik). Pobrane pliki i baza danych zostają na Twoim komputerze (`%LOCALAPPDATA%\Refundator`).

## Wymagania
Windows 10 lub 11 (64-bit).

## Licencja i źródła danych
Program: [LICENCJA.txt](LICENCJA.txt) – bezpłatny do użytku, wszelkie prawa zastrzeżone. Program zawiera biblioteki open source (m.in. Qt/PySide6 na licencji LGPL) – ich wykaz i licencje są w folderze `licencje` po instalacji; kod źródłowy bibliotek LGPL-2.1 jest dołączony do każdego wydania.

Nazwy kodów ICD-10: Rejestr Systemów Kodowania, Centrum e-Zdrowia, [dane.gov.pl](https://dane.gov.pl/pl/dataset/27), licencja [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.pl).

To repozytorium zawiera tylko wydania i instrukcję.
