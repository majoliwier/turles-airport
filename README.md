# EDA zgłoszeń kolizji ze zwierzętami

Projekt zawiera eksploracyjną analizę danych z pliku `database.csv`. Każdy wiersz
reprezentuje zgłoszenie; szczegółowe znaczenie kodów i jednostek wymaga
zewnętrznego słownika danych, którego nie ma w tym zbiorze.

## Struktura

```text
.
├── data/
│   └── database.csv       # oryginalne dane wejściowe
├── eda.ipynb              # analiza i wizualizacje
├── pyproject.toml         # zależności projektu
├── uv.lock                # zablokowane wersje zależności
└── .python-version        # wersja Pythona dla uv
```

## Uruchomienie

Potrzebne jest [uv](https://docs.astral.sh/uv/). W katalogu projektu:

```powershell
uv sync
uv run jupyter lab
```

Otwórz `eda.ipynb` i uruchom komórki po kolei. W VS Code wybierz kernel
Pythona ze środowiska `.venv`. Notatnik szuka danych względem katalogu
projektu, dlatego uruchom Jupyter z jego katalogu głównego.
Notatnik zawiera angielskie opisy, macierz korelacji oraz przykłady zgłoszeń
dotyczących m.in. żółwi, aligatorów, węży i niedźwiedzi.
Sekcja żółwi pokazuje wszystkie pasujące zgłoszenia z pełnego zbioru, niezależnie
od analizy korelacji. `turtle_reports` przechowuje wszystkie ich kolumny.
Analiza żółwi porównuje lata i stany oraz pokazuje udział zgłoszeń o żółwiach
wśród wszystkich zgłoszeń w poszczególnych latach.
Obejmuje też lotniska, sezonowość, zmiany zgłoszonych gatunków i jakość danych
w czasie. Niepełne lata i mała liczba zgłoszeń ograniczają porównywalność.

## Ograniczenia

- Liczba zgłoszeń nie jest miarą ryzyka kolizji: brak danych o liczbie operacji
  lotniczych, zmianach raportowania i kompletności poszczególnych lat.
- Brak wartości nie oznacza zera. W szczególności nie należy traktować pustych
  pól dotyczących ofiar i rannych jako potwierdzenia ich braku.
- Wykresy udziału uszkodzeń wykorzystują wyłącznie rekordy z wartością 0 lub 1
  w kolumnie `Aircraft Damage`. Kody i jednostki nie są interpretowane bez
  słownika danych.
- Macierz korelacji Pearsona obejmuje wszystkie wiersze z kompletnymi wartościami
  `Height`, `Speed` i `Distance`; pominięcie braków może wpływać na wyniki.
  `complete_records` zawiera te same wiersze z wszystkimi
  kolumnami źródłowymi; w pozostałych kolumnach mogą występować braki.
