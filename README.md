# Minecraft — Wyzwanie Wiedzy

Nieoficjalny karciany quiz wiedzy o Minecraft w języku polskim. Gra zawiera 72 pytania z dziewięciu kategorii i działa w całości w przeglądarce, również offline.

## Uruchomienie

1. Otwórz folder z grą.
2. Kliknij dwukrotnie `index.html` lub otwórz go za pomocą przeglądarki.
3. Wybierz talię i kliknij **Rozpocznij przygodę**.

Potrzebna jest współczesna przeglądarka z włączonym JavaScript. Instalacja, serwer, konto i połączenie z internetem nie są wymagane. Grę można przenieść na inny komputer, kopiując sam plik `index.html`.

## Warianty rozgrywki

| Talia | Liczba kart | Maksymalny wynik |
| --- | ---: | ---: |
| Szybka przygoda | 5 | 5 punktów |
| Wyprawa odkrywcy | 15 | 15 punktów |
| Wyzwanie mistrza | 30 | 30 punktów |

## Zasady

- Każda karta zawiera jedno pytanie i trzy odpowiedzi: A, B i C. Tylko jedna jest prawidłowa.
- Zaznaczenie odpowiedzi nie zatwierdza wyboru. Możesz zmieniać go do kliknięcia **Sprawdź odpowiedź**.
- Poprawna odpowiedź daje 1 punkt, błędna 0 punktów. Nie ma punktów ujemnych.
- Po sprawdzeniu wybór zostaje zablokowany. Prawidłowa odpowiedź jest oznaczona kolorem zielonym, symbolem ✓ i tekstem. Błędny wybór ma kolor czerwony, symbol ✕ i opis.
- Po każdej odpowiedzi pojawia się krótkie wyjaśnienie. Kliknij **Następna karta**, aby kontynuować, lub **Zobacz wynik** po ostatniej karcie.
- Nie ma limitu czasu ani automatycznego przechodzenia między kartami.

Pytania są losowane bez powtórzeń w obrębie jednej partii. Kolejność odpowiedzi również jest losowa. W następnych partiach mogą pojawić się pytania znane z poprzednich rozgrywek.

## Wyniki i kolejna partia

Ekran wyniku pokazuje liczbę punktów, procent poprawnych odpowiedzi zaokrąglony do liczby całkowitej oraz przyjazny komunikat. Dziennik odkryć zawiera wszystkie rozegrane pytania, odpowiedzi gracza, prawidłowe rozwiązania i wyjaśnienia.

- **Zagraj ponownie** losuje nową partię o tej samej liczbie kart i zeruje wynik.
- **Wybierz inną talię** wraca do ekranu startowego.
- Przy wyniku co najmniej 80% pojawia się krótkie kwadratowe konfetti, o ile użytkownik nie ograniczył animacji w ustawieniach urządzenia lub przeglądarki.

## Sterowanie i dostępność

Gra obsługuje mysz, dotyk i klawiaturę:

- **Tab / Shift+Tab** — przechodzenie między elementami sterującymi.
- **Strzałki** — zmiana zaznaczonej talii lub odpowiedzi w grupie.
- **Spacja** — zaznaczenie opcji lub aktywowanie przycisku z fokusem.
- **Enter** — aktywowanie przycisku z fokusem.

Strona ma widoczny fokus, semantyczne formularze, komunikaty dla czytników ekranu i układ dopasowany do telefonu, tabletu oraz komputera. Informacja o poprawności odpowiedzi nie opiera się wyłącznie na kolorze. Preferencja `prefers-reduced-motion` wyłącza animacje i przejścia.

## Prywatność i działanie offline

Stan rozgrywki jest przechowywany wyłącznie w zmiennych JavaScript. Odświeżenie lub zamknięcie strony usuwa bieżącą partię i wynik.

Gra nie korzysta z backendu, logowania, cookies, analityki, `localStorage`, `sessionStorage` ani IndexedDB. Nie wysyła żądań sieciowych. Nie pobiera bibliotek, fontów, grafik ani innych zasobów z internetu.

## Pliki i technologia

```text
Gra Minecraft/
├── index.html   # kompletna gra: HTML, CSS, JavaScript i autorska ilustracja SVG
└── README.md    # instrukcja i opis projektu
```

Cały kod gry znajduje się w jednym pliku `index.html`. Projekt nie wymaga frameworków, menedżera pakietów, kompilacji ani instalowania zależności. Krajobraz wykonano w SVG, a pozostałe dekoracje i animacje w CSS.

## Edycja i dodawanie pytań

Otwórz `index.html` w edytorze tekstu obsługującym UTF-8 i znajdź tablicę `const QUESTIONS`. Każdy wpis ma następującą strukturę:

```javascript
{
  "id": "mc-073",
  "category": "Crafting",
  "question": "Ile patyków otrzymasz z dwóch desek ułożonych pionowo?",
  "answers": ["4", "2", "8"],
  "correctIndex": 0,
  "explanation": "Dwie deski ułożone jedna nad drugą w siatce craftingu dają cztery patyki."
}
```

Powyższy wpis jest przykładem do samodzielnego dodania; gotowa gra zawiera 72 pytania.

- Używaj unikalnego `id` i niepowtarzającej się treści pytania.
- Podawaj dokładnie trzy różne odpowiedzi i tylko jedną prawidłową.
- `correctIndex` wskazuje pozycję poprawnej odpowiedzi w źródłowej tablicy `answers`: `0` to pierwsza, `1` druga, `2` trzecia. Gra sama zachowuje właściwe przypisanie po przetasowaniu.
- Dostępne kategorie: `Moby`, `Surowce`, `Narzędzia`, `Crafting`, `Biomy`, `Budowanie`, `Przetrwanie`, `Nether`, `End`. Nowa kategoria wymaga także dodania jej ikony w `ICONS`.
- Zachowaj poprawne przecinki między wpisami i zapisz plik jako UTF-8.
- Utrzymuj co najmniej 30 pytań, aby najdłuższa talia działała poprawnie. Dla różnorodności zalecane jest minimum 60.
- Po zmianie liczby pytań lub kategorii zaktualizuj również ich liczniki na ekranie startowym i opis w metadanych strony.
- Sprawdzaj mechaniki wspólne dla Java i Bedrock. Unikaj treści zależnych od modów, eksperymentalnych funkcji lub konkretnej wersji gry.

## Weryfikacja przygotowanej wersji

Przed przekazaniem gry wykonano testy automatyczne w Chrome obejmujące:

- Pełne partie po 5, 15 i 30 kart, wynik mieszany, zerowy i maksymalny.
- Zmianę wyboru przed sprawdzeniem i blokadę odpowiedzi po zatwierdzeniu.
- Ochronę przed ponownym naliczeniem punktu za tę samą kartę.
- Pasek postępu, końcowe podsumowanie i obliczanie procentu odpowiedzi.
- Ponowną grę, powrót do wyboru talii i reset po odświeżeniu.
- 200 losowych talii: brak powtórzeń pytań i poprawność przypisania odpowiedzi po tasowaniu.
- Obsługę klawiatury, układy o szerokości 360, 390 i 768 pikseli oraz widok komputerowy.
- Konfetti i respektowanie ograniczenia animacji.
- Uruchomienie pliku lokalnego przy wyłączonym dostępie do sieci, brak zewnętrznych żądań i brak błędów JavaScript podczas testów.

Po edycji warto powtórzyć powyższe scenariusze w przeglądarce, w której gra będzie używana.

## Informacja fanowska

Nieoficjalna gra fanowska. Nie jest powiązana z Mojang ani Microsoft.

Projekt nie korzysta z oficjalnego logo, pobieranych tekstur ani zewnętrznych grafik Minecraft.
