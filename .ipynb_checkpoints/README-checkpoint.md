# Sales forecasting

### Treść polecenia:
Sprzedawca A handluje asortymentem w kategorii Drobne AGD. Sprzedawca A ma już historię sprzedaży dla około 200 wystawionych produktów. Biorąc pod uwagę parametry historycznych aukcji sprzedawcy A oraz agregaty danych dotyczące sprzedaży produktów na platformie allegro.pl przed wystawieniem ich przez sprzedawcę A,  należy zbudować model prodnozujący 30 dniową sprzedaż(Sztuk_sprzedanych_pierwsze_30_dni). 	


### Plan projektu

1. **Data Cleaning** 
- Usunięcie kolumn bezwartościowych
- Konwersja zmiennych kategorycznych na liczbowe
- Usunięcie braków w danych
- Tworzenie nowych zmiennych (feature engineering)

2. **Feature Selection**
- Usunięcie zmiennych mocno skorelowanych
- Selekcja zmiennych przy użyciu lasu losowego
- Weryfikacja rozkładów zmiennych względem zmiennej objaśnianej

3. **Modele liniowe**
- Próba pozbycia się obserwacji odstających
- Zbliżenie rozkładu zmiennych do normalnego
- **Regresja liniowa** (z/bez transformacją y)
- **Regresja grzbietowa** (z/bez transformacji y)
- Weryfikacja wyników 

4. **Modele bazowane na drzewie**
- Optymalizacja hiper-parametrów drzewa (walidacja krzyżowa, wyszukiwanie siatkowe)
- Budowa i wizualizacja **drzewa decyzyjnego**
- Optymalizacja hiper-parametrów lasów losowych (walidacja krzyżowa, wyszukiwanie siatkowe)
- Model **lasów losowych**
- Optymalizacja hiper-parametrów **XGBoost** (walidacja krzyżowa, wyszukiwanie siatkowe)
- Model XGboost
- Weryfikacja wyników


### Podsumowanie

Niestety **żaden z uzyskanych rezultatów nie jest satysfakcjonujący**. W przypadku **metod liniowych** najlepszy uzyskany wynik to **RMSE=44** w przypadku regresji grzbietowej bez transformacji zmiennej objaśnianej. W przypadku **lasu losowego** udało się uzyskać **RMSE=40**, co było najwyższym wynikiem spośród modeli bazowanych na drzewach. Uzyskane wyniki nie pozwalają na praktyczne używanie modeli do celów predykcyjnych - są tylko nieznacznie lepsze od **predykcji średnią** która uzyskuje **RMSE=50**.

Kolejnymi krokami, które moglibyśmy poczynić w celu poprawy ich jakości byłoby **zwiększenie wolumenu danych**. 202 obserwacje to bardzo mała próba w przypadku której budowanie zaawansowanych modelów mija się praktycznie z celem. 
Warto zwrócić uwagę, że pomineliśmy cenne informacje z kolumn **kategoria i marka**. Prawdopodobnie stosując OneHotEncoding albo inną transformację i wrzucając te zmienne do modelu usyskalibyśmy znacznie lepsze wyniki. Niestety wystąpiłoby wtedy bardzo duże ryzyko overfittu. W przypadku tak małego zbioru danych **nie bylibyśmy w stanie go zwerfyfikować**. Stąd jest duża szansa, że zwiększenie liczby obserwacji zaaowocowałoby dużo lepszymi rezultatami, lecz w przypadku zadanego zbioru ryzyko takiego podejścia jest zbyt duże.