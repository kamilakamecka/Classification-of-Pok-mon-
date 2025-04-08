# Grupa projektowa 2

**Data wykonania:** 18.03.2025  
**Data odbioru:**  

## Temat ćwiczenia
Opisanie tematu, bazy danych, założeń i celów projektu

**Imiona i nazwiska:**  
Kamila Kamecka, Tymoteusz Maca, Kacper Mazur

---

## 1. Określenie tematu i celu projektu

Celem projektu jest stworzenie modelu sztucznej inteligencji do klasyfikacji Pokémonów na podstawie ich zdjęć.  
Wykorzystujemy konwolucyjne sieci neuronowe (CNN) z transfer learningiem w PyTorch, aby zapewnić wysoką skuteczność klasyfikacji.  

System obsługuje niejednorodne obrazy w różnych formatach (JPG, JPEG, PNG) i rozmiarach, typu RGB, dlatego uwzględniamy preprocessing (zmiana rozmiaru i normalizacja).  
Możliwe jest dodanie większej liczby zdjęć i/lub klas Pokémonów.

### Oczekiwany wynik

- Model zdolny do klasyfikacji Pokémonów z wysoką dokładnością.  
- System, który w przypadku pewności powyżej 70% zwraca odnośnik do PokeWiki dla danego Pokémona.  
- Jeśli model nie jest pewny, zwraca listę podobnych Pokémonów.  
- Model nie musi działać w czasie rzeczywistym, ale powinien być relatywnie szybki i użyteczny.  
- System może być poszerzany o nowe Pokémony — zdjęcia będą podzielone między odpowiednie foldery (każdy Pokémon posiada swój folder), co umożliwi ponowny trening modelu na rozszerzonym zbiorze danych.  
- Dokumentacja zawierająca analizę wyników oraz wnioski.

---

## 2. Analiza wymagań

### Technologie i narzędzia

- **Język programowania:** Python  
- **Frameworki:** PyTorch, torchvision, Pillow  
- **Platforma kodu:** GitHub  
- **Baza danych:** [Zbiór zdjęć Pokémonów](https://www.kaggle.com/datasets/lantian773030/pokemonclassification?resource=download&fbclid=IwZXh0bgNhZW0CMTEAAR1ZLA05A7VMFZ3NzQkcHmZAx73V7Y2nXmCRx3a2ytd__thmK7Mq2uxRveQ_aem_LpooBBHErJoVdP330QZRtQ)

### Zbiory danych

- **Formaty:** JPG, JPEG, PNG  
- **Rozmiary:** Obrazy są różnej wielkości, wymagają normalizacji  

### Metoda

- Konwolucyjna sieć neuronowa (CNN) z transfer learningiem  
- Ujednolicenie rozmiaru obrazów poprzez preprocessing  
- Możliwe rozdzielczości obrazów: 250x250 lub 500x500 (do ustalenia)

## 3. Przygotowanie danych do obróbki:

Na początku ze względu na niedobór zdjęć w niektórych klasach, dpododawliśmy kolejne zdjecia z grafiki Google, Pinterestu i innych źródeł dodatkowe. Następnie w programie przy użyciu funkcji z biblioteki PIL wczytaliśmy i przekształciliśmy wszytski zdjecia do jednego formatu .jpg. 
Napisane funkcje:

- convert_to_jpg()

Funkcja otwierająca obraz w innym formacie niż jpg, konwertująca do przestrzeni barw RGB i zapisująca do formatu .jpg.

- process_pokemon_folders()

Przetwarzanie całej struktury folderów PokemonData - zlicza ile plików nalezało przekonwertować, a ile pominięto.

- Sekcja do augmentacji i testowy preprocessing:

Treningowe skalowanie. Dzieli dane na Treningowe, Walidacyjne i Testowe po załadowaniu zdjęć z PokemonData.

- Sekcja do wizualizacji danych:

Wizualizacja przykładowych klas ze zdjęciami im odpowiadającymi:

![zdjecia_poke](https://github.com/KmazuR-afk/Pokemon_Classification/blob/main/zdjecia_poke.png)
